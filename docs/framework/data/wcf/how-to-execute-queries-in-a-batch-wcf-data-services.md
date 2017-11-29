---
title: "Nasıl yapılır: bir toplu işlemi (WCF Veri Hizmetleri) sorgularını Yürüt"
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d868881a3ff5c79f1f003881f58c726ebf25385e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Nasıl yapılır: bir toplu işlemi (WCF Veri Hizmetleri) sorgularını Yürüt
Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, tek bir toplu işlemde birden fazla sorgu veri hizmeti karşı çalıştırabilirsiniz. Daha fazla bilgi için bkz: [toplu işlemleri](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> bir dizi yürütülecek yöntem <xref:System.Data.Services.Client.DataServiceRequest%601> her ikisi de döndüren sorgular içeren nesneleri `Customers` ve `Products` Northwind veri hizmetinden nesneleri. Koleksiyonunu <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülen nesnelerin <xref:System.Data.Services.Client.DataServiceResponse> numaralandırılır ve her yer alan nesneleri koleksiyonu <xref:System.Data.Services.Client.QueryOperationResponse%601> de numaralandırılır.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
