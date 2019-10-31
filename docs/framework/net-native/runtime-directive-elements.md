---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128164"
---
# <a name="runtime-directive-elements"></a>Çalışma Zamanı Yönerge Öğeleri
Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler. Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<uygulama >](application-element-net-native.md)  
 , Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. Bu, [\<yönergelerinin >](directives-element-net-native.md) öğesinin bir alt öğesidir.  
  
 [Derleme > \<](assembly-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md) öğelerinin bir alt öğesidir.  
  
 [\<Attribute>](attributeimplies-element-net-native.md)  
 Kendi kapsayıcı [\<türü >](type-element-net-native.md) yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular.  
  
 [\<yönergeler >](directives-element-net-native.md)  
 .NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe. Alt öğeleri [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md).  
  
 [\<olayı >](event-element-net-native.md)  
 Bir olaya çalışma zamanı ilkesi uygular. Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<alan >](field-element-net-native.md)  
 Çalışma zamanı ilkesini bir alana uygular. Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.  
  
 [\<ımpliestype >](impliestype-element-net-native.md)  
 Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.  
  
 [\<kitaplığı >](library-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md) öğelerinin bir alt öğesidir.  
  
 [\<yöntemi >](method-element-net-native.md)  
 Bir yönteme çalışma zamanı ilkesi uygular. Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<Methodörneklemesi >](methodinstantiation-element-net-native.md)  
 Oluşturulan genel metoda çalışma zamanı ilkesi uygular. Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<ad alanı >](namespace-element-net-native.md)  
 Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.  
  
 [\<parametresi >](parameter-element-net-native.md)  
 Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.  
  
 [\<Özellik >](property-element-net-native.md)  
 Çalışma zamanı ilkesini bir özelliğe uygular. Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.  
  
 [\<alt türleri >](subtypes-element-net-native.md)  
 Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.  
  
 [\<türü >](type-element-net-native.md)  
 Bir türe çalışma zamanı ilkesi uygular.  
  
 [\<Typeörneklemesi >](typeinstantiation-element-net-native.md)  
 Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Bir yönteme geçirilen <xref:System.Type> bağımsız değişkeniyle temsil edilen türe çalışma zamanı ilkesi uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RD. xml yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
