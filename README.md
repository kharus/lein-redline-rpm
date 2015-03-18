# lein-redline-rpm
A pure java RPM Leiningen plugin

Currently this is rather incomplete but there is enough to make a simple rpm.

## Usage

Add `lein-redline-rpm "0.2.0"` to `:plugins` in your `project.clj` as well as
configure `:rpm`

```
  :rpm {:package-name "The name the rpm system uses"
        :distribution "The textual human name for this rpm"
        :summary "Whatever you want"
        :vendor "The name of the person or organization responsible"
        :packager "The name and possibly email address of the person who built this"
        :group "Application/System"
        :release "1"
        :pre-install-script "script/rpm/pre-install"
        :post-install-script "script/rpm/post-install"
        :pre-uninstall-script "script/rpm/pre-uninstall"
        :post-uninstall-script "script/rpm/post-uninstall"
        :prefixes ["/relocatable/paths"]
        :directories [["/this/directory/will/be/created" 0750 "user" "group"]]
        :files [["target/your.jar" "/opt/business/your.jar" 0640 0750 "user" "group"]]
        :symlinks [["/source" "/target"]]}
```

`:directories` is for creating a bare directory not doing file traversal

To create the rpm:

```
lein rpm
```

## Needs Done

Name the rpm based on the project with a configure and/or command line override.

Input validation. Redline does very little input validation and rarely throws.

Add all the other stuff in Redline not exposed yet.

Add directory traversal file addition ( the thing you thought .addDirectory() did ).

Tests? We could use the redline Scanner to validate various `:rpm` configurations.

Figure out what to do with redline's desire for slf4j. Currently ignoring.

## License

Distributed under the Eclipse Public License, the same as Clojure.
