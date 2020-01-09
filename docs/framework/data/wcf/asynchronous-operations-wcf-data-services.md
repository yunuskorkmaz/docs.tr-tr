---
title: Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 5191f3d03facaafc64f6df494ff90cd0ce1c1988
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346189"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
Web uygulamaları, istemci ve sunucu arasında iç ağların içinde çalışan uygulamalardan daha yüksek gecikme süresine sahip olmalıdır. Uygulamanızın performans ve Kullanıcı deneyimini iyileştirmek için, Web üzerinden WCF Veri Hizmetleri sunuculara erişirken <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıflarının zaman uyumsuz yöntemlerini kullanmanızı öneririz.  
  
 WCF Veri Hizmetleri sunucuları HTTP isteklerini zaman uyumsuz olarak işetse de, WCF Veri Hizmetleri istemci kitaplıklarının bazı yöntemleri zaman uyumludur ve yürütmeye devam etmeden önce tüm istek-yanıt alışverişi tamamlanana kadar bekler. WCF Veri Hizmetleri istemci kitaplıklarının zaman uyumsuz yöntemleri, bu Exchange 'in tamamlanmasını beklemez ve uygulamanızın bu sırada yanıt veren bir kullanıcı arabirimini korumasına izin verebilir.  
  
 <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> ve sırasıyla *BEGIN* ve *End* ile başlayan sınıflar arasında bir yöntem çifti kullanarak zaman uyumsuz işlemler gerçekleştirebilirsiniz. *Begin* yöntemleri, işlem tamamlandığında hizmetin çağırdığı bir temsilciyi kaydeder. *Bitiş* yöntemleri, tamamlanan işlemlerden geri çağırma işlemini işlemek için kayıtlı olan temsilde çağrılmalıdır. Zaman uyumsuz bir işlemi gerçekleştirmek için *End* metodunu çağırdığınızda, işlemi başlatmak için kullandığınız <xref:System.Data.Services.Client.DataServiceQuery%601> veya <xref:System.Data.Services.Client.DataServiceContext> örneğinden bunu yapmanız gerekir. Her *BEGIN* yöntemi bir durum nesnesini geri aramaya geçirebileceğiniz bir `state` parametresi alır. Bu durum nesnesi, geri çağırma ile sağlanan <xref:System.IAsyncResult> alınır ve zaman uyumsuz işlemi tamamlamaya yönelik karşılık gelen *bitiş* yöntemini çağırmak için kullanılır. Örneğin, örnekte <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemini çağırdığınızda `state` parametresi olarak <xref:System.Data.Services.Client.DataServiceQuery%601> örneğini sağlarsanız, <xref:System.IAsyncResult>tarafından aynı <xref:System.Data.Services.Client.DataServiceQuery%601> örneği döndürülür. Bu <xref:System.Data.Services.Client.DataServiceQuery%601> örneği daha sonra sorgu işlemini tamamlamaya yönelik <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemini çağırmak için kullanılır. Daha fazla bilgi için bkz. [nasıl yapılır: zaman uyumsuz veri hizmeti sorguları yürütme](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
> Yalnızca zaman uyumsuz işlemler, Silverlight için .NET Framework belirtilen istemci kitaplıkları tarafından desteklenir. Daha fazla bilgi için bkz. [WCF veri Hizmetleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 .NET Framework istemci kitaplıkları aşağıdaki zaman uyumsuz işlemleri destekler:  
  
|Çalışma|Yöntemler|  
|---------------|-------------|  
|<xref:System.Data.Services.Client.DataServiceQuery%601>yürütülüyor.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext>bir sorgu yürütülüyor.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext>Batch sorgusu yürütülüyor.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext>ilişkili bir varlık yükleniyor.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> nesnelerde yapılan değişiklikler kaydediliyor|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zaman uyumsuz Işlemler için iş parçacığı konuları  
 Çok iş parçacıklı bir uygulamada, zaman uyumsuz işlem için geri arama olarak kaydedilen temsilcinin, *başlangıç yöntemini çağırmak* için kullanılan aynı iş parçacığında çağrılması gerekmez, bu da ilk isteği oluşturur. Geri aramanın belirli bir iş parçacığında çağrılması gereken bir uygulamada, yanıtı işleyen *bitiş* yönteminin yürütülmesini, istenen iş parçacığına açıkça sıramalısınız. Örneğin, Windows Presentation Foundation (WPF) tabanlı uygulamalar ve Silverlight tabanlı uygulamalarda, yanıt, <xref:System.Windows.Threading.Dispatcher> nesnesindeki <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi kullanılarak UI iş parçacığına geri sıralanmalıdır. Daha fazla bilgi için bkz. [veri hizmetini sorgulama (WCF veri Hizmetleri/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
