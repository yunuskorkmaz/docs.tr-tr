---
title: Yönetilmeyen türler- C# başvuru
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374110"
---
# <a name="unmanaged-types-c-reference"></a>Yönetilmeyen türler (C# başvuru)

Bir tür, aşağıdaki türlerden biri ise, **yönetilmeyen bir türdür** :

- `sbyte``byte` ,,`int`, ,,`uint`, ,`ulong`,,, ,`double`, veya `float` `long` `ushort` `short` `char` `decimal``bool`
- Herhangi bir [numaralandırma](../keywords/enum.md) türü
- Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü
- Yalnızca yönetilmeyen türlerin ve [](../keywords/struct.md) 7,3 ve önceki sürümlerde bulunan C# alanları içeren Kullanıcı tanımlı herhangi bir yapı türü, oluşturulmuş bir tür değildir (en az bir tür bağımsız değişkeni içeren bir tür)

7,3 ile C# başlayarak, bir tür parametresinin işaretçiden yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.

8,0 ' C# den başlayarak, aşağıdaki örnekte gösterildiği gibi, yalnızca yönetilmeyen türlerin alanlarını içeren *oluşturulmuş* bir yapı türü de yönetilmez:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Genel bir yapı, yönetilmeyen ve yönetilmeyen oluşturulmuş türlerin kaynağı olabilir. Yukarıdaki örnek, genel bir struct `Coords<T>` tanımlar ve yönetilmeyen oluşturulmuş türlerin örneklerini gösterir. Yönetilmeyen bir tür `Coords<object>`örneği. Yönetilmeyen değildir çünkü `object` türünde alanları vardır, yönetilmeyen değildir. Oluşturulan *Tüm* türlerin yönetilmeyen türler olmasını istiyorsanız, genel bir yapının tanımında `unmanaged` kısıtlamayı kullanın:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [sizeof işleci](../operators/sizeof.md)
- [stackalloc işleci](../operators/stackalloc.md)
