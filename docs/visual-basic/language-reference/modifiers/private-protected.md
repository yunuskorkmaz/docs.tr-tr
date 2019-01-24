---
title: Özel korumalı (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 70f725712d52ad055ff69046096da10b8edfb67c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701150"
---
# <a name="private-protected-visual-basic"></a>Özel korumalı (Visual Basic)

`Private Protected` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur. A `Private Protected` üye olduğu tüm üyelerini içeren sınıfındaki yanı sıra içeren sınıfından türetilen türler tarafından erişilebilir, ancak yalnızca içeren, derlemesi içinde bulunan. 

Belirtebileceğiniz `Private Protected` yalnızca; sınıfların üyeleri üzerinde uygulayamazsınız `Private Protected` bir yapının üyelerine yapıları devraldığından.

`Private Protected` Erişim değiştiricisi, Visual Basic 15.5 ve sonraki sürümlerinde desteklenir. Bunu kullanmak için aşağıdaki öğeyi Visual Basic projenize ekleyebilirsiniz (\*.vbproj) dosya. Sisteminizde sürece Visual Basic 15.5 veya üzeri yüklü olduğu, en son sürümü Visual Basic derleyicisi tarafından desteklenen dil özellikleri yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için [Visual Basic dil sürümü ayarını](../../language-reference/configure-language-version.md).

> [!NOTE]
> Visual Studio'da F1 Yardımı seçme `private protected` ya da Yardım sağlayan [özel](private.md) veya [korumalı](protected.md). IDE bileşik sözcüğü yerine imleç altında tek belirteç seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Private Protected` yalnızca sınıf düzeyinde. Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilirsiniz. Kod, bir taban sınıftan türetilen ve aynı bütünleştirilmiş kodda yer alan herhangi bir sınıf içinde tüm erişebilir `Private Protected` öğeleri temel sınıf. Ancak, kod bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıf içinde temel sınıf erişemez `Private Protected` öğeleri.

- **Erişim değiştiricileri.** Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*. Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 `Private Protected` Bu bağlamda değiştirici kullanılabilir:  
  
 [Sınıf bildirimi](../../../visual-basic/language-reference/statements/class-statement.md) iç içe geçmiş bir sınıfı  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) temsilcisi, bir sınıf içinde iç içe geçmiş  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md) bir eumeration bir sınıf içinde iç içe geçmiş 
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [İnterface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md) bir arabiriminin, bir sınıf içinde iç içe geçmiş 
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Yapı bildirimi](../../../visual-basic/language-reference/statements/structure-statement.md) yapısını, bir sınıf içinde iç içe geçmiş 
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
