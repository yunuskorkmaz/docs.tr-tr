---
title: Anonim İstemci ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3acea654cc84ede4b264c2db3ae6e9d042f4f5cb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748018"
---
# <a name="transport-security-with-an-anonymous-client"></a>Anonim İstemci ile Taşıma Güvenliği
Windows Communication Foundation (WCF) Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (HTTPS) kullanır. Sunucu bir Güvenli Yuva Katmanı (SSL) sertifikası ile doğrulanması gerekir ve istemcilerin sunucu sertifikasına güvenmelidir. İstemci tarafından herhangi bir mekanizma doğrulanmaz ve, bu nedenle, anonimdir.  
  
 Örnek bir uygulama için bkz: [WS aktarım güvenliği](../../../../docs/framework/wcf/samples/ws-transport-security.md). Aktarım güvenliği hakkında daha fazla bilgi için bkz: [aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
 Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 ![Anonim istemci ile Aktarım güvenliği kullanarak](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Taşıma|  
|Birlikte Çalışabilirlik|Mevcut Web Hizmetleri ve istemcileri ile|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet<br /><br /> Uygulama düzeyinde (WCF desteği)|  
|Bütünlüğü|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTPS|  
|Bağlama|<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, aktarım güvenliği kullanarak bir uç nokta oluşturma işlemi gösterilmektedir:  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, yapılandırma kullanarak aynı uç noktasını ayarlar. İstemci, herhangi bir mekanizma tarafından doğrulanmaz ve bu nedenle anonimdir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
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
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırmayı kod yerine barındırılan hizmeti kurmak için kullanılabilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [WS Aktarım Güvenliği](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [Aktarım Güvenliğine Genel Bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
