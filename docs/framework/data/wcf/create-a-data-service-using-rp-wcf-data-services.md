---
title: 'Nasıl yapılır: Yansıma sağlayıcısını (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: fb40a60850739147b2bf0f15a3babfe1d0dfa486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965802"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: Yansıma sağlayıcısını (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bu sınıfların <xref:System.Linq.IQueryable%601> arabirimini uygulayan nesneler olarak kullanıma sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar. Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ve `Orders` `Items`içeren bir veri modelini tanımlar. Varlık kapsayıcı sınıfında `OrderItemData` arabirimler döndüren <xref:System.Linq.IQueryable%601> iki ortak yöntem vardır. Bu arabirimler, `Orders` ve `Items` varlık türlerinin varlık kümeleridir. `Items` `Orders` `Items` , Birden çok içerebilir, bu nedenle varlık türünün bir `Items` nesne koleksiyonu döndüren bir gezinti özelliği vardır. `Order` Varlık kapsayıcı sınıfı, `OrderItems` veri hizmetinin türetildiği <xref:System.Data.Services.DataService%601> sınıfın genel türüdür. `OrderItemData`  
  
> [!NOTE]
> Bu örnekte, bellek içi veri sağlayıcısı ve değişiklikler geçerli nesne örneklerinin dışında kalıcı olmadığından, <xref:System.Data.Services.IUpdatable> arabirimi uygulamadan türetilmiş bir avantaj yoktur. <xref:System.Data.Services.IUpdatable> Arabirimini uygulayan bir örnek için bkz [. nasıl yapılır: LINQ to SQL veri kaynağı](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)kullanarak veri hizmeti oluşturun.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
