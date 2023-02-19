# automate-the-boring-stuff-with-python

Code and notes for the book

## Notes

### Copying files and folders

- `shutil.copy(source, destination)`
  - copy a single file
  - `source` and `destination` can be strings or `Path` objects

- `shutil.copytree(source, destination)`
  - copy an entire folder including its children recursively
  - both args are strings

### Moving and renaming files and folders

- `shutil.move(source, destination)`
  - If there is a file with the same name as `source` in `destination` folder, it will be overriden
  - If `destination` folder does not exist and its parent folder exists, `source` will be renamed to `destination` folder
  - If the folders that make up the `destination` does not exist, an exception will be thrown
  
### Permanently deleting files and folders

- `os.unlink(path)`
  - delete file at `path`

- `os.rmdir(path)`
  - delete the folder at `path`, this folder must be empty

- `shutil.rmtree(path)`
  - remove the folder at `path`, along with its children

### Safely deleting

- use `send2trash` third-party module that can be installed via `pip`
- `send2trash.send2trash(path)`
  - send to recyle bin

### Walking through a directory tree

- `os.walk(path)`
  - walk through all sub folders and files
  - `for folderName, subfolders, filenames in os.walk('/workspace')`
  
### Compressing ZIP files

- use `zipfile` module

### Reading ZIP files

- create a `ZipFile` object
  - `example_zip = zipfile.ZipFile('test.zip')`

### Extracting from ZIP files

- create a `ZipFile` and call `extractall` method
  - `example_zip.extractall(path)`
  - If `path` is empty, files will be extracted to the current directory

### Creating and adding to ZIP files

- open `ZipFile` object in write mode
  - `new_zip = zipfile.ZipFile('new.zip', 'w')`
- add a file to this zip. the 2nd arg is the compression type
  - `newZip.write('test.txt', compress_type=zipfile.ZIP_DEFLATED)`
- open a ZIP in write mode will erase all its existing contents. If we want to add new files to existing ZIP file, open it as append mode: `'a'`
