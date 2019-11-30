---
title: 'Nasıl yapılır: veri hizmeti sorgusuna sorgu seçenekleri ekleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 7b5a9c15f2d46c89abf8fb5bc0f4be99e501a267
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569178"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sorgusuna sorgu seçenekleri ekleme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, oluşturulan istemci veri hizmeti sınıflarını kullanarak bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasından sorgulamanızı sağlar. Bunu yapmanın en kolay yolu, istenen sorgu seçeneklerini içeren bir dil tümleşik sorgu (LINQ) sorgu ifadesi oluşturmak olur. Ayrıca, eşdeğer bir sorgu oluşturmak için bir dizi LINQ sorgu yöntemi çağırabilirsiniz. Son olarak, sorgu seçeneklerini sorguya eklemek için <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemini kullanabilirsiniz. Bu durumların her birinde, istemci tarafından oluşturulan URI, seçilen sorgu seçenekleri uygulanmış şekilde istenen varlık kümesini içerir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca $30 'den daha fazla nakliye maliyeti olan siparişleri döndüren ve sonuçları teslim tarihi azalan sırada sıralayan bir LINQ sorgu ifadesinin nasıl oluşturulacağını göstermektedir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki sorguyla eşdeğer olan LINQ sorgu yöntemlerini kullanarak bir LINQ sorgusunun nasıl oluşturulacağını göstermektedir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneklere eşdeğer bir <xref:System.Data.Services.Client.DataServiceQuery%601> oluşturmak için <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `$orderby` sorgu seçeneğinin, nakliye özelliği tarafından döndürülen sipariş nesnelerine filtre ve sıralama için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Nasıl Yapılır: Sorgu Sonuçlarını Yansıtma](how-to-project-query-results-wcf-data-services.md)
