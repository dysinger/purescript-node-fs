# Module Documentation

## Module Node.FS

### Types

    data FS :: !

    data SymlinkType where
      FileLink :: SymlinkType
      DirLink :: SymlinkType
      JunctionLink :: SymlinkType


### Type Class Instances

    instance eqSymlinkType :: Eq SymlinkType

    instance showSymlinkType :: Show SymlinkType


## Module Node.FS.Async

### Types

    type Callback eff a = Either Error a -> Eff (fs :: FS | eff) Unit


### Values

    appendFile :: forall eff. FilePath -> Buffer -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    appendTextFile :: forall eff. Encoding -> FilePath -> String -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    chmod :: forall eff. FilePath -> Number -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    chown :: forall eff. FilePath -> Number -> Number -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    exists :: forall eff. FilePath -> (Boolean -> Eff eff Unit) -> Eff (fs :: FS | eff) Unit

    link :: forall eff. FilePath -> FilePath -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    mkdir :: forall eff. FilePath -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    mkdir' :: forall eff. FilePath -> Number -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    readFile :: forall eff. FilePath -> Callback eff Buffer -> Eff (fs :: FS | eff) Unit

    readTextFile :: forall eff. Encoding -> FilePath -> Callback eff String -> Eff (fs :: FS | eff) Unit

    readdir :: forall eff. FilePath -> Callback eff [FilePath] -> Eff (fs :: FS | eff) Unit

    readlink :: forall eff. FilePath -> Callback eff FilePath -> Eff (fs :: FS | eff) Unit

    realpath :: forall eff. FilePath -> Callback eff FilePath -> Eff (fs :: FS | eff) Unit

    realpath' :: forall eff cache. FilePath -> {  | cache } -> Callback eff FilePath -> Eff (fs :: FS | eff) Unit

    rename :: forall eff. FilePath -> FilePath -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    rmdir :: forall eff. FilePath -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    stat :: forall eff. FilePath -> Callback eff Stats -> Eff (fs :: FS | eff) Unit

    symlink :: forall eff. FilePath -> FilePath -> SymlinkType -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    truncate :: forall eff. FilePath -> Number -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    unlink :: forall eff. FilePath -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    utimes :: forall eff. FilePath -> Date -> Date -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    writeFile :: forall eff. FilePath -> Buffer -> Callback eff Unit -> Eff (fs :: FS | eff) Unit

    writeTextFile :: forall eff. Encoding -> FilePath -> String -> Callback eff Unit -> Eff (fs :: FS | eff) Unit


## Module Node.FS.Stats

### Types

    data Stats where
      Stats :: StatsObj -> Stats

    type StatsObj = { isSocket :: Fn0 Boolean, isFIFO :: Fn0 Boolean, isCharacterDevice :: Fn0 Boolean, isBlockDevice :: Fn0 Boolean, isDirectory :: Fn0 Boolean, isFile :: Fn0 Boolean, ctime :: JSDate, mtime :: JSDate, atime :: JSDate, size :: Number, ino :: Number, rdev :: Number, gid :: Number, uid :: Number, nlink :: Number, mode :: Number, dev :: Number }


### Type Class Instances

    instance showStats :: Show Stats


### Values

    accessedTime :: Stats -> Date

    isBlockDevice :: Stats -> Boolean

    isCharacterDevice :: Stats -> Boolean

    isDirectory :: Stats -> Boolean

    isFIFO :: Stats -> Boolean

    isFile :: Stats -> Boolean

    isSocket :: Stats -> Boolean

    isSymbolicLink :: Stats -> Boolean

    modifiedTime :: Stats -> Date

    statusChangedTime :: Stats -> Date


## Module Node.FS.Sync

### Values

    appendFile :: forall eff. FilePath -> Buffer -> Eff (err :: Exception, fs :: FS | eff) Unit

    appendTextFile :: forall eff. Encoding -> FilePath -> String -> Eff (err :: Exception, fs :: FS | eff) Unit

    chmod :: forall eff. FilePath -> Number -> Eff (err :: Exception, fs :: FS | eff) Unit

    chown :: forall eff. FilePath -> Number -> Number -> Eff (err :: Exception, fs :: FS | eff) Unit

    exists :: forall eff. FilePath -> Eff (fs :: FS | eff) Boolean

    link :: forall eff. FilePath -> FilePath -> Eff (err :: Exception, fs :: FS | eff) Unit

    mkdir :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) Unit

    mkdir' :: forall eff. FilePath -> Number -> Eff (err :: Exception, fs :: FS | eff) Unit

    readFile :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) Buffer

    readTextFile :: forall eff. Encoding -> FilePath -> Eff (err :: Exception, fs :: FS | eff) String

    readdir :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) [FilePath]

    readlink :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) FilePath

    realpath :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) FilePath

    realpath' :: forall eff cache. FilePath -> {  | cache } -> Eff (err :: Exception, fs :: FS | eff) FilePath

    rename :: forall eff. FilePath -> FilePath -> Eff (err :: Exception, fs :: FS | eff) Unit

    rmdir :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) Unit

    stat :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) Stats

    symlink :: forall eff. FilePath -> FilePath -> SymlinkType -> Eff (err :: Exception, fs :: FS | eff) Unit

    truncate :: forall eff. FilePath -> Number -> Eff (err :: Exception, fs :: FS | eff) Unit

    unlink :: forall eff. FilePath -> Eff (err :: Exception, fs :: FS | eff) Unit

    utimes :: forall eff. FilePath -> Date -> Date -> Eff (err :: Exception, fs :: FS | eff) Unit

    writeFile :: forall eff. FilePath -> Buffer -> Eff (err :: Exception, fs :: FS | eff) Unit

    writeTextFile :: forall eff. Encoding -> FilePath -> String -> Eff (err :: Exception, fs :: FS | eff) Unit