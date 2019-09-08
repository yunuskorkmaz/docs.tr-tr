---
title: 'Nasıl yapılır: Bilgi Sorgulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793542"
---
# <a name="how-to-query-for-information"></a>Nasıl yapılır: Bilgi Sorgulama
İçindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgular, içindeki [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]sorgularla aynı sözdizimini kullanır. Tek fark, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda başvurulan nesnelerin bir veritabanındaki öğelerle eşlendiğine sahiptir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]yazdığınız sorguları eşdeğer SQL sorgularına çevirir ve işlenmek üzere sunucuya gönderir.  
  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] Sorguların bazı özelliklerinin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalarda özel ilgilenilmesi gerekebilir. Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu, Londra 'dan müşterilerin bir listesini ister. Bu örnekte, `Customers` Northwind örnek veritabanındaki bir tablodur.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veritabanını Sorgulama](querying-the-database.md)
