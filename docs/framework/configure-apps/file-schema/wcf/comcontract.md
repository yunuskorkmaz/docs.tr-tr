---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b22c8d0b72d4dfc63eb5fa9afa073f993f75418e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractgt"></a>&lt;comContract&gt;
COM + tümleştirme hizmet sözleşmesini belirtir.  
  
 \<Sistem. ServiceModel >  
\<comContracts >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Sözleşme|Sözleşme türü içeren bir dize.|  
|name|Sözleşme adı içeren bir dize.|  
|ad alanı|Sözleşme ad alanı içeren bir dize.|  
|requiresSession|Sözleşme süre sonuyla bağlantılarına yalnızca kullanılabilir olup olmadığını belirten bir Boole değeri. Hizmet başlatıldığında tümleştirmesi çalışma zamanı bu ayar kullanılacak bağlama türü ile tutarlı olmasını sağlar. Bir özel durum oluşturulur veya daha fazla sözleşme bağlama çakışıyor. Bu özellik ise `false`, tek yönlü bir kanal kullanımda ve herhangi bir [out] parametreleri, bir özel durum da oluşturulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|persistableTypes|Tüm kalıcı türleri.|  
|userDefinedTypes|Bir koleksiyon, kullanıcı tanımlı türler (hizmet sözleşmesinde dahil edilecek olan UDT).|  
|exposedMethods|Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda gösterilen COM + yöntemleri topluluğu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|comContracts|Bir koleksiyonu içerir `comContract` öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM + tümleştirme Hizmet sözleşmeleri "http://tempuri.org" ad alanına şu anda kısıtlı ve sözleşme adı destek COM arabiriminden türetilir. Bununla birlikte, alternatifleri kullanarak belirleyebilirsiniz `comContracts` bölümünde yanı sıra `comContract` yapılandırma dosyası öğesi. Örneğin, bir hizmet sözleşmesini için ad alanı, sözleşme adı ve dahil edilecek kullanıcı tanımlı türler belirtmek için aşağıdaki yapılandırma gibi diğer ayarları kullanabilirsiniz.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 Hizmet başlatıldığında belirtilen ad alanları ve sözleşmesi adları için oluşturulan hizmet açıklamaları uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [COM + uygulamaları ile tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
