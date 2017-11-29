---
title: "Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> yöntemi bir özel toplama işlevi için kaynak sıradaki uygular.  
  
> [!WARNING]
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tamsayı bir dizi standart sapmayı hesaplar.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Bu örnek bir aşırı yüklemesini PLINQ için benzersizdir toplama standart sorgu işleci kullanır. Bu aşırı fazladan alır <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak. Toplanan sonuçlarına son hesaplama gerçekleştirmeden önce bu temsilci tüm iş parçacıklarının gelen sonuçları birleştirir. Bu örnekte, biz birlikte tüm iş parçacıklarının SUM'ları ekleyin.  
  
 Lambda ifadesi gövdesi tek bir ifade, dönüş değerini oluşuyorsa unutmayın <xref:System.Func%602?displayProperty=nameWithType> temsilci ifade değerdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
