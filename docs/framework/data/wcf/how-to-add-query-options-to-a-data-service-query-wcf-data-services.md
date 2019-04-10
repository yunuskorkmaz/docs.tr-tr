---
title: 'Nasıl yapılır: Bir veri hizmeti sorgusuna (WCF Veri Hizmetleri) sorgu seçenekleri ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 07e327846e2fdda279e38b4f05ca0a2b3bbacb61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211081"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Nasıl yapılır: Bir veri hizmeti sorgusuna (WCF Veri Hizmetleri) sorgu seçenekleri ekleme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] oluşturulan istemci veri hizmeti sınıfları kullanarak bir .NET Framework tabanlı istemci uygulamadan bir veri hizmetini sorgulama olanak tanır. İstenen sorgu seçenekleri içeren bir dilde tümleşik sorgu (LINQ) sorgu ifadesi oluşturmak için bunu yapmanın en kolay yoldur. Bir dizi denk bir sorgu oluşturmak için LINQ Sorgu yöntemlerini de çağırabilirsiniz. Son olarak, kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> bir sorgu için sorgu seçenekleri ekleme yöntemi. Her durumda, istemci tarafından oluşturulan URI uygulanan seçili sorgu seçenekleri ile istenen varlık kümesini içerir. Daha fazla bilgi için [veri hizmetini sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sonuçları yalnızca siparişleri fazla $30 freight maliyetli ve bu siparişleri kullanıma sunulduğundan bu göre azalan sırada döndürür. bir LINQ sorgu ifadesi oluşturma gösterilmektedir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki sorguya eşdeğer LINQ Sorgu yöntemlerini kullanarak LINQ sorgusu oluşturmak nasıl gösterir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için nasıl kullanılacağını gösteren <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi oluşturmak için bir <xref:System.Data.Services.Client.DataServiceQuery%601> diğer bir deyişle önceki örneklerde eşdeğerdir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `$orderby` hem filter hem de sipariş için sorgu seçeneği siparişler nesneleri nakliye özelliği tarafından döndürülen.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Nasıl yapılır: Sorgu Sonuçlarını Yansıtma](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
