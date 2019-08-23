---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: fcfd338e289b5151688724f0e84b6878707d32be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933830"
---
# <a name="persistabletype"></a>\<persistableType >
Tüm kalıcı türlerini belirtir.  
  
 \<system.ServiceModel>  
\<comContracts >  
\<comContract >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|kimlik|Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.|  
|name|Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<persistableTypes >](persistabletypes.md)|`persistableType` Öğelerin koleksiyonu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
