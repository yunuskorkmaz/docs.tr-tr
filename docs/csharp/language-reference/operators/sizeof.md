---
title: sizeof işleci- C# başvuru
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 4852e1166a975b1a45c5bd905123a35fc846aa28
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513162"
---
# <a name="sizeof-operator-c-reference"></a>sizeof işleci (C# başvuru)

`sizeof` İşleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür. `sizeof` İşlecin bağımsız değişkeni, yönetilmeyen bir [türün](../builtin-types/unmanaged-types.md) adı veya yönetilmeyen bir tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresi olmalıdır.

Operatör güvenli olmayan bir bağlam gerektiriyor. [](../keywords/unsafe.md) `sizeof` Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:

|İfade|Sabit değer|
|---------|---------------|
|`sizeof(sbyte)`|1\.|
|`sizeof(byte)`|1\.|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1\.|

Ayrıca, `sizeof` işlecin işleneni bir [sabit](../keywords/enum.md) listesi türünün adı olduğunda güvenli olmayan bir bağlam kullanmanıza gerek kalmaz.

Aşağıdaki örnek `sizeof` işlecinin kullanımını gösterir:

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

İşleci `sizeof` , yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür. [Yapı](../keywords/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir. `sizeof` İşlecinin sonucu, *yönetilmeyen* bellekteki bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yönteminin sonuçlarından farklılık gösterebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [İşaretçiyle ilgili işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
