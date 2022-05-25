# jenkins-junit-maven-example
This is the maven basic project with Junit test cases for Jenkins integration.
auto-increment-plugin
This plugin works by generating a properties file saving three values:

Major: Major version number X.0.0
Minor: Minor version number 0.X.0
Patch: Patch version number 0.0.X
everytime a install or package is initiated, the build number keep increasing.
as soon as the Patch hit the limit (default is 9) the Minor version increases by 1
and the same thing goes for minor, as soon as it hits the limit (default is 9), the Major version increases by 1

Using this plugin
Using maven, you can now implement and use this plugin without the need for extra configuration
add this inside <build> tag

<plugin>
  <groupId>io.github.invvk</groupId>
  <artifactId>auto-increment-plugin</artifactId>
  <version>1.1.2</version>
  <executions>
      <execution>
          <goals>
              <goal>modifyVersion</goal>
          </goals>
      </execution>
  </executions>
</plugin>
Plugin compatibility with Java
Here is an overview of the current plugin compatibility with Java

Plugin Version	Required Java Version
1.0.X	Java 1.8
1.1.X	Java 1.8
Common issues
Problem: Sometimes maven might not recognize the property ${aip.version.full} and highlight it as an error.

Solution: don't worry, in the building process maven is going to recognize this property. you can suppress the error by adding this line on top of the property like in shown picture.
image
copy and paste: <!--suppress UnresolvedMavenProperty -->
Problem: Commit has isn't appearing in (aip.git.commit.cut) or in (aip.version.full)

Solution: Make sure that your project is linked up with a git repository and it contains .git directory. Also, Make sure that you don't have disableGit option enabled.
