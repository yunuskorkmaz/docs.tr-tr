---
title: 'Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 8168c89a6edecd5f7e33a710c9a89c92a6f82005
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588238"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma
Bu örnek, bir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> kaynak diziye özel bir toplama işlevi uygulamak için yöntemin nasıl kullanılacağını gösterir.  
  
> [!WARNING]
> Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tamsayı dizisinin standart sapını hesaplar.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Bu örnek, PLINQ'ye özgü Toplam standart sorgu işlecinin aşırı yüklenmesini kullanır. Bu aşırı yük, <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak fazladan yük alır. Bu temsilci, toplanan sonuçlar üzerinde son hesaplamayı gerçekleştirmeden önce tüm iş parçacıklarının sonuçlarını birleştirir. Bu örnekte, tüm iş parçacıklarının toplamlarını bir araya getiriyoruz.  
  
 Lambda ifade gövdesi tek bir ifadeden oluşuyorsa, <xref:System.Func%602?displayProperty=nameWithType> temsilcinin dönüş değeri ifadenin değeridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
