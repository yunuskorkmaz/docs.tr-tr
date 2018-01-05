---
title: "Zaman uyumsuz işlemleri (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18e8be0668fa13c43f31d5314cacf91165ba8519
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-operations-wcf-data-services"></a>Zaman uyumsuz işlemleri (WCF Veri Hizmetleri)
Web uygulamaları, iç ağlar içinde çalışan uygulamalar daha yüksek gecikme süreleri istemci ve sunucu arasındaki uyum gerekir. Uygulamanızın performansı ve kullanıcı deneyimini iyileştirmek için zaman uyumsuz yöntemleri kullanmanızı öneririz <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfları erişirken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Web üzerinden sunucuları.  
  
 Ancak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sunucuları işlemi HTTP isteklerini zaman uyumsuz olarak, bazı yöntemleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları zaman uyumlu ve yürütme devam etmeden önce tüm istek-yanıt exchange tamamlanana kadar bekleyin. Zaman uyumsuz yöntemleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları tamamlamak ya da exchange beklemez ve esnek kullanıcı arabirimi zarfında korumak, uygulamanızın izin verebilirsiniz.  
  
 Çifti yöntemlerden birini kullanarak zaman uyumsuz işlemleri gerçekleştirebilir <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> ile başlayan sınıfları *başlamak* ve *son* sırasıyla. *Başlamak* yöntemleri kaydetme işlemi tamamlandığında, hizmet çağıran bir temsilci. *Son* yöntemleri tamamlanmış işlemlerinin ten geri işlemek üzere kaydettirilmiş temsilci olarak çağrılabilir. Çağırdığınızda *son* yöntemi zaman uyumsuz bir işlem tamamlamak için bunu aynı yapmalısınız <xref:System.Data.Services.Client.DataServiceQuery%601> veya <xref:System.Data.Services.Client.DataServiceContext> işlemine başlamak için kullanılan örnek. Her *başlamak* metodu bir `state` bir durum nesnesi için geri iletebilirsiniz parametresi. Bu durum nesnesi alınır <xref:System.IAsyncResult> geri arama ile sağlanan ve karşılık gelen çağırmak için kullanılan *son* zaman uyumsuz işlemi tamamlamak için yöntem. Ne zaman sağlayın, örneğin, <xref:System.Data.Services.Client.DataServiceQuery%601> örneği `state` çağırdığınızda parametresi <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> örneğindeki aynı <xref:System.Data.Services.Client.DataServiceQuery%601> örneği tarafından döndürülen <xref:System.IAsyncResult>. Bu örneği <xref:System.Data.Services.Client.DataServiceQuery%601> sonra çağırmak için kullanılan <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sorgu işlemi tamamlamak için yöntem. Daha fazla bilgi için bkz: [nasıl yapılır: zaman uyumsuz veri hizmeti sorguları yürütmek](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Yalnızca zaman uyumsuz işlemleri, Silverlight için .NET Framework sağlanan istemci kitaplıkları tarafından desteklenir. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149).  
  
 .NET Framework istemci kitaplıkları aşağıdaki zaman uyumsuz işlemleri destekler:  
  
|Çalışma|Yöntemler|  
|---------------|-------------|  
|Yürütülen bir <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Bir sorgu yürütme <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Bir toplu iş sorgusu yürütme <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|İlgili varlık kümesine yüklenirken <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Nesneleri için değişiklikler kaydediliyor<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zaman uyumsuz işlemleri için ilgili önemli noktalar iş parçacığı oluşturma  
 Çok iş parçacıklı uygulamada, zaman uyumsuz işlemi için bir geri çağırma olarak kayıtlı temsilci değil mutlaka çağrılır çağırmak için kullanılan aynı iş parçacığı üzerinde *başlamak* ilk isteği oluşturur yöntemi. Burada geri çağırma gerekir çağrılabilir belirli bir iş parçacığı üzerinde bir uygulamada, açıkça yürütülmesi sıralamanız gerekir *son* yanıt, istenen iş parçacığı işleme yöntemi. Örneğin, Windows Presentation Foundation WPF tabanlı uygulamalar ve Silverlight tabanlı uygulamalar, yanıt geri UI kullanarak iş parçacığına gereken <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi <xref:System.Windows.Threading.Dispatcher> nesnesi. Daha fazla bilgi için bkz: [veri hizmeti (WCF Veri Hizmetleri/Silverlight) sorgulama](http://msdn.microsoft.com/en-us/3a7cdc07-c37e-4da2-b98b-c3763fd0970b).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
