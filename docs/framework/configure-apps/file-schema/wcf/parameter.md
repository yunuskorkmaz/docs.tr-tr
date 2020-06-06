---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400106"
---
# \<parameter>
Tanımlanmış bir tür genel bir tür olduğunda genel parametreyi belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
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
|tür|Serileştirme ve seri durumdan çıkarma için kullanılan bilinen türü tanımlayan bir dize.|  
  
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
|[\<knownType>](knowntype.md)|Tanımlı türün bir alanı veya özelliği tarafından döndürülebilecek bilinen bir türü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..  
  
 Bu yapılandırma öğesinin her iki özniteliği de aynı anda olamaz. Her iki öznitelik de ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
