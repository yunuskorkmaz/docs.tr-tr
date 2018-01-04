---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3066ee9247e69c746c28251b975bb80425ccbc8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
İçeren bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> çıkarılırken kullanır.  
  
 Veri sözleşmeleri ve bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Bilinen türler gereksinim türlerini ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Örnek  
 Bildirilen türlerini ve bilinen türleri için eklenen aşağıdaki XML kodunu gösterir bir `DataContractSerializer` öğesi. Örnek eklenmekte olan üç tür gösterir. İlk "Öğesi" adlı bir bilinen türünü kullanan "Siparişler" adlı bir özel türüdür. İkinci bildirilmiş türü bir <xref:System.Collections.Generic.List%601> kullanan `Item` bilinen türü. Son olarak üçüncü türü bildirilen bir <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Collections.Generic.Dictionary%602> Sınıf türüdür iki tür parametreleri ile genel bir tür. İlk anahtarı temsil eder ve ikinci değer temsil eder. Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> türünün ikinci (değer) listesine bilinen türler. Kullanmalısınız `index` özniteliği bilinen türünü kullanmak için hangi tür parametresi belirtin. Bu durumda, değer türü "1" dizini özniteliği belirttiği (sıfır tabanlı derlemedir).  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
