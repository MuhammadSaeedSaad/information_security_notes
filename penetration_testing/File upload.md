## server side validation
the server should validate the file's:
1. type
2. name
3. size
if the validation failed in:
1. file type -> RCE
2. file name -> critical files overwrite
3. file size -> DOS .. filling the available disk space

## Testing
