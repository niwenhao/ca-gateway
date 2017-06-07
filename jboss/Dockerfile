from jboss/wildfly
add mysql.tar /opt/jboss/wildfly/modules/system/layers/base/com/
add datasource.xml /tmp/
add driver.xml /tmp/

run sed -i '/<datasources>/r /tmp/datasource.xml' /opt/jboss/wildfly/standalone/configuration/standalone.xml
run sed -i '/<drivers>/r /tmp/driver.xml' /opt/jboss/wildfly/standalone/configuration/standalone.xml
