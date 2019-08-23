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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c03a6dadae98d75b06b96bb3cde67db4747b8c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950878"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
<xref:System.IAsyncResult> Tasarım modelini kullanan zaman uyumsuz bir işlem, adlı `BeginOperationName` ve sırasıyla zaman uyumsuz işlem *OperationName* ' i başlayan ve `EndOperationName` biten iki yöntem olarak uygulanır. Örneğin, <xref:System.IO.FileStream> sınıfı bir dosyadan zaman uyumsuz olarak <xref:System.IO.FileStream.EndRead%2A> okunan baytları <xref:System.IO.FileStream.BeginRead%2A> ve yöntemleri sağlar. Bu yöntemler, <xref:System.IO.FileStream.Read%2A> yönteminin zaman uyumsuz sürümünü uygular.  
  
> [!NOTE]
> .NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Çağrıldıktan sonra bir uygulama ,farklıbirişparçacığındazamanuyumsuzişlemgerçekleşirkençağıranişparçacığıüzerindeyönergeleriyürütmeyedevamedebilir.`BeginOperationName` Her çağrısı `BeginOperationName`için, uygulamanın, işlemin sonuçlarını almak için `EndOperationName` de çağırması gerekir.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem başlatılıyor  
 Yöntemi zaman uyumsuz işlem *OperationName* ' i başlatır ve <xref:System.IAsyncResult> arabirimi uygulayan bir nesne döndürür. `BeginOperationName` <xref:System.IAsyncResult>nesneler, zaman uyumsuz bir işlemle ilgili bilgileri depolar. Aşağıdaki tabloda bir zaman uyumsuz işlemle ilgili bilgiler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlem hakkında bilgi içeren, uygulamaya özel isteğe bağlı bir nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle> Zaman uyumsuz işlem tamamlanana kadar uygulama yürütmeyi engellemek için kullanılabilir.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|`BeginOperationName` Ayrı<xref:System.Threading.ThreadPool> bir iş parçacığında tamamlamak yerine, çağırmak için kullanılan iş parçacığında zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 Bir `BeginOperationName` Yöntem, değer veya başvuruya göre geçirilen yöntemin zaman uyumlu sürümünün imzasında belirtilen parametreleri alır. Tüm out parametreleri `BeginOperationName` yöntem imzasının bir parçası değildir. `BeginOperationName` Yöntem imzası Ayrıca iki ek parametre içerir. Bunlardan ilki, zaman uyumsuz işlem <xref:System.AsyncCallback> tamamlandığında çağrılan bir yönteme başvuran bir temsilciyi tanımlar. Çağıran `null` , işlem tamamlandığında bir`Nothing` yöntemin çağrılmasını istemediğinden (Visual Basic). İkinci ek parametre Kullanıcı tanımlı bir nesnedir. Bu nesne, zaman uyumsuz işlem tamamlandığında çağrılan yönteme uygulamaya özgü durum bilgilerini geçirmek için kullanılabilir. Bir `BeginOperationName` Yöntem bir dosyadan <xref:System.AsyncCallback> okunan baytları depolamak için bir bayt dizisi gibi işleme özgü ek parametreler alırsa, ve uygulama durumu nesnesi `BeginOperationName` Yöntem imzasında son parametrelerdir.  
  
 `BeginOperationName`denetimi çağıran iş parçacığına hemen döndürür. `BeginOperationName` Yöntem özel durumlar oluşturursa, zaman uyumsuz işlem başlatılmadan önce özel durumlar oluşturulur. `BeginOperationName` Yöntem özel durumlar oluşturursa, geri çağırma yöntemi çağrılmaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem sonlandırılıyor  
 Yöntemi `EndOperationName` , zaman uyumsuz işlem *OperationName*öğesini sonlandırır. `EndOperationName` Yöntemin dönüş değeri, zaman uyumlu karşılığına göre döndürülen türdür ve zaman uyumsuz işleme özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi bir <xref:System.IO.FileStream> öğesinden okunan bayt sayısını döndürür ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi bir ana bilgisayar hakkında bilgi içeren bir <xref:System.Net.IPHostEntry> nesne döndürür. `EndOperationName` Yöntemi, yönteminin zaman uyumlu sürümünün imzasında belirtilen tüm out veya ref parametrelerini alır. Zaman uyumlu yöntemin parametrelerinin yanı sıra, `EndOperationName` yöntemi de bir <xref:System.IAsyncResult> parametre içerir. Çağıranlar öğesine `BeginOperationName`karşılık gelen çağrının döndürdüğü örneği iletmelidir.  
  
 Çağrıldığında <xref:System.IAsyncResult> nesnenin temsil ettiği zaman uyumsuz işlem `EndOperationName` tamamlandıysa, `EndOperationName` zaman uyumsuz işlem tamamlanana kadar çağıran iş parçacığını engeller. Zaman uyumsuz işlem tarafından oluşturulan özel durumlar `EndOperationName` yönteminden oluşturulur. `EndOperationName` Yöntemi aynı<xref:System.IAsyncResult> ile birden çok kez çağırma efekti tanımlı değil. Benzer şekilde, ilgili `EndOperationName` BEGIN yöntemi tarafından <xref:System.IAsyncResult> döndürülmediğinde yöntemi çağırmak da tanımlanmamıştır.  
  
> [!NOTE]
> Tanımsız senaryolardan herhangi biri için, ımplemenonun oluşturulması gerektiğini düşünmelidir <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Bu tasarım deseninin uygulayıcıları, zaman uyumsuz işlemin tamamlandığını çağıran tarafından, zaman uyumsuz geri <xref:System.IAsyncResult.IsCompleted%2A> çağırma yöntemini çağırarak (belirtilmişse) ve <xref:System.IAsyncResult.AsyncWaitHandle%2A>sinyal sinyaline doğru ayarlanarak bildirim almalıdır.  
  
 Uygulama geliştiricilerinin zaman uyumsuz işlemin sonuçlarına erişmek için çeşitli tasarım seçimleri vardır. Doğru seçim, uygulamanın işlem tamamlandığında yürütebileceğiniz yönergeler içerip içermediğini bağlıdır. Bir uygulama, zaman uyumsuz işlemin sonuçlarını alıncaya kadar ek bir iş gerçekleştire, sonuçlar kullanılabilir olana kadar uygulamanın engellenmesi gerekir. Zaman uyumsuz bir işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
- Uygulamanın `EndOperationName` ana iş parçacığından, işlem tamamlanana kadar uygulama yürütmeyi engelleyen çağrı. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Bir veya daha fazla işlem tamamlanana kadar uygulama yürütmeyi engellemek içinkullanın.<xref:System.IAsyncResult.AsyncWaitHandle%2A> Bu tekniği gösteren bir örnek için bkz. [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlem tamamlandığında engellemek Gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilir:  
  
- Özelliği düzenli aralıklarla denetleyerek ve işlem tamamlandığında çağırarak <xref:System.IAsyncResult.IsCompleted%2A> `EndOperationName` , işlem tamamlanma durumu için yoklama yapın. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- İşlem tamamlandığında <xref:System.AsyncCallback> çağrılacak yöntemi belirtmek için bir temsilci kullanın. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
