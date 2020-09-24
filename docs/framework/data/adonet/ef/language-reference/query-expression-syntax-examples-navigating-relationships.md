---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: c09a0458f5b0b7d313da3379b5dda9b969eaf7e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156803"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme

Entity Framework gezinti özellikleri, varlıkların sonunda varlıkların yerini bulmak için kullanılan kısayol özellikleridir. Gezinti özellikleri, bir kullanıcının bir varlıktan diğerine veya bir varlıktan bir ilişki kümesi aracılığıyla ilgili varlıklara dolaşmayı sağlar. Bu konuda, LINQ to Entities sorgularda gezinti özellikleri aracılığıyla ilişkilerde nasıl geziniminin sorgu ifadesi sözdiziminde örnekler verilmektedir.  
  
 Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> son adı "Zhou" olan her kişi için tüm Iletişim kimliklerini ve toplam toplamını almak için yöntemini kullanır. `Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` . `Sum`Yöntemi, her bir `Contact.SalesOrderHeader` kişi için tüm siparişlerin ödenmesi gereken toplam miktarı toplamak için gezinti özelliğini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, son adı "Zhou" olan kişilerin tüm emirlerini alır. `Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` . Kişinin adı ve siparişleri anonim bir türde döndürülür.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `SalesOrderHeader.Address` ve ' `SalesOrderHeader.Contact` nin `Address` her bir `Contact` siparişle ilişkili nesneleri ve koleksiyonunu al ve gezinti özelliklerini kullanır. Kişinin Soyadı, sokak adresi, satış siparişi numarası ve Seattle şehrine yönelik her bir sipariş için bir anonim türde döndürülen toplam ad.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Where` 1 aralık 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından `order.SalesOrderDetail` her bir siparişin ayrıntılarını almak için gezinti özelliğini kullanır.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
