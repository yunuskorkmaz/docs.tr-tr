---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 1c4d131b21c69e11dd6d8b574e4c22a6af7c5a25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766242"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

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
