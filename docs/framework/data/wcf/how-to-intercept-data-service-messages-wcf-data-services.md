---
title: 'Nasıl yapılır: Veri hizmeti Iletilerini kesme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: cecfdd74779e3ab1c908957afac3c9fccf79f383
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780042"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Nasıl yapılır: Veri hizmeti Iletilerini kesme (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir işleme özel mantık ekleyebilmeniz için istek iletilerini ele alabilirsiniz. Bir iletiyi ele almak için veri hizmetinde özel olarak öznitelikli yöntemleri kullanırsınız. Daha fazla bilgi için bkz. [yakalayıcılar](interceptors-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmetini kullanır. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Siparişler varlık kümesi için bir sorgu yakalayıcısı tanımlamak için  
  
1. Northwind Data Service projesinde, Northwind. svc dosyasını açın.  
  
2. `Northwind` Sınıfına ait kod sayfasında, aşağıdaki `using` ifadeyi ekleyin (`Imports` Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. Sınıfında, aşağıdaki gibi adlı `OnQueryOrders` bir hizmet işlemi yöntemi tanımlayın: `Northwind`  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Ürünler varlık kümesi için bir değişiklik yakalayıcısı tanımlamak için  
  
1. Northwind Data Service projesinde, Northwind. svc dosyasını açın.  
  
2. Sınıfında, aşağıdaki gibi adlı `OnChangeProducts` bir hizmet işlemi yöntemi tanımlayın: `Northwind`  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Orders` bir lambda ifadesi döndüren varlık kümesi için bir sorgu yakalayıcısı yöntemi tanımlar. Bu ifade, `Orders` belirli bir kişi adına sahip olan ilişkili `Customers` öğesine bağlı olarak filtre uygulayan bir temsilci içerir. Ad, istekte bulunan kullanıcıya göre belirlenir. Bu örnekte, veri hizmetinin WCF kullanan bir ASP.NET Web uygulaması içinde barındırıldığı ve kimlik doğrulamasının etkinleştirildiği varsayılmaktadır. <xref:System.Web.HttpContext> Sınıfı, geçerli isteğin ilkesini almak için kullanılır.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Products` varlık kümesi için bir değişiklik yakalayıcısı yöntemi tanımlar. Bu yöntem bir <xref:System.Data.Services.UpdateOperations.Add> veya <xref:System.Data.Services.UpdateOperations.Change> işlemi için hizmete girişi doğrular ve üretimi durdurulmuş bir ürüne yapılan bir değişiklik yapılırsa bir özel durum oluşturur. Ayrıca, ürünlerin desteklenmeyen bir işlem olarak silinmesini engeller.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet Işlemi tanımlama](how-to-define-a-service-operation-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
