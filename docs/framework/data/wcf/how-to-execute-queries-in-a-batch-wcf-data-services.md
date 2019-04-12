---
title: 'Nasıl yapılır: Bir toplu işlemi (WCF Veri Hizmetleri) sorguları yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: e5cd44ee7c3b2c2744e87ebf66973b637961893c
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517583"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Nasıl yapılır: Bir toplu işlemi (WCF Veri Hizmetleri) sorguları yürütme
Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, tek bir toplu işlemde birden fazla sorgu veri hizmetinden yürütebilirsiniz. Daha fazla bilgi için [toplu işleme işlemlerini](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> dizisi yürütülecek yöntemi <xref:System.Data.Services.Client.DataServiceRequest%601> hem döndüren sorgular içeren nesneleri `Customers` ve `Products` Northwind verileri hizmeti nesneleri. Koleksiyonu <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülen nesneleri <xref:System.Data.Services.Client.DataServiceResponse> numaralandırılmış alan şeklinde ve her nesnelerinin koleksiyonunu <xref:System.Data.Services.Client.QueryOperationResponse%601> da numaralandırılmış alan şeklinde.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
