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
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453006"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ ve TPL'deki Lambda İfadeleri

Görev Paralel Kitaplığı (TPL), giriş parametreleri <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Action?displayProperty=nameWithType> olarak temsilci veya aile deneyenlerden birini alan birçok yöntem içerir. Bu temsilciler, özel program mantığınızı paralel döngüye, göreve veya sorguya geçirmek için kullanırsınız. TPL ve PLINQ için kod örnekleri, bu temsilcilerin satır satırlı kod blokları olarak örneklerini oluşturmak için lambda ifadelerini kullanır. Bu konu Func ve Action'a kısa bir giriş sağlar ve Görev Paralel Kitaplığı ve PLINQ'da lambda ifadelerinin nasıl kullanılacağını gösterir.

> [!NOTE]
> Genel olarak temsilciler hakkında daha fazla bilgi [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md) [için, bkz.](../../csharp/programming-guide/delegates/index.md) C# ve Visual Basic'teki lambda ifadeleri hakkında daha fazla bilgi için [Lambda İfadeleri](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Lambda İfadeleri'ne](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)bakın.

## <a name="func-delegate"></a>Func Delegesi

Bir `Func` temsilci, bir değer döndüren bir yöntemi kapsüller. Bir `Func` imzada, en son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir. Derleyici hatalarının yaygın bir nedeni, iki giriş parametresini bir <xref:System.Func%602?displayProperty=nameWithType>; aslında bu tür yalnızca bir giriş parametresi alır. .NET 17 versiyonunu `Func`tanımlar <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType>: <xref:System.Func%603?displayProperty=nameWithType>, , ve <xref:System.Func%6017?displayProperty=nameWithType>benzeri kadar .

## <a name="action-delegate"></a>Eylem Delegesi

Bir <xref:System.Action?displayProperty=nameWithType> temsilci, bir değer döndürmeyen bir yöntemi (Visual Basic'te Alt) kapsüller. Bir `Action` tür imzasında, tür parametreleri yalnızca giriş parametrelerini temsil eder. Gibi `Func`, .NET 16 `Action`tür parametreleri olan bir sürüm aracılığıyla hiçbir tür parametreleri olan bir sürümden 17 sürümlerini tanımlar.

## <a name="example"></a>Örnek

<xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> Yöntem için aşağıdaki örnek, lambda ifadelerini kullanarak hem Func hem de Eylem temsilcilerinin nasıl ifade edilebildiğini gösterir.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
