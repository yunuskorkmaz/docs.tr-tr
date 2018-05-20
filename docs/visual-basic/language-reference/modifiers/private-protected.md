---
title: Korumalı özel (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>Korumalı özel (Visual Basic)

`Private Protected` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi. A `Private Protected` üyesidir içeren sınıfındaki tüm üyeleri tarafından yanı sıra içeren sınıfından türetilen tür tarafından erişilebilir, ancak yalnızca kendi içeren bütünleştirilmiş kodunda bulunursa. 

Belirleyebileceğiniz `Private Protected` yalnızca sınıfları; üyelerinde uygulayamazsınız `Private Protected` bir yapı üyelerine yapıları devraldığından.

`Private Protected` Erişim değiştiricisi Visual Basic 15,5 tarafından ve sonraki sürümlerinde desteklenir. Kullanmak için aşağıdaki öğeyi, Visual Basic proje (*.vbproj) dosyasına ekleyebilirsiniz. Visual Basic 15,5 sürece veya üzeri, sisteminizde yüklü gibi Visual Basic derleyici en son sürümü tarafından desteklenen tüm dil özellikleri yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Visual Studio'da F1 Yardımı seçme `private protected` ya da Yardım sağlar [özel](private.md) veya [korumalı](protected.md). IDE bileşik word yerine imleci altında tek belirteç seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Private Protected` yalnızca sınıf düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir sınıftaki tüm kod öğeleri erişebilir. Bir taban sınıftan türeyen ve aynı bütünleştirilmiş kodda yer alan herhangi bir sınıf kodda tüm erişebilir `Private Protected` öğeleri temel sınıf. Ancak, bir taban sınıftan türeyen ve farklı bir derlemede bulunan herhangi bir sınıf kodda temel sınıfı erişemiyor `Private Protected` öğeleri.

- **Erişim değiştiricileri.** Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*. Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 `Private Protected` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Sınıf bildirimi](../../../visual-basic/language-reference/statements/class-statement.md) iç içe bir sınıf  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) temsilcisi iç içe bir sınıf  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md) bir eumeration iç içe bir sınıf 
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [İnterface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md) bir arabiriminin iç içe bir sınıf 
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Yapı deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) yapısını iç içe bir sınıf 
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Arkadaş](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Korumalı Friend](./protected-friend.md)   
[Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
