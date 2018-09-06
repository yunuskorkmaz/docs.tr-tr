---
title: Güvenilir Alt Sistem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: ac789ba81d728c067be515479e749440bb5809d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042471"
---
# <a name="trusted-subsystem"></a>Güvenilir Alt Sistem
Bir istemci, bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir. Web Hizmetleri, Web hizmetinin uygulamadaki iş mantığının bu ek kaynaklara (örneğin, veritabanları veya diğer Web hizmetlerini) erişim kapsüllenir şekilde tasarlanmıştır. Bu kaynakların yetkisiz erişime karşı korunması gerekir. Aşağıdaki çizimde, bir güvenilir alt sistem işlemi gösterilmektedir.  
  
 ![Güvenilir alt sistem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 Aşağıdaki adımlarda gösterildiği gibi güvenilir alt sistem işlemi açıklanmaktadır:  
  
1.  İstemci kimlik bilgileriyle birlikte güvenilir alt sistem için bir istek gönderir.  
  
2.  Güvenilir alt sistem doğrular ve kullanıcıya yetki verir.  
  
3.  Güvenilir alt sistem uzak kaynak için bir istek iletisi gönderir. Bu istek, güvenilir alt sistem (veya hizmet hesabı altında güvenilir alt sistem işlemi yürütülmekte olduğu) için kimlik bilgilerini eşlik eder.  
  
4.  Arka uç kaynak kimliğini doğrular ve güvenilir alt sistem yetkisi verir. İsteği işler ve güvenilir alt sistem yanıt verir.  
  
5.  Güvenilir alt sistem yanıta işler ve istemciye kendi yanıt verir.  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Windows Communication Foundation (WCF) yalnızca.|  
|Kimlik doğrulaması (hizmet)|Güvenlik belirteci hizmeti doğrular ve istemcilerin yetkisi verir.|  
|Kimlik doğrulaması (istemci)|Güvenilir alt sistem istemcinin kimliğini doğrular ve güvenilir alt sistem hizmeti kaynak kimliğini doğrular.|  
|Bütünlüğü|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTP istemci ve güvenilir alt sistem hizmeti arasında.<br /><br /> NET. Güvenilir alt sistem hizmeti ve kaynak (arka uç hizmeti) arasında TCP.|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Kaynak (arka uç hizmeti)  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, bir hizmet uç noktası TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanır kaynak için oluşturma gösterilmektedir.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırmayı Yapılandırması'nı kullanarak aynı uç noktasını ayarlar.  
  
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
 Aşağıdaki kod, kimlik doğrulaması için ve bir kullanıcı adı ve parola HTTP protokolü ileti güvenliğini kullanan güvenilir alt sistem için bir hizmet uç noktası oluşturma işlemini gösterir.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Aşağıdaki kod, TCP Aktarım Protokolü üzerinden aktarım güvenliği kullanarak arka uç hizmetiyle iletişim kurar güvenilen bir alt sistemdeki hizmet gösterir.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırmayı Yapılandırması'nı kullanarak aynı uç noktasını ayarlar. İki bağlaması Not: bir güvenilen alt barındırılan hizmete güvenliğini sağlar ve diğer güvenilir alt sistem ve arka uç hizmeti arasındaki iletişim kurar.  
  
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
 Aşağıdaki kodu ve bir kullanıcı adı ve parola HTTP protokolü kimlik doğrulaması için ileti güvenliği kullanarak iletişim kuran istemci ile güvenilir alt sistem oluşturma işlemini gösterir.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, ileti güvenliği ve bir kullanıcı adı ve parola HTTP protokolü kimlik doğrulaması için kullanmak üzere istemciyi yapılandırır. Kullanıcı adı ve parola yalnızca kod (yapılandırılabilir değildir) kullanılarak belirtilebilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
