---
title: Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: bb62b9ad214e5e268c3905df486f5914437b36d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780521"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
Web uygulamaları, istemci ve sunucu arasında iç ağların içinde çalışan uygulamalardan daha yüksek gecikme süresine sahip olmalıdır. Uygulamanızın performans ve Kullanıcı deneyimini iyileştirmek için, Web üzerinden sunuculara erişirken <xref:System.Data.Services.Client.DataServiceContext> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıflarının zaman uyumsuz yöntemlerini kullanmanızı öneririz.  
  
 Sunucular http isteklerini zaman uyumsuz olarak işlese de, bazı [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı yöntemleri zaman uyumludur ve yürütmeye devam etmeden önce tüm istek-yanıt alışverişi tamamlanana kadar bekler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplıklarının zaman uyumsuz yöntemleri, bu Exchange 'in tamamlanmasını beklemez ve uygulamanızın aynı sırada bir yanıt veren kullanıcı arabirimini korumasına izin verebilir.  
  
 <xref:System.Data.Services.Client.DataServiceContext> Ve<xref:System.Data.Services.Client.DataServiceQuery%601> sırasıyla *BEGIN* ve *End* ile başlayan sınıflarda bir yöntem çifti kullanarak zaman uyumsuz işlemler gerçekleştirebilirsiniz. *Begin* yöntemleri, işlem tamamlandığında hizmetin çağırdığı bir temsilciyi kaydeder. *Bitiş* yöntemleri, tamamlanan işlemlerden geri çağırma işlemini işlemek için kayıtlı olan temsilde çağrılmalıdır. Zaman uyumsuz bir işlemi gerçekleştirmek için *bitiş* yöntemini çağırdığınızda, bu işlemi başlatmak için kullandığınız aynı <xref:System.Data.Services.Client.DataServiceQuery%601> veya <xref:System.Data.Services.Client.DataServiceContext> örnekten bunu yapmanız gerekir. Her *BEGIN* yöntemi, bir `state` durum nesnesini geri aramaya geçirebileceğiniz bir parametre alır. Bu durum nesnesi, <xref:System.IAsyncResult> geri çağırma ile sağlanan öğesinden alınır ve zaman uyumsuz işlemi gerçekleştirmek için karşılık gelen *bitiş* yöntemini çağırmak için kullanılır. Örneğin <xref:System.Data.Services.Client.DataServiceQuery%601> , örneğinde <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemini çağırdığınızda örneği `state` parametre olarak sağlarsanız, aynı <xref:System.Data.Services.Client.DataServiceQuery%601> örnek tarafından <xref:System.IAsyncResult>döndürülür. Bu örneği <xref:System.Data.Services.Client.DataServiceQuery%601> daha sonra sorgu işlemini tamamlamaya yönelik <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi çağırmak için kullanılır. Daha fazla bilgi için [nasıl yapılır: Zaman uyumsuz veri hizmeti sorguları](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)yürütün.  
  
> [!NOTE]
> Yalnızca zaman uyumsuz işlemler, Silverlight için .NET Framework belirtilen istemci kitaplıkları tarafından desteklenir. Daha fazla bilgi için bkz. [WCF veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 .NET Framework istemci kitaplıkları aşağıdaki zaman uyumsuz işlemleri destekler:  
  
|Çalışma|Yöntemler|  
|---------------|-------------|  
|Bir <xref:System.Data.Services.Client.DataServiceQuery%601>yürütülüyor.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Öğesinden bir sorgu yürütülüyor <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Öğesinden bir toplu iş sorgusu yürütülüyor <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|İle ilgili bir varlık <xref:System.Data.Services.Client.DataServiceContext>yükleme.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|İçindeki nesnelerde yapılan değişiklikler kaydediliyor<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zaman uyumsuz Işlemler için iş parçacığı konuları  
 Çok iş parçacıklı bir uygulamada, zaman uyumsuz işlem için geri arama olarak kaydedilen temsilcinin, *başlangıç yöntemini çağırmak* için kullanılan aynı iş parçacığında çağrılması gerekmez, bu da ilk isteği oluşturur. Geri aramanın belirli bir iş parçacığında çağrılması gereken bir uygulamada, yanıtı işleyen *bitiş* yönteminin yürütülmesini, istenen iş parçacığına açıkça sıramalısınız. Örneğin, Windows Presentation Foundation (WPF) tabanlı uygulamalar ve Silverlight tabanlı uygulamalarda, yanıt, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> <xref:System.Windows.Threading.Dispatcher> nesne üzerindeki yöntemi kullanılarak UI iş parçacığına geri sıralanmalıdır. Daha fazla bilgi için bkz. [veri hizmetini sorgulama (WCF veri Hizmetleri/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
