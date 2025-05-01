# PyAraCrypt
ARACrypt [implementation](https://www.codeproject.com/articles/2329/aracrypt-a-crypto-class) in Python, based on the original source and in the [C# implementation](https://gist.github.com/HakanL/f67fb9452d086856f105d64bc13a3f46) by [HakanL](https://gist.github.com/HakanL/f67fb9452d086856f105d64bc13a3f46).

## Usage

ARACrypt works directly with bytes, both for the key and the data:

```python
from ARACrypt import ARACrypt

# Handle files as binary
with open(path, 'rb') as f:
    content = f.read()

    # Key must be a bytes object. To use a str, convert like this: 
    key: bytes = bytes('my_key', 'utf-8')

    # Create ARACrypt object
    crypt = ARACrypt()
    encrypted_content = crypt.transform_bytes(key, content)

    with open(output_path, 'wb') as output_f:
        output_f.write(encrypted_content)
```

ARACrypt is symmetric: the encryption/decryption process is done in the same way:

```python
crypt = ARACrypt()
# To encrypt:
encrypted_content = crypt.transform_bytes(key, content)

# To decrypt:
decrypted_content = crypt.transform_bytes(key, encrypted_content)

# Such that:
# decrypted_content == content
```

---
Licensed under the [MIT License](https://mit-license.org/).
