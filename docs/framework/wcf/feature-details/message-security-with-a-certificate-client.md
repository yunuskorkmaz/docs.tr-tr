---
title: Sertifika İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 6221f253746ac304115fe844966e2cf552263d04
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551151"
---
# <a name="message-security-with-a-certificate-client"></a>Sertifika İstemcisi ile İleti Güvenliği
Aşağıdaki senaryoda ileti güvenliği modu kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir. İstemci ve hizmetin her ikisi de sertifikalarla doğrulanır. Daha fazla bilgi için bkz. [Dağıtılmış uygulama güvenliği](distributed-application-security.md).

 ![Sertifikayı içeren bir istemciyi gösteren ekran görüntüsü.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 Örnek bir uygulama için bkz. [Ileti güvenliği sertifikası](../samples/message-security-certificate.md).  

|Özellik|Description|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Yalnızca WCF|  
|Kimlik doğrulaması (sunucu)|Hizmet sertifikası kullanma|  
|Kimlik doğrulaması (Istemci)|İstemci sertifikası kullanma|  
|Bütünlük|Yes|  
|Gizlilik|Yes|  
|Aktarım|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, güvenli bir bağlam oluşturmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturmayı gösterir.  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma kod yerine kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
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
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:  
  
- Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).  
  
- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın. Örnek:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod istemcisini oluşturur. Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `Certificate` .  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma, bir uç nokta davranışı kullanarak istemci sertifikasını belirtir. Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md). Kod ayrıca, `identity` beklenen sunucu kimliğinin etki alanı adı sistemi (DNS) belirtmek için bir <> öğesi kullanır. Kimlik hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe genel bakış](security-overview.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](service-identity-and-authentication.md)
- [Sertifikalarla Çalışma](working-with-certificates.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
