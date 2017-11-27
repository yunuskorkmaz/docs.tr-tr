---
title: "Yöntem temelli sorgu sözdizimi örnekler: İlişkilerinde gezinme"
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
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7c5e1c17fbb0758cc395b6a76b7c0d1065be04a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Yöntem temelli sorgu sözdizimi örnekler: İlişkilerinde gezinme
Gezinti özelliklerinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunun varlıkları bulmak için kullanılan kısayol özellik. Gezinti özellikleri bir kullanıcının başka bir varlıktan gidin veya bir ilişki ile ilgili varlıklar için bir varlık kümesine izin verin. Bu konu, gezinti özellikleri sayesinde ilişkilerini gitmek nasıl yöntemi tabanlı sorgu sözdiziminde örnekleri sağlar [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.  
  
 Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Örnek  
 Yöntem temelli sorgu sözdizimini kullanır aşağıdaki örnekte <xref:System.Linq.Queryable.SelectMany%2A> Soyadı kişilerin tüm siparişleri almak için yöntemi olduğu "Zhou". `Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Örnek  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte kullanır <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve her kişi için Soyadı toplam süre "Zhou" toplamıdır. `Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için. `Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplanacak gezinti özelliği her kişi için tüm sipariş sonu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Örnek  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte "Zhou" Soyadı olan kişileri tüm siparişleri alır. `Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için. Kişinin adı ve siparişleri anonim bir tür döndürür.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` Gezinti özellikleri koleksiyonunu alma `Address` ve `Contact` nesneleri her sipariş ile ilişkilendirilmiş. Her biri Şehir Seattle siparişe döndürülür için anonim bir tür Soyadı ilgili kişi, adres sayısı ve toplam süre satış siparişi.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Where` 1 Aralık 2003'ten sonra yapılan siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her sipariş için ayrıntıları almak için gezinme özelliği.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gezinti özellikleri](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [LINQ to Entities sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
