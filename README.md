# VIVO Custom Webapp

This project replaces the legacy "VIVO Installer". It is used to create a "third-tier" overlay on the standard `vivo.war` file.

## Usage

1. Clone this repository
2. Add any overlay files to their expected location with the `src` directory tree
3. Add any overlay files to their expected location with the `home` directory tree
   e.g.
   ```
   home/src/main/resources/config/applicationSetup.n3
   home/src/main/resources/config/runtime.properties
   home/src/main/resources/rdf/display/firsttime/menu.n3
   ```
4. Build base VIVO webapp
   ```
   cd <location of VIVO source code>
   mvn clean install
   ```
5. Build the custom webapp
   ```
   cd <location of custom webapp code>
   mvn clean install -Dapp-name=<my-app> -Dvivo-dir=<path-to-vivo-home>
   ```
   - The provided 'app-name' will be the name of the produced `.war` file (e.g. `my-app.war`) as well as the name of the application log file (`my-app.all.log`).
      - Default: "vivo-custom-webapp"
   - The provided 'vivo-dir' must be the absolute path of an existing directory in which VIVO home files will be copied. The directory must have "write" permissions for the system user from which the Tomcat service will be running.
      - Default: current-working-directory
