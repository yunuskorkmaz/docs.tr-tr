---
title: İki Diziyi Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: a2f2510cb334f4e22a7b0c6015a0a93b4dc11579
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142785"
---
# <a name="concatenate-two-sequences"></a>İki Diziyi Birleştirme
Kullanım <xref:System.Linq.Queryable.Concat%2A> iki diziyi birleştirme için işleci.  
  
 <xref:System.Linq.Queryable.Concat%2A> İşleci siparişleri alıcı ve bağımsız değişken olduğu aynı sıralı multisets için tanımlanır.  
  
 Sonuçları üretti önce SQL sıralama son adımdır. Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerinin sırası korumaz. Sonuçlarda doğru sıralama emin olmak için açıkça sonuçlarını sıralama emin olun.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizisini döndürmek için `Customer` ve `Employee` telefon ve Faks numaraları.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizisini döndürmek için `Customer` ve `Employee` adlandırın ve telefon numarası eşlemeleri.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
