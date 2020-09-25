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
ms.openlocfilehash: 11a37340df879db7c2f8fdeaa792c1466e4a75d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184761"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sorgularını yürütme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, oluşturulan istemci veri hizmeti sınıflarını kullanarak bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasından sorgulamanızı sağlar. Aşağıdaki yöntemlerden birini kullanarak sorguları yürütebilirsiniz:  
  
- Aracın oluşturduğu adlandırılmış ada karşı bir LINQ sorgusu yürütme <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceContext> `Add Data Service Reference` .  
  
- Araç tarafından, <xref:System.Data.Services.Client.DataServiceQuery%601> aracın oluşturduğu, aldığınız adlandırılmış adı silerek örtülü olarak <xref:System.Data.Services.Client.DataServiceContext> `Add Data Service Reference` .  
  
- Açıkça, <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> zaman uyumsuz yürütme yöntemi aracılığıyla çağırarak.  
  
 Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Customers` Northwind veri hizmetine karşı tümünü döndüren BIR LINQ sorgusunun nasıl tanımlanacağını ve yürütüleceğini gösterir.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Add Data Service Reference` Tüm Northwind Data Service 'e karşı bir sorgu dolaylı olarak yürütmek üzere aracın oluşturduğu bağlamın nasıl kullanılacağını gösterir `Customers` . İstenen varlık kümesinin URI 'SI `Customers` bağlam tarafından otomatik olarak belirlenir. Numaralandırma gerçekleştiğinde sorgu örtük olarak yürütülür.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext> `Customers` Northwind veri hizmetine karşı tümünü döndüren bir sorguyu açık olarak yürütmek için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Veri Hizmeti Sorgusuna Sorgu Seçenekleri Ekleme](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
