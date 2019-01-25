---
title: '&lt;Parametre&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: a68fdecaba6ad4e64e4d3a4161d9fef6c099d60a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690741"
---
# <a name="ltparametergt"></a>&lt;Parametre&gt;
Bildirilen tür genel bir tür olduğunda genel parametre belirler.  
  
 \<System.Runtime.Serialization >  
\<dataContractSerializer >  
\<declaredTypes > öğesi  
\<Ekle > öğesi için \<declaredTypes >  
\<knownType > öğesi  
\<parametresi > öğesi  
  
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
|dizin|Bildirilen tür genel bir tür olduğunda, bilinen türü döndüren genel parametre belirler.|  
|türü|Serileştirme ve seri durumundan çıkarma için kullanılan bilinen türü tanımlayan bir dize.|  
  
## <a name="index-attribute"></a>Dizin öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|"0"|İlk genel tür parametre. Örneğin, bir <xref:System.Collections.Generic.List%601> yalnızca bir parametresi vardır. Bildirilen tür olarak kullanılıyorsa, dizin "0" olarak ayarlanır.|  
|"1"|İkinci bir genel tür parametresi. Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir. İkinci parametre tarafından döndürülen bilinen türü, "1" dizini özniteliği ayarlayın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Bir alan veya özellik bildirilen türü tarafından döndürülen bilinen bir türünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.  
  
 Bu yapılandırma öğesi, her iki öznitelik aynı anda sahip olamaz. Her iki öznitelik ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
