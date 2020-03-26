---
title: stackalloc ifade - C# referans
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546607"
---
# <a name="stackalloc-expression-c-reference"></a>stackalloc ifadesi (C# başvurusu)

İfade, `stackalloc` yığında bellek bloğunu ayırır. Yöntem yürütülmesi sırasında oluşturulan bir yığın ayrılmış bellek bloğu, yöntem döndüğünde otomatik olarak atılır. 'ile ayrılan belleği açıkça `stackalloc`serbest kalamazsınız. Yığın ayrılmış bellek bloğu çöp [toplama](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` deyim](../keywords/fixed-statement.md)ile sabitlenmiş olması gerekmez.

Bir `stackalloc` ifadenin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:

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

Yığında bulunan bellek miktarı sınırlıdır. Yığına çok fazla bellek ayırırsanız, <xref:System.StackOverflowException> bir atılır. Bunu önlemek için aşağıdaki kurallara uyun:

- Ayırdığınız bellek miktarını `stackalloc`sınırlandırın:

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  Yığında kullanılabilir bellek miktarı kodun yürütüldürün bulunduğu ortama bağlı olduğundan, gerçek sınır değerini tanımlarken tutucu olun.

- İç `stackalloc` döngüleri kullanmaktan kaçının. Bellek bloğunu bir döngünün dışına ayırın ve döngü içinde yeniden kullanın.

Yeni ayrılan belleğin içeriği tanımsız. Kullanmadan önce paranızı almalısınız. Örneğin, tüm öğeleri <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> varsayılan değer türüne `T`ayarlayan yöntemi kullanabilirsiniz.

C# 7.3 ile başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlandırıcı sözdizimini kullanabilirsiniz. Aşağıdaki örnek, bunu yapmanın çeşitli yollarını göstermektedir:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

`stackalloc T[E]`İfadede, `T` [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür `E` olmalı ve negatif olmayan bir [int](../builtin-types/integral-numeric-types.md) değerine değer vermelidir.

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
- [Stackalloc Dos ve Don'ts](https://vcsjones.dev/2020/02/24/stackalloc/)
