#!/bin/bash
page=breadcrumb
page=numbered
# page=empty

cd "$(dirname "$(readlink -f "$0")" )"

i=0
for f in $( find split/ -name \*.html |sort )
do
	g="${f#split/}"
	h="${g%.html}"
	echo
	echo
	# echo "<!-- $g -->"
	echo
	echo
	h=$i
	if [ "$page" = empty ]
	then
		cat "$f"
	elif [ "$page" = breadcrumb -a \
		"$(tail -n 1 < "$f" |sed 's/[	]//g')" = '</div>' ]
	then
		head -n -1 < "$f"
		echo "<div class="'"'"page"'"'">$h</div>"
		echo '</div>'
	elif [ "$page" = numbered -a \
		"$(tail -n 1 < "$f" |sed 's/[	]//g')" = '</div>' ]
	then
		head -n -1 < "$f"
		echo "<div class="'"'"page"'" style="font-size:2rem"'">$i</div>"
		echo '</div>'
		i=$(( i + 1 ))
	else
		cat "$f"
	fi
done > index.html
