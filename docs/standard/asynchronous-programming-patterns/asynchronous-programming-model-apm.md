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
ms.openlocfilehash: 3a1921f1a0f0e724bfc8d8289ac1b654cc8198d2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152389"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
Kullanan zaman uyumsuz bir işlem <xref:System.IAsyncResult> tasarım deseni adlı iki yöntem uygulanan `BeginOperationName` ve `EndOperationName` başlar ve zaman uyumsuz işlemi sonlandıran *OperationName* sırasıyla. Örneğin, <xref:System.IO.FileStream> sağlar sınıfını <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.EndRead%2A> bayt bir dosyadan zaman uyumsuz olarak okumak için yöntemleri. Bu yöntemlerin zaman uyumsuz bir sürümüne uygulamak <xref:System.IO.FileStream.Read%2A> yöntemi.  
  
> [!NOTE]
>  .NET Framework 4 ile başlayarak, görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar. Daha fazla bilgi için [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Arama sonra `BeginOperationName`, bir uygulama, zaman uyumsuz işlemi gerçekleşirken farklı bir iş parçacığında yönergeleri çağıran iş parçacığı üzerinde yürütülüyor. devam edebilirsiniz. Her çağrı için `BeginOperationName`, uygulama de çağırmalı `EndOperationName` işlemin sonuçları elde etmek için.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlangıcı  
 `BeginOperationName` Yöntemi zaman uyumsuz işlem başlamadan *OperationName* ve uygulayan bir nesne döndürür <xref:System.IAsyncResult> arabirimi. <xref:System.IAsyncResult> nesneler zaman uyumsuz bir işlem hakkında bilgi depolar. Aşağıdaki tabloda, zaman uyumsuz bir işlem hakkında bilgi gösterir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlemi hakkında bilgi içeren bir isteğe bağlı bir uygulamaya özgü nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> zaman uyumsuz işlem tamamlanana kadar uygulamanın yürütülmesini engellemek için kullanılabilir.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Tamamlanan iş parçacığında zaman uyumsuz işlemi çağırmak için kullanılan olup olmadığını gösteren bir değer `BeginOperationName` yerine ayrı bir tamamlama <xref:System.Threading.ThreadPool> iş parçacığı.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlem tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 A `BeginOperationName` yöntemi değer veya başvuruya göre geçirildiği yöntemin zaman uyumlu sürümü imzasında bildirilen herhangi bir parametre alır. Herhangi bir out parametreleri olmayan parçası `BeginOperationName` metodu imzası. `BeginOperationName` Yöntem imzası, iki ek parametreler de içerir. Bunlardan ilki tanımlayan bir <xref:System.AsyncCallback> zaman uyumsuz işlem tamamlandığında çağrılan bir yönteme başvuran temsilci. Çağıranın belirtebilirsiniz `null` (`Nothing` Visual Basic'te) işlemi tamamlandıktan sonra çağrılan bir yöntem istemiyorsa. İkinci ek parametre kullanıcı tanımlı bir nesnedir. Bu nesne, uygulamaya özel durum bilgilerini zaman uyumsuz işlem tamamlandığında çağrılan yönteme geçirmek için kullanılabilir. Varsa bir `BeginOperationName` yöntemi, bir dosyadan okunan bayt depolamak için bir bayt dizisi gibi ek özel işlem parametreleri alır <xref:System.AsyncCallback> ve uygulama durumu nesnesi son parametrelerinde `BeginOperationName` metodu imzası.  
  
 `BeginOperationName` çağıran iş parçacığını hemen denetimine döndürür. Varsa `BeginOperationName` yöntemin oluşturduğu özel durumlar, zaman uyumsuz işlem başlamadan önce özel durumlar. Varsa `BeginOperationName` yöntemin oluşturduğu özel durumlar, geri çağırma yöntemi çağrılamaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem bitiş  
 `EndOperationName` Yöntemi zaman uyumsuz işlemi sonlandırır *OperationName*. Dönüş değeri `EndOperationName` yöntemi zaman uyumlu karşılığı tarafından döndürülen aynı türde ve zaman uyumsuz işlem için özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi okunan bayt sayısını döndüren bir <xref:System.IO.FileStream> ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi döndürür bir <xref:System.Net.IPHostEntry> bir konak bilgisayar hakkında bilgi içeren nesne. `EndOperationName` Yöntemi herhangi alan veya yöntem zaman uyumlu sürümü imzasında ref parametreleri bildirilmiş. Zaman uyumlu yöntem, parametrelerinden yanı sıra `EndOperationName` yöntemi de içeren bir <xref:System.IAsyncResult> parametresi. Çağıranlar, karşılık gelen çağrısı tarafından döndürülen örneği geçmesi gerekir `BeginOperationName`.  
  
 Zaman uyumsuz işlemi temsil, <xref:System.IAsyncResult> nesne ne zaman tamamlanmadı `EndOperationName` çağrıldığında `EndOperationName` zaman uyumsuz işlem tamamlanana kadar çağıran iş parçacığını engeller. Zaman uyumsuz işlemi tarafından oluşturulan özel durumları durum `EndOperationName` yöntemi. Arama etkisini `EndOperationName` yöntemiyle birden çok kez aynı <xref:System.IAsyncResult> tanımlı değil. Benzer şekilde, çağırma `EndOperationName` yöntemi ile bir <xref:System.IAsyncResult> yöntemi de tanımlı değil ilgili Begin tarafından getirilen değil.  
  
> [!NOTE]
>  Özel durum atma uygulayıcılar ya da tanımlanmamış senaryoları için düşünmelisiniz <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Uygulayıcılar, bu tasarım deseni ayarlayarak zaman uyumsuz işlemi tamamlandı. çağıranın bildir <xref:System.IAsyncResult.IsCompleted%2A> (belirtilmişse) zaman uyumsuz geri çağırma yöntemini çağırarak ve sinyal true olarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Uygulama geliştiricileri, zaman uyumsuz işlemin sonuçları erişmek için çeşitli tasarım seçenekleri sahiptir. Uygulama işlemi tamamlanırken yürütebilir yönergeleri olup doğru seçim bağlıdır. Zaman uyumsuz işlemin sonuçları alana kadar bir uygulama herhangi bir ek çalışma gerçekleştiremiyorsanız sonuçları kullanılabilir olana kadar uygulamayı engellemeniz gerekir. Zaman uyumsuz işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Çağrı `EndOperationName` uygulamanın ana iş parçacığından işlemi kadar uygulamanın yürütülmesini engelleme tamamlanmıştır. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulama yürütmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> için bir veya daha fazla işlem tamamlanana kadar uygulamanın yürütülmesini engelleme. Bu teknik gösteren bir örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlemi tamamlanırken engellemek için gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Denetleyerek işlemi tamamlama durumu için yoklama <xref:System.IAsyncResult.IsCompleted%2A> düzenli aralıklarla özelliği ve arama `EndOperationName` işlemi tamamlandığında. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemin durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Kullanım bir <xref:System.AsyncCallback> işlemi tamamlandığında çağrılacak bir yöntem belirtmek için temsilci. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
