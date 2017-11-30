---
title: "&lt;MethodInstantiation&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37e3ff3e792b8067b6d9409d799cf6e30350606a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
|[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|Yansıma ilke türü ve tüm üyeleri için geçerlidir.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<MethodInstantiation>` Öğesi kendi karşılık gelen açık genel yöntem çalışma zamanı yansıma ilkesini geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<Yöntem > öğesi](../../../docs/framework/net-native/method-element-net-native.md)
