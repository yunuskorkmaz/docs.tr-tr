---
title: stackalloc işleci- C# başvuru
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433836"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc işleci (C# başvuru)

`stackalloc` İşleci, yığında bir bellek bloğu ayırır. Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır. `stackalloc` İşleçle ayrılan belleği açık olarak serbest bırakılamaz. Yığın tarafından ayrılan bir bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve [ `fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenmiş olması gerekmez.

İfadesinde `stackalloc T[E]` `E` `int`, `T` [yönetilmeyen bir tür](../builtin-types/unmanaged-types.md) olmalıdır ve türünde bir ifade olmalıdır.

`stackalloc` İşlecin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:

- Aşağıdaki örnekte C# gösterildiği gibi <xref:System.Span%601?displayProperty=nameWithType> 7,2 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>veya sonraki bir sürümünden itibaren:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Bir<xref:System.Span%601> veya<xref:System.ReadOnlySpan%601> değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez.

  Bu türlerle çalıştığınızda, aşağıdaki örnekte gösterildiği gibi [koşullu](conditional-operator.md) veya atama `stackalloc` ifadelerinde bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > Mümkün olduğunda yığın <xref:System.Span%601> tarafından <xref:System.ReadOnlySpan%601> ayrılan bellekle çalışmak için veya türlerini kullanmanızı öneririz.

- Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md):

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Yukarıdaki örnekte gösterildiği gibi, işaretçi türleriyle çalışırken bir `unsafe` bağlam kullanmanız gerekir.

Yeni ayrılan belleğin içeriği tanımlı değil. 7,3 ile C# başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlatıcısı sözdizimini kullanabilirsiniz. Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Güvenlik

Kullanımı, ortak `stackalloc` dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak etkinleştirmektedir. Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [İşaretçiyle ilgili işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
