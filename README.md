# data_generator

This repository automatically runs the [Data Generator](https://minecraft.wiki/w/Tutorial:Running_the_data_generator) for every available server version and publishes the resulting dumps to dedicated branches.

A GitHub Actions workflow executes the generator on a schedule (via `cron`), using the official Mojang server JAR for each version.  
The generated data is then committed to a corresponding branch named after the version.

---

## Branch Structure

The repository uses a simple naming scheme to separate release and snapshot versions:

- **Release versions:** `r-<version>`  
  Example: `r-1.20.4`, `r-1.14.4`

- **Snapshot versions:** `s-<yearwXX>`  
  Example: `s-24w05a`, `s-23w46a`

Each branch contains the raw output of the Minecraft Data Generator for that version.

---

## How It Works

1. A GitHub Actions workflow runs on a schedule (`cron`) or manually.
2. For each known version:
   - The workflow downloads the official Mojang server JAR.
   - It runs the Data Generator included in that version of the Minecraft server.
   - It commits the generated dump to the branch for that version.
3. Branches are updated only when a change in the generated data is detected.

---

## 📝 Notes on Licensing

The generated data originates from the official Mojang server JAR.  
While the generator output is not explicitly licensed by Mojang, it is derivative of Minecraft’s game data.  

Because of that, **it is unclear whether a custom open-source license should be applied**.  
For now, the repository **does not apply an additional license** to avoid implying permissions that may not exist.

If you intend to use the data, please ensure you comply with Mojang’s guidelines and EULA.
