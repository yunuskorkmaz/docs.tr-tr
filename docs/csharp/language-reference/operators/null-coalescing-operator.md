---
title: ?? Operator - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689339"
---
# <a name="-operator-c-reference"></a>?? operator (C# Başvurusu)

`??` İşleci, null birleşim işleci çağrılır.  İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.

## <a name="remarks"></a>Açıklamalar

Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur). Kullanabileceğiniz `??` söz dizimsel anlamlılık (sağ el işlenenini) uygun bir değer döndürmek için işlecin sol işlenen null yapılabilir bir tür değeri null olduğunda. Null bir değer türü kullanmadan bir NULL olmayan değer türüne atamayı denerseniz, `??` işleci, bir derleme zamanı hatası oluşturacağını. Bir yayın kullanırsanız ve null yapılabilir değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durumu oluşturulur.

Daha fazla bilgi için [boş değer atanabilir türler](../../programming-guide/nullable-types/index.md).

Sonucu bir?? işleci, hem bağımsız değişkenlerinden sabitleri olsa bile, bir sabit değer için dikkate alınmaz.

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# işleçleri](index.md)
- [Boş Değer Atanabilir Tipler](../../programming-guide/nullable-types/index.md)
- [Hangi tam olarak 'Yükseltilmiş' anlamına mu?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)