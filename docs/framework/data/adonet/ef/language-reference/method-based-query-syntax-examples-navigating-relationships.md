---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: İlişkilerde gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 450fa284254c9a78a287c922424f0deaafd7534f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692252"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Metot tabanlı sorgu söz dizimi örnekleri: İlişkilerde gezinme
Gezinti özellikleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunda varlıkları bulmak için kullanılan kısayol özellik. Bir varlıktan diğerine giderler veya ilgili varlıkları ilişkilendirme aracılığıyla tek bir varlık kümesi bir kullanıcı Gezinti özellikleri sağlar. Metot tabanlı sorgu söz dizimi örnekleri Gezinti özellikleri ile ilişkilerde gezinme konusunda bu konuda sunmaktadır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.  
  
 Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Örnek  
 Metot tabanlı sorgu söz dizimi kullanan aşağıdaki örnekte <xref:System.Linq.Queryable.SelectMany%2A> Soyadı tüm siparişleri kişileri almak için yöntemi olan "Zhou". `Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Örnek  
 Metot tabanlı sorgu söz dizimi aşağıdaki örnekte kullanan <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve Soyadı her kişi için toplam süre "Zhou" toplamıdır. `Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri. `Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplamak için gezinme özelliği her kişi için tüm siparişleri son.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Örnek  
 Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, "Zhou" Soyadı olan kişileri tüm siparişleri alır. `Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri. Kişinin adı ve sipariş anonim bir tür döndürülür.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` koleksiyonu almak için Gezinti özellikleri `Address` ve `Contact` her siparişle ilişkili nesneleri. Her bir siparişe şehri Seattle döndürülür için anonim bir tür içinde olan sokak adresi kişinin soyadı sayısı ve toplam süre satış siparişi.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Where` 1 Aralık 2003 sonra yapıldığı siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her siparişi için ayrıntıları almak için gezinme özelliği.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Gezinti özellikleri](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
