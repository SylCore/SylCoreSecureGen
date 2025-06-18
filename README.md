# SylCoreSecureGen

A secure encryption and obfuscation tool for [SylCore](https://github.com/SylCore/SylCore-WoTLK).  
This tool enables developers to encrypt and protect sensitive table data, generate modular encryption keys, and output C++ header files for seamless integration into the SylCore.

---

## 🔐 Features

- **AES-256 Encryption** with CBC mode
- **Multi-layer XOR Obfuscation** with rotative transformations
- **Randomized key/IV generation**
- **Prefix tagging system** for identifying encrypted strings
- **Config-driven architecture** (`config.ini`)
- **Automatic C++ header generation** with:
  - Obfuscated AES key & IV
  - Matching XOR constants
  - Prefix string
- **Backup system** before overwriting keys or headers

---

## 🧠 How It Works

1. Run the tool and choose the **XOR complexity level** (e.g. 5 layers)
2. The tool will:
   - Auto-generate a unique encryption prefix (e.g. `ABC_`)
   - Randomly create a 256-bit AES key and 128-bit IV
   - Generate XOR constant arrays based on selected complexity
   - Obfuscate the key and IV
   - Save all values to a `config.ini` file
   - Export a matching C++ header for use with SylCore
3. Backups of `config.ini` and the C++ header are created automatically

---

## 📂 Output Files

- `config.ini`: Stores your encryption configuration
- `Encryption.generated.h`: Drop-in ready header for use in SylCore
- `Backups/`: Time-stamped and hashed backups of your previous keys

---

## 🛠 Usage

1. Run the tool
2. Make sure you changed your login details for the database inside `database-config` 
3. Generate a new batch of encryption details.
4. Restart the program (To load the new encryption details)
5. Click "Encrypt All". This will take some time, but it encrypts all tables in the `plans.json` file.
6. While it's encrypting, go into your folder, find the file `Encryption.generated.h`, open it, and copy everything.
7. Open SylCore Visual Studio Solution, open the file called `EncryptionProtection.h`, and replace lines 17 - 32.
8. After that, recompile your SylCore project, and you are all done!

---

## 🧰 Requirements

- Windows 10/11
- .NET 6.0+ or .NET Framework 4.8+

---

## 💡 Example

```ini
[Encryption]
Prefix=ENC_
XORConst1=0xB3,0x2F,0x74,0x11,0x9C
XORConst2=0x8D,0x0A,0xCE,0x47,0xD8
XORComplexity=5

[AES]
Key=FE34A9C38F29...
IV=12F91E8CFA40...

[Obfuscated]
Key=...
IV=...
