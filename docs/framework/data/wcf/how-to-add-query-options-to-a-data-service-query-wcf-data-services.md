---
title: 'Nasıl yapılır: Veri hizmeti sorgusuna sorgu seçenekleri ekleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: f7b0557938d1419b79c3191cf8f9110cab2f5ce6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790785"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Nasıl yapılır: Veri hizmeti sorgusuna sorgu seçenekleri ekleme (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]oluşturulan istemci veri hizmeti sınıflarını kullanarak bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasından sorgulamanızı sağlar. Bunu yapmanın en kolay yolu, istenen sorgu seçeneklerini içeren bir dil tümleşik sorgu (LINQ) sorgu ifadesi oluşturmak olur. Ayrıca, eşdeğer bir sorgu oluşturmak için bir dizi LINQ sorgu yöntemi çağırabilirsiniz. Son olarak, bir sorguya sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> seçenekleri eklemek için yöntemini kullanabilirsiniz. Bu durumların her birinde, istemci tarafından oluşturulan URI, seçilen sorgu seçenekleri uygulanmış şekilde istenen varlık kümesini içerir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
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
 Aşağıdaki örnek, önceki örneklere denk gelen bir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> oluşturmak için yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hem nakliye özelliğine göre hem `$orderby` de döndürülen sipariş nesnelerini filtrelemek ve sıralamak için Query seçeneğinin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Nasıl yapılır: Proje sorgu sonuçları](how-to-project-query-results-wcf-data-services.md)
