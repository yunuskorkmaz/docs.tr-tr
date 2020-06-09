---
title: Intranet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 591f7db0f6b4e928a991961d3bc7c404f41028bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579286"
---
# <a name="intranet-unsecured-client-and-service"></a>Intranet Güvenli Olmayan Hizmet ve İstemci
Aşağıdaki çizimde, bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen basit bir Windows Communication Foundation (WCF) hizmeti gösterilmektedir. Veriler düşük öneme sahip olduğundan, ağın kendiliğinden güvenli olması beklendiğinden ve güvenlik, WCF altyapısının altındaki bir katman tarafından sağlandığı için güvenlik gerekli değildir.  
  
 ![Intranet güvenli olmayan istemci ve hizmet senaryosu.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Yok|  
|Aktarım|TCP|  
|Bağlama|<xref:System.ServiceModel.NetTcpBinding>|  
|Birlikte çalışabilirlik|Yalnızca WCF|  
|Kimlik Doğrulaması|Yok|  
|Bütünlük|Yok|  
|Gizlilik|Yok|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Aşağıdakilerden birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, güvenliği olmayan bir uç noktanın nasıl oluşturulacağını gösterir:  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Aşağıdakilerden birini yapın:  
  
- Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).  
  
- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın. Örnek:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, TCP protokolünü kullanarak güvenli olmayan bir uç noktaya erişen temel bir WCF istemcisi gösterir.  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma kodu istemci için geçerlidir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpBinding>
- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
