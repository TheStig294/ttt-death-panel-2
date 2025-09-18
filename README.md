## ttt death panel 2

shows killer info on death with verbose (and overengineered) death messages like:\
\- You were shot in the head with a Deagle by Player (Traitor)\
\- You were shot in the crotch with a Shotgun by Player (Detective)\
\- You were blown up with an Incendiary Grenade by Player (Innocent)\
\- You were blown up with an explosive barrel by Player (Traitor)\
\- You were incinerated with a Flare gun by Player (Traitor)\
\- You fell to your death

![](https://cdn.discordapp.com/attachments/462389994204561419/940463997361225798/unknown.png)

this is named "death panel 2" because it's inspired by an older addon called "death panel": <https://web.archive.org/web/20160811170715/http://facepunch.com/showthread.php?t=1282806>

this uses the Bebas Neue font: <https://github.com/dharmatype/Bebas-Neue>

#### linux and osx clients

you have to install the Bebas Neue font because of a bug with gmod: <https://github.com/Facepunch/garrysmod-issues/issues/415>

on linux, you have to put the ttf file in a directory like `~/.local/share/fonts/`

on osx, idk lol just look up "how to install ttf on mac"

#### compatibility with other addons

this should be compatible with other ttt addons that are written properly

i've found this to be not fully compatible with some steam workshop weapon addons because they don't set the correct entities for `CTakeDamageInfo`'s `attacker` and `inflictor` fields\
they won't crash or cause errors, but inaccurate information will be displayed by the panel on death

for a weapon addon to be fully compatible with this addon, it must follow this simple standard for setting correct values for `CTakeDamageInfo`:

* `attacker` is who to credit for killing someone, `inflictor` is what was used to kill someone
  * if i dropped a banana peel and somebody slips and breaks their neck because of it,\
  then i was the "attacker" while the banana peel was the "inflictor"
* `attacker` should typically be a player, an npc, or the world
* `attacker` should NEVER be a weapon or projectile
  * seriously stop doing this, this prevents kills with your weapon from being credited properly
  * use common sense: if you threw a rock at someone, the rock is NOT the attacker, you are
* `inflictor` should be the weapon or projectile that was used to deal damage
  * Steven shooting Jeremy with a revolver:\
  `attacker` = Steven, `inflictor` = revolver, `victim` = Jeremy
  * Steven hitting Jeremy with a thrown spear:\
  `attacker` = Steven, `inflictor` = spear, `victim` = Jeremy
  * Steven planting a bomb and blowing it up next to Jeremy:\
  `attacker` = Steven, `inflictor` = bomb, `victim` = Jeremy
  * Steven's sentry gun shooting Jeremy:\
  `attacker` = Steven, `inflictor` = sentry gun, `victim` = Jeremy
  * Jeremy stepping on a bear trap left by Steven:\
  `attacker` = Steven, `inflictor` = bear trap, `victim` = Jeremy
* `inflictor` can also just be the attacker if the damage was dealt immediately using a weapon that's currently held by the attacker
  * cool: instant damage (e.g. guns, melee weapons)
  * not cool:\
  damage over time (e.g. poison damage, fire damage)\
  has travel time (e.g. projectiles, grenades)\
  indirect damage (e.g. turrets, booby-traps)
  * basically, this is only cool to do if the attacker can't switch weapons before the damage is actually dealt
* weapon addons that don't follow this standard are written incorrectly, so any issues they cause with this addon are none of my fault

### bebasneue font licence

Copyright © 2010 by Dharma Type.

This Font Software is licensed under the SIL Open Font License, Version 1.1.
This license is copied below, and is also available with a FAQ at:
<http://scripts.sil.org/OFL>

-----------------------------------------------------------

SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded,
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.
