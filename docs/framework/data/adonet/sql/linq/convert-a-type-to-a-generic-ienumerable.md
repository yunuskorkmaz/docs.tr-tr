---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d75c9b9123b52b3e241bea1bbd1d302c406715e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032714"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Türü Genel IEnumerable Öğesine Dönüştürme
Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanılarak `Query`) SQL sorgu dönüştürün ve sunucu üzerinde yürütülen isteriz. Ancak `where` yan tümcesi kullanıcı tanımlı bir istemci-tarafı yöntemi başvurur (`isValidProduct`), dönüştürülemeyen SQL.  
  
 İstemci tarafı genel belirtmek için çözümüdür <xref:System.Collections.Generic.IEnumerable%601> uygulaması `where` genel değiştirilecek <xref:System.Linq.IQueryable%601>. Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
