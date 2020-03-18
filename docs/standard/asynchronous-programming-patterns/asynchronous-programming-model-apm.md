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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140145"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
Tasarım deseni kullanan bir eşzamanlı işlem, sırasıyla asynchronous işlemi *OperationName'i* başlatan ve `BeginOperationName` `EndOperationName` sona erdirebilen iki yöntem olarak uygulanır. <xref:System.IAsyncResult> Örneğin, <xref:System.IO.FileStream> sınıf bir <xref:System.IO.FileStream.BeginRead%2A> dosyadan baytları eşit bir şekilde okumak için ve <xref:System.IO.FileStream.EndRead%2A> yöntemleri sağlar. Bu yöntemler <xref:System.IO.FileStream.Read%2A> yöntemin asynchronous sürümünü uygular.  
  
> [!NOTE]
> .NET Framework 4'ten başlayarak, Görev Paralel Kitaplığı asynchronous ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [Görev Tabanlı Eşzamanlı Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)bakın.  
  
 Aramadan `BeginOperationName`sonra, asynchronous işlemi farklı bir iş parçacığı üzerinde gerçekleşirken bir uygulama arama iş parçacığı üzerinde yönergeleri yürütmeye devam edebilirsiniz. Her arama `BeginOperationName`için , uygulama `EndOperationName` da operasyonun sonuçlarını almak için aramak gerekir.  
  
