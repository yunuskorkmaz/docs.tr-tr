---
title: 'Nasıl yapılır: Zaman uyumsuz veri hizmeti sorguları (WCF Veri Hizmetleri) yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: f89a5004afeffe5aa9a28cb2d43374aede8a935e
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518168"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Nasıl yapılır: Zaman uyumsuz veri hizmeti sorguları (WCF Veri Hizmetleri) yürütme
Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, sorgu yürütme ile değişiklikleri kaydetme gibi istemci-sunucu işlemlerini zaman uyumsuz olarak gerçekleştirebilir. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  Nereye geri çağırma gerekir çağrılacak belirli bir iş parçacığında bir uygulamada, açıkça yürütülmesini sıralamanız gerekir <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zaman uyumsuz sorgu çağırarak yürütmek gösterilmektedir <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> sorguyu başlatmak için yöntemi. Satır içi temsilci seçme çağrıları <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sorgu sonuçlarını görüntülemek için yöntemi.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
