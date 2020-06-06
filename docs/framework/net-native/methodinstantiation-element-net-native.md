---
title: <MethodInstantiation>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128322"
---
# <a name="methodinstantiation-element-net-native"></a>\<MethodInstantiation>Öğesi (.NET Native)
Oluşturulmuş bir genel metoda çalışma zamanı yansıtma ilkesi uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Öznitelik türü|Açıklama|  
|---------------|--------------------|-----------------|  
|`Name`|Genel|Gerekli öznitelik. Yöntem adını belirtir.|  
|`Signature`|Genel|İsteğe bağlı öznitelik. Metodun adlandırılmış parametrelerini belirtir. Birden çok adlandırılmış parametre virgüller ile ayrılır. `Signature`Özniteliği, aşırı yüklenmiş yöntemleri ayırt etmek için kullanılır.|  
|`Arguments`|Genel|Gerekli öznitelik. Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Bir yöntem hakkında bilgi sorgulama veya bir yöntemi numaralandırma, ancak çalışma zamanında dinamik çağırma etkinleştirmeyin.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için bir oluşturucuya veya yönteme çalışma zamanı erişimini denetler. Bu ilke, bir üyenin çalışma zamanında dinamik olarak çağrılabilir olmasını sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Metodun türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Signature özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Metodun adlandırılmış parametrelerini belirtir. Birden çok parametre varsa, bunlar virgülle ayrılır.|  
  
## <a name="arguments-attribute"></a>Arguments özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_arguments*|Genel tür bağımsız değişkenlerini belirtir. Birden çok bağımsız değişken varsa, bunlar virgülle ayrılır. Her bağımsız değişken tam nitelikli tür adından oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Diğer tüm öznitelikler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Yöntemi için bu ilke türüne uygulanacak ayar. Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` . Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<MethodInstantiation>`Öğesi, karşılık gelen açık genel yönteminin çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
- [\<Method>Dosyalarında](method-element-net-native.md)
