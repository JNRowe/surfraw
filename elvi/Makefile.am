# $Id$
elvidir="@ELVIDIR@"
elvi_SCRIPTS	= \
		  alioth \
		  altavista \
		  amazon \
		  appwatch \
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
		  ftpfind \
		  ftpsearch \
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
		  raging \
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
		  woffle \
		  xxx \
		  yahoo
sysconf_DATA	= surfraw_elvi.list

EXTRA_DIST	= $(elvi_SCRIPTS)

surfraw_elvi.list: $(elvi_SCRIPTS)
	cat $(elvi_SCRIPTS)|egrep '^#.*elvis:'|sed 's/^.*elvis: *//'|sort > $@
