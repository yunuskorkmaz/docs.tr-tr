---
title: 'Nasıl yapılır: Veri Hizmeti sorguları (WCF Veri Hizmetleri) yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: aac0e4c71ae2752d4f56ae5eadb5f0a8d381d5fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623293"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Nasıl yapılır: Veri Hizmeti sorguları (WCF Veri Hizmetleri) yürütme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] oluşturulan istemci veri hizmeti sınıfları kullanarak bir .NET Framework tabanlı istemci uygulamadan bir veri hizmetini sorgulama olanak tanır. Aşağıdaki yöntemlerden birini kullanarak sorgu yürütebilirsiniz:  
  
-   Adlandırılmış bir LINQ Sorgu yürütülürken <xref:System.Data.Services.Client.DataServiceQuery%601> , elde <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` aracı oluşturur.  
  
-   Adlandırılmış numaralandırma tarafından dolaylı olarak <xref:System.Data.Services.Client.DataServiceQuery%601> , elde <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` aracı oluşturur.  
  
-   Çağırarak açıkça <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodunda <xref:System.Data.Services.Client.DataServiceQuery%601>, veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> zaman uyumsuz yürütme için yöntemi.  
  
 Daha fazla bilgi için [veri hizmetini sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl tanımlanacağını ve tüm döndüren bir LINQ Sorgu yürütme gösterir `Customers` karşı Northwind verileri hizmeti.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bağlam işlemi gösterilir, `Add Data Service Reference` aracının oluşturduğu tüm döndüren bir sorgu örtük olarak yürütülecek `Customers` karşı Northwind verileri hizmeti. İstenen URI'sini `Customers` varlık kümesi bağlam tarafından otomatik olarak belirlenir. Sabit olduğunda sorguyu örtük olarak yürütülür.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext> açıkça tüm döndüren bir sorgu yürütmek için `Customers` karşı Northwind verileri hizmeti.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bir veri hizmeti sorgusuna sorgu seçenekleri ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
