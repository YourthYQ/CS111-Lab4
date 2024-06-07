# Hey! I'm Filing Here

In this lab, I successfully implemented a `mountable ext2 filesystem image`. Specifically in this image, I implemented a root directory, a lost+found directory, a regular file named hello-world, and a symbolic linked name hello which points to hello-world.

## Building

To build the program, navigate to the directory containing the source code and run the following command in the terminal: 

```shell
make
```

Which will create an exectuable file called `ext2-create` . Then we can run the following command:

```shell
./ext2-create
```

This will create `cs111-base.img`  filesystem image for us.

## Running

**Example 1:**

We can dump the filesystem information by running the following command:

```shell
dumpe2fs cs111-base.img
```

**Example 2:**

We can also check whether the filesystem is correct by running the following command:

```shell
fsck.ext2 cs111-base.img
```

Which will get the following similar output as:

```shell
e2fsck 1.46.2 (28-Feb-2021)
cs111-base has gone 0 days without being checked, check forced.
Pass 1: Pass 2: Pass 3: Pass 4: Pass 5:
Checking Checking Checking Checking Checking
inodes , blocks , and sizes directory structure directory connectivity reference counts
group summary information
cs111-base: 13/128 files (0.0% non-contiguous), 24/1024 blocks
```

To mount our filesystem image, we can run the following command in a temporary directory:

```shell
mkdir mnt
sudo mount -o loop cs111-base.img mnt
```

## Cleaning up

After testing the file system, we can uninstall(unmount) it from the temporary directory using the following command.

```shell
sudo umount mnt
rmdir mnt
```

Run the following command to clean up your working directory:

```shell
make clean
```

This will remove any compiled binaries and other temporary files created during the build process.

## Testing

```python
python -m unittest
```

### Expected Results

The test cases should pass without any errors, indicating the program is correctly running. After testing, the keyword **OK** will be printed which represents the success.
