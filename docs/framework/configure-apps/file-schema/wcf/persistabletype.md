---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256530"
---
# <a name="persistabletype"></a>\<Persistebletype >
Kalıcı türlerini belirtir.  
  
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
|kimlik|Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.|  
|name|Kalıcı türünün adını belirten bir dize içeren isteğe bağlı öznitelik.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|Bir koleksiyonu `persistableType` öğeleri.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
