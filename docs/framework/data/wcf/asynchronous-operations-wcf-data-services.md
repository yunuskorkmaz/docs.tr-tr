---
title: Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: d1f45979dba5c3ab0dccc8d0a61a7abaa9913e11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556869"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Zaman uyumsuz Işlemler (WCF Veri Hizmetleri)
Web uygulamaları, istemci ve sunucu arasında iç ağların içinde çalışan uygulamalardan daha yüksek gecikme süresine sahip olmalıdır. Uygulamanızın performans ve Kullanıcı deneyimini iyileştirmek için, <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> Web üzerinden WCF veri Hizmetleri sunucularına erişirken ve sınıflarının zaman uyumsuz yöntemlerini kullanmanızı öneririz.  
  
 WCF Veri Hizmetleri sunucuları HTTP isteklerini zaman uyumsuz olarak işetse de, WCF Veri Hizmetleri istemci kitaplıklarının bazı yöntemleri zaman uyumludur ve yürütmeye devam etmeden önce tüm istek-yanıt alışverişi tamamlanana kadar bekler. WCF Veri Hizmetleri istemci kitaplıklarının zaman uyumsuz yöntemleri, bu Exchange 'in tamamlanmasını beklemez ve uygulamanızın bu sırada yanıt veren bir kullanıcı arabirimini korumasına izin verebilir.  
  
 <xref:System.Data.Services.Client.DataServiceContext>Ve <xref:System.Data.Services.Client.DataServiceQuery%601> sırasıyla *BEGIN* ve *End* ile başlayan sınıflarda bir yöntem çifti kullanarak zaman uyumsuz işlemler gerçekleştirebilirsiniz. *Begin* yöntemleri, işlem tamamlandığında hizmetin çağırdığı bir temsilciyi kaydeder. *Bitiş* yöntemleri, tamamlanan işlemlerden geri çağırma işlemini işlemek için kayıtlı olan temsilde çağrılmalıdır. Zaman uyumsuz bir işlemi gerçekleştirmek için *bitiş* yöntemini çağırdığınızda, <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceContext> Bu işlemi başlatmak için kullandığınız aynı veya örnekten bunu yapmanız gerekir. Her *BEGIN* yöntemi, bir `state` durum nesnesini geri aramaya geçirebileceğiniz bir parametre alır. Bu durum nesnesi, <xref:System.IAsyncResult> geri çağırma ile sağlanan öğesinden alınır ve zaman uyumsuz işlemi gerçekleştirmek için karşılık gelen *bitiş* yöntemini çağırmak için kullanılır. Örneğin, örneğinde <xref:System.Data.Services.Client.DataServiceQuery%601> yöntemini çağırdığınızda örneği parametre olarak sağlarsanız, `state` <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> aynı <xref:System.Data.Services.Client.DataServiceQuery%601> örnek tarafından döndürülür <xref:System.IAsyncResult> . Bu örneği <xref:System.Data.Services.Client.DataServiceQuery%601> daha sonra <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sorgu işlemini tamamlamaya yönelik yöntemi çağırmak için kullanılır. Daha fazla bilgi için bkz. [nasıl yapılır: zaman uyumsuz veri hizmeti sorguları yürütme](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
> Yalnızca zaman uyumsuz işlemler, Silverlight için .NET Framework belirtilen istemci kitaplıkları tarafından desteklenir. Daha fazla bilgi için bkz. [WCF veri Hizmetleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 .NET Framework istemci kitaplıkları aşağıdaki zaman uyumsuz işlemleri destekler:  
  
|İşlem|Yöntemler|  
|---------------|-------------|  
|Bir yürütülüyor <xref:System.Data.Services.Client.DataServiceQuery%601> .|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Öğesinden bir sorgu yürütülüyor <xref:System.Data.Services.Client.DataServiceContext> .|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Öğesinden bir toplu iş sorgusu yürütülüyor <xref:System.Data.Services.Client.DataServiceContext> .|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|İle ilgili bir varlık yükleme <xref:System.Data.Services.Client.DataServiceContext> .|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|İçindeki nesnelerde yapılan değişiklikler kaydediliyor <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Zaman uyumsuz Işlemler için iş parçacığı konuları  
 Çok iş parçacıklı bir uygulamada, zaman uyumsuz işlem için geri arama olarak kaydedilen temsilcinin, *başlangıç yöntemini çağırmak* için kullanılan aynı iş parçacığında çağrılması gerekmez, bu da ilk isteği oluşturur. Geri aramanın belirli bir iş parçacığında çağrılması gereken bir uygulamada, yanıtı işleyen *bitiş* yönteminin yürütülmesini, istenen iş parçacığına açıkça sıramalısınız. Örneğin, Windows Presentation Foundation (WPF) tabanlı uygulamalar ve Silverlight tabanlı uygulamalarda, yanıt, nesne üzerindeki yöntemi kullanılarak UI iş parçacığına geri sıralanmalıdır <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> <xref:System.Windows.Threading.Dispatcher> . Daha fazla bilgi için bkz. [veri hizmetini sorgulama (WCF veri Hizmetleri/Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
