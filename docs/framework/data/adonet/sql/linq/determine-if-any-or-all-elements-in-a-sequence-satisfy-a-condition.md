---
title: "Bir dizi veya tamamını öğelerinde bir koşul karşılayıp karşılamadığını belirlemek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b9b79915e94ed1015c7869692647c10da58f60
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Bir dizi veya tamamını öğelerinde bir koşul karşılayıp karşılamadığını belirlemek
<xref:System.Linq.Enumerable.All%2A> Operatörü döndürür `true` dizisindeki tüm öğeler bir koşulla eşleşmesi durumunda.  
  
 <xref:System.Linq.Queryable.Any%2A> Operatörü döndürür `true` bir dizisinde herhangi bir öğe koşulu uymazsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, en az bir sipariş olan müşterilerin bir dizi döndürür. `Where` / `where` Yan tümcesi hesaplar için `true` , verilen `Customer` içeren `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Visual Basic kodu siparişleri yerleştirilmedi müşteriler listesi belirler ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır sağlar.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnek siparişleri sahip müşteriler bir dizi döndürür bir `ShipCity` "C" ile başlayan. Return de dahil hiç siparişi olmayan müşteriler etkilenmez. (Tasarıma göre <xref:System.Linq.Queryable.All%2A> operatörü döndürür `true` boş bir dizi için.) Müşteri siparişi ortadan konsol çıktısı kullanarak `Count` işleci.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
