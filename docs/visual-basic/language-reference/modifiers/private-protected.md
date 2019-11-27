---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351341"
---
# <a name="private-protected-visual-basic"></a>Özel korumalı (Visual Basic)

`Private Protected` anahtar sözcük birleşimi bir üye erişim değiştiricisidir. `Private Protected` üyeye, kapsayan sınıftaki tüm üyeler tarafından ve kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı derlemesinde bulunur.

Yalnızca sınıfların üyelerinde `Private Protected` belirtebilirsiniz; yapılar devralınamadığı için `Private Protected` bir yapının üyelerine uygulayamazsınız.

`Private Protected` erişim değiştiricisi Visual Basic 15,5 ve üzeri tarafından desteklenir. Bunu kullanmak için, Visual Basic projesi (\*. vbproj) dosyanıza aşağıdaki öğeyi ekleyebilirsiniz. Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../language-reference/configure-language-version.md).

> [!NOTE]
> Visual Studio 'da F1 Yardımı ' nı seçmek `private protected` [özel](private.md) veya [korumalı](protected.md)yardım sağlar. IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Private Protected` yalnızca sınıf düzeyinde kullanabilirsiniz. Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilir. Bir taban sınıftan türetilen ve aynı derlemede yer alan herhangi bir sınıftaki kod, temel sınıfın tüm `Private Protected` öğelerine erişebilir. Ancak, bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıftaki kod, temel sınıfa `Private Protected` öğelerine erişemez.

- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`Private Protected` değiştiricisi şu bağlamlarda kullanılabilir:

- İç içe bir sınıfın [sınıf ekstresi](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

- Sınıf içinde iç içe bir temsilcinin [temsilci ekstresi](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)

- Bir sınıfta iç içe geçmiş bir numaralandırmanın [enum bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- Bir sınıfta iç içe yerleştirilmiş bir arabirimin [arabirim ekstresi](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- Bir sınıfta iç içe yerleştirilmiş bir yapının [Yapı ekstresi](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
