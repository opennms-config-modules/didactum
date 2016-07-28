# Didactum Monitoring System II

OpenNMS configuration module to support monitoring for Didactum devices.
The configuration adds capabilities for SNMP traps with and performance data collection for the following metrics:

- Temperature
- Humidity
- Voltage

## Requirements

- Monitoring System II 100 / 500
- OpenNMS Meridian 2015+ or OpenNMS Horizon 14+

## Download the configuration package

.Download the configuration files
[source, bash]
----
mkdir /tmp
cd /tmp
curl https://github.com/opennms-config-modules/didactum/archive/master.tar.gz | tar xz
----

## Enable SNMP trap support

.Copy into OpenNMS configuration folders
[source, bash]
----
cp events/didactum.events.xml ${OPENNMS_HOME}/etc/events
----

.Add include statement as first entry in ${OPENNMS_HOME}/etc/eventconf.xml
[source, bash]
----
<event-file>events/didactum.events.xml</event-file>
----

## Enable performance data collection

[source, bash]
----
cp datacollection/didactum.xml ${OPENNMS_HOME}/etc/datacollection
----

.Add include statement in alphabetical order in ${OPENNMS_HOME}/etc/datacollection-config.xml
[source, bash]
----
<include-collection dataCollectionGroup="Didactum"/>
----

## Add performance graphs

[source, bash]
----
cp snmp-graph.properties.d/didactum-graph-graph.properties ${OPENNMS_HOME}/etc/snmp-graph.properties.d/
----

# License & Authors

- Author:: Marcel Fuhrmann <fuhrmann@n3rd.org>

Licensed under the GNU Affero General Public License 3+. You may obtain a copy of the License at http://www.gnu.org/licenses/agpl-3.0.html.
