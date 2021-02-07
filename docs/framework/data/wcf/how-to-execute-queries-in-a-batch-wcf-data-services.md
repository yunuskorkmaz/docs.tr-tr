---
description: 'Daha fazla bilgi edinin: nasıl yapılır: bir toplu Işte sorgu yürütme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: bir toplu Işte sorguları yürütme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: bcd95be57d2f3f2cea075a4b87fb6858c59ea41e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765301"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Nasıl yapılır: bir toplu Işte sorguları yürütme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri istemci kitaplığını kullanarak, tek bir toplu işte veri hizmetinde birden fazla sorgu yürütebilirsiniz. Daha fazla bilgi için bkz. [toplu Işlem işlemleri](batching-operations-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> <xref:System.Data.Services.Client.DataServiceRequest%601> `Customers` `Products` Northwind Data Service 'ten hem hem de nesneleri döndüren sorguları içeren bir nesne dizisi yürütmek için yönteminin nasıl çağrılacağını gösterir. <xref:System.Data.Services.Client.QueryOperationResponse%601>Döndürülen nesne koleksiyonu <xref:System.Data.Services.Client.DataServiceResponse> numaralandırılır ve her birinde bulunan nesnelerin koleksiyonu <xref:System.Data.Services.Client.QueryOperationResponse%601> da numaralandırılır.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
