---
title: 'Nasıl yapılır: Bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: fc738f7e81c02e44075ce5ed151ed42452650c94
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518129"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Nasıl yapılır: Bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sunucuda hizmet işlemleri tanımlanmış olan yöntemleri kullanıma sunar. Hizmet işlemlerine izin ver sunucuda tanımlı bir yönteme bir URI aracılığıyla erişim sağlamak bir veri hizmeti. Bir hizmet işlemi tanımlamak için uygulama [`WebGet]` veya `[WebInvoke]` özniteliğini yöntemine. Sorgu işleçleri desteklemek için hizmet işlemi döndürmelidir bir <xref:System.Linq.IQueryable%601> örneği. Hizmet işlemleri, temel alınan veri kaynağı aracılığıyla erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> özellikte <xref:System.Data.Services.DataService%601>. Daha fazla bilgi için [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Bu konudaki örnek adlı bir hizmet işlemi tanımlar `GetOrdersByCity` filtrelenmiş bir döndüren <xref:System.Linq.IQueryable%601> örneğini `Orders` ve ilgili `Order_Details` nesneleri. Erişen örnek <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı örneği. Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind veri hizmetinde bir hizmet işlemi tanımlamak için  
  
1. Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.  
  
2. İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` gibi:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3. İçinde `InitializeService` yöntemi `Northwind` sınıf, hizmet işlemi erişimi etkinleştirmek için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>Sorgu GetOrdersByCity hizmet işlemi  
  
-   Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki bir URI'leri birini girin:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı bir hizmet işlemlerinizi `GetOrderByCity` Northwind verileri hizmeti üzerinde. Bu işlem, bir dizi döndürmek için ADO.NET varlık çerçevesi kullanır. `Orders` ve ilgili `Order_Details` olarak nesneleri bir <xref:System.Linq.IQueryable%601> örnek tabanlı üzerinde sağlanan şehir adı.  
  
> [!NOTE]
>  Sorgu işleçleri, bu hizmet işlemi uç noktasında desteklenir, yöntemin döndürdüğü için bir <xref:System.Linq.IQueryable%601> örneği.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
