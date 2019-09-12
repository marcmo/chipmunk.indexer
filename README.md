# chipmunk indexer

This project was always intended to be part of the chipmunk log-viewer and now was moved to https://github.com/esrlabs/chipmunk and can now be found in `chipmunk.git/application/apps/indexer`.

this will allow us to more easily maintain automated and consistent builds.

# Changelog

### [0.34.0] - 08/27/2019
  * rename completed
  * added optional parsing of timestamp
  * wip
  * handle wrong AM PM settings
  * rename to extract_posix_timestamp

### [0.33.0] - 08/12/2019
  * when detecting format in file, also report min and max timestamp
  * allow using the append option when concatenating even when out file does not exist
  * limit lines that need to be checked when timespan is queried
  * when creating a regex for a format string check the pre-filled map first
  * added more timeformats to be recognized
  * timestamp recognition more exact

### [0.32.1] - 08/07/2019
  * fix merge/concat command: -s did not write to stdout

### [0.32.0] - 08/07/2019
  * feature: concatenate files
  * wip removed unused arguments
  * wip: concat files

### [0.31.2] - 08/06/2019
  * fix: report correct path in results for discover
  * fix: remove unnecessary quotation marks in json output

### [0.31.1] - 08/06/2019
  * fixed: order of checked regular expressions was incorrect
  * and we did not detect timestamps correctly

### [0.31.0] - 08/06/2019
  * detect time format in file
  * most cases are detected correctly
  * support short month in date stamps
  * better error reporting (with lines when possible)
  * removed unused old parsing
  * do not report same timestamp parsing error so often, collect all

### [0.30.0] - 07/31/2019
  * using humantime package for date formating for improved perfomance
  * added copyright comments

### [0.29.0] - 07/29/2019
  * [](feat): more robust error handling for invalid DLT files
  * [](fix) add missing dlt column markers for some cases