## <a name="beginning-an-asynchronous-operation"></a>Bir Eşzamanlı İşlem Ebaş  
 Yöntem, `BeginOperationName` asynchronous işlemi *OperationName* başlar ve <xref:System.IAsyncResult> arabirimi uygulayan bir nesne döndürür. <xref:System.IAsyncResult>nesneler, bir eşzamanlı işlem le ilgili bilgileri depolar. Aşağıdaki tabloda bir eşzamanlı işlem hakkında bilgi gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Eşzamanlı işlem hakkında bilgi içeren isteğe bağlı uygulamaya özgü bir nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Eşil <xref:System.Threading.WaitHandle> işlem tamamlanana kadar uygulama yürütmesini engellemek için kullanılabilecek bir a.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Ayrı `BeginOperationName` <xref:System.Threading.ThreadPool> bir iş parçacığı üzerinde tamamlamak yerine aramak için kullanılan iş parçacığı üzerinde eşenkron işlemin tamamlanıp tamamlanmadığını gösteren bir değer.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Eşsenkronize işlemin tamamlanıp tamamlanmadığını gösteren bir değer.|  
  
 Yöntem, `BeginOperationName` yöntemin değer veya başvuru ile geçirilen eşzamanlı sürümünün imzasında bildirilen parametreleri alır. Herhangi bir çıkış parametreleri `BeginOperationName` yöntem imzasının bir parçası değildir. Yöntem `BeginOperationName` imzası da iki ek parametre içerir. Bunlardan ilki, eşzamanlı <xref:System.AsyncCallback> işlem tamamlandığında adı verilen bir yönteme başvuran bir temsilci tanımlar. Arayan, işlem `null` `Nothing` tamamlandığında bir yöntemin çağrılması istemiyorsa (Visual Basic'te) belirtebilir. İkinci ek parametre kullanıcı tanımlı bir nesnedir. Bu nesne, uygulama için özel durum bilgilerini, eşzamanlı işlem tamamlandığında çağrılan yönteme geçirmek için kullanılabilir. Bir `BeginOperationName` yöntem, dosyadan okunan baytları depolamak için bayt dizisi gibi <xref:System.AsyncCallback> ek işlem özgü parametreleri alırsa, `BeginOperationName` yöntem imzasındaki son parametreler ve uygulama durumu nesnesi olur.  
  
 `BeginOperationName`denetimi hemen arama iş parçacığına döndürür. `BeginOperationName` Yöntem özel durumlar atarsa, özel durumlar eşenkron işlem başlamadan önce atılır. `BeginOperationName` Yöntem özel durumlar atarsa, geri arama yöntemi çağrılmaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Eşkron İşleme Son Verme  
 Yöntem `EndOperationName` asynchronous işlemi *OperationName*sona erer. Yöntemin `EndOperationName` geri dönüş değeri, senkron muadili tarafından döndürülen tipteki tiptir ve eşzamanlı işlem için özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntem a'dan <xref:System.IO.FileStream> okunan bayt sayısını <xref:System.Net.Dns.EndGetHostByName%2A> döndürür <xref:System.Net.IPHostEntry> ve yöntem ana bilgisayar hakkında bilgi içeren bir nesneyi döndürür. Yöntem, `EndOperationName` yöntemin senkron sürümünün imzasında bildirilen herhangi bir çıkar veya ref parametrelerini alır. Senkron yöntemden parametrelere ek olarak, `EndOperationName` yöntem de <xref:System.IAsyncResult> bir parametre içerir. Arayanlar, karşılık gelen çağrı tarafından döndürülen örneği `BeginOperationName`geçmelidir.  
  
 <xref:System.IAsyncResult> Nesne tarafından temsil edilen eşzamanlı işlem çağrıldığında `EndOperationName` tamamlanmadıysa, `EndOperationName` çağrı iş parçacığı asynchronous işlemi tamamlanana kadar engeller. Eşsenkronize işlem tarafından atılan özel durumlar `EndOperationName` yöntemden atılır. `EndOperationName` Yöntemi aynı <xref:System.IAsyncResult> ile birden çok kez çağırmanın etkisi tanımlanmamıştır. Aynı şekilde, `EndOperationName` ilgili Begin <xref:System.IAsyncResult> yöntemi tarafından döndürülmeyen bir yöntemle çağrılması da tanımlanmaz.  
  
> [!NOTE]
> Tanımlanmamış senaryolardan biri için, uygulayıcılar <xref:System.InvalidOperationException>atmayı düşünmelidir.  
  
> [!NOTE]
> Bu tasarım deseninin uygulayıcıları, asenkron işlemin doğru <xref:System.IAsyncResult.IsCompleted%2A> ayarlanarak tamamlandığını, eşzamanlı geri arama yöntemini (belirtilmişse) <xref:System.IAsyncResult.AsyncWaitHandle%2A>ve sinyalizasyonu yapan asenkron işlemin tamamlandığını arayana bildirmelidir.  
  
 Uygulama geliştiricilerin, eşzamanlı işlemin sonuçlarına erişmek için çeşitli tasarım seçenekleri vardır. Doğru seçim, uygulamanın işlem tamamlandığında yürütülebilecek yönergelere sahip olup olmadığına bağlıdır. Bir uygulama, eşenkron işlemin sonuçlarını alana kadar ek bir çalışma gerçekleştiremiyorsa, sonuçlar kullanılabilir olana kadar uygulamanın engellenmesi gerekir. Bir eşzamanlı işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
- Uygulamanın ana iş parçacığından arama, `EndOperationName` işlem tamamlanana kadar uygulama yürütmesini engelleyin. Bu tekniği gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)örnek için bkz.  
  
- Bir <xref:System.IAsyncResult.AsyncWaitHandle%2A> veya daha fazla işlem tamamlanana kadar uygulama yürütmesini engellemek için kullanın. Bu tekniği gösteren bir örnek için, [bkz.](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)  
  
 Eşkron işlemi tamamlarken engellenmesi gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilir:  
  
- <xref:System.IAsyncResult.IsCompleted%2A> Mülkü periyodik olarak kontrol ederek ve işlem `EndOperationName` tamamlandığında arayarak işlemi tamamlama durumu için anket. Bu tekniği gösteren bir örnek için, Bir [Eşzamanlı İşlemin Durumu Için Yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)bölümüne bakın.  
  
- İşlem <xref:System.AsyncCallback> tamamlandığında çağrılacak bir yöntem belirtmek için bir temsilci kullanın. Bu tekniği gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)örnek için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
