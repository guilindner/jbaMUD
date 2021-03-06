Armor and Weapon Generation
===========================

This document explains AFKMud's weapons and armor generation system. The
concept behind this system is simple - it sets up a list of armors, a list
of weapons, and a list of materials, which combine to create fully functioning
items. This system is used by the random treasure generator (see Treasure.txt)
and the blacksmithy code (see help forge). Also, items can be set to use this
code by either the OLC or in the area files.

To do so is easy:

For armor, <value3> is the armor type. <value4> is the material type.

For weapons, <value8> is the weapon type. <value9> is the material type.
<value10> is the weapon quality.

Why use a generation system like this? Standardization. This system offers a
chance to have all steel longswords have exactly the same stats, or all
bronze chainmail. Sound good? Read on.

Materials:
----------

The materials list can be found in treasure.c, and the struct for it in
treasure.h. Each material has the following attributes:

<Name> - Name of the material.  

<Weight Mod> - This is multiplied by the weight of the armor or weapon to
get a final weight.

<AC Mod> - For armor, this is added to the AC of the armor type.

<WD Mod> - For weapons, this is added to the min and max damage.

<Cost Mod> - Multiplied by the value of the weapon or armor to get a final cost.

<Mob Level> - Used by the random treasure system. Balancer to keep very good
materials out of low level hands.

The materials themselves are:

Name:          Weight: AC Mod: WD Mod: Cost: Mob Level:
Iron          | 1.25  | 0     | 0     | 0.9 | 1
Steel         | 1     | 0     | 0     | 1   | 1
Bronze        | 1     | -1    | -1    | 1.1 | 1
Dwarven Steel | 1     | 0     | 1     | 1.4 | 10
Silver        | 1     | -2    | -2    | 2   | 10
Gold          | 2     | -4    | -4    | 4   | 15
Elven Steel   | 0.5   | 0     | 0     | 5   | 10
Mithril       | 0.75  | 2     | 1     | 5   | 20
Titanium      | 0.25  | 2     | 1     | 5   | 25
Adamantine    | 0.5   | 4     | 2     | 7   | 30
Blackmite     | 1.2   | 5     | 3     | 7   | 40
Stone         | 3     | 3     | -1    | 2   | 5
Generic       | 0     | 0     | 0     | 1   | 5

Generic is a special material, used for organic armors. When making 
organic-flagged armor, set this as the material.

Blackmite is another special material - all pieces of it gain a -2 save vs
spell affect, which is applied by the weapongen code.

Armor:
------

The list of armors can be found in treasure.c, and the struct in treasure.h.
Each armor has the following attributes:

<Name> - Name of the armor.

<Base Weight> - Multiplied by material weight to get the final weight.

<Base AC> - Added to material AC Mod to get final AC.

<Base Cost> - Multiplied by material Cost Mod to get final cost.

<Flags> - Item flags set by the armor.

The armors themselves are:

Name:           Weight: AC: Cost:  Flags:
Padded          | 2    | 1  | 200   | organic
Leather         | 3    | 2  | 500   | organic anti-mage/necro/monk
Hide            | 5    | 4  | 500   | organic anti-mage/necro/monk
Studded Leather | 5    | 3  | 700   | organic anti-mage/necro/monk
Chainmail       | 8    | 5  | 750   | metal anti-mage/necro/monk/druid
Splintmail      | 13   | 6  | 800   | metal anti-mage/necro/monk/druid/bard/cleric/rogue
Ringmail        | 10   | 3  | 1000  | metal anti-mage/necro/monk/druid
Scalemail       | 13   | 4  | 1200  | metal anti-mage/necro/monk/druid
Banded Mail     | 12   | 6  | 2000  | metal anti-mage/necro/monk/druid/bard/cleric/rogue
Platemail       | 14   | 8  | 6000  | metal anti-mage/necro/monk/druid/bard/cleric/rogue
Field Plate     | 10   | 9  | 20000 | metal anti-mage/necro/monk/druid/bard/cleric/rogue
Full Plate      | 12   | 10 | 40000 | metal anti-mage/necro/monk/druid/bard/cleric/rogue
Buckler         | 3    | 3  | 200   |
Small Shield    | 5    | 7  | 500   |
Medium Shield   | 5    | 10 | 1000  |
Body Shield     | 10   | 15 | 1500  |

