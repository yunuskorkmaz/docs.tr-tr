---
title: "Sorgu ifade sözdizimi örnekleri: İlişkilerinde gezinme"
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
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c029ce130e0bc8a6f959c6c27d863422794c22e5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Sorgu ifade sözdizimi örnekleri: İlişkilerinde gezinme
Gezinti özelliklerinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunun varlıkları bulmak için kullanılan kısayol özellik. Gezinti özellikleri bir kullanıcının başka bir varlıktan gidin veya bir ilişki ile ilgili varlıklar için bir varlık kümesine izin verin. Bu konu, gezinti özellikleri sayesinde ilişkilerini gitmek nasıl sorgu ifade sözdizimi örnekleri sağlar [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.  
  
 Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve her kişi için Soyadı toplam süre "Zhou" toplamıdır. `Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için. `Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplanacak gezinti özelliği her kişi için tüm sipariş sonu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte "Zhou" Soyadı olan kişileri tüm siparişleri alır. `Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için. Kişinin adı ve siparişleri anonim bir tür döndürür.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` Gezinti özellikleri koleksiyonunu alma `Address` ve `Contact` nesneleri her sipariş ile ilişkilendirilmiş. Her biri Şehir Seattle siparişe döndürülür için anonim bir tür Soyadı ilgili kişi, adres sayısı ve toplam süre satış siparişi.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Where` 1 Aralık 2003'ten sonra yapılan siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her sipariş için ayrıntıları almak için gezinme özelliği.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
