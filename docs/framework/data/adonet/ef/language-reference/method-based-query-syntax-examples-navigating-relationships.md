---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: bb40d10165592b25cc6afc1eac799a05b4504e8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191976"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme

Entity Framework gezinti özellikleri, varlıkların sonunda varlıkların yerini bulmak için kullanılan kısayol özellikleridir. Gezinti özellikleri, bir kullanıcının bir varlıktan diğerine veya bir varlıktan bir ilişki kümesi aracılığıyla ilgili varlıklara dolaşmayı sağlar. Bu konu, LINQ to Entities sorgularda gezinti özellikleri aracılığıyla ilişkilerde nasıl geziniminin Yöntem tabanlı sorgu söz dizimine örnekler sağlar.  
  
 Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Örnek  

 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, <xref:System.Linq.Queryable.SelectMany%2A> son adı "Zhou" olan kişilerin tüm emirlerini almak için yöntemini kullanır. `Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Örnek  

 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> son adı "Zhou" olan her kişi için tüm Iletişim kimliklerini ve toplam toplamı almak için yöntemini kullanır. `Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` . `Sum`Yöntemi, her bir `Contact.SalesOrderHeader` kişi için tüm siparişlerin ödenmesi gereken toplam miktarı toplamak için gezinti özelliğini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Örnek  

 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, son adı "Zhou" olan kişilerin tüm emirlerini alır. `Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` . Kişinin adı ve siparişleri anonim bir türde döndürülür.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, ve ' `SalesOrderHeader.Address` `SalesOrderHeader.Contact` nin `Address` `Contact` her bir siparişle ilişkili nesneleri ve koleksiyonunu almak için ve gezinti özelliklerini kullanır. Kişinin Soyadı, sokak adresi, satış siparişi numarası ve Seattle şehrine yönelik her bir sipariş için bir anonim türde döndürülen toplam ad.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Where` 1 aralık 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından `order.SalesOrderDetail` her bir siparişin ayrıntılarını almak için gezinti özelliğini kullanır.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
