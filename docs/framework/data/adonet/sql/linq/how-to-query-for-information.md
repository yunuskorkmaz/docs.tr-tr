---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bilgi sorgula'
title: 'Nasıl yapılır: Bilgi Sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 41774834fe919b28d71691203941cb8e0a8a0397
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802027"
---
# <a name="how-to-query-for-information"></a>Nasıl yapılır: Bilgi Sorgulama

İçindeki sorgular [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] LINQ içindeki sorgularla aynı sözdizimini kullanır. Tek fark, sorgularda başvurulan nesnelerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanındaki öğelerle eşlendiğine sahiptir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir.  
  
 LINQ sorgularının bazı özelliklerinin uygulamalarda özel ilgilenilmesi gerekebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki sorgu, Londra 'dan müşterilerin bir listesini ister. Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veritabanını Sorgulama](querying-the-database.md)
