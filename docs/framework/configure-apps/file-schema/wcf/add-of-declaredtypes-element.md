---
title: <add> ' ın <declaredTypes> öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9b280a63e85beac3231bc1a414430239bea4a1f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701118"
---
# <a name="add-of-declaredtypes-element"></a>\<Ekle >, \<declaredTypes > öğesi
Tarafından kullanılan bir tür ekler <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında. Bildirilen her tür, alan veya özellik bildirilen tür döndürülecek bilinen türleri içerir.  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
\<Ekle >, \<declaredTypes >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Gerekli dize özniteliği.<br /><br /> Tür adı (ad uzayı dahil), derleme adı, sürüm numarasını, kültürü ve ortak anahtar belirteci belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Eklenmekte olan bildirilen türü bilinen türünü belirtir. Bildirilen tür genel bir tür olduğu, ardından da bir parametre öğesine eklemeniz gerekir, `<knownType>` hangi genel parametre bilinen türü döndürmek için kullanıldığını belirtmek için öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türler içeren <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.  
  
> [!NOTE]
>  Eklerseniz <xref:System.Object> olarak bir `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> oluşturulur. Bunun nedeni, <xref:System.Object> türü yapılandırma bildirilen tür olarak kullanılamaz.  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<Ekle >, \<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
