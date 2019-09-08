---
title: 'Nasıl yapılır: Toplu Işteki sorguları yürütme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a825fe83ff62d935740fb69871ba2d1e2120e9ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790499"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Nasıl yapılır: Toplu Işteki sorguları yürütme (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığını kullanarak, tek bir toplu işte veri hizmetinde birden fazla sorgu yürütebilirsiniz. Daha fazla bilgi için bkz. [toplu Işlem işlemleri](batching-operations-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Northwind Data Service 'ten hem <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> hem de `Customers` `Products` nesneleri döndüren sorguları içeren <xref:System.Data.Services.Client.DataServiceRequest%601> bir nesne dizisi yürütmek için yönteminin nasıl çağrılacağını gösterir. <xref:System.Data.Services.Client.QueryOperationResponse%601> Döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> nesne<xref:System.Data.Services.Client.DataServiceResponse> koleksiyonu numaralandırılır ve her birinde bulunan nesnelerin koleksiyonu da numaralandırılır.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
