---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb3ad0d39d47297b7d26a5c28cfbbc269ce99e44
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052407"
---
# <a name="runtime-directive-elements"></a>Çalışma Zamanı Yönerge Öğeleri
Çalışma zamanı yönergeleri (rd.xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğeleri destekler. Bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) hiyerarşik bir sunumunu için.  
  
 [\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)  
 Uygulama tarafından kullanılan tüm türler için çalışma zamanı yansıma ilke uygulanır ve birçok farklı uygulama türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir için kapsayıcı görevi görür. Bu bir alt öğesidir [ \<yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) öğesi.  
  
 [\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Çalışma zamanı İlkesi derlemedeki tüm türleri için geçerlidir. Bu bir alt öğesidir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.  
  
 [\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Kapsayıcı [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) yönergesi bir özniteliktir, çalışma zamanı İlkesi bu özniteliğin uygulandığı kod öğeleri için geçerlidir.  
  
 [\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)  
 .NET Native her çalışma zamanı yönergeleri dosyasının kök öğesi. Alt öğeleri olan [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)  
 Çalışma zamanı İlkesi, bir olay için geçerlidir. Bu bir alt öğesidir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<alan >](../../../docs/framework/net-native/field-element-net-native.md)  
 Çalışma zamanı ilkesi için bir alan için geçerlidir. Bu bir alt öğesidir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Çalışma zamanı ilkesi için bir genel tür veya yöntemin parametre türü için geçerlidir.  
  
 [\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Bu ilkeyi kapsayan tür veya yöntem uygulanmışsa, çalışma zamanı İlkesi bir türü için geçerlidir.  
  
 [\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)  
 Çalışma zamanı İlkesi derlemedeki tüm türleri için geçerlidir. Bu bir alt öğesidir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.  
  
 [\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)  
 Çalışma zamanı İlkesi, bir yönteme uygulanır. Bu bir alt öğesidir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Çalışma zamanı İlkesi oluşturulmuş bir genel yöntem için geçerlidir. Bu bir alt öğesidir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Çalışma zamanı ilkesi için bir ad alanındaki tüm türleri geçerlidir.  
  
 [\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Çalışma zamanı İlkesi bir yönteme geçirilen bağımsız değişken türü için geçerlidir.  
  
 [\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)  
 Çalışma zamanı İlkesi, bir özellik için geçerlidir. Bu bir alt öğesidir [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Çalışma zamanı İlkesi kapsayan türden devralınan tüm sınıflar için geçerlidir.  
  
 [\<türü >](../../../docs/framework/net-native/type-element-net-native.md)  
 Çalışma zamanı İlkesi, bir türü için geçerlidir.  
  
 [\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Çalışma zamanı İlkesi oluşturulmuş bir genel türü için geçerlidir.  
  
 [\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Tarafından temsil edilen bir türün çalışma zamanı ilkenin uygulanacağı bir <xref:System.Type> bir yönteme geçirilen bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RD.XML yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
