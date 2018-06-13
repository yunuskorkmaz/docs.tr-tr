---
title: İnternet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 93bf7a038a46ff6c03f89e576f3e4150cd069dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491481"
---
# <a name="internet-unsecured-client-and-service"></a>İnternet Güvenli Olmayan Hizmet ve İstemci
Aşağıdaki çizimde bir ortak, güvenli olmayan Windows Communication Foundation (WCF) istemci ve hizmet örneği gösterir.  
  
 ![Güvenli olmayan Internet cleint ve hizmet senaryo](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Yok.|  
|Taşıma|HTTP|  
|Bağlama|<xref:System.ServiceModel.BasicHttpBinding> kodda, veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırma öğesinde.|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve Hizmetleri|  
|Kimlik doğrulaması|Yok.|  
|Bütünlük|Yok.|  
|Gizliliği|Yok.|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod ile herhangi bir güvenliğin bir uç nokta oluşturulacağını gösterir. Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sahip ayarlamak kullanılan güvenlik modunu <xref:System.ServiceModel.BasicHttpSecurityMode.None>.  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a>Hizmet yapılandırması  
 Aşağıdaki kod Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
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
 Aşağıdaki kod, güvenli olmayan bir uç nokta erişen temel bir WCF istemcisi gösterir.  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a>İstemci Yapılandırması  
 Aşağıdaki kod istemci yapılandırır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
