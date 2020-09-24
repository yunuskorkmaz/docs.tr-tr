---
title: 'Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 6bab9d9be484cf90cb85df63a1b237b5cc39a5e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152773"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, bu sınıflar arabirimini uygulayan nesneler olarak sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar <xref:System.Linq.IQueryable%601> . Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, ve içeren bir veri modelini tanımlar `Orders` `Items` . Varlık kapsayıcı sınıfında `OrderItemData` arabirimler döndüren iki ortak yöntem vardır <xref:System.Linq.IQueryable%601> . Bu arabirimler, `Orders` ve `Items` varlık türlerinin varlık kümeleridir. `Order`, Birden çok içerebilir `Items` , bu nedenle `Orders` varlık türünün `Items` bir nesne koleksiyonu döndüren bir gezinti özelliği vardır `Items` . `OrderItemData`Varlık kapsayıcı sınıfı, <xref:System.Data.Services.DataService%601> `OrderItems` veri hizmetinin türetildiği sınıfın genel türüdür.  
  
> [!NOTE]
> Bu örnekte, bellek içi veri sağlayıcısı ve değişiklikler geçerli nesne örneklerinin dışında kalıcı olmadığından, arabirimi uygulamadan türetilmiş bir avantaj yoktur <xref:System.Data.Services.IUpdatable> . Arabirimi uygulayan bir örnek için <xref:System.Data.Services.IUpdatable> bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-linq-to-sql-wcf.md)
- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md)
