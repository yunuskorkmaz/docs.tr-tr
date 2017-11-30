---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c89acb38678879f882d8bb2a2b5277b555a1eb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexposedmethodgt"></a>&lt;exposedMethod&gt;
Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda sunulan bir COM + yöntemi temsil eder.  
  
 \<Sistem. ServiceModel >  
\<comContracts >  
\<comContract >  
\<yöntemleri >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda sunulan COM + yöntemini içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<exposedMethods >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Bir koleksiyonu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM + tümleştirme Yapılandırma Aracı (ComSvcConfig.exe) oluşturulan hizmet sözleşmesini görünmesi bir COM arabirimden belirli yöntemleri eklemek için kullanılabilir.  
  
 Örneğin, üç adlandırılmış yöntemleri eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` COM arabirimde `ItemOrders`. Oluşturulan servis sözleşmesi finansal bileşeni.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Sonra da ComSvcConfig.exe çalıştırdığınızda, yukarıda açıklanan yöntemleri olarak listeleniyor aşağıdaki hizmet sözleşmesini ürettiği [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 Hizmet başlatma zamanında çalışma zamanı hizmet sözleşmesi üzerinden yansıtma ve yalnızca listesinde yer yöntemleri ekleyerek oluşturmaya çalıştığında [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri. İzleme, hizmet sözleşmesini dahil edilmeyen her arabirim yöntemi için oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [COM + uygulamaları ile tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
