---
title: Karşılıklı Sertifikalar ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ad5862064966ccae4c313e7fa3d982ec9abbbcd2
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332193"
---
# <a name="message-security-with-mutual-certificates"></a>Karşılıklı Sertifikalar ile İleti Güvenliği
Aşağıdaki senaryoda, bir Windows Communication Foundation (WCF) hizmeti ve istemcisine ileti güvenlik modunu kullanarak güvenli gösterilmektedir. Hizmet ve istemci sertifikaları ile doğrulanır.  
  
 X.509 Sertifika belirteci profiliyle WS-güvenlik kullandığından bu birlikte çalışabilen bir senaryodur.  
  
> [!NOTE]
>  Bu senaryo, hizmet sertifikasının anlaşma gerçekleştirmez. Hizmet sertifikası, öncesinde herhangi bir iletişim istemciye sağlanmalıdır. Sunucu sertifikası uygulamayla birlikte dağıtılmış veya bir bant dışı iletişimi sağlanan.  
  
 ![Karşılıklı sertifikalar ile güvenlik iletisi](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Evet, WS-Security, X.509 Sertifika belirteci profili uyumlu istemcileri ve Hizmetleri.|  
|Kimlik doğrulaması|İstemci ve sunucu, karşılıklı kimlik doğrulaması.|  
|Bütünlüğü|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kodun gösterdiği ileti güvenliği kullanan bir hizmet uç noktası oluşturur. Hizmete kendi kimliğini doğrulamak için bir sertifika gerektirir.  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırmayı kod yerine aynı hizmet oluşturmak için kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
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
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.  
  
-   Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın. Örneğin:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, istemci oluşturur. İleti güvenlik modunu ayarlanır ve istemci kimlik bilgisi türü için sertifika ayarlanır.  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a>Yapılandırma  
 İstemciyi yapılandırır. Bir istemci sertifikası kullanılarak belirtilmelidir [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md). Ayrıca, hizmet sertifikası kullanılarak belirtilir [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)  
 [Nasıl yapılır: oluşturma ve yükleme geçici sertifikalar WCF'de aktarım güvenliği için geliştirme sırasında](https://go.microsoft.com/fwlink/?LinkId=244264)
