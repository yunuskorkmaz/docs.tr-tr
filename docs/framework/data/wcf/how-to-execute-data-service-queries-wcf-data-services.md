---
title: "Nasıl yapılır: veri hizmeti sorgular (WCF Veri Hizmetleri) yürütme"
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
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ed40236fd902536a45e821abea768d5117fafde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sorgular (WCF Veri Hizmetleri) yürütme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Veri Hizmeti .NET Framework tabanlı istemci uygulamasından oluşturulan istemci veri hizmeti sınıflarını kullanarak sorgulama olanak tanır. Aşağıdaki yöntemlerden birini kullanarak sorguları çalıştırabilirsiniz:  
  
-   Adlandırılmış bir LINQ Sorgu yürütme <xref:System.Data.Services.Client.DataServiceQuery%601> alanından elde <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` aracı oluşturur.  
  
-   Adlandırılmış numaralandırma tarafından dolaylı olarak <xref:System.Data.Services.Client.DataServiceQuery%601> alanından elde <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` aracı oluşturur.  
  
-   Çağırarak açıkça <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601>, veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> zaman uyumsuz yürütme yöntemi.  
  
 Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayın ve tüm döndüren bir LINQ Sorgu yürütme gösterilmektedir `Customers` karşı Northwind veri hizmeti.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bağlamı kullanmayı gösterir, `Add Data Service Reference` aracının oluşturduğu tüm döndüren bir sorgu örtük olarak yürütülecek `Customers` karşı Northwind veri hizmeti. İstenen URI'sini `Customers` varlık kümesi kapsamında otomatik olarak belirlenir. Numaralandırma oluştuğunda sorgu örtük olarak yürütülür.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext> açıkça tüm döndüren bir sorgu yürütmek için `Customers` karşı Northwind veri hizmeti.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Veri Hizmeti Sorgusuna Sorgu Seçenekleri Ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
