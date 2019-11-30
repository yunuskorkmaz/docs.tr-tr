---
title: 'Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569135"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)

WCF Veri Hizmetleri sunucuda hizmet işlemleri olarak tanımlanan yöntemleri kullanıma sunar. Hizmet işlemleri bir veri hizmetinin, sunucuda tanımlı bir yönteme URI aracılığıyla erişim sağlamasına izin verir. Bir hizmet işlemi tanımlamak için yönteme [`WebGet]` veya `[WebInvoke]` özniteliğini uygulayın. Sorgu işleçlerini desteklemek için, hizmet işleminin bir <xref:System.Linq.IQueryable%601> örneği döndürmesi gerekir. Hizmet işlemleri, <xref:System.Data.Services.DataService%601><xref:System.Data.Services.DataService%601.CurrentDataSource%2A> özelliği aracılığıyla temel alınan veri kaynağına erişebilir. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).

Bu konudaki örnekte, `Orders` ve ilgili `Order_Details` nesnelerinin filtrelenmiş bir <xref:System.Linq.IQueryable%601> örneğini döndüren `GetOrdersByCity` adlı bir hizmet işlemi tanımlanmaktadır. Örnek, Northwind örnek veri hizmeti için veri kaynağı olan <xref:System.Data.Objects.ObjectContext> örneğine erişir. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind Data Service 'te bir hizmet işlemi tanımlamak için

1. Northwind Data Service projesinde, Northwind. svc dosyasını açın.

2. `Northwind` sınıfında, `GetOrdersByCity` adlı bir hizmet işlemi yöntemini aşağıdaki gibi tanımlayın:

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. `Northwind` sınıfının `InitializeService` yönteminde, hizmet işlemine erişimi etkinleştirmek için aşağıdaki kodu ekleyin:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>GetOrdersByCity hizmeti işlemini sorgulamak için

- Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI 'lerden birini girin:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Örnek

Aşağıdaki örnek, Northwind Data Service üzerinde `GetOrderByCity` adlı bir hizmet işlemi uygular. Bu işlem, bir `Orders` kümesini ve ilgili `Order_Details` nesnelerini, belirtilen şehir adına göre <xref:System.Linq.IQueryable%601> örneği olarak döndürmek için ADO.NET Entity Framework kullanır.

> [!NOTE]
> Yöntem bir <xref:System.Linq.IQueryable%601> örneği döndürdüğünden, bu hizmet işlemi uç noktasında sorgu işleçleri destekleniyor.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
