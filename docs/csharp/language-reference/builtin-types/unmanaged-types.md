---
title: Yönetilmeyen türler- C# başvuru
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512070"
---
# <a name="unmanaged-types-c-reference"></a>Yönetilmeyen türler (C# başvuru)

**Yönetilmeyen tür** , başvuru türü olmayan veya oluşturulmuş tür olmayan (en az bir tür bağımsız değişkeni içeren bir tür) bir tür ve herhangi bir iç içe geçme düzeyinde başvuru türü veya oluşturulmuş tür alanları içermez. Diğer bir deyişle, yönetilmeyen bir tür aşağıdakilerden biridir:

- `sbyte``byte` ,,`int`, ,,`uint`, ,`ulong`,,, ,`double`, veya `float` `long` `ushort` `short` `char` `decimal``bool`
- Herhangi bir [numaralandırma](../keywords/enum.md) türü
- Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü
- Oluşturulmuş bir tür olmayan ve yalnızca yönetilmeyen türlerin alanlarını içeren Kullanıcı tanımlı herhangi bir [Yapı](../keywords/struct.md) türü

7,3 ile C# başlayarak, bir tür parametresinin işaretçiden yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [sizeof işleci](../operators/sizeof.md)
- [stackalloc işleci](../operators/stackalloc.md)
