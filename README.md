# repeatable_random_seeds_python

```
# Helper Function
def get_seed_sha256_hash(file_path):
    sha256_hash = hashlib.sha256()
    with open(file_path, "rb") as f:
        # Read file in chunks of 4K
        for byte_block in iter(lambda: f.read(4096), b""):
            sha256_hash.update(byte_block)
    return sha256_hash.hexdigest()


# Helper Function
def string_get_seed_from_sha256_hash(input_string, log_name):
    """
    turn input_string into a sha256 hash
    to use a seed to randomly but repeatably
    """

    # start hash
    list_hash = hashlib.sha256()

    # remove escape characters
    input_string = input_string.replace("\\", "")

    # remove escape characters
    input_string = input_string.replace("\\\\", "")

    print_and_log(f"input string for seed: {input_string}", log_name)

    # hash the string
    list_hash.update(input_string.encode('utf-8'))

    # make the hash an int not hex
    list_hash = list_hash.hexdigest()

    print_and_log(f"hash for seed: {list_hash}", log_name)

    return list_hash


# Helper Function
def get_seed_from_list_sha256_hash(str_list, log_name):
    """
    turn each set of steps into a sha256 hash
    to use a seed to randomly but repeatably
    """

    # start hash
    list_hash = hashlib.sha256()

    # turn list into string
    concatenated_str = ''.join(str_list)

    # remove escape characters
    concatenated_str = concatenated_str.replace("\\", "")

    # remove escape characters
    concatenated_str = concatenated_str.replace("\\\\", "")

    print_and_log(f"input string for row: {concatenated_str}", log_name)

    # hash the string
    list_hash.update(concatenated_str.encode('utf-8'))

    # make the hash an int not hex
    list_hash = list_hash.hexdigest()

    print_and_log(f"list hash for row: {list_hash}", log_name)

    return list_hash


```
