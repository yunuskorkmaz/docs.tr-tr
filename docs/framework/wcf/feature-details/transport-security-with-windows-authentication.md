---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184309"
---
# <a name="transport-security-with-windows-authentication"></a>Windows Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki senaryo, Windows Security tarafından güvenli bir Windows Communication Foundation (WCF) istemcisi ve hizmetini gösterir. Programlama hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
  
 Bir intranet Web hizmeti insan kaynakları bilgilerini görüntüler. İstemci bir Windows Form uygulamasıdır. Uygulama, etki alanını koruyan bir Kerberos denetleyicisi olan bir etki alanında dağıtılır.  
  
 ![Windows kimlik doğrulaması ile taşıma güvenliği](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik Modu|Aktarım|  
|Birlikte çalışabilirlik|Yalnızca WCF|  
|Kimlik Doğrulama (Sunucu)<br /><br /> Kimlik Doğrulama (İstemci)|Evet (Windows tümleşik kimlik doğrulamakullanarak)<br /><br /> Evet (Windows tümleşik kimlik doğrulamakullanarak)|  
|Bütünlük|Evet|  
|Gizlilik|Evet|  
|Aktarım|Net. Tcp|  
|Bağlama|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir. Aşağıdakilerden birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, Windows güvenliği kullanan bir hizmet bitiş noktasının nasıl oluşturulurunun gösteriş olduğunu gösterir.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Yapılandırma  
 Hizmet bitiş noktasını ayarlamak için kod yerine aşağıdaki yapılandırma kullanılabilir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir. Aşağıdakilerden birini yapın:  
  
- Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.  
  
- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın. Örnek:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod istemciyi oluşturur. Bağlama, TCP aktarımını ve istemci kimlik bilgisi türünü Windows'a ayarlı olarak aktarım modu güvenliğini kullanacak şekilde yapılandırılır.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Yapılandırma  
 İstemciyi oluşturmak için kod yerine aşağıdaki yapılandırma kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
