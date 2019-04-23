---
title: 'Nasıl yapılır: Intercept Data Service Messages (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: ad0673f72b1a81d6bcfaf0704ccd698eda7bb20c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517854"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Nasıl yapılır: Intercept Data Service Messages (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], işlem için özel mantığı ekleyebilirsiniz, böylece istek iletilerinin yakalayabilirsiniz. Bir ileti kesmeye data Service'te özel öznitelikli yöntem kullanın. Daha fazla bilgi için [dinleyicileri](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti kullanır. Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Siparişler varlık kümesi için bir sorgu dinleyiciyi tanımlamak için  
  
1. Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.  
  
2. Kod sayfasını `Northwind` sınıfında, aşağıdaki `using` deyimi (`Imports` Visual Basic'te).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `OnQueryOrders` gibi:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Ürünleri varlık kümesi için bir değişiklik dinleyiciyi tanımlamak için  
  
1. Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.  
  
2. İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `OnChangeProducts` gibi:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için bir sorgu dinleyiciyi yöntemi tanımlar `Orders` döndüren bir lambda ifadesi varlık kümesi. Bu ifade istenen filtreleyen bir temsilci içerir `Orders` üzerinde ilgili temel `Customers` belirli bir kişi adına sahip. Adı, sırayla istekte bulunan kullanıcı göre belirlenir. Bu örnek, veri hizmeti WCF kullanan bir ASP.NET Web uygulamasında barındırılır ve bu kimlik doğrulamasının etkin varsayar. <xref:System.Web.HttpContext> Sınıfı, geçerli istek ilkesini almak için kullanılır.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Örnek  
 Bu örnek için bir değişiklik dinleyiciyi yöntemi tanımlar `Products` varlık kümesi. Bu yöntem için hizmetine giriş doğrular bir <xref:System.Data.Services.UpdateOperations.Add> veya <xref:System.Data.Services.UpdateOperations.Change> işlemi ve artık sağlanmayan bir ürüne yapılan bir değişikliği bir özel durum başlatır. Ayrıca, desteklenmeyen bir işlem olarak ürünleri silinmesini engeller.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet işlemi tanımlama](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