Weapons:
--------

The list of weapons can be found in treasure.c, the struct in treasure.h.
Each weapon has the following attributes:

<Name> - Name of the weapon.

<Base Damage> - Adds to the material WD Mod to determine max damage.

<Weight> - Multiplied by material weight mod to get a final weight.

<Cost> - Multiplied by material cost mod to get a final cost.

<Skill> - Skill needed to use the weapon.

<Damtype> - Type of damage the weapon does.

<Flags> - Item flags set by weapon.

The weapons themselves are:

Dagger     | 4 | 4   | 200  | Dagger | Pierce | metal anti-cleric/monk
Claw       | 4 | 4   | 300  | Talon  | Slash  | metal anti-cleric/monk 
Shortsword | 5 | 6   | 500  | Sword  | Pierce | metal anti-cleric/monk/mage/necro/druid
Longsword  | 6 | 10  | 800  | Sword  | Slash  | metal anti-cleric/monk/mage/necro/druid
Claymore   | 10 | 20 | 1600 | Sword  | Slash  | metal twohand anti-cleric/monk/mage/necro/druid/bard/rogue
Mace       | 6  | 12 | 700  | Mace   | Crush  | metal anti-monk/mage/necro/rogue
Maul       | 10 | 24 | 1500 | Mace   | Crush  | metal twohand anti-monk/mage/necro/rogue
Staff      | 5  | 8  | 600  | Staff  | Crush  | twohand
Axe        | 7  | 14 | 800  | Axe    | Hack   | metal anti-cleric/monk/mage/necro/druid/rogue
War Axe    | 11 | 26 | 1600 | Axe    | Hack   | metal twohand anti-cleric/monk/mage/necro/druid/rogue
Spear      | 5  | 10 | 600  | Spear  | Thrust | twohand anti-mage/cleric/necro
Pike       | 9  | 15 | 900  | Spear  | Thrust | twohand anti-mage/cleric/necro/druid/rogue

In addition, each weapon has a quality rating that is either set by the
random treasure generator, the smithy code, or by hand edit/OLC. This rating
is the number of dice the weapon uses, and is handled like so in the code:

If moblevel 1-20 = 1
If moblevel 21-59 = 2
If moblevel 60-99 = 3
If moblevel 100 = 4

Examples:
---------

No doubt you are entirely confused at this point. Most are.
Fortunately, there are examples.

You'll want to be looking at the syntax part of Objects.txt, because the
examples refer to it quite a bit.

Generating Armor:

Let us say we want, oh, Titanium Platemail. This is how we make it so.

<value3> we set to 10 (the value for platemail. Padded is 1, etc.) 
<value4> we set to 9 (the value for titanium. Iron is 1, etc.)

<value0> is set to 10 (8+2, or AC + AC Mod)
<value1> is the same.
<cost> is set to 30000 (6000*5, or Cost * Cost Mod)
<weight> is set to 5 (14*.25, or Weight * Weight Mod)

<extra-flags> is set to metal antimage antinecro antimonk antidruid antibard
anticleric antirogue. Be aware that during OLC this will totally wipe any
pre-existing flags, so do your armorgen first and THEN the rest of the item.

Generating Weapons:

Let us say we want, oh, a Stone Spear. This is how we make it so.

<value8> we set to 11 (the value for spear.)
<value9> we set to 12 (the value for stone.)
<value10> we set to a number, following the guide above. Call it 3.

<value1> is set to 2 (3-1, or Quality + WD Mod)
<value2> is set to 14 ((3*5)-1 or Damage * Quality + WD Mod)
<value3> is set to Thrust
<value4> is set to Spear
