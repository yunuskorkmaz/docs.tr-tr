---
title: PLINQ ve TPL'deki Lambda İfadeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b1739bf8d98bbee49cf3cb3d83cac27796ccf72
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ ve TPL'deki Lambda İfadeleri
Görev paralel kitaplığı (TPL) birini birçok yöntem içerir <xref:System.Func%601?displayProperty=nameWithType> veya <xref:System.Action?displayProperty=nameWithType> giriş parametresi olarak temsilciler ailesi. Bu temsilci paralel döngü, görev veya sorgu için özel bir program mantığınızı geçirmek için kullanın. Kod örnekleri PLINQ yanı sıra TPL için lambda ifadeleri Bu temsilci satır içi kod blokları olarak örneklerini oluşturmak için kullanın. Bu konu, işlev ve eylem kısa bir giriş sağlar ve görev paralel kitaplığı ve PLINQ'da lambda ifadeleri kullanmayı gösterir.  
  
 **Not** genel olarak, temsilciler hakkında daha fazla bilgi için bkz [Temsilciler](../../csharp/programming-guide/delegates/index.md) ve [Temsilciler](../../visual-basic/programming-guide/language-features/delegates/index.md). C# ve Visual Basic lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Lambda ifadeleri](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>İşlev temsilcisi  
 A `Func` temsilci bir değer döndüren bir yöntem yalıtır. Bir işlev imzası son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir. Bir genel derleyici hataları nedenidir iki giriş parametreleri geçirin girişimi için bir <xref:System.Func%602?displayProperty=nameWithType>; aslında bu tür, yalnızca bir giriş parametresi alır. 17 sürümleri Framework sınıf kitaplığı tanımlar `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, vb. Yukarı aracılığıyla <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Eylem temsilcisi  
 A <xref:System.Action?displayProperty=nameWithType> temsilci yalıtan bir değer döndürmez veya döndüren bir yöntem (Visual Basic'te alt) [void](~/docs/csharp/language-reference/keywords/void.md). Bir eylem türü imzası tür parametreleri yalnızca giriş parametreleri temsil eder. FUNC gibi eylem, 17 sürümleri olan hiçbir tür parametreleri 16 türü parametrelerine sahip bir sürüm sürümünden Framework sınıf kitaplığı tanımlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> yöntemi lambda ifadeleri kullanarak işlev ve eylem temsilciler express nasıl gösterir.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
