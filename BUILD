#!/bin/bash
page=true

cd "$(dirname "$(readlink -f "$0")" )"

for f in $( find split/ -name \*.html |sort )
do
	g="${f#split/}"
	h="${g%.html}"
	echo
	echo
	# echo "<!-- $g -->"
	echo
	echo
	if $page && [ "$(tail -n 1 < "$f" |sed 's/[	]//g')" = '</div>' ]
	then
		head -n -1 < "$f"
		echo "<div class="'"'"page"'"'">$h</div>"
		echo '</div>'
	else
		cat "$f"
	fi
done > index.html
