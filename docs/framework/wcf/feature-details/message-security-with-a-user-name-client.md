---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 73e984193f87b20e0e00d8ab92a7c0fd67f7968f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046586"
---
# <a name="message-security-with-a-user-name-client"></a>Kullaıcı Adı İstemcisi ile İleti Güvenliği
Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmet ve istemci ileti düzeyi güvenliği kullanılarak güvenli gösterir. Hizmet bir X.509 sertifikası ile doğrulanır. İstemci, bir kullanıcı adı ve parolasını kullanarak kimliğini doğrular.  
  
 Örnek bir uygulama için bkz: [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![İleti güvenliği kullanıcı adı kimlik doğrulaması kullanarak](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Windows Communication Foundation (WCF) yalnızca|  
|Kimlik doğrulaması (sunucu)|İlk anlaşma sunucu kimlik doğrulaması gerektirir|  
|Kimlik doğrulaması (istemci)|Kullanıcı adı/parola|  
|Bütünlüğü|Evet, paylaşılan bir güvenlik bağlamı kullanma|  
|Gizliliği|Evet, paylaşılan bir güvenlik bağlamı kullanma|  
|Taşıma|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
- Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturma gösterilmektedir.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Yapılandırma  
 Kod yerine aşağıdaki yapılandırma kullanılabilir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, istemci oluşturur. İleti modu güvenlik bağlamadır ve istemci kimlik bilgisi türü `UserName`. Kullanıcı adı ve parola yalnızca kod (yapılandırılabilir değildir) kullanılarak belirtilebilir. Kullanıcı adını ve parolasını döndürmek için kodu, uygulama düzeyinde yapılması gerekir çünkü burada gösterilmez. Örneğin, kullanıcıdan veri sorgulamak için bir Windows Forms iletişim kutusunu kullanın.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemciyi yapılandırır. İleti modu güvenlik bağlamadır ve istemci kimlik bilgisi türü `UserName`. Kullanıcı adı ve parola yalnızca kod (yapılandırılabilir değildir) kullanılarak belirtilebilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [İleti Güvenliği Kullanıcı Adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<Kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
