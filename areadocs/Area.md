Purpose of this file
--------------------
The purpose of this file is to allow builders to create areas offline 
if preferred, or to allow them an aid for converting areas from other 
mud formats. Refer to any documentation from other muds to assist in 
converting your areas to our format.

Overview of Areas
-----------------
An area is one piece of the world. Each area is defined in a separate 
file. All area files require the '.are' extension for the code to load them.

Because each area is defined in one file, it is easy to incorporate 
new areas into AFKMud, or to send AFKMud areas to others for use.

Sections of an Area
-------------------
An area file contains the following sections:

    #AREADATA
    #MOBILE
    #OBJECT
    #ROOM

A complete area file will have a complete #AREADATA section and several #MOBILE,
#OBJECT, and #ROOM sections. Each of these primary sections can contain other
subsections which are covered in the respective files.

Mobiles, objects, and rooms are identified by vnum (virtual number).  
The range of vnum's is 1 to somewhere around 2 billion. Vnum's must be 
unique (for that particular kind of vnum). Vnums do not have to be in 
increasing order.

An area uses the same range of vnum's for mobile vnums, object vnums,
and room vnum's, starting with a multiple of 100. This facilitates 
adding the area into an existing set of areas.

Each of the sections above is covered in a seperate file.

An area file must begin with the literal string:
#AFKAREA

It must end with the literal string:
#ENDAREA

These two lines identify it as an AFKMud 2.0 area format.

Though obviously an area needs to have purpose, an area file is considered technically complete
with none of the other sections defined. The remaining sections covered are optional but highly
desired if you plan to be building anything of consequence :)

Header.txt covers the #AREADATA section.

Mobiles.txt covers #MOBILE sections.

Objects.txt covers #OBJECT sections.

Rooms.txt covers #ROOM sections.

Values.txt covers various tables of numerical values needed for some
of the sections.
