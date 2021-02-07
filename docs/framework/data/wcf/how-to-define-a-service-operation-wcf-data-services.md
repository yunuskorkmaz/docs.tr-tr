---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 9fcad3a31ea5b439c248ba103cbf4ddd75b8109a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765626"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri sunucuda hizmet işlemleri olarak tanımlanan yöntemleri kullanıma sunar. Hizmet işlemleri bir veri hizmetinin, sunucuda tanımlı bir yönteme URI aracılığıyla erişim sağlamasına izin verir. Bir hizmet işlemi tanımlamak için, [ `WebGet]` veya `[WebInvoke]` özniteliğini metoduna uygulayın. Sorgu işleçlerini desteklemek için, hizmet işleminin bir örnek döndürmesi gerekir <xref:System.Linq.IQueryable%601> . Hizmet işlemleri, içindeki özelliği aracılığıyla temel alınan veri kaynağına erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> . Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).

Bu konudaki örnek, `GetOrdersByCity` filtrelenmiş bir <xref:System.Linq.IQueryable%601> örneği `Orders` ve ilgili nesneleri döndüren adlı bir hizmet işlemini tanımlar `Order_Details` . Örnek, <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı olan örneğe erişir. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind Data Service 'te bir hizmet işlemi tanımlamak için

1. Northwind Data Service projesinde, Northwind. svc dosyasını açın.

2. `Northwind`Sınıfında, aşağıdaki gibi adlı bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` :

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. `InitializeService` `Northwind` Sınıfının yönteminde, hizmet işlemine erişimi etkinleştirmek için aşağıdaki kodu ekleyin:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>GetOrdersByCity hizmeti işlemini sorgulamak için

- Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI 'lerden birini girin:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Örnek

Aşağıdaki örnek, Northwind veri hizmetinde adlı bir hizmet işlemi uygular `GetOrderByCity` . Bu işlem, `Orders` `Order_Details` <xref:System.Linq.IQueryable%601> belirtilen şehir adına göre bir dizi ve ilgili nesneleri örnek olarak döndürmek için ADO.NET Entity Framework kullanır.

> [!NOTE]
> Yöntem bir örnek döndürdüğünden, bu hizmet işlemi uç noktasında sorgu işleçleri destekleniyor <xref:System.Linq.IQueryable%601> .

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
