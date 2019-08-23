---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928863"
---
# <a name="knowntype"></a>\<knownType >
Seri durumdan çıkarma sırasında tarafından <xref:System.Runtime.Serialization.DataContractSerializer> kullanılacak bir tür belirtir. Öğesi, bir "bildirildiği tür" alanı veya özelliği tarafından döndürülen bir "bilinen tür" belirtir. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).  
  
 \<System. Runtime. Serialization >  
\<dataContractSerializer >  
\<declaredTypes > öğesi  
\<\<DeclaredTypes > > ekleyin  
\<knownType > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a>Tür  
 `string`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Türü (ad uzayı dahil), derleme adı, sürüm, kültür ve ortak anahtar belirtecini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<parametre >](parameter.md)|Belirtilen tür genel bir tür olduğunda bir parametre dizini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-of-declaredtypes-element.md)|Tanımlı türler koleksiyonuna, belirtilen bir tür ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer >](datacontractserializer-element.md)
- [\<> Ekle](add-of-declaredtypes-element.md)
