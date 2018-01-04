---
title: '&lt;parametre&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdbb47fcb65273d03d226e13730849170d4345c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt"></a>&lt;parametre&gt;
Bildirilen bir türe genel bir tür olduğunda genel parametresini belirtir.  
  
 \<System.Runtime.Serialization >  
\<dataContractSerializer >  
\<declaredTypes > öğesi  
\<Ekle > öğesi için \<declaredTypes >  
\<knownType > öğesi  
\<parametresi > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|dizin|Bildirilen genel bir tür olduğunda, bilinen bir tür döndürür genel parametresini belirtir.|  
|türü|Serileştirme ve seri durumundan çıkarma için kullanılan bilinen türünü tanımlayan bir dize.|  
  
## <a name="index-attribute"></a>Dizin özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|"0"|Genel tür ilk parametre. Örneğin, bir <xref:System.Collections.Generic.List%601> yalnızca bir parametre içeriyor. Bildirilen türü olarak kullanılıyorsa, dizin "0" olarak ayarlanır.|  
|"1"|Genel bir tür ikinci bir parametre. Örneğin, bir <xref:System.Collections.Generic.Dictionary%602> iki parametreye sahiptir. İkinci parametresi tarafından bilinen türü döndürülürse, "1" dizini özniteliğini ayarlayın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Bir alan veya türü, özellik tarafından döndürülen bilinen bir türünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.  
  
 Bu yapılandırma öğesi her iki öznitelik aynı anda sahip olamaz. Her iki öznitelik ayarlanırsa, bir <xref:System.Configuration.ConfigurationErrorsException> oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
