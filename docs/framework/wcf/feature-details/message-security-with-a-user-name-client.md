---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 3dd21268d4ea7dc59c74889ac94dc86678e91865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184632"
---
# <a name="message-security-with-a-user-name-client"></a>Kullaıcı Adı İstemcisi ile İleti Güvenliği
Aşağıdaki resimde bir Windows Communication Foundation (WCF) hizmeti ve ileti düzeyinde güvenlik kullanılarak güvenli istemci gösterilmektedir. Hizmet, X.509 sertifikası ile kimlik doğrulanır. İstemci bir kullanıcı adı ve parola kullanarak kimlik doğrular.  
  
 Örnek bir uygulama için [İleti Güvenliği Kullanıcı Adı'na](../../../../docs/framework/wcf/samples/message-security-user-name.md)bakın.  
  
 ![Kullanıcı adı kimlik doğrulamasını kullanarak ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik Modu|İleti|  
|Birlikte çalışabilirlik|Yalnızca Windows Communication Foundation (WCF)|  
|Kimlik Doğrulama (Sunucu)|İlk anlaşma sunucu kimlik doğrulaması gerektirir|  
|Kimlik Doğrulama (İstemci)|Kullanıcı adı/şifre|  
|Bütünlük|Evet, paylaşılan güvenlik bağlamını kullanma|  
|Gizlilik|Evet, paylaşılan güvenlik bağlamını kullanma|  
|Aktarım|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir. Aşağıdakilerden birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, ileti güvenliğini kullanan bir hizmet bitiş noktasının nasıl oluşturulurunun gösteriş olduğunu gösterir.  
  
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
 Aşağıdaki kod istemciyi oluşturur. Bağlama ileti modu güvenliği için ve istemci kimlik bilgisi türü `UserName`olarak ayarlanır. Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılamaz). Kullanıcı adını ve parolayı döndürecek kod, uygulama düzeyinde yapılması gerektiğinden burada gösterilmez. Örneğin, verileri kullanıcıyı sorgulamak için bir Windows Forms iletişim kutusu kullanın.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemciyi yapılandırır. Bağlama ileti modu güvenliği için ve istemci kimlik bilgisi türü `UserName`olarak ayarlanır. Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılamaz).  
  
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
- [\<kimlik>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
