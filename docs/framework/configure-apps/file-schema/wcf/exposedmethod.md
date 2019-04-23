---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 91eafa46aa73b5e6d359fcbe48f098f9f8a4d0f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174518"
---
# <a name="exposedmethod"></a>\<exposedMethod >
Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan bir COM + metodunu temsil eder.  
  
 \<system.ServiceModel>  
\<comContracts >  
\<comContract >  
\<yöntemleri >  
  
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
|name|Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + metodunu içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<exposedMethods >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Bir koleksiyonu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM + tümleştirme Yapılandırma Aracı (ComSvcConfig.exe), bir COM arabiriminden oluşturulan hizmet sözleşmesini görünmesini belirli yöntemler eklemek için kullanılabilir.  
  
 Örneğin, üç adlandırılmış yöntemleri eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` COM arabirimi `ItemOrders`. Oluşturulan hizmet sözleşmesi için finansal bileşeni.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Sonra da ComSvcConfig.exe çalıştırdığınızda, daha önce bahsedilen yöntemler olarak listeleme aşağıdaki hizmet sözleşmesi ürettiği [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 Üzerinden yansıtarak ve yalnızca listesine dahil yöntemleri ekleyerek bir hizmet sözleşmesini oluşturmak çalışma zamanı hizmet başlangıç zamanında çalışır [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri. İzleme, hizmet sözleşmesinde yer almayan her arabirim yöntemi için oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
