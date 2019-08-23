---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918993"
---
# <a name="exposedmethod"></a>\<exposedMethod >
Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan bir COM+ yöntemini temsil eder.  
  
 \<system.ServiceModel>  
\<comContracts >  
\<comContract >  
\<Yöntemler >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemini içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<exposedMethods >](exposedmethods.md)|Bir [ \<ExposedMethod >](exposedmethod.md) öğeleri koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM+ tümleştirme yapılandırma aracı (ComSvcConfig. exe), bir COM arabiriminden oluşturulan hizmet sözleşmesinde görünecek belirli yöntemler eklemek için kullanılabilir.  
  
 Örneğin, ' `IFinances` `ItemOrders`de com arabiriminden üç adlandırılmış yöntemi eklemek için aşağıdaki komutu kullanabilirsiniz. Finans bileşeni, oluşturulan hizmet sözleşmesine.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 ComSvcConfig. exe dosyasını da çalıştırdığınızda, daha önce bahsedilen yöntemleri [ \<ExposedMethod >](exposedmethod.md) öğeleri olarak listeleyerek aşağıdaki hizmet sözleşmesini oluşturur.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 Hizmet başlatma sırasında çalışma zamanı, yalnızca [ \<ExposedMethod >](exposedmethod.md) öğeleri listesine dahil edilen yöntemleri inceleyerek ve ekleyerek bir hizmet sözleşmesi oluşturmaya çalışır. Hizmet sözleşmesine dahil olmayan her arabirim yöntemi için bir izleme oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
