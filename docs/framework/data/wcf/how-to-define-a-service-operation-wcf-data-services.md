---
title: 'Nasıl yapılır: Hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 3154fadeda400440f68a184b430b7ff15a02203d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780078"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Nasıl yapılır: Hizmet Işlemi tanımlama (WCF Veri Hizmetleri)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]sunucusunda hizmet işlemleri olarak tanımlanan yöntemleri kullanıma sunun. Hizmet işlemleri bir veri hizmetinin, sunucuda tanımlı bir yönteme URI aracılığıyla erişim sağlamasına izin verir. Bir hizmet işlemi tanımlamak için, [`WebGet]` veya `[WebInvoke]` özniteliğini metoduna uygulayın. Sorgu işleçlerini desteklemek için, hizmet işleminin bir <xref:System.Linq.IQueryable%601> örnek döndürmesi gerekir. Hizmet işlemleri, <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601>içindeki özelliği aracılığıyla temel alınan veri kaynağına erişebilir. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).

Bu `GetOrdersByCity` konudaki örnek, filtrelenmiş <xref:System.Linq.IQueryable%601> bir örneği `Orders` ve ilgili `Order_Details` nesneleri döndüren adlı bir hizmet işlemini tanımlar. Örnek, Northwind örnek <xref:System.Data.Objects.ObjectContext> veri hizmeti için veri kaynağı olan örneğe erişir. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind Data Service 'te bir hizmet işlemi tanımlamak için

1. Northwind Data Service projesinde, Northwind. svc dosyasını açın.

2. Sınıfında, aşağıdaki gibi adlı `GetOrdersByCity` bir hizmet işlemi yöntemi tanımlayın: `Northwind`

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. `Northwind` Sınıfının yönteminde, hizmet işlemine erişimi etkinleştirmek için aşağıdaki kodu ekleyin: `InitializeService`

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>GetOrdersByCity hizmeti işlemini sorgulamak için

- Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI 'lerden birini girin:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Örnek

Aşağıdaki örnek, Northwind veri hizmetinde adlı `GetOrderByCity` bir hizmet işlemi uygular. Bu işlem, belirtilen şehir adına göre bir dizi `Orders` ve ilgili `Order_Details` nesneleri <xref:System.Linq.IQueryable%601> örnek olarak döndürmek için ADO.NET Entity Framework kullanır.

> [!NOTE]
> Yöntem bir <xref:System.Linq.IQueryable%601> örnek döndürdüğünden, bu hizmet işlemi uç noktasında sorgu işleçleri destekleniyor.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
