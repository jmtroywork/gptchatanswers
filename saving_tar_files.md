To write a TGZ (compressed tar) file to disk in Python, you can use the `tarfile` module along with the `gzip` module. Here's an example code snippet that demonstrates how to achieve this:

```python
import tarfile
import gzip

# Assuming you have retrieved the contents of the TGZ file from an S3 bucket and stored it in a variable called `file_contents`
tgz_file_path = "/path/to/output/file.tgz"

with open(tgz_file_path, "wb") as f:
    # Write the compressed file using gzip
    with gzip.GzipFile(fileobj=f, mode="wb") as gz_file:
        # Use tarfile to create the tar archive
        with tarfile.open(fileobj=gz_file, mode="w") as tar:
            # Add files to the tar archive (assuming `file_contents` is a list of file paths)
            for file_path in file_contents:
                # Add each file to the tar archive
                tar.add(file_path)
```

In the code above, the `tgz_file_path` variable should contain the desired output path and filename for the TGZ file. The `file_contents` variable is assumed to be a list of file paths that you have retrieved from the S3 bucket using the AWS API.

Make sure to replace `/path/to/output/file.tgz` with the actual desired output path and filename for the TGZ file. Also, modify the code to adapt to your specific use case, such as adding appropriate error handling or modifying the way you retrieve the file contents from the S3 bucket.
