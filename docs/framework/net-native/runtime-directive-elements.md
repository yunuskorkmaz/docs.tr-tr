---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e8f0902e0d3ebd010ff639b329707881c29fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="runtime-directive-elements"></a>Çalışma Zamanı Yönerge Öğeleri
Çalışma zamanı yönergeleri (rd.xml) dosya biçimi şu çalışma zamanı yönerge öğeleri destekler. Bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) hiyerarşik bir gösterim için.  
  
 [\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)  
 Çalışma zamanı yansıma ilke uygulama tarafından kullanılan tüm türleri için geçerlidir ve uygulama genelinde türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür. Bu bir alt öğesi değil [ \<yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) öğesi.  
  
 [\<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Derlemedeki tüm türleri runnntime ilke uygulanır. Bu bir alt öğesi değil [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.  
  
 [\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Varsa, içeren [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) yönergesi bir özniteliktir, çalışma zamanı İlkesi bu öznitelik uygulanan kod öğelere uygulanır.  
  
 [\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)  
 Her çalışma zamanı yönergeleri dosyasının kök öğesinin [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Alt öğeleri olan [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)  
 Çalışma zamanı İlkesi bir olay için geçerlidir. Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)  
 Çalışma zamanı İlkesi bir alan için geçerlidir. Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Çalışma zamanı İlkesi genel türü veya yöntemi parametresinin türü için geçerlidir.  
  
 [\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Bu ilkeyi içeren türü veya yöntemi uygulanmışsa, çalışma zamanı İlkesi bir türü için geçerlidir.  
  
 [\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)  
 Çalışma zamanı İlkesi derleme içindeki tüm türler için geçerlidir. Bu bir alt öğesi değil [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.  
  
 [\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)  
 Çalışma zamanı ilke için bir yöntem uygulanır. Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Çalışma zamanı İlkesi oluşturulan genel yöntem için geçerlidir. Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Çalışma zamanı İlkesi, bir ad alanı içindeki tüm türler için geçerlidir.  
  
 [\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Çalışma zamanı İlkesi bir yönteme geçirilen bağımsız değişken türü için geçerlidir.  
  
 [\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)  
 Çalışma zamanı İlkesi bir özellik için geçerlidir. Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.  
  
 [\<türü >](../../../docs/framework/net-native/type-element-net-native.md)  
 Çalışma zamanı ilke türü için geçerlidir.  
  
 [\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Çalışma zamanı İlkesi oluşturulmuş bir genel türü için geçerlidir.  
  
 [\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Tarafından temsil edilen türü çalışma zamanı ilkenin uygulandığı bir <xref:System.Type> yöntemi için bağımsız değişken geçirildi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RD.XML yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
