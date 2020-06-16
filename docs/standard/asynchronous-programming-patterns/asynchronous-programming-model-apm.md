---
title: Zaman Uyumsuz Programlama Modeli (APM)
description: .NET 'te zaman uyumsuz programlama modeli (APM) hakkında bilgi edinin. Zaman uyumsuz bir işlemin nasıl başlayıp sonlandıralınacağını öğrenin.
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
ms.openlocfilehash: 5ab5d15d24aac80ef4a31c039f7af9dacce4a8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769190"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
Tasarım modelini kullanan zaman uyumsuz bir işlem, <xref:System.IAsyncResult> adlı `BeginOperationName` ve `EndOperationName` sırasıyla zaman uyumsuz işlem *OperationName* ' i başlayan ve biten iki yöntem olarak uygulanır. Örneğin, <xref:System.IO.FileStream> sınıfı <xref:System.IO.FileStream.BeginRead%2A> <xref:System.IO.FileStream.EndRead%2A> bir dosyadan zaman uyumsuz olarak okunan baytları ve yöntemleri sağlar. Bu yöntemler, yönteminin zaman uyumsuz sürümünü uygular <xref:System.IO.FileStream.Read%2A> .  
  
> [!NOTE]
> .NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar. Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md)).  
  
 Çağrıldıktan sonra `BeginOperationName` bir uygulama, farklı bir iş parçacığında zaman uyumsuz işlem gerçekleşirken çağıran iş parçacığı üzerinde yönergeleri yürütmeye devam edebilir. Her çağrısı için `BeginOperationName` , uygulamanın, `EndOperationName` işlemin sonuçlarını almak için de çağırması gerekir.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem başlatılıyor  
 `BeginOperationName`Yöntemi zaman uyumsuz Işlem *OperationName* ' i başlatır ve arabirimi uygulayan bir nesne döndürür <xref:System.IAsyncResult> . <xref:System.IAsyncResult>nesneler, zaman uyumsuz bir işlemle ilgili bilgileri depolar. Aşağıdaki tabloda bir zaman uyumsuz işlemle ilgili bilgiler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlem hakkında bilgi içeren, uygulamaya özel isteğe bağlı bir nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle>Zaman uyumsuz işlem tamamlanana kadar uygulama yürütmeyi engellemek için kullanılabilir.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|`BeginOperationName`Ayrı bir iş parçacığında tamamlamak yerine, çağırmak için kullanılan iş parçacığında zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer <xref:System.Threading.ThreadPool> .|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlemin tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 Bir `BeginOperationName` Yöntem, değer veya başvuruya göre geçirilen yöntemin zaman uyumlu sürümünün imzasında belirtilen parametreleri alır. Tüm out parametreleri yöntem imzasının bir parçası değildir `BeginOperationName` . `BeginOperationName`Yöntem imzası Ayrıca iki ek parametre içerir. Bunlardan ilki, <xref:System.AsyncCallback> zaman uyumsuz işlem tamamlandığında çağrılan bir yönteme başvuran bir temsilciyi tanımlar. Çağıran, `null` `Nothing` işlem tamamlandığında bir yöntemin çağrılmasını istemediğinden (Visual Basic). İkinci ek parametre Kullanıcı tanımlı bir nesnedir. Bu nesne, zaman uyumsuz işlem tamamlandığında çağrılan yönteme uygulamaya özgü durum bilgilerini geçirmek için kullanılabilir. Bir `BeginOperationName` Yöntem bir dosyadan okunan baytları depolamak için bir bayt dizisi gibi işleme özgü ek parametreler alırsa, <xref:System.AsyncCallback> ve uygulama durumu nesnesi yöntem imzasında son parametrelerdir `BeginOperationName` .  
  
 `BeginOperationName`denetimi çağıran iş parçacığına hemen döndürür. `BeginOperationName`Yöntem özel durumlar oluşturursa, zaman uyumsuz işlem başlatılmadan önce özel durumlar oluşturulur. `BeginOperationName`Yöntem özel durumlar oluşturursa, geri çağırma yöntemi çağrılmaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem sonlandırılıyor  
 `EndOperationName`Yöntemi, zaman uyumsuz Işlem *OperationName*öğesini sonlandırır. Yöntemin dönüş değeri, `EndOperationName` zaman uyumlu karşılığına göre döndürülen türdür ve zaman uyumsuz işleme özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi bir öğesinden okunan bayt sayısını döndürür <xref:System.IO.FileStream> ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi <xref:System.Net.IPHostEntry> bir ana bilgisayar hakkında bilgi içeren bir nesne döndürür. `EndOperationName`Yöntemi, yönteminin zaman uyumlu sürümünün imzasında belirtilen tüm out veya ref parametrelerini alır. Zaman uyumlu yöntemin parametrelerinin yanı sıra, `EndOperationName` yöntemi de bir <xref:System.IAsyncResult> parametre içerir. Çağıranlar öğesine karşılık gelen çağrının döndürdüğü örneği iletmelidir `BeginOperationName` .  
  
 Çağrıldığında nesnenin temsil ettiği zaman uyumsuz işlem <xref:System.IAsyncResult> tamamlandıysa `EndOperationName` , `EndOperationName` zaman uyumsuz işlem tamamlanana kadar çağıran iş parçacığını engeller. Zaman uyumsuz işlem tarafından oluşturulan özel durumlar `EndOperationName` yönteminden oluşturulur. `EndOperationName`Yöntemi aynı ile birden çok kez çağırma efekti <xref:System.IAsyncResult> tanımlı değil. Benzer şekilde, `EndOperationName` <xref:System.IAsyncResult> ilgili BEGIN yöntemi tarafından döndürülmediğinde yöntemi çağırmak da tanımlanmamıştır.  
  
