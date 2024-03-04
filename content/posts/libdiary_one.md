---
title: "Introduction to libdiary 📖🔐"
date: 2024-03-04T18:05:57+01:00
---

After a few weeks of coding, I'm finally completed the initial release of a very special (not really) project that I would like to share with the world.

Today, I am proud to introduce [**libdiary**](https://github.com/albertyablonskyi/libdiary/) - a C library designed for managing portable encrypted diaries.

---

### Throwback
Pursuing a master's degree in computer science comes with certain implications, one of them being the diploma project. Fortunately, being a venture-minded individual (or at least thinking this way), I decided to try to make something **special** of it. This led me to the idea of developing a personal diary application, but in the right way. That means:

- **Make the diary encrypted** - period.
- **Make the diary portable** - the diary is stored in .diary format, and it is up to the user to choose where to keep the diary, whether it is some folder on the drive or cloud storage.

Based on these very restrictive requirements, it was chosen to separate the project into two parts:

- A library responsible for managing all diary operations, such as reading/writing, encryption/decryption, and data handling.
- A GUI, acting as the missing link between the library and the end user.

With the basic requirements in place, we can now dive into the details of the library's implementation. For data storage, the [sqlite3](https://www.sqlite.org/) library was chosen, while [libsodium](https://libsodium.org/) was selected for encryption/decryption operations, with ChaCha20-Poly1305 chosen as the main algorithm.

---

### Current status
**libdiary:**
- Already implemented all basic functions, like creating/opening/saving a diary, creating and editing notes.
- A separate highlight deserves the implementation of file attachment, exporting, and opening in memory with the default application.
- Currently investigating the separation of `get_notes_json()`, which returns all the data (notes and attached files) of the diary in JSON format, to `get_notes_json()` and `get_attached_files_json()`, which will benefit the performance of data retrieval.

**Pensieve (working title):**
- In plans to create a GTK4/Libadwaita application, probably in Python, which will use libdiary to interact with diaries.
- My main design inspiration comes from [Nautilus](https://gitlab.gnome.org/GNOME/nautilus), where the sidebar would be used to display a list of notes with short info (title, date) and content area with the chosen note itself (title, body, list of attached files), but I'm not sure which implementation to choose: [Navigation Split View](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/1-latest/widget-gallery.html#navigation-split-view) or [Overlay Split View](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/1-latest/widget-gallery.html#overlay-split-view), because while they offer basically the same functionality, I'm still unsure which option I would like more.
- It should also definitely come with proper XDG MIME setup!

---

### Final thoughts
So, that's probably it... If you are interested in the project and would like to contribute to it - I'm open to it! The source code is available [here](https://github.com/albertyablonskyi/libdiary/), feel free to contact me!