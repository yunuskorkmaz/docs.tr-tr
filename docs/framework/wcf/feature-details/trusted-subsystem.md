---
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: b226eed9218207cde99add61ef1f3eb64b459009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184300"
---
# <a name="trusted-subsystem"></a>Güvenilir Alt Sistem
İstemci, ağ da dağıtılan bir veya daha fazla Web hizmetine erişir. Web hizmetleri, ek kaynaklara (veritabanları veya diğer Web hizmetleri gibi) erişimin Web hizmetinin iş mantığına eklenmiş olması için tasarlanmıştır. Bu kaynaklar yetkisiz erişime karşı korunmalıdır. Aşağıdaki resimde güvenilir bir alt sistem işlemi gösterilmektedir.  
  
 ![Güvenilir alt sistem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 Aşağıdaki adımlar, güvenilir alt sistem işlemini gösterildiği gibi açıklar:  
  
1. İstemci, kimlik bilgileriyle birlikte güvenilen alt sisteme bir istek gönderir.  
  
2. Güvenilen alt sistem kullanıcıyı doğrular ve yetkilendirır.  
  
3. Güvenilen alt sistem uzak kaynağa bir istek iletisi gönderir. Bu isteğe, güvenilen alt sistem (veya güvenilen alt sistem işleminin yürütüldedildiği hizmet hesabı) kimlik bilgileri eşlik eder.  
  
4. Arka uç kaynağı güvenilir alt sistemi doğrular ve yetkilendirır. Daha sonra isteği işler ve güvenilen alt sisteme yanıt yayınlar.  
  
5. Güvenilen alt sistem yanıtı işler ve istemciye kendi yanıtını yayınlar.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik Modu|İleti|  
|Birlikte çalışabilirlik|Yalnızca Windows Communication Foundation (WCF)|  
|Kimlik doğrulama (hizmet)|Güvenlik belirteci hizmeti, istemcilerin kimliğini doğrular ve yetkilendirin.|  
|Kimlik doğrulama (istemci)|Güvenilen alt sistem istemcinin kimliğini doğrular ve kaynak güvenilir alt sistem hizmetini doğrular.|  
|Bütünlük|Evet|  
|Gizlilik|Evet|  
|Aktarım|Istemci ve güvenilir alt sistem hizmeti arasında HTTP.<br /><br /> Net. Güvenilen alt sistem hizmeti ile kaynak (arka uç hizmeti) arasındaki TCP.|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NetTcpBinding> [ve \<wsFederationHttpBağlayıcı>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Kaynak (Arka Uç Hizmeti)  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, TCP aktarım protokolü üzerinden aktarım güvenliğini kullanan kaynak için bir hizmet bitiş noktasının nasıl oluşturulurunun olduğunu gösterir.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma yapılandırmayı kullanarak aynı bitiş noktasını ayarlar.  
  
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
 Aşağıdaki kod, HTTP protokolü üzerinden ileti güvenliğini ve kimlik doğrulaması için bir kullanıcı adı ve parola kullanan güvenilir alt sistem için bir hizmet bitiş noktasının nasıl oluşturulurunu gösterir.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Aşağıdaki kod, TCP aktarım protokolü üzerinden aktarım güvenliğini kullanarak arka uç hizmetiyle iletişim sağlayan güvenilir bir alt sistemdeki bir hizmeti gösterir.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma yapılandırmayı kullanarak aynı bitiş noktasını ayarlar. İki bağlamaya dikkat edin: Biri güvenilir alt sistemde barındırılan hizmeti güvence altına almakta, diğeri ise güvenilen alt sistem ile arka uç hizmeti arasında iletişim kurar.  
  
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
 Aşağıdaki kod, http protokolü üzerinden ileti güvenliği ve kimlik doğrulaması için bir kullanıcı adı ve parola kullanarak güvenilir alt sistemle iletişim sağlayan istemcinin nasıl oluşturulutamamını gösterir.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemciyi HTTP protokolü üzerinden ileti güvenliği ve kimlik doğrulaması için bir kullanıcı adı ve parola kullanacak şekilde yapılandırır. Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılamaz).  
  
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
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