> [!NOTE]
> Tanımsız senaryolardan herhangi biri için, ımplemenonun oluşturulması gerektiğini düşünmelidir <xref:System.InvalidOperationException> .  
  
> [!NOTE]
> Bu tasarım deseninin uygulayıcıları, zaman uyumsuz işlemin tamamlandığını çağıran tarafından <xref:System.IAsyncResult.IsCompleted%2A> , zaman uyumsuz geri çağırma yöntemini çağırarak (belirtilmişse) ve sinyal sinyaline doğru ayarlanarak bildirim almalıdır <xref:System.IAsyncResult.AsyncWaitHandle%2A> .  
  
 Uygulama geliştiricilerinin zaman uyumsuz işlemin sonuçlarına erişmek için çeşitli tasarım seçimleri vardır. Doğru seçim, uygulamanın işlem tamamlandığında yürütebileceğiniz yönergeler içerip içermediğini bağlıdır. Bir uygulama, zaman uyumsuz işlemin sonuçlarını alıncaya kadar ek bir iş gerçekleştire, sonuçlar kullanılabilir olana kadar uygulamanın engellenmesi gerekir. Zaman uyumsuz bir işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
- Uygulamanın `EndOperationName` ana iş parçacığından, işlem tamamlanana kadar uygulama yürütmeyi engelleyen çağrı. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](blocking-application-execution-by-ending-an-async-operation.md).  
  
- <xref:System.IAsyncResult.AsyncWaitHandle%2A>Bir veya daha fazla işlem tamamlanana kadar uygulama yürütmeyi engellemek için kullanın. Bu tekniği gösteren bir örnek için bkz. [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlem tamamlandığında engellemek Gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilir:  
  
- <xref:System.IAsyncResult.IsCompleted%2A>Özelliği düzenli aralıklarla denetleyerek ve işlem tamamlandığında çağırarak, işlem tamamlanma durumu için yoklama yapın `EndOperationName` . Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- <xref:System.AsyncCallback>İşlem tamamlandığında çağrılacak yöntemi belirtmek için bir temsilci kullanın. Bu tekniği gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](calling-synchronous-methods-asynchronously.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](using-an-asynccallback-delegate-and-state-object.md)
