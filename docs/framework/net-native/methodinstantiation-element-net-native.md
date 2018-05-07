---
title: '&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltmethodinstantiationgt-element-net-native"></a>&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)
Çalışma zamanı yansıma İlkesi oluşturulan genel yöntem için geçerlidir.  
  
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
|`Signature`|Genel|İsteğe bağlı öznitelik. Yönteminin adlandırılmış parametreleri belirtir. Birden çok adlandırılmış parametreleri virgülle ayrılır. `Signature` Özniteliği aşırı yüklenmiş yöntemler ayırt etmek için kullanılır.|  
|`Arguments`|Genel|Gerekli öznitelik. Genel tür bağımsız değişkenleri belirtir. Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır.|  
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Hakkında bilgi için sorgulama veya bir yöntem numaralandırma kontrol eder, ancak çalışma zamanında dinamik herhangi çağırma etkinleştirmez.|  
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Programlama Oluşturucusu veya dinamik etkinleştirmek için yöntemi çalışma zamanı erişimi kontrol eder. Bu ilke üyesi çalışma zamanında dinamik olarak çağrılabilir sağlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_name*|Yöntem adı. Yöntem türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.|  
  
## <a name="signature-attribute"></a>İmza özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_signature*|Yöntem adlandırılmış parametreleri belirtir. Birden çok parametre varsa, bunların virgülle ayrılır.|  
  
## <a name="arguments-attribute"></a>Bağımsız değişkenler özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*method_arguments*|Genel tür bağımsız değişkenleri belirtir. Birden fazla bağımsız değişken varsa, bunların virgülle ayrılır. Her bağımsız değişken tam olarak nitelenmiş tür adını oluşmalıdır.|  
  
## <a name="all-other-attributes"></a>Tüm diğer özniteliklerle  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*policy_setting*|Bu ilke türü yöntemi için geçerli ayar. Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`. Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<MethodInstantiation>` Öğesi kendi karşılık gelen açık genel yöntem çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<Yöntem > öğesi](../../../docs/framework/net-native/method-element-net-native.md)
