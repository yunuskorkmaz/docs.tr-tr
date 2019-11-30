---
title: 'Nasıl yapılır: bir toplu Işte sorguları yürütme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: 0ddf5b4f68ca08fca0c55cfcdfcd5431bcec6de2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569049"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Nasıl yapılır: bir toplu Işte sorguları yürütme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri istemci kitaplığını kullanarak, tek bir toplu işte veri hizmetinde birden fazla sorgu yürütebilirsiniz. Daha fazla bilgi için bkz. [toplu Işlem işlemleri](batching-operations-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Northwind Data Service 'ten hem `Customers` hem de `Products` nesnelerini döndüren sorguları içeren bir <xref:System.Data.Services.Client.DataServiceRequest%601> nesneleri dizisini yürütmek için <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> yönteminin nasıl çağrılacağını gösterir. Döndürülen <xref:System.Data.Services.Client.DataServiceResponse> <xref:System.Data.Services.Client.QueryOperationResponse%601> nesneleri koleksiyonu numaralandırılır ve her bir <xref:System.Data.Services.Client.QueryOperationResponse%601> içerilen nesne koleksiyonu da numaralandırılır.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
