# Personal Academic Website (`igorsdub.github.io`)

Personal academic and cultural portfolio of Igors Dubanevics, built with Quarto and styled after the minimalist centered-column aesthetic of Griffin Chure (`gchure.bio`) and the stripped-down shelf aesthetic of Brian Hie (`brianhie.com/bookshelf`).

## Language

**Snapshot Strip**:
A compact 3-to-4 image masonry grid on the homepage (`index.qmd`) displaying personal, academic, or Okinawa snapshots beneath the introductory bio.
_Avoid_: Carousel, hero banner, photo gallery page

**Beyond Lab**:
The single non-academic curation page (`beyond-lab.qmd`) housing three distinct media shelves: Books, Music, and Movies.
_Avoid_: Hobbies, blog categories, portfolio

**Shelf**:
A stripped-down Quarto listing gallery within `Beyond Lab` dedicated to a single medium, where items sit on thin horizontal hairlines with zero Bootstrap card chrome.
_Avoid_: Card grid, table, carousel

**Standing Book**:
An entry on the Books shelf rendered with a vertical (`2:3` portrait) cover aspect ratio, title, and author.
_Avoid_: Book post, book review article

**Album Square**:
An entry on the Music shelf rendered with a square (`1:1` vinyl sleeve) artwork aspect ratio, album title, and artist.
_Avoid_: Tracklist, audio player widget

**Cinema Frame**:
An entry on the Movies shelf rendered with a horizontal (`16:9` widescreen still or landscape poster) aspect ratio to evoke a screen, alongside film title, director, and year.
_Avoid_: Vertical movie poster, video embed
