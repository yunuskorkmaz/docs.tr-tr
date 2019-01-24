---
title: 'Nasıl yapılır: Bilgi sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 9476144d84454aedc331214a55c77547697c378f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608420"
---
# <a name="how-to-query-for-information"></a>Nasıl yapılır: Bilgi sorgulama
Sorgulara [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda olarak aynı sözdizimini kullanır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Nesneler, başvurulan tek fark, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları bir veritabanında öğelerine eşleştirilir. Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşdeğer SQL sorguları yazma sorguları çevirir ve işlem sunucusuna gönderir.  
  
 Bazı özellikleri [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorguları özel dikkat ihtiyaç duyabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar. Daha fazla bilgi için [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## <a name="example"></a>Örnek  
 Londralı müşteriler listesi için aşağıdaki sorguyu ister. Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
