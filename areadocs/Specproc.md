Special Procedures List
=======================

Last modified by Samson, 6/19/03

The following is a list of special procedures available for mobiles.
The procs do tend to take up a significant number of clock cycles on the 
server, so try to restirct their use to only the special mobs, DON'T go
around planting these on every mob that matches the class!

spec_janitor: Mob picks up items on the ground.

spec_snake: Gives the mob a poison bite, as the name implies.

spec_fido: Mob devours corpses left lying around.

spec_cast_adept: The procedure used for healer mobs - they cast the following:
   armor, bless, cure blindness, cure light, cure poison, refresh, cure serious,
   remove curse, heal, and cure critical.
   
spec_Rustmonster: Mob takes and destroys all items lying on the ground,
   with the exception of player corpses.

spec_GenericCityguard: Ported from DOTD. A nifty little proc that when
   placed on a guard mob, causes the mob to call for help when attacked,
   which in turn causes other similar mobs to begin tracking the attacker.
   It causes the mob to instantly attack any opponent who is of opposite
   alignment, or to attack any undead ( assuming the mob is not undead )
   in the room. And on top of all that, if the mob is not fighting, and
   has a GREET flag on them, they will greet people in the room.

spec_executioner: 
spec_guard:       The mob attacks anyone with a KILLER or THIEF flag.
   More or less obsolete since PK isn't a real problem.

spec_GenericCitizen: The mob will call for help if attacked, otherwise
   it greets people if it has a GREET flag.

spec_warrior: The mob will use certain warrior skills in combat.

spec_thief: The mob picks pockets for gold.

spec_cast_mage: The mob casts from the following pool of mage spells, based on level:
   	magic missile
	burning hands
	shocking grasp
	sleep
	weaken
	acid blast
	dispel magic
	blindness
	web
	colour spray
	lightning bolt
	cone of cold
	fireball
	stinking cloud
	acetum primus
	galvanic whip
	quantum spike
	meteor swarm

   The mob must be of sufficient level to be able to cast the spell, which is
   the same level that players are first able to learn it. Obviously a high level
   mob with this proc becomes a formidable opponent.
   ( The same holds true for any of the casting procs )

spec_cast_cleric: The mob casts from the following pool of cleric spells:
  	cause light
	curse
	spiritual hammer
	dispel evil
	cause serious
	blindness
	hold person
	dispel magic
	cause critical
	silence
	harm
	lethargy
	flamestrike
	fatigue
	earthquake
	feebleness
	spectral furor

spec_cast_undead: The mob casts from the following pool of necromancer spells:
	magic missile
	chill touch
	sleep
	weaken
	black hand
	black fist
	dispel magic
	fatigue
	lethargy
	necromantic touch
	withering hand
	paralyze
	cone of cold
	harm
	black lightning

spec_ranger: Gives the mob a 50-50 chance of either using spec_warrior, or
   casting from the following pool of ranger spells:
	faerie fire
	cause light
	entangle
	faerie fog
	poison

spec_paladin: The mob will either use spec_warrior, or cast from the following
   pool of paladin spells:
	spiritual hammer
	dispel evil
	flamestrike
	disruption
	spectral furor

   spec_paladin favors the warrior abilities 2 out of 3 times.

spec_druid: The mob will cast from the following pool of druid spells:
	cause light
	faerie fire
	cause serious
	entangle
	poison
	gust of wind
	earthquake
	cause critical
	flamestrike
	dispel magic
	call lightning
	harm
	firestorm

spec_antipaladin: The mob will either use spec_warrior, or cast from the
   following pool of antipaladin spells:
	chill touch
	curse
	cause light
	weaken
	spectral furor
	fireball
	quantum spike

   spec_antipaladin favors casting 2 out of 3 times.

spec_bard: The mob will cast from the following pool of bard spells:
	magic missile
	shocking grasp
	despair
	enrage
	sonic resonance
	blindness
	lightning bolt

spec_breath_acid: Gives the mob acid breating ability. Used primarily by dragons.

spec_breath_fire: ditto for fire breathing

spec_breath_frost: ditto for frost breathing

spec_breath_gas: ditto for noxious gas breathing

spec_breath_lightning: ditto for lightning breathing

spec_breath_any: Mob will pick at random from one of the 5 types of breath attack.
