---
title: 'Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569287"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bu sınıfların <xref:System.Linq.IQueryable%601> arabirimini uygulayan nesneler olarak kullanıma sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar. Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Orders` ve `Items`içeren bir veri modelini tanımlar. `OrderItemData` varlık kapsayıcı sınıfı, <xref:System.Linq.IQueryable%601> arabirimleri döndüren iki ortak yöntem içerir. Bu arabirimler `Orders` ve `Items` varlık türlerinin varlık kümeleridir. `Order` birden çok `Items`içerebilir, bu nedenle `Orders` varlık türünün `Items` nesnelerden oluşan bir koleksiyonu döndüren bir `Items` gezinti özelliği vardır. `OrderItemData` varlık kapsayıcı sınıfı, `OrderItems` veri hizmetinin türetildiği <xref:System.Data.Services.DataService%601> sınıfının genel türüdür.  
  
> [!NOTE]
> Bu örnek, bellek içi bir veri sağlayıcısını gösterdiği ve değişiklikler geçerli nesne örnekleri dışında kalıcı olmadığından, <xref:System.Data.Services.IUpdatable> arabirimini uygulamadan elde edilen bir avantaj yoktur. <xref:System.Data.Services.IUpdatable> arabirimini uygulayan bir örnek için bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-linq-to-sql-wcf.md)
- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md)
