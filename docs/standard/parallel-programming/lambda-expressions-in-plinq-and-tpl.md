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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a003c96e81996e304fc4347ed05bf7a255c224
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943838"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ ve TPL'deki Lambda İfadeleri
Görev paralel kitaplığı (TPL) birini birçok yöntem içerir <xref:System.Func%601?displayProperty=nameWithType> veya <xref:System.Action?displayProperty=nameWithType> giriş parametresi olarak temsilci ailesinden olan. Bu temsilciler paralel döngü, görev veya sorgu için özel bir program mantığınızda geçirmek için kullanın. TPL ve bunun yanı sıra PLINQ için kod örnekleri, bu temsilci olarak satır içi kod blokları bir örneğini oluşturmak için lambda ifadeleri kullanma. Bu konu, işlev ve eylem kısa bir giriş sağlar ve görev paralel kitaplığı ve PLINQ'da lambda ifadeleri kullanma işlemi gösterilmektedir.  
  
 **Not** genel temsilciler hakkında daha fazla bilgi için bkz [Temsilciler](../../csharp/programming-guide/delegates/index.md) ve [Temsilciler](../../visual-basic/programming-guide/language-features/delegates/index.md). C# ve Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Lambda ifadeleri](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>İşlev temsilcisi  
 A `Func` temsilci bir değer döndüren bir yöntem kapsüller. Bir işlev imzasında son veya sağdaki tür parametresi her zaman dönüş türünü belirtir. Derleyici hataları yaygın nedenlerinden biri olan iki giriş parametreleri geçirin denemek için bir <xref:System.Func%602?displayProperty=nameWithType>; aslında bu tür, yalnızca bir giriş parametresi alır. Framework sınıf kitaplığı 17 sürümlerini tanımlar `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, vb. Yukarı aracılığıyla <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Eylem temsilcisi  
 A <xref:System.Action?displayProperty=nameWithType> temsilci kapsülleyen bir değer döndürmez veya döndüren bir yöntemi (Visual Basic'te Sub) [void](~/docs/csharp/language-reference/keywords/void.md). Bir eylem türü imzada tür parametreleri yalnızca giriş parametrelerini temsil eder. FUNC gibi Framework sınıf kitaplığı 17 eylem sürümlerinden 16 tür parametreleri olan bir sürümü hiçbir tür parametresi yok bir sürümünü tanımlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneğin <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> yöntemi hem işlev ve eylem Temsilciler, lambda ifadeleri kullanarak express nasıl gösterir.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
