---
title: "Nasıl yapılır: bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcf4ffd46bbbca0e7e00cad7ae0b2a88f7bd986b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Nasıl yapılır: bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]sunucuda hizmet işlemleri tanımlanan yöntemler kullanıma sunar. Hizmet işlemleri sunucuda tanımlanmış bir yönteme bir URI üzerinden erişim sağlamak için bir veri hizmeti sağlar. Bir hizmet işlemi tanımlamak için uygulama [`WebGet]` veya `[WebInvoke]` özniteliği yöntemi. Sorgu işleçleri desteklemek için hizmet işlemi döndürmelidir bir <xref:System.Linq.IQueryable%601> örneği. Hizmet işlemleri, altta yatan veri kaynağını aracılığıyla erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> özelliği <xref:System.Data.Services.DataService%601>. Daha fazla bilgi için bkz: [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Bu konudaki örnek adlı bir hizmet işlemi tanımlar `GetOrdersByCity` bir filtre uygulanmış döndüren <xref:System.Linq.IQueryable%601> örneğini `Orders` ve ilgili `Order_Details` nesneleri. Örnek erişen <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı örneği. Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind veri hizmetinde bir hizmet işlemi tanımlamak için  
  
1.  Northwind veri hizmeti projesi Northwind.svc dosyasını açın.  
  
2.  İçinde `Northwind` sınıfı, adlı bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` gibi:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  İçinde `InitializeService` yöntemi `Northwind` sınıfı, hizmet işlemi erişimi etkinleştirmek için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>Sorgu GetOrdersByCity hizmet işlemi  
  
-   Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI'ler birini girin:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir hizmet işlemi uygulayan `GetOrderByCity` Northwind veri hizmeti. Bu işlem bir dizi dönmek için ADO.NET Entity Framework kullanan `Orders` ve ilgili `Order_Details` olarak nesneleri bir <xref:System.Linq.IQueryable%601> örnek tabanlı üzerinde sağlanan şehir adı.  
  
> [!NOTE]
>  Sorgu işleçleri, bu hizmet işlemi noktadaki desteklenir, yöntem döndürdüğünden bir <xref:System.Linq.IQueryable%601> örneği.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF veri hizmetleri tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
