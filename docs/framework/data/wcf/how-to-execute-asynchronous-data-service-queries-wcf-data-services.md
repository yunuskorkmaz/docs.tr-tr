---
title: "Nasıl yapılır: zaman uyumsuz veri hizmeti sorgular (WCF Veri Hizmetleri) yürütme"
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
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfffd8405411327d0c31510850ceaa389bdc2d72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Nasıl yapılır: zaman uyumsuz veri hizmeti sorgular (WCF Veri Hizmetleri) yürütme
Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, sorguları yürütme ve değişiklikleri kaydetme gibi istemci-sunucu işlemlerini zaman uyumsuz olarak gerçekleştirebilir. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  Burada geri çağırma gerekir çağrılabilir belirli bir iş parçacığı üzerinde bir uygulamada, açıkça yürütülmesi sıralamanız gerekir <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çağırarak zaman uyumsuz bir sorguyu yürütmek gösterilmiştir <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> sorguyu başlatmak için yöntem. Satır içi temsilci çağrılarını <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi sorgu sonuçları görüntüler.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
