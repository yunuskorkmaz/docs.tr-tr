---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 9447487012cae370d35880e5b780465f9434051b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602628"
---
# <a name="message-security-with-a-user-name-client"></a>Kullaıcı Adı İstemcisi ile İleti Güvenliği
Aşağıdaki çizimde, ileti düzeyi güvenlik kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir. Hizmetin kimliği bir X. 509.440 sertifikasıyla doğrulanır. İstemci, bir Kullanıcı adı ve parola kullanarak kimlik doğrular.  
  
 Örnek bir uygulama için bkz. [Ileti güvenliği Kullanıcı adı](../samples/message-security-user-name.md).  
  
 ![Kullanıcı adı kimlik doğrulamasını kullanan ileti güvenliği](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42F5-B1AF-195bfee5b3c6")  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte çalışabilirlik|Yalnızca Windows Communication Foundation (WCF)|  
|Kimlik doğrulaması (sunucu)|İlk anlaşma sunucu kimlik doğrulaması gerektiriyor|  
|Kimlik doğrulaması (Istemci)|Kullanıcı adı/parola|  
|Bütünlük|Evet, paylaşılan güvenlik bağlamını kullanma|  
|Gizlilik|Evet, paylaşılan güvenlik bağlamını kullanma|  
|Aktarım|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Aşağıdakilerden birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.  
  
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
 Aşağıdaki kod istemcisini oluşturur. Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `UserName` . Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir). Kullanıcı adını ve parolayı döndüren kod, uygulama düzeyinde yapılması gerektiğinden burada gösterilmez. Örneğin, verileri Kullanıcı için sorgulamak üzere bir Windows Forms iletişim kutusu kullanın.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemcisini yapılandırır. Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `UserName` . Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).  
  
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

- [Güvenliğe genel bakış](security-overview.md)
- [İleti Güvenliği Kullanıcı Adı](../samples/message-security-user-name.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
