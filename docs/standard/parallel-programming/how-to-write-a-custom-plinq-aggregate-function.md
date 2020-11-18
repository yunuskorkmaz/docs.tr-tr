---
title: 'Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: d04f90e9c763c8ddba5ba07b650ffb878869ff3a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825474"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma
Bu örnek, <xref:System.Linq.ParallelEnumerable.Aggregate%2A> bir kaynak dizisine özel toplama işlevi uygulamak için yönteminin nasıl kullanılacağını gösterir.  
  
> [!WARNING]
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tamsayı dizisinin standart sapmasını hesaplar.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Bu örnek, PLıNQ için benzersiz olan toplam standart sorgu işlecinin aşırı yüklemesini kullanır. Bu aşırı yükleme <xref:System.Func%603?displayProperty=nameWithType> , üçüncü giriş parametresi olarak ek sürer. Bu temsilci, toplanan sonuçlarda nihai hesaplamayı gerçekleştirmeden önce tüm iş parçacıklarından sonuçları birleştirir. Bu örnekte, tüm iş parçacıklarından toplamları toplayın.  
  
 Lambda ifadesi gövdesi tek bir ifadeden oluşuyorsa, temsilcinin dönüş değeri <xref:System.Func%602?displayProperty=nameWithType> ifadenin değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
