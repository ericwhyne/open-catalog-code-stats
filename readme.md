These scripts have been broken since the schema extension to support multiple programs.

The new schemas can be found in the new data repository here:
https://github.com/ericwhyne/darpa_open_catalog


Once all the public code repos are cloned into ./code here is an example script to generate stats for each of them. If you can't read this code you shouldn't run it. It will lock up your computer with threads until it completes.

    #!/bin/bash
    mkdir stats
    cd code
    for f in *
    do 
      if [ -d "$f" ]
      then
        mkdir "../stats/$f"
        echo "Generating stats for $f"
        ../gitstats-urk/gitstats "$f" "../stats/$f" & > /dev/null
      fi
    done
