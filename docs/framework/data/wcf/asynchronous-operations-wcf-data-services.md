---
title: Zaman uyumsuz işlemler (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 665e424ada24e5e2990eccde7193a91dc039b265
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743806"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Zaman uyumsuz işlemler (WCF Data Services)
Web uygulamaları, iç ağ içinde çalışan uygulamalar daha yüksek gecikme istemci ve sunucu arasında uyum gerekir. Uygulamanızın performans ve kullanıcı deneyimini iyileştirmek için zaman uyumsuz yöntemleri kullanılarak öneririz <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfları erişirken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sunucuları Web üzerinden.  
  
 Ancak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sunucuları işlem HTTP isteklerini zaman uyumsuz olarak bazı yöntemleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları, zaman uyumlu ve yürütme devam etmeden önce tüm istek-yanıt exchange tamamlanana kadar bekleyin. Zaman uyumsuz yöntemleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kütüphaneleri, bu exchange için beklemeyin ve duyarlı kullanıcı arabirimi sırada korumak için uygulamanıza izin verebilirsiniz.  
  
 Bir çift yöntemleri kullanarak zaman uyumsuz işlemleri gerçekleştirebilir <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> ile başlayan sınıfları *başlamak* ve *son* sırasıyla. *Başlamak* yöntemleri kaydetme işlemi tamamlandığında hizmetine çağrı yapan bir temsilci. *Son* yöntemleri tamamlanmış işlemleri geri çağırmadan işlemek üzere kaydettirilmiş temsilci çağrılabilir. Çağırdığınızda *son* yöntemi zaman uyumsuz bir işlemi tamamlamak için bunu aynı yapmalısınız <xref:System.Data.Services.Client.DataServiceQuery%601> veya <xref:System.Data.Services.Client.DataServiceContext> işlemine başlamak için kullanılan bir örnek. Her *başlamak* yöntemi bir `state` durum nesnesi geri aramaya geçirebilirsiniz parametresi. Bu durum nesnesine alınır <xref:System.IAsyncResult> geri çağırmayı sağlanır ve karşılık gelen çağırmak için kullanılan *son* zaman uyumsuz işlemi tamamlamak için yöntemi. Örneğin, ne zaman sağlamanız <xref:System.Data.Services.Client.DataServiceQuery%601> örneği `state` çağırdığınızda parametresi <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> örneğinde aynı yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601> örneği tarafından döndürülen <xref:System.IAsyncResult>. Bu örneği <xref:System.Data.Services.Client.DataServiceQuery%601> ardından çağırmak için kullanılan <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sorgu işlemi tamamlamak için yöntemi. Daha fazla bilgi için [nasıl yapılır: zaman uyumsuz veri hizmeti sorguları yürütme](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Yalnızca zaman uyumsuz işlemler, Silverlight için .NET Framework içinde sağlanan istemci kitaplıkları tarafından desteklenir. Daha fazla bilgi için [WCF Veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 .NET Framework istemci kitaplıkları, aşağıdaki zaman uyumsuz işlemleri destekler:  
  
|İşlem|Yöntemler|  
|---------------|-------------|  
|Yürütülen bir <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Bir sorgu yürütme <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Bir batch sorgu yürütülürken <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Bir ilgili varlığa yüklenirken <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Nesneler için değişiklikler kaydediliyor <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zaman uyumsuz işlemler için Değerlendirmeler iş parçacığı oluşturma  
 Çok iş parçacıklı bir uygulamada, zaman uyumsuz işlem için bir geri çağırma olarak kayıtlı temsilci değil gerekmeyen çağrıldığında çağırmak için kullanılan aynı iş parçacığında *başlamak* yönteminin, ilk istek oluşturur. Nereye geri çağırma gerekir çağrılacak belirli bir iş parçacığında bir uygulamada, açıkça yürütülmesini sıralamanız gerekir *son* istenen iş parçacığı, yanıtı işleyen yöntem. Örneğin, Windows Presentation Foundation WPF tabanlı uygulamalar ve Silverlight tabanlı uygulamaların yanıt UI iş parçacığına geri kullanarak sıralanması gerekir <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metodunda <xref:System.Windows.Threading.Dispatcher> nesne. Daha fazla bilgi için [(WCF Veri Hizmetleri/Silverlight) veri hizmetini sorgulama](https://msdn.microsoft.com/library/3a7cdc07-c37e-4da2-b98b-c3763fd0970b).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
