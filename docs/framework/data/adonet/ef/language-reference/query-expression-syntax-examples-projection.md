---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: b5139cc310689eb05833ead8d35c03d02eb2fc58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398426"
---
# <a name="query-expression-syntax-examples-projection"></a>Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon
Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak `From … From …` için `Select` yönteminin ve anahtar sözcüklerinin nasıl kullanılacağı gösterilmektedir. `From … From …`, `SelectMany` yönteminin sorgu tabanlı eşdeğeri olur. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a>Seçim  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Product` tablodaki tüm <xref:System.Linq.Enumerable.Select%2A> satırları döndürmek ve ürün adlarını göstermek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca <xref:System.Linq.Enumerable.Select%2A> ürün adlarından oluşan bir dizi döndürmek için kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> `Product.Name` ve `Product.ProductID` özelliklerini bir anonim türler dizisi halinde proje yapmak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a>Kaynak... Kaynak... (SelectMany)  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 500,00 `From … From …` ' den küçük `TotalDue` olan tüm <xref:System.Linq.Enumerable.SelectMany%2A> siparişleri seçmek için (yönteminin eşdeğeri) kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 1 `From … From …` Ekim 2002 veya sonraki bir <xref:System.Linq.Enumerable.SelectMany%2A> sürümde siparişin yapıldığı tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, siparişin toplamının `From … From …` 10000,00 ' den büyük olduğu <xref:System.Linq.Enumerable.SelectMany%2A> tüm siparişleri seçmek ve toplamı iki kez istememek için atamayı kullanması `From` için bir (yönteminin eşdeğeri) kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
