---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049267"
---
# <a name="runtime-directive-elements"></a>Çalışma Zamanı Yönerge Öğeleri
Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler. Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<Uygulama >](application-element-net-native.md)  
 , Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. Bu, [ \<yönergelerin >](directives-element-net-native.md) öğesinin bir alt öğesidir.  
  
 [\<Bütünleştirilmiş kod >](assembly-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md) öğelerinin bir alt öğesidir.  
  
 [\<Attribute>](attributeimplies-element-net-native.md)  
 Kapsayan tür > yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular. [ \<](type-element-net-native.md)  
  
 [\<Yönergeler >](directives-element-net-native.md)  
 .NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe. Alt öğeleri [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md).  
  
 [\<Olay >](event-element-net-native.md)  
 Bir olaya çalışma zamanı ilkesi uygular. Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<Alan >](field-element-net-native.md)  
 Çalışma zamanı ilkesini bir alana uygular. Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.  
  
 [\<Impliestype >](impliestype-element-net-native.md)  
 Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.  
  
 [\<Kitaplık >](library-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md) öğelerinin bir alt öğesidir.  
  
 [\<Yöntem >](method-element-net-native.md)  
 Bir yönteme çalışma zamanı ilkesi uygular. Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<Methodörneklemesi >](methodinstantiation-element-net-native.md)  
 Oluşturulan genel metoda çalışma zamanı ilkesi uygular. Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<Ad alanı >](namespace-element-net-native.md)  
 Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.  
  
 [\<Parametre >](parameter-element-net-native.md)  
 Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.  
  
 [\<Özellik >](property-element-net-native.md)  
 Çalışma zamanı ilkesini bir özelliğe uygular. Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<Alt türler >](subtypes-element-net-native.md)  
 Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.  
  
 [\<Tür >](type-element-net-native.md)  
 Bir türe çalışma zamanı ilkesi uygular.  
  
 [\<Typeörneklemesi >](typeinstantiation-element-net-native.md)  
 Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Yönteme geçirilen bir <xref:System.Type> bağımsız değişkenle temsil edilen türe çalışma zamanı ilkesi uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RD. xml yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
