---
title: stackalloc işleci- C# başvuru
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: b2188bc94db42ab6d581c339f046ed81eb42d297
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239007"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc işleci (C# başvuru)

`stackalloc` işleci, yığında bir bellek bloğu ayırır. Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır. `stackalloc` işleçle ayrılan belleği açık olarak serbest bırakılamaz. Yığın tarafından ayrılan bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve bir [`fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenmemelidir.

`stackalloc` işlecinin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:

- Aşağıdaki örnekte C# gösterildiği gibi 7,2, <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>ile başlayarak:

  [!code-csharp[stackalloc span](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez.

  Bu türlerle çalışırken, aşağıdaki örnekte gösterildiği gibi, [koşullu](conditional-operator.md) veya atama ifadelerinde `stackalloc` bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc expression](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  8,0 ' C# den başlayarak, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenine izin verildiğinde diğer ifadelerin içinde `stackalloc` bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc in nested expressions](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Mümkün olduğunda yığın tarafından ayrılan bellekle çalışmak için <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> türlerini kullanmanızı öneririz.

- Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md):

  [!code-csharp[stackalloc pointer](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Yukarıdaki örnekte gösterildiği gibi, işaretçi türleriyle çalışırken `unsafe` bağlamı kullanmanız gerekir.

  İşaretçi türleri söz konusu olduğunda, değişkeni başlatmak için yalnızca yerel değişken bildiriminde bir `stackalloc` ifadesini kullanabilirsiniz.

Yeni ayrılan belleğin içeriği tanımlı değil. 7,3 ile C# başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlatıcısı sözdizimini kullanabilirsiniz. Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:

[!code-csharp[stackalloc initialization](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

İfade `stackalloc T[E]`, `T` [yönetilmeyen bir tür](../builtin-types/unmanaged-types.md) olmalıdır ve `E` [int](../builtin-types/integral-numeric-types.md)türünde bir ifade olmalıdır.

## <a name="security"></a>Güvenlik

`stackalloc` kullanımı, ortak dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak sunar. Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve [iç içe bağlamlardaki `stackalloc` izin ver](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) Özellik teklifi notuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [İşaretçiyle ilgili işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
