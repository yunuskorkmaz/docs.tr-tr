---
description: 'Daha fazla bilgi edinin: Iki diziyi birleştirme'
title: İki Diziyi Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 5e48f3e2900bf53d042eb9c2aad6535bad9ec7e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773179"
---
# <a name="concatenate-two-sequences"></a>İki Diziyi Birleştirme

<xref:System.Linq.Queryable.Concat%2A>İki diziyi birleştirmek için işlecini kullanın.  
  
 <xref:System.Linq.Queryable.Concat%2A>İşleci, alıcı ve bağımsız değişken siparişlerinin aynı olduğu sıralı çoklu kümeler için tanımlanır.  
  
 SQL 'de sıralama sonuçları üretilmekte olan son adımdır. Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak uygulanır `UNION ALL` ve bağımsız değişkenlerinin sırasını korumaz. Sonuçların sonuçlarda doğru olduğundan emin olmak için sonuçları açıkça sıralediğinizden emin olun.  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` telefon ve faks numaralarının bir dizisini döndürmek için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` ad ve telefon numarası eşlemelerinin bir dizisini döndürmek için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
