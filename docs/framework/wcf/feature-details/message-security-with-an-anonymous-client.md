---
title: "Anonim İstemci ile İleti Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a>Anonim İstemci ile İleti Güvenliği
Aşağıdaki senaryoda bir istemci ve hizmet tarafından güvenli hale getirilmiş gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti güvenlik. Böylece gelecekte daha zengin bir talep tabanlı modeli destekleyebilir tasarım hedefi taşıma güvenliği yerine ileti güvenliği kullanmaktır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]yetkilendirme için zengin talep kullanarak bkz [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Örnek bir uygulama için bkz: [ileti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md).  
  
 ![İleti anynymous istemci ile güvenliği](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]yalnızca|  
|Kimlik doğrulaması (sunucu)|İlk anlaşma sunucu kimlik doğrulaması, ancak değil istemci kimlik doğrulaması gerektirir|  
|Kimlik doğrulaması (istemci)|Yok.|  
|Bütünlük|Evet, paylaşılan güvenlik bağlamını kullanarak|  
|Gizliliği|Evet, paylaşılan güvenlik bağlamını kullanarak|  
|Taşıma|HTTP|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod ileti güvenliği kullanan hizmet uç noktası oluşturulacağını gösterir.  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma kodu yerine kullanılabilir. Hizmet davranışı öğesi istemci hizmete kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır. Hizmet öğesinin davranışını kullanarak belirtmelisiniz `behaviorConfiguration` özniteliği. İstemci kimlik bilgisi türü olduğunu bağlama öğesi belirtir `None`, hizmeti kullanmak anonim istemcilerinin olanak tanır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.  
  
-   Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın. Örneğin:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, istemci bir örneğini oluşturur. İleti mod güvenliği bağlama kullanır ve istemci kimlik bilgisi türü hiçbiri olarak ayarlanır.  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemci yapılandırır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
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
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Dağıtılan uygulama güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [İleti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [Hizmet kimliği ve kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
