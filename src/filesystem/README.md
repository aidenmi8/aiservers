# Filesystem MCP Server

Node.js server implementing Model Context Protocol (MCP) for filesystem operations.

## Features

- Read/write files
- Create/list/delete directories
- Move files/directories
- Search files
- Get file metadata

## API

### Resources

- `file://system`: File system operations interface

### Tools

- **read_file**
  - Read complete contents of a file
  - Input: `path` (string)
  - Reads complete file contents with UTF-8 encoding

- **read_multiple_files**
  - Read multiple files simultaneously
  - Input: `paths` (string[])
  - Failed reads won't stop the entire operation

- **write_file**
  - Create new file or overwrite existing
  - Inputs:
    - `path` (string): File location
    - `content` (string): File content

- **create_directory**
  - Create new directory or ensure it exists
  - Input: `path` (string)
  - Creates parent directories if needed
  - Succeeds silently if directory exists

- **list_directory**
  - List directory contents with [FILE] or [DIR] prefixes
  - Input: `path` (string)

- **delete_file**
  - Remove files or directories
  - Inputs:
    - `path` (string)
    - `recursive` (boolean, optional): For directory deletion
  - Use with caution - deletions are permanent

- **move_file**
  - Move or rename files and directories
  - Inputs:
    - `source` (string)
    - `destination` (string)
  - Fails if destination exists

- **search_files**
  - Recursively search for files/directories
  - Inputs:
    - `path` (string): Starting directory
    - `pattern` (string): Search pattern
  - Case-insensitive matching
  - Returns full paths to matches

- **get_file_info**
  - Get detailed file/directory metadata
  - Input: `path` (string)
  - Returns:
    - Size
    - Creation time
    - Modified time
    - Access time
    - Type (file/directory)
    - Permissions

## Notes

- Exercise caution with `delete_file` (deletes files permanently) and `write_file` (overwrites existing files)
- File paths can be absolute or relative