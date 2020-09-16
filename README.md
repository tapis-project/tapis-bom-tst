#Tapis BOM


### Profiles

There is a profile with ID `ossrh` in the tapis-bom. This is the profile that is needed to deploy/release as it activates 
the plugins that are used for signing/javadocs/sourcemaps etc. 

### settings.xml

Credentials are required to push to maven central. There is a jenkins secretfile on Jenkins03 that has a very
basic settings.xml which includes the username and password for the cicsupport user which is tied to maven central. 


### Deploy / Release
A *deployment* pushes a new snapshot build to maven central. By default snapshot repositories are disabled by maven. 

    mvn clean deploy -P ossrh

A *release* pushes a new production version to maven central and is available for all to download.  
    
    mvn clean release:prepare release:perform -P ossrh

A typical workflow is to deploy snapshots continually, then when features are tested and stabilized, push a new
release based on the latest snapshot. 

