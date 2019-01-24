---
title: İki diziyi birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 831905ca5a712bcb80d5bab1aef61a81d2ade1b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734290"
---
# <a name="concatenate-two-sequences"></a>İki diziyi birleştirme
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
