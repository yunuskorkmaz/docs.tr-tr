---
title: (C# üzerinde LINQ) sorgu ifadelerinde özel durumları işleme
description: C# LINQ Sorgu ifadelerinde özel durumları işleme hakkında bilgi edinin.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 344d11129814516a5ed3dcf0eba73a5ecbb96981
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403845"
---
# <a name="handle-exceptions-in-query-expressions"></a>Sorgu ifadelerinde özel durumları işleme

Sorgu ifadesi bağlamında herhangi bir yöntemi çağırmak mümkündür. Ancak, veri kaynağı içeriğini değiştirme ya da bir özel durum gibi bir yan etkisi oluşturabilmeniz için bir sorgu ifadesinde herhangi bir yöntemini çağırmadan kaçınmanızı öneririz. Bu örnek, genel özel durum işleme .NET yönergeleri ihlal etmeden sorgu ifadesinde yöntem çağırdığınızda, özel durumlarını oluşturma önlemek gösterilmektedir. Kabul edilebilir neden belirli bir bağlamda durum anladığınızda, belirli bir özel durum yakalamak için bu yönergeleri durumu. Daha fazla bilgi için [özel durumlar için en iyi yöntemler](../../standard/exceptions/best-practices-for-exceptions.md).

Son örnek bir sorgu yürütülürken bir özel durum gerekir, bu durumların nasıl işleneceğini gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel durum işleme bir sorgu ifadesinin dışındaki kod taşımak gösterilmektedir. Yalnızca yöntemi sorguya yerel değişkenlerin bağlı olmayan mümkün olur.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Örnek

Bazı durumlarda, sorgu yürütme hemen durdurmak için bir sorgu içinde oluşturulan bir özel durum için en iyi yanıtı olabilir. Aşağıdaki örnek, gelen sorgu gövdesi içinde oluşturulabilecek özel durumların nasıl işleneceğini gösterir. Varsayımında `SomeMethodThatMightThrow` durdurmak için sorgu yürütme gerektiren bir özel durum neden olabilir.

Unutmayın `try` blok kapsayan `foreach` döngüsü ve sorgunun kendisi. Bunun nedeni, `foreach` döngü, hangi sorgu gerçekte yürütülür noktasıdır. Daha fazla bilgi için [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

[Dil ile Tümleşik Sorgu (LINQ)](index.md)  
