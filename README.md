<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<xsd:schema xmlns="http://www.kktv1.com/schema/kkrpc"
	xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
	xmlns:beans="http://www.springframework.org/schema/beans"
	xmlns:tool="http://www.springframework.org/schema/tool"
	targetNamespace="http://www.kktv1.com/schema/kkrpc">
	
	<xsd:import namespace="http://www.w3.org/XML/1998/namespace"/>
	<xsd:import namespace="http://www.springframework.org/schema/beans"/>
	<xsd:import namespace="http://www.springframework.org/schema/tool"/>

	<xsd:annotation>
		<xsd:documentation><![CDATA[ Namespace support for the kkrpc services provided by kkrpc framework. ]]></xsd:documentation>
	</xsd:annotation>
	
	<xsd:complexType name="abstractInvokerType">
		<xsd:attribute name="timeout" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method invoke timeout. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="retries" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method invoke retry times. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="failthreshold" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ Failed threshold to trigger circuit-breaker. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="failcountwindow" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ Count window for failed threshold. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="halfopentimeout" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ Half open timeout to try again. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="closethreshold" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ succeed threshold to trigger close circuit-breaker. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="loadbalance" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method load balance. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="async" type="xsd:string" use="optional" default="false">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method does async. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="cluster" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method invoke cluster strategy ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="cache" type="xsd:string" use="optional" default="false">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method cache result. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="cachesize" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method cache max size. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="cachettl" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method cache ttl in seconds. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="degrade" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The method has been degraded. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
	</xsd:complexType>
	
	<xsd:complexType name="interfaceType">
		<xsd:complexContent>
			<xsd:extension base="abstractInvokerType">
				<xsd:attribute name="id" type="xsd:ID">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The unique identifier for a bean. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="filter" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The filter. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="listener" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The listener. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="monitor" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The monitor name. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="heartbeat" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The heartbeat interval. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="heartbeattimeout" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The heartbeat timeout ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="tps" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The tps invoke rate. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="tpsinterval" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The tps interval default 60000ms ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="group" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The interface group ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="application" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service application ref. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="registry" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service registry ref. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="methodType">
		<xsd:complexContent>
			<xsd:extension base="abstractInvokerType">
				<xsd:attribute name="id" type="xsd:ID">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The unique identifier for a bean. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="name" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The method name. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="abstractReferenceType">
		<xsd:complexContent>
			<xsd:extension base="interfaceType">
				<xsd:attribute name="version" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service version. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="host" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The remote server host. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="port" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The remote server port. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="connecttimeout" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The connect to remote server timeout. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="sticky" type="xsd:string" use="optional">
						<xsd:annotation>
							<xsd:documentation><![CDATA[ Enable/Disable cluster sticky policy.Default false ]]></xsd:documentation>
						</xsd:annotation>
					</xsd:attribute>
				<xsd:attribute name="reconnect" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ remoting reconnect timer. false represent close reconnect. integer represent interval(ms) .default true(2000ms).]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="connections" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The connection num to server ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="iprouter" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The ip router to select remote servers ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="init" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ Init immediately after load bean ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="injvm" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ Use jvm exported service ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="abstractServiceType">
		<xsd:complexContent>
			<xsd:extension base="interfaceType">
				<xsd:attribute name="version" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service version. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="host" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The local server host. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="port" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The local server port. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="workerthreads" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The worker threads num. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="iothreads" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The io threads num. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="queuesize" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The request queue size. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="applicationType">
		<xsd:attribute name="id" type="xsd:ID">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The unique identifier for a bean. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="appname" type="xsd:string" use="required">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The application name. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="appversion" type="xsd:string" default="0.0.0">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The application version. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="author" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The application author. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
	</xsd:complexType>
	
	
	<xsd:complexType name="registryType">
		<xsd:attribute name="id" type="xsd:ID">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The unique identifier for a bean. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="address" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The registry address. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="sessiontimeout" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The registry session timeout. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
		<xsd:attribute name="connecttimeout" type="xsd:string" use="optional">
			<xsd:annotation>
				<xsd:documentation><![CDATA[ The registry connection timeout. ]]></xsd:documentation>
			</xsd:annotation>
		</xsd:attribute>
	</xsd:complexType>
	
	<xsd:complexType name="consumerType">
		<xsd:complexContent>
			<xsd:extension base="abstractReferenceType">
				<xsd:anyAttribute namespace="##other" processContents="lax" />
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="monitorType">
		<xsd:complexContent>
			<xsd:extension base="abstractReferenceType">
				<xsd:attribute name="name" type="xsd:string" use="required">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The monitor name. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="interval" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The monitor send statinfo interval. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:anyAttribute namespace="##other" processContents="lax" />
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="referenceType">
		<xsd:complexContent>
			<xsd:extension base="abstractReferenceType">
				<xsd:choice minOccurs="0" maxOccurs="unbounded">
					<xsd:element ref="method" minOccurs="0" maxOccurs="unbounded" />
				</xsd:choice>
				<xsd:attribute name="interface" type="xsd:string" use="required">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service interface class name. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="consumer" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ consumer reference-default. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:anyAttribute namespace="##other" processContents="lax" />
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:complexType name="providerType">
		<xsd:complexContent>
			<xsd:extension base="abstractServiceType">
				<xsd:anyAttribute namespace="##other" processContents="lax" />
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>

	<xsd:complexType name="serviceType">
		<xsd:complexContent>
			<xsd:extension base="abstractServiceType">
				<xsd:choice minOccurs="0" maxOccurs="unbounded">
					<xsd:element ref="method" minOccurs="0" maxOccurs="unbounded" />
				</xsd:choice>
				<xsd:attribute name="interface" type="xsd:string" use="required">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service interface class name. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="target" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ The service implementation instance bean id. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:attribute name="provider" type="xsd:string" use="optional">
					<xsd:annotation>
						<xsd:documentation><![CDATA[ Provider service-default. ]]></xsd:documentation>
					</xsd:annotation>
				</xsd:attribute>
				<xsd:anyAttribute namespace="##other" processContents="lax" />
			</xsd:extension>
		</xsd:complexContent>
	</xsd:complexType>
	
	<xsd:element name="application" type="applicationType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ The application config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>

	<xsd:element name="registry" type="registryType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ The registry config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="method" type="methodType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ The service method config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="provider" type="providerType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ Export service default config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="consumer" type="consumerType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ Service reference default config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="monitor" type="monitorType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ Monitor service reference config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="service" type="serviceType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ Export service config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
	<xsd:element name="reference" type="referenceType">
		<xsd:annotation> 
			<xsd:documentation><![CDATA[ Reference service config ]]></xsd:documentation> 
		</xsd:annotation>
	</xsd:element>
	
</xsd:schema>
