---
title: 'Nasıl yapılır: veri hizmeti sorgularını yürütme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: b06a21a45dcf6e67c41287c4cd59cdda4aa7b447
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569077"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sorgularını yürütme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, oluşturulan istemci veri hizmeti sınıflarını kullanarak bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasından sorgulamanızı sağlar. Aşağıdaki yöntemlerden birini kullanarak sorguları yürütebilirsiniz:  
  
- `Add Data Service Reference` aracının oluşturduğu <xref:System.Data.Services.Client.DataServiceContext> elde ettiğiniz adlandırılmış <xref:System.Data.Services.Client.DataServiceQuery%601> karşı bir LINQ sorgusu yürütme.  
  
- `Add Data Service Reference` aracının oluşturduğu <xref:System.Data.Services.Client.DataServiceContext> elde ettiğiniz adlandırılmış <xref:System.Data.Services.Client.DataServiceQuery%601> silerek örtülü olarak.  
  
- Açık olarak, <xref:System.Data.Services.Client.DataServiceQuery%601><xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi veya zaman uyumsuz yürütme için <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi çağırarak.  
  
 Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm `Customers` Northwind Data Service 'e karşı döndüren bir LINQ sorgusunun nasıl tanımlanacağını ve yürütüleceğini gösterir.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Northwind Data Service 'e karşı tüm `Customers` döndüren bir sorguyu örtük olarak yürütmek üzere `Add Data Service Reference` aracının oluşturduğu bağlamın nasıl kullanılacağını gösterir. İstenen `Customers` varlık kümesinin URI 'SI bağlam tarafından otomatik olarak belirlenir. Numaralandırma gerçekleştiğinde sorgu örtük olarak yürütülür.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Northwind Data Service 'e karşı tüm `Customers` döndüren bir sorguyu açıkça yürütmek için <xref:System.Data.Services.Client.DataServiceContext> nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Veri Hizmeti Sorgusuna Sorgu Seçenekleri Ekleme](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
