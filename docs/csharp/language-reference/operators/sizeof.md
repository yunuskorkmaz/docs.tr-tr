---
title: işleç boyutları - C# referans
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847293"
---
# <a name="sizeof-operator-c-reference"></a>işlecinin boyutları (C# referansı)

İşletici, `sizeof` belirli bir türdeki bir değişken tarafından işgal edilen bayt sayısını döndürür. `sizeof` İşleç için bağımsız değişken [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür veya yönetilmeyen bir tür olarak [sınırlandırılmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametre adı olmalıdır.

İşleç `sizeof` [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir. Ancak, aşağıdaki tabloda sunulan ifadeler, ilgili sabit değerlere derleme zaman olarak değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:

|İfadeler|Sabit değer|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
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
|`sizeof(bool)`|1|

`sizeof` Ayrıca, işleç operand [bir enum](../builtin-types/enum.md) türünün adı olduğunda güvenli olmayan bir bağlam kullanmanız gerekmez.

Aşağıdaki örnek, işleç `sizeof` kullanımını gösterir:

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

İşleç, `sizeof` yönetilen bellekte ortak dil çalışma süresi tarafından ayrılacak bir dizi bayt döndürür. [Yapı](../builtin-types/struct.md) türleri için, yukarıdaki örnekte gösterildiği gibi, bu değer herhangi bir dolgu içerir. `sizeof` İşleç sonucu, *yönetilmeyen* bellekte bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemin sonucundan farklı olabilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)işleç bölümünün [boyutlarına](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [İşaretçi bağlantılı işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
