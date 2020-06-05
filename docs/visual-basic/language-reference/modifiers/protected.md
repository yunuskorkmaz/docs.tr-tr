---
title: Korumalı
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398226"
---
# <a name="protected-visual-basic"></a>Korumalı (Visual Basic)

Bir veya daha fazla tanımlanmış programlama öğesinin yalnızca kendi sınıfının içinden veya türetilmiş bir sınıftan erişilebilir olduğunu belirten bir üye erişim değiştiricisi.

## <a name="remarks"></a>Açıklamalar

Bazen bir sınıfta tanımlanan programlama öğesi hassas veriler veya kısıtlı kod içeriyorsa ve öğeye erişimi sınırlandırmak istiyorsanız. Ancak, sınıf devralınabilir ise ve türetilmiş sınıfların hiyerarşisini düşünüyorsanız, bu türetilmiş sınıfların verilere veya koda erişmesi gerekebilir. Böyle bir durumda, öğesinin hem taban sınıftan hem de tüm türetilmiş sınıflardan erişilebilir olmasını istersiniz. Bu şekilde bir öğeye erişimi sınırlandırmak için, ile bildirimini yapabilirsiniz `Protected` .

> [!NOTE]
> `Protected`Erişim değiştiricisi iki farklı değiştiriciyle birleştirilebilir:
>
> - [Protected Friend](protected-friend.md) değiştiricisi, bir sınıf üyesini türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getirir.
> - [Özel korumalı](private-protected.md) değiştirici, bir sınıf üyesini türetilmiş türler tarafından erişilebilir hale getirir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde.

## <a name="rules"></a>Kurallar

**Bildirim bağlamı.** `Protected`Yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilir. Bir taban sınıftan türetilen herhangi bir sınıftaki kod, `Protected` temel sınıfın tüm öğelerine erişebilir. Bu, tüm türetme oluşumlarında geçerlidir. Bu, bir sınıfın `Protected` temel sınıfın temel sınıfının öğelerine erişebileceği anlamına gelir.

     Korumalı erişim arkadaş erişiminin bir üst kümesi veya alt kümesi değil.

- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

`Protected`Değiştirici şu bağlamlarda kullanılabilir:

- [Class Deyimi](../statements/class-statement.md)

- [Const Deyimi](../statements/const-statement.md)

- [Declare Deyimi](../statements/declare-statement.md)

- [Delegate Deyimi](../statements/delegate-statement.md)

- [Dim Deyimi](../statements/dim-statement.md)

- [Enum Deyimi](../statements/enum-statement.md)

- [Event Deyimi](../statements/event-statement.md)

- [Function Deyimi](../statements/function-statement.md)

- [Interface Deyimi](../statements/interface-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- [Structure Yapısı](../statements/structure-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Geneldir](public.md)
- [Dost](friend.md)
- [Özelleştirme](private.md)
- [Özel korumalı](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