### [0.28.0] - 07/27/2019
  * [](chore): version bump from 0.27.1 => 0.28.0
  * [#362](feat): provide log level distribution for statistics
  * report errors and warnings as json objects

### [0.28.0] - 07/27/2019
  * [#362](feat): provide log level distribution for statistics
  * report errors and warnings as json objects

### [0.27.1] - 07/24/2019
  * [](fix): avoid writing to stderr when not specified

### [0.27.0] - 07/24/2019
  * implemented filtering for app_ids, ecu_ids and context_ids
  * change hash function for merging for better performance
  * support filtering with components
  * added first start of server frontend
  * use criterion for benchmarks
  * convert project to cargo workspace
  * version bump from 0.26.3 => 0.27.0
  * spelling error

### [0.27.0] - 07/22/2019
  * convert project to cargo workspace
  * spelling error

### [0.26.3] - 07/21/2019
  * fix: use correct mapping when filtering out entries
  * added support for listing available components of dlt files

### [0.26.2] - 07/19/2019
  * rearrange tests (integration style tests moved to "tests")
  * add feature flag for running benchmarks so nightly is not required to build
  * fixed filtering by log level

### [0.26.1] - 07/18/2019
  * dlt parser: allow invalid values for some message info fields
  * also: cope with invalid utf-8 encodings
  * enable filter for log level

### [0.26.0] - 07/16/2019
  * loop over parse results instead of using an iterator
  * with an iterator we create too many heap allocations for strings

### [0.25.1] - 07/09/2019
  * remove debug println in dlt parsing

### [0.25.0] - 07/08/2019
  * test merging adb files
  * use current year for timestamp when year is missing
  * also report offending lines (where year was missing)
  * simplify proptest strategies
  * reformat
  * all tests passing with proptests using arbitrary
  * use proptest for regular build...makes things easier
  * generate test cases with proptest for Arguments
  * got rid of reduntancy in TypeInfo (fixed-point)
  * test aribrary arguments

### [0.24.0] - 07/02/2019
  * remove newlines from dlt arguments

### [0.23.0] - 07/01/2019


### [0.22.0] - 07/01/2019
  * support correct delimiters for DLT indexed file
  * added missing line endings for dlt index files

### [0.21.4] - 07/01/2019
  * do not panic on invalid dates to parse
  * more stderr cleanup
  * added win32 build
  * add windows cross build
  * small addition to rakefile

### [0.21.3] - 06/29/2019
  * use stdout instead of stderr for format to regex results

### [0.21.2] - 06/29/2019
  * bugfix: print matching regex for format string to stdout

### [0.21.1] - 06/28/2019
  * fix: merging still printed to stdout even without -v flag

### [0.21.0] - 06/28/2019
  * cleaned up printing to stderr (only done in "-v" verbose mode)
  * DLT support for files now produces valid index files and mapping files
  * reading/writing dlt with constant memory consumption (no matter how
  * big the file)
  * simpler function to index and map
  * get rid of warnings
  * dlt file indexing with tags and mapping file

### [0.20.0] - 06/26/2019
  * DLT: nom parsing of dlt messages
    * added header parsing
    * parsing extended headers
    * parsing string,signed,unsigned,bool arguments
    * fixed point parsing
    * implemented float parsing
    * support for parsing dlt raw arguments
    * parsing correct timestamp in dlt
  * DLT: added Message serialization
    * add type for TypeInfo in Argument
    * serializing signed/unsigned values
    * serializing float values (only support f32 and f64)
    * raw support for serialization
  * DLT: iterator for dlt messages
  * DLT: Display implementation for DLT messages
  * DLT: dlt: accept invalid string format (interpret as UTF8)
  * split tokio functionality away from dlt module
  * testing with proptest
  * fixes #283: no stupid output to stderr
  * error messages
  * working version with tokio codecs

### [0.19.0] - 06/07/2019
  * added basic dlt support
  * read dlt from file stream, write to file sink
  * added support for absolute timestamp in milliseconds
  * add timestamp option to DLT output

### [0.18.1] - 06/05/2019
  * print results of testing format string to stdout instead of stderr;

### [0.18.0] - 06/05/2019

  * for testing a format string you know can use `logviewer_parser format -c format.cfg`
  * the configuration for this has to include the `file` to test, how many lines at max to check,
    and the format specifier
  * result will be the regex we created for this match, the number of matched lines and the number of
    unmatched lines

### [0.17.0] - 06/05/2019
  * removed automatic detection
  * introduced more general detection function
  * based on format strings

### [0.16.0] - 06/05/2019
  * add support for subcommands
    * switch to clap library
  * Note: new command line semantics
    * indexing
      - old: `logviewer_parser -i access_small.log -t TAG`
      - new: `logviewer_parser index access_small.log -t TAG`
    * merging
      - old: `logviewer_parser -m config.json  -o m.out`
      - new: `logviewer_parser merge config.json -o m.out`

### [0.15.0] - 06/03/2019
  * implemented support to define date format string for parsing dates in
  * files to be merged
    * basic proptype tests
    * basic format parsing
    * create regex by parsing date format
    * handle more then 1 space
    * use ISO 8601 like format specifiers
    * add command line support to test date format

### [0.14.0] - 05/20/2019
  * update indexed file as soon as we write chunks to stdout
  * playing with nom

### [0.13.0] - 05/20/2019
  * append to empty file starts rows at 0 now
  * report mapping on the fly and not only at end

### [0.12.0] - 05/19/2019
  * play with other parsing mechanisms for merging
  * timestamp in files to merge does not need to be at beginning

### [0.11.0] - 05/18/2019
  * merging now done with constant memory
  * progress reports on merging

### [0.10.0] - 05/16/2019
  * better error handling
  * report mapping for merging to stdout

### [0.9.2] - 05/16/2019
  * using BufWriter to write to files
  * better than doing it by hand, perfomance looks the same
  * code is simpler
  * extracted creating the index file functionality

### [0.9.1] - 05/15/2019
  * corrected timestamp parsing: day and month were mixed up

### [0.9.0] - 05/15/2019
  * feat: first support for merging
  * implemented regex discovery
    * line detection
  * rearranged test folders
    * get use temp-dir for all tests where we create files
  * first implementation of merge
  * add option to use config file for merging
  * improoved error handling
  * push functionality to util for reuse
  * add tags and line numbers to merged file
  * deal with missing timestamp for a line

### [0.8.2] - 05/13/2019
  * fixed row offsets in mapping file
  * basic timestamp parsing works

### [0.8.1] - 05/13/2019
  * add missing newlines to stdout mapping

### [0.8.0] - 05/13/2019
  * added option to spit out mapping info on stdout (use `-t` to get
    all chunks that have been written to stdout)
  * replace tests with example input output tests
  * more test cases in file form
  * started work on merging files by timestamp

### [0.7.1] - 05/11/2019
  * nicer progress reporting

### [0.7.0] - 05/10/2019
  * print all chunks to stdout for progress tracking
  * test case for utf8 invalid characters
  * porting test cases to example folders, testcases
  * based on file samples

### [0.6.0] - 05/09/2019
  * added rake task to create changelog for release
  * improve performance for processing large files
  * now we use BufReader::read_until to avoid UTF-8 validity checks

### [0.5.0] - 5/7/2019
  * allow for text files that contain invalid UTF-8 characters without discarding illegal lines

### [0.4.6] - 5/7/2019
  * allow for text files that contain invalid UTF-8 characters

### [0.4.5] - 5/6/2019
  * fix row number starting row when appending (was wrong in json mapping)
  * allow for using append mode (`-a`) even if file does not exist

### [0.4.4] - 5/6/2019
  * handle empty index files

### [0.4.3] - 5/6/2019
  * handle empty files

### [0.4.2] - 5/6/2019
  * correctly handle CRLF at start of line

### [0.4.1] - 5/6/2019
  * remove verbose output

### [0.4.0] - 5/6/2019
  * append to mapping file supported

### [0.3.0] - 5/6/2019
  * fix bug in mapping file
  * rename mapping file to [infile_name].mapping.json
