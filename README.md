# Morbig
 ## A trustworthy parser for POSIX shell

## Download

    git clone git@github.com:colis-anr/morbig.git

## License and Copyright

   please see the file COPYING

## Are you in a hurry?

   Yes? Build a docker image from the root of this repository:

```
   docker build -t morbig # to build a docker image with morbig inside.
```

   Then, define the following shell function:

```
   morbig () {
      B=`basename $1`
      touch $1.sjson
      docker run \
         -v $1:/home/opam/$B \
	 -v $1.sjson:/home/opam/$B.sjson \
	 morbig --as simple $B
   }
```

   After that, you should be able to run ``morbig`` like this:

```
   morbig my-script.sh
```

   This will create a JSON file named ``my-script.sh.sjson``.

   Now if you want to use more features of ``morbig``, take the time
   to follow the building instructions of the next section.

## Building instructions

### Dependencies

``morbig`` depends on the following software:

```
    - ocaml               (>= 4.02.1 && <= 4.04.2)
    - menhir              (>= 20170509)
    - yojson              (>= 1.3.3)
    - ppx_deriving_yojson (>= 3.0)
    - visitors            (>= 20170725)
```

### Building

    make

### Installing

    make install            # for opam-based environments
    PREFIX=... make install # for system-wide install

### Testing

    make check
