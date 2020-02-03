---
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 4f3166b8f1e59a100f54574ab548f5dae88eb5cd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742630"
---
# <a name="trusted-subsystem"></a>Güvenilir Alt Sistem
İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir. Web Hizmetleri, ek kaynaklara erişimin (veritabanları veya diğer Web Hizmetleri gibi) Web hizmetinin iş mantığıyla kapsüllenmesi için tasarlanmıştır. Bu kaynakların yetkisiz erişime karşı korunması gerekir. Aşağıdaki çizimde, güvenilir bir alt sistem işlemi gösterilmektedir.  
  
 ![Güvenilen alt sistem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 Aşağıdaki adımlar gösterildiği gibi güvenilir alt sistem işlemini anlatmaktadır:  
  
1. İstemci, kimlik bilgileriyle birlikte güvenilen alt sisteme bir istek gönderir.  
  
2. Güvenilen alt sistem, kullanıcının kimliğini doğrular ve yetkilendirir.  
  
3. Güvenilen alt sistem, uzak kaynağa bir istek iletisi gönderir. Bu isteğe, güvenilen alt sistem (veya güvenilir alt sistem işleminin yürütüldüğü hizmet hesabı) için kimlik bilgileri eşlik eder.  
  
4. Arka uç kaynağı, güvenilen alt sistemi doğrular ve yetkilendirir. Ardından, isteği işler ve güvenilir alt sisteme yanıt verir.  
  
5. Güvenilen alt sistem yanıtı işler ve istemciye kendi yanıtını verir.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Yalnızca Windows Communication Foundation (WCF).|  
|Kimlik doğrulaması (hizmet)|Güvenlik belirteci hizmeti, istemcilerin kimliğini doğrular ve yetkilendirir.|  
|Kimlik doğrulaması (istemci)|Güvenilen alt sistem istemcinin kimliğini doğrular ve kaynak, güvenilen alt sistem hizmetinin kimliğini doğrular.|  
|Bütünlük|Evet|  
|Gizlilik|Evet|  
|Aktarım|İstemci ile güvenilen alt sistem hizmeti arasında HTTP.<br /><br /> NET. Güvenilen alt sistem hizmeti ve kaynak (arka uç hizmeti) arasında TCP.|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Kaynak (arka uç hizmeti)  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanan kaynak için bir hizmet uç noktası oluşturmayı gösterir.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a>Güvenilir Alt Sistem  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, HTTP protokolü üzerinde ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanan güvenilir alt sistem için bir hizmet uç noktası oluşturmayı gösterir.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanarak bir arka uç hizmetiyle iletişim kuran güvenilir bir alt sistemdeki hizmeti gösterir.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma, yapılandırmayı kullanarak aynı uç noktayı ayarlar. İki bağlamayı aklınızda bulunan bir tane, güvenilen alt sistemde barındırılan hizmetin güvenliğini sağlar ve diğer güvenilen alt sistem ile arka uç hizmeti arasında iletişim kurar.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, HTTP protokolü üzerinden ileti güvenliği ve kimlik doğrulaması için bir Kullanıcı adı ve parola kullanarak güvenilir alt sistemle iletişim kuran istemcinin nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemcisini HTTP protokolü ve kimlik doğrulaması için bir Kullanıcı adı ve parola üzerinden ileti güvenliği kullanacak şekilde yapılandırır. Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
