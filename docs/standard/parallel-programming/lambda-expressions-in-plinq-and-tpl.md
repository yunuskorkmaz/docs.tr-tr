---
title: PLINQ ve TPL'deki Lambda İfadeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 3d985a003fe613699c89e38583f84be9e21b383d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290674"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ ve TPL'deki Lambda İfadeleri

Görev paralel kitaplığı (TPL), <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Action?displayProperty=nameWithType> giriş parametreleri olarak temsilci veya temsilcilerden birini alan birçok yöntem içerir. Bu temsilcileri, özel program mantığınızı paralel döngü, görev veya sorguya geçirmek için kullanabilirsiniz. Bu temsilcilerin satır içi kod blokları gibi örneklerini oluşturmak için, TPL ve PLıNQ için kod örnekleri lambda ifadeleri kullanır. Bu konu, Func ve Action 'a kısa bir giriş sağlar ve paralel kitaplığı ve PLıNQ görevinde lambda ifadelerinin nasıl kullanılacağını gösterir.

> [!NOTE]
> Genel olarak Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../csharp/programming-guide/delegates/index.md) ve [Temsilciler](../../visual-basic/programming-guide/language-features/delegates/index.md). C# ve Visual Basic lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [lambda ifadeleri](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="func-delegate"></a>Func temsilcisi

Bir `Func` temsilci, bir değer döndüren bir yöntemi kapsüller. Bir `Func` İmzada, son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir. Derleyici hatalarının yaygın nedenlerinden biri, ' a iki giriş parametresi geçirmeye çalışmasıdır <xref:System.Func%602?displayProperty=nameWithType> ; aslında bu tür yalnızca bir giriş parametresi alır. .Net, ' ın 17 sürümlerini (,, vb.) tanımlar `Func` <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Func%603?displayProperty=nameWithType> <xref:System.Func%6017?displayProperty=nameWithType> .

## <a name="action-delegate"></a>Eylem temsilcisi

Bir <xref:System.Action?displayProperty=nameWithType> temsilci, bir değeri döndürmeyen bir yöntemi (Visual Basic Sub) kapsüller. `Action`Tür imzasında, tür parametreleri yalnızca giriş parametrelerini temsil eder. Benzer şekilde `Func` , .net, `Action` 16 tür parametrelere sahip bir sürüm aracılığıyla hiçbir tür parametresi olmayan bir sürümden, ' nin 17 sürümlerini tanımlar.

## <a name="example"></a>Örnek

Yöntemi için aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> lambda ifadeleri kullanılarak hem Func hem de eylem temsilcilerinin nasıl ifade alınacağını gösterir.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](index.md)
