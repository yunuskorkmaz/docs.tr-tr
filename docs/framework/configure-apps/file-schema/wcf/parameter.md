---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932842"
---
# <a name="parameter"></a>\<parametre >
Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.  
  
 \<System. Runtime. Serialization >  
\<dataContractSerializer >  
\<declaredTypes > öğesi  
\<DeclaredTypes > için \<> öğesi ekleme  
\<knownType > öğesi  
\<Parameter > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|dizin|Belirtilen tür genel bir tür olduğunda, bilinen türü döndürecek genel parametreyi belirtir.|  
|türü|Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.|  
  
## <a name="index-attribute"></a>Index özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|"0"|Genel türdeki ilk parametre. Örneğin, a <xref:System.Collections.Generic.List%601> yalnızca bir parametreye sahiptir. Belirtilen tür olarak kullanılırsa, Dizin "0" olarak ayarlanır.|  
|"1"|Genel türde ikinci parametre. Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir. Bilinen tür ikinci parametre tarafından döndürülürse, Dizin özniteliğini "1" olarak ayarlayın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<knownType >](knowntype.md)|Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)  
  
 Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz. Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer >](datacontractserializer-element.md)
- [\<> Ekle](add-of-declaredtypes-element.md)
