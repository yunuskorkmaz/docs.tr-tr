---
title: stackalloc operatörü - C# referans
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846264"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc operatörü (C# referansı)

İşleç `stackalloc` yığına bir bellek bloğu ayırır. Yöntem yürütülmesi sırasında oluşturulan bir yığın ayrılmış bellek bloğu, yöntem döndüğünde otomatik olarak atılır. `stackalloc` İşleç ile ayrılan belleği açıkça boşaltamazsınız. Yığın ayrılmış bellek bloğu çöp [toplama](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` deyim](../keywords/fixed-statement.md)ile sabitlenmiş olması gerekmez.

İşleticinin `stackalloc` sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:

- C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> ile <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>başlayarak veya aşağıdaki örnekte görüldüğü gibi:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Bir yığın ayrılmış bellek [unsafe](../keywords/unsafe.md) bloğu bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenata atadığınızda güvenli olmayan bir bağlam kullanmanız gerekmez.

  Bu türlerle çalışırken, aşağıdaki örnekte görüldüğü gibi `stackalloc` [koşullu](conditional-operator.md) veya atama ifadelerinde bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  C# 8.0 ile başlayarak, `stackalloc` aşağıdaki örnekte görüldüğü <xref:System.Span%601> gibi, bir veya <xref:System.ReadOnlySpan%601> değişkene izin verildiğinde diğer ifadelerin içinde bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Mümkün olduğunda <xref:System.Span%601> <xref:System.ReadOnlySpan%601> yığın ayrılmış bellekle çalışmak için kullanmanızı veya türleri kullanmanızı öneririz.

- Aşağıdaki örnekte görüldüğü gibi bir [işaretçi türü:](../../programming-guide/unsafe-code-pointers/pointer-types.md)

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Önceki örnekte de görüldüğü gibi, `unsafe` işaretçi türleri ile çalışırken bir bağlam kullanmanız gerekir.

  İşaretçi türleri söz konusu olduğunda, `stackalloc` değişkeni başlatmak için yalnızca yerel bir değişken bildiriminde bir ifade kullanabilirsiniz.

Yeni ayrılan belleğin içeriği tanımsız. C# 7.3 ile başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlandırıcı sözdizimini kullanabilirsiniz. Aşağıdaki örnek, bunu yapmanın çeşitli yollarını göstermektedir:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

`stackalloc T[E]`İfadede, `T` [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür `E` olmalı ve yazı [int](../builtin-types/integral-numeric-types.md)bir ifadesi olmalıdır.

## <a name="security"></a>Güvenlik

Otomatik `stackalloc` olarak kullanılması, ortak dil çalışma zamanında (CLR) arabellek taşma algılama özelliklerini etkinleştirir. Arabellek taşması algılanırsa, kötü amaçlı kod yürütülme olasılığını en aza indirmek için işlem mümkün olduğunca çabuk sonlandırılır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve iç içe [alınan bağlamlarda `stackalloc` İzin'e](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) ilişkin teklif notuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [İşaretçi bağlantılı işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
