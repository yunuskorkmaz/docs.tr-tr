---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362235"
---
# <a name="private-protected-visual-basic"></a>Özel korumalı (Visual Basic)

`Private Protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Bir `Private Protected` üyeye, kapsayan sınıfındaki tüm üyeler tarafından erişilebilir ve ancak kapsayan sınıftan türetilmiş türler, ancak yalnızca kendi kapsayıcı derlemesinde bulunur.

`Private Protected`Yalnızca sınıfların üyelerinde belirtebilirsiniz; `Private Protected` yapılar devralınamadığı için bir yapının üyelerine uygulayamazsınız.

`Private Protected`Erişim değiştiricisi Visual Basic 15,5 ve üzeri sürümlerde desteklenir. Bunu kullanmak için, Visual Basic projesi ( \* . vbproj) dosyanıza aşağıdaki öğeyi ekleyebilirsiniz. Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../configure-language-version.md).

> [!NOTE]
> Visual Studio 'da F1 Yardımı ' nı seçmek, `private protected` [özel](private.md) veya [korumalı](protected.md)için yardım sağlar. IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Private Protected`Yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilir. Bir taban sınıftan türetilen ve aynı derlemede yer alan herhangi bir sınıftaki kod, `Private Protected` temel sınıfın tüm öğelerine erişebilir. Ancak, bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıftaki kod, temel sınıf `Private Protected` öğelerine erişemez.

- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

`Private Protected`Değiştirici şu bağlamlarda kullanılabilir:

- İç içe bir sınıfın [sınıf ekstresi](../statements/class-statement.md)

- [Const Deyimi](../statements/const-statement.md)

- [Declare Deyimi](../statements/declare-statement.md)

- Sınıf içinde iç içe bir temsilcinin [temsilci ekstresi](../statements/delegate-statement.md)

- [Dim Deyimi](../statements/dim-statement.md)

- Bir sınıfta iç içe geçmiş bir numaralandırmanın [enum bildirimi](../statements/enum-statement.md)

- [Event Deyimi](../statements/event-statement.md)

- [Function Deyimi](../statements/function-statement.md)

- Bir sınıfta iç içe yerleştirilmiş bir arabirimin [arabirim ekstresi](../statements/interface-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- Bir sınıfta iç içe yerleştirilmiş bir yapının [Yapı ekstresi](../statements/structure-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Geneldir](public.md)
- [Korunamadı](protected.md)
- [Dost](friend.md)
- [Özelleştirme](private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
