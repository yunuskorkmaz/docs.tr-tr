---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128164"
---
# <a name="runtime-directive-elements"></a>Çalışma Zamanı Yönerge Öğeleri
Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler. Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .  
  
 [\<Application>](application-element-net-native.md)  
 , Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın. Bu, öğesinin bir alt [\<Directives>](directives-element-net-native.md) öğesidir.  
  
 [\<Assembly>](assembly-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 Kapsayan [\<Type>](type-element-net-native.md) yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular.  
  
 [\<Directives>](directives-element-net-native.md)  
 .NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe. Alt öğeleri [\<Application>](application-element-net-native.md) ve ' dir [\<Library>](library-element-net-native.md) .  
  
 [\<Event>](event-element-net-native.md)  
 Bir olaya çalışma zamanı ilkesi uygular. Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Field>](field-element-net-native.md)  
 Çalışma zamanı ilkesini bir alana uygular. Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.  
  
 [\<Library>](library-element-net-native.md)  
 Çalışma zamanı ilkesini derlemedeki tüm türlere uygular. Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .  
  
 [\<Method>](method-element-net-native.md)  
 Bir yönteme çalışma zamanı ilkesi uygular. Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Oluşturulan genel metoda çalışma zamanı ilkesi uygular. Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.  
  
 [\<Parameter>](parameter-element-net-native.md)  
 Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.  
  
 [\<Property>](property-element-net-native.md)  
 Çalışma zamanı ilkesini bir özelliğe uygular. Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.  
  
 [\<Type>](type-element-net-native.md)  
 Bir türe çalışma zamanı ilkesi uygular.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 Yönteme geçirilen bir bağımsız değişkenle temsil edilen türe çalışma zamanı ilkesi uygular <xref:System.Type> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RD. xml yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
