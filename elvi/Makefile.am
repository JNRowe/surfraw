# $Id$
elvidir="@ELVIDIR@"
elvi_SCRIPTS	= \
		  alioth \
		  altavista \
		  amazon \
		  ask \
		  austlii \
		  bbcnews \
		  britannica \
		  cddb \
		  cite \
		  cnn \
		  currency \
		  debbugs \
		  debcontents \
		  deblists \
		  debpackages \
		  deja \
		  excite \
		  fast \
		  filesearching \
		  freebsd \
		  freedb \
		  freshmeat \
		  jake \
		  google \
		  happypenguin \
		  imdb \
		  scpan \
		  slinuxdoc \
		  leodict \
		  netbsd \
		  openbsd \
		  pubmed \
		  rhyme \
		  slashdot \
		  sundocs \
		  sourceforge \
		  stockquote \
		  scaleplus \
		  sunsolve \
		  swhois \
		  thesaurus \
		  translate \
		  webster \
		  wetandwild \
		  wikipedia \
		  woffle \
		  xxx \
		  yahoo
sysconf_DATA	= surfraw_elvi.list

EXTRA_DIST	= $(elvi_SCRIPTS)

surfraw_elvi.list: $(elvi_SCRIPTS)
	cat $(elvi_SCRIPTS)|egrep '^#.*elvis:'|sed 's/^.*elvis: *//'|sort > $@
