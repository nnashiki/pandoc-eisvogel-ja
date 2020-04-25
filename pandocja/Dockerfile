ARG base_tag="edge"
FROM pandoc/core:${base_tag}

# NOTE: `libsrvg`, pandoc uses `rsvg-convert` for working with svg images.
# NOTE: to maintainers, please keep this listing alphabetical.
RUN apk --no-cache add \
        freetype \
        fontconfig \
        gnupg \
        gzip \
        librsvg \
        perl \
        tar \
        wget \
        xz

# DANGER: this will vary for different distributions, particularly the
# `linuxmusl` suffix.  Alpine linux is a musl libc based distribution, for other
# "more common" distributions, you likely want just `-linux` suffix rather than
# `-linuxmusl` -----------------> vvvvvvvvvvvvvvvv
ENV PATH="/opt/texlive/texdir/bin/x86_64-linuxmusl:${PATH}"
WORKDIR /root

COPY texlive.profile /root/texlive.profile
COPY install-texlive.sh /root/install-texlive.sh
RUN /root/install-texlive.sh

COPY install-tex-packages.sh /root/install-tex-packages.sh
RUN /root/install-tex-packages.sh

RUN rm -f /root/texlive.profile \
          /root/install-texlive.sh \
          /root/install-tex-packages.sh

# japanesse
RUN tlmgr install collection-langjapanese

# eisvogel
RUN tlmgr install csquotes mdframed needspace sourcesanspro ly1 mweights sourcecodepro titling pagecolor
RUN tlmgr install adjustbox babel-german background bidi collectbox csquotes everypage filehook footmisc footnotebackref framed fvextra letltxmacro ly1 mdframed mweights needspace pagecolor sourcecodepro sourcesanspro titling ucharcat ulem unicode-math upquote xecjk xurl zref

# set eisvogel templates dir
COPY templates/eisvogel.latex /root/.pandoc/templates/eisvogel.latex


WORKDIR /data