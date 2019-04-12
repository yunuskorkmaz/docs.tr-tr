---
title: 'Nasıl yapılır: Yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517102"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: Yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bu sınıfların uygulayan nesneler sunulan sürece, rastgele sınıflara göre bir veri modeli tanımlamanızı sağlayan <xref:System.Linq.IQueryable%601> arabirimi. Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlar içeren bir veri modeli `Orders` ve `Items`. Varlık kapsayıcı sınıfı `OrderItemData` döndüren iki genel yöntemler olan <xref:System.Linq.IQueryable%601> arabirimleri. Bu arabirimler varlık kümeleridir `Orders` ve `Items` varlık türleri. Bir `Order` birden çok içerebilir `Items`, bu nedenle `Orders` varlık türüne sahip bir `Items` koleksiyonunu döndüren bir gezinti özelliği `Items` nesneleri. `OrderItemData` Varlık kapsayıcı sınıfı genel türü, <xref:System.Data.Services.DataService%601> sınıfı `OrderItems` veri hizmeti türetilmiştir.  
  
> [!NOTE]
>  Bu örnek, bir bellek içi veri sağlayıcısı gösterir ve geçerli nesne örneklerini dışında değişiklikler kalıcı değildir çünkü uygulama öğesinden türetilmiş herhangi bir avantajı yoktur <xref:System.Data.Services.IUpdatable> arabirimi. Uygulayan bir örnek <xref:System.Data.Services.IUpdatable> arabirim için bkz: [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: Bir ADO.NET varlık çerçevesi veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
