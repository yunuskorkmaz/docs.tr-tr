---
title: 'Nasıl yapılır: bilgi sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634657"
---
# <a name="how-to-query-for-information"></a>Nasıl yapılır: bilgi sorgulama
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları LINQ içindeki sorgularla aynı sözdizimini kullanır. Tek fark, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda başvurulan nesnelerin bir veritabanındaki öğelerle eşlendiğine sahiptir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir.  
  
 LINQ sorgularının bazı özelliklerinin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalarda özel ilgilenilmesi gerekebilir. Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu, Londra 'dan müşterilerin bir listesini ister. Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veritabanını Sorgulama](querying-the-database.md)
