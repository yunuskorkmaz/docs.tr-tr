---
title: stackalloc işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025008"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc işleci (C# Başvurusu)

`stackalloc` İşleci bir yığında bellek bloğu ayırır. Bu yöntem döndürüldüğünde ayrılmış bellek bloğu yöntem yürütme işlemi sırasında oluşturulan bir yığın otomatik olarak atılır. Açıkça atanan bellek bırakılamıyor `stackalloc` işleci. Bir yığın ayrılmış bellek bloğu konusu değil [çöp toplama](../../../standard/garbage-collection/index.md) ve sabitlenmiş olmak zorunda değildir [ `fixed` deyimi](../keywords/fixed-statement.md).

Sonucu atayabilirsiniz `stackalloc` şu türlerden birinde bir değişkene işleci:

- İle başlayarak C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Kullanmak zorunda değilsiniz bir [güvenli olmayan](../keywords/unsafe.md) yığın atadığınızda içerik ayrılan bellek bloğu için bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkeni.

  Bu türler ile çalışırken kullanabileceğiniz bir `stackalloc` ifadesinde [koşullu](conditional-operator.md) veya atama ifadeleri, aşağıdaki örnekte gösterildiği gibi:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > Kullanmanızı öneririz <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> ayrılan bellek mümkün olduğunda yığın ile çalışmak için türleri.

- A [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md)aşağıdaki örnekte gösterildiği gibi:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Yukarıdaki örnekte gösterildiği gibi kullanmalısınız bir `unsafe` işaretçi türleri ile çalışırken bağlamı.

Yeni ayrılan bellek içeriğini tanımsızdır. İle başlayarak C# 7.3, yeni ayrılan bellek içeriğini tanımlamasını dizi Başlatıcısı sözdizimi kullanabilirsiniz. Aşağıdaki örnek, bunu yapmak için çeşitli yollar gösterir:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Güvenlik

Kullanımını `stackalloc` otomatik olarak ortak dil çalışma zamanı (CLR) arabellek taşması algılama özelliklerini etkinleştirir. İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [İşaretçi bağlantılı işleçleri](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
