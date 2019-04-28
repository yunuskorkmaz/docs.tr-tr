---
title: 'Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bbb9b7cf33eda1cc479759740e6c5325f635fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608768"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> yöntemi bir kaynak dizisi için bir özel toplama işlevi uygular.  
  
> [!WARNING]
>  Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tamsayı bir dizi standart sapmayı hesaplar.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Bu örnekte, bir PLINQ için benzersiz olan toplama standart sorgu işleci aşırı yüklemesi kullanılır. Bu aşırı ek alan <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak. Toplu sonuçları son hesaplama gerçekleştirmeden önce bu temsilci tüm iş parçacıklarının sonuçları birleştirir. Bu örnekte biz birlikte tüm iş parçacıklarından SUM'ları ekleyin.  
  
 Bir lambda ifadesi gövdesi, dönüş değeri gibi tek bir ifade oluşuyorsa unutmayın <xref:System.Func%602?displayProperty=nameWithType> ifadenin değerini temsilcisidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
