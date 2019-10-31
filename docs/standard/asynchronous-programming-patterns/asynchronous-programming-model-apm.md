---
title: Zaman Uyumsuz Programlama Modeli (APM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
ms.openlocfilehash: 0a9ea3c8c9c589bb5954fa9771ffd1bb095f6d73
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140145"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
<xref:System.IAsyncResult> tasarım modelini kullanan zaman uyumsuz bir işlem, `BeginOperationName` ve `EndOperationName` zaman uyumsuz işlem *OperationName* ' i başlayan ve biten iki yöntem olarak uygulanır. Örneğin <xref:System.IO.FileStream> sınıfı, bir dosyadan zaman uyumsuz olarak okunan <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.EndRead%2A> yöntemlerini sağlar. Bu yöntemler <xref:System.IO.FileStream.Read%2A> yönteminin zaman uyumsuz sürümünü uygular.  
  
> [!NOTE]
> .NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 `BeginOperationName`çağrıldıktan sonra bir uygulama, farklı bir iş parçacığında zaman uyumsuz işlem gerçekleşirken çağıran iş parçacığı üzerinde yönergeleri yürütmeye devam edebilir. Her `BeginOperationName`çağrısı için uygulama, işlemin sonuçlarını almak için de `EndOperationName` çağırmalıdır.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem başlatılıyor  
 `BeginOperationName` yöntemi zaman uyumsuz işlem *OperationName* ' a başlar ve <xref:System.IAsyncResult> arabirimini uygulayan bir nesne döndürür. <xref:System.IAsyncResult> nesneler, zaman uyumsuz bir işlemle ilgili bilgileri depolar. Aşağıdaki tabloda bir zaman uyumsuz işlemle ilgili bilgiler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlem hakkında bilgi içeren, uygulamaya özel isteğe bağlı bir nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Zaman uyumsuz işlem tamamlanana kadar uygulama yürütmeyi engellemek için kullanılabilen bir <xref:System.Threading.WaitHandle>.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Ayrı bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde tamamlamak yerine `BeginOperationName` çağırmak için kullanılan iş parçacığında zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 `BeginOperationName` yöntemi, değer veya başvuruya göre geçirilen yöntemin zaman uyumlu sürümünün imzasında belirtilen parametreleri alır. Tüm out parametreleri `BeginOperationName` yöntemi imzasının bir parçası değildir. `BeginOperationName` yöntemi imzası Ayrıca iki ek parametre içerir. Bunlardan ilki, zaman uyumsuz işlem tamamlandığında çağrılan bir yönteme başvuran bir <xref:System.AsyncCallback> temsilcisini tanımlar. Çağıran, işlem tamamlandığında çağrılan bir yöntemin`Nothing` `null` (Visual Basic) belirtebilir. İkinci ek parametre Kullanıcı tanımlı bir nesnedir. Bu nesne, zaman uyumsuz işlem tamamlandığında çağrılan yönteme uygulamaya özgü durum bilgilerini geçirmek için kullanılabilir. Bir `BeginOperationName` yöntemi bir dosyadan okunan baytları depolamak için bir bayt dizisi gibi, işleme özgü ek parametreler alırsa, <xref:System.AsyncCallback> ve uygulama durumu nesnesi `BeginOperationName` yöntemi imzasında son parametrelerdir.  
  
 `BeginOperationName`, denetimi çağıran iş parçacığına hemen döndürür. `BeginOperationName` yöntemi özel durumlar oluşturursa, özel durumlar zaman uyumsuz işlem başlatılmadan önce oluşturulur. `BeginOperationName` yöntemi özel durumlar oluşturursa, geri çağırma yöntemi çağrılmaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem sonlandırılıyor  
 `EndOperationName` yöntemi zaman uyumsuz işlem *OperationName*'ı sonlandırır. `EndOperationName` yönteminin dönüş değeri, zaman uyumlu karşılığına göre döndürülen türdür ve zaman uyumsuz işleme özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi bir <xref:System.IO.FileStream> okunan bayt sayısını döndürür ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi bir ana bilgisayar hakkında bilgi içeren bir <xref:System.Net.IPHostEntry> nesnesi döndürür. `EndOperationName` yöntemi, yöntemin zaman uyumlu sürümünün imzasında belirtilen tüm out veya ref parametrelerini alır. Zaman uyumlu yöntemden parametrelere ek olarak `EndOperationName` yöntemi de bir <xref:System.IAsyncResult> parametresi içerir. Çağıranlar `BeginOperationName`için karşılık gelen çağrının döndürdüğü örneği iletmelidir.  
  
 `EndOperationName` çağrıldığında <xref:System.IAsyncResult> nesnesi tarafından temsil edilen zaman uyumsuz işlem tamamlanmışsa `EndOperationName`, zaman uyumsuz işlem tamamlanana kadar çağıran iş parçacığını engeller. Zaman uyumsuz işlem tarafından oluşturulan özel durumlar `EndOperationName` yönteminden oluşturulur. `EndOperationName` yöntemini aynı <xref:System.IAsyncResult> birden çok kez çağırma efekti tanımlı değil. Benzer şekilde, ilgili Begin yöntemi tarafından döndürülmüş olan bir <xref:System.IAsyncResult> `EndOperationName` yöntemi çağrılması de tanımlanmamıştır.  
  
> [!NOTE]
> Tanımsız senaryolardan herhangi biri için, uygulayıcıları <xref:System.InvalidOperationException>yapmayı düşünmelidir.  
  
> [!NOTE]
> Bu tasarım deseninin uygulayıcıları, zaman uyumsuz işlemin tamamlandığını, <xref:System.IAsyncResult.IsCompleted%2A> true olarak ayarlayarak, zaman uyumsuz geri arama yöntemini çağırarak (belirtilmişse) ve <xref:System.IAsyncResult.AsyncWaitHandle%2A>sinyalleyerek çağrıyı yapana bildirir.  
  
 Uygulama geliştiricilerinin zaman uyumsuz işlemin sonuçlarına erişmek için çeşitli tasarım seçimleri vardır. Doğru seçim, uygulamanın işlem tamamlandığında yürütebileceğiniz yönergeler içerip içermediğini bağlıdır. Bir uygulama, zaman uyumsuz işlemin sonuçlarını alıncaya kadar ek bir iş gerçekleştire, sonuçlar kullanılabilir olana kadar uygulamanın engellenmesi gerekir. Zaman uyumsuz bir işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
- Uygulamanın ana iş parçacığından `EndOperationName` çağırın, işlem tamamlanana kadar uygulama yürütmeyi engeller. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Bir veya daha fazla işlem tamamlanana kadar uygulama yürütmeyi engellemek için <xref:System.IAsyncResult.AsyncWaitHandle%2A> kullanın. Bu tekniği gösteren bir örnek için bkz. [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlem tamamlandığında engellemek Gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilir:  
  
- <xref:System.IAsyncResult.IsCompleted%2A> özelliğini düzenli olarak denetleyerek ve işlem tamamlandığında `EndOperationName` çağırarak işlem tamamlanma durumu için yoklama yapın. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- İşlem tamamlandığında çağrılacak yöntemi belirtmek için bir <xref:System.AsyncCallback> temsilcisini kullanın. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
