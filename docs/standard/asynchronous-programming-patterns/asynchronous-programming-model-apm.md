---
title: Zaman Uyumsuz Programlama Modeli (APM)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66553d18d46d94fb0febfff8460ac7764e9b62bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
Kullanan zaman uyumsuz bir işlem <xref:System.IAsyncResult> tasarım deseni adlı iki yöntem uygulanan **başlamak***OperationName* ve **son**  *OperationName* başlar ve zaman uyumsuz işlemi sona *OperationName* sırasıyla. Örneğin, <xref:System.IO.FileStream> SAX <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.EndRead%2A> bayt bir dosyadan zaman uyumsuz olarak okumak için yöntemleri. Bu yöntemlerin zaman uyumsuz sürümü uygulamak <xref:System.IO.FileStream.Read%2A> yöntemi.  
  
> [!NOTE]
>  .NET Framework 4 ile başlayarak, görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar. Daha fazla bilgi için bkz: [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Çağırdıktan sonra **başlamak***OperationName*, bir uygulama zaman uyumsuz işlemi gerçekleştirilirken farklı bir iş parçacığı üzerinde yönergeleri çağıran iş parçacığında yürütme devam eder. Her çağrı için **başlamak***OperationName*, uygulama da çağırmalıdır **son***OperationName* sonuçlarını almak için işlem.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlangıcı  
 **Başlamak***OperationName* yöntemi zaman uyumsuz işlemi başlar *OperationName* ve uygulayan bir nesne döndürür <xref:System.IAsyncResult> arabirimi. <xref:System.IAsyncResult>nesneler zaman uyumsuz bir işlem hakkında bilgi depolar. Aşağıdaki tabloda, zaman uyumsuz bir işlem hakkında bilgi gösterir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlemi hakkında bilgi içeren bir isteğe bağlı bir uygulamaya özgü nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> zaman uyumsuz işlemi tamamlanana kadar uygulamanın yürütülmesini engellemek için kullanılabilir.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|İş parçacığı üzerinde tamamlanan zaman uyumsuz işlem çağırmak için kullanılan olup olmadığını belirten bir değer **başlamak***OperationName* ayrı bir Tamamlanıyor yerine <xref:System.Threading.ThreadPool> iş parçacığı.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlemi tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 A **başlamak***OperationName* yöntemi değere veya başvuruya göre geçirilen yöntemi zaman uyumlu sürümünü imzada bildirilen parametreleri alır. Out Parametreleri herhangi olmayan parçası **başlamak***OperationName* yöntem imzası. **Başlamak***OperationName* yöntem imzası da iki ek parametreler içerir. Bunlardan ilki tanımlayan bir <xref:System.AsyncCallback> zaman uyumsuz işlemi tamamlandıktan sonra çağrılan bir yönteme başvuran temsilci. Arayan belirtebilirsiniz `null` (`Nothing` Visual Basic'te) işlem tamamlandığında başlatılan bir yöntem istemiyorsa. İkinci ek parametre kullanıcı tanımlı bir nesnedir. Bu nesne, uygulamaya özgü durum bilgilerini zaman uyumsuz işlemi tamamlandıktan sonra çağrılan yöntemin geçirmek için kullanılabilir. Varsa bir **başlamak***OperationName* yöntemi bir dosyadan okunan bayt depolamak için bir bayt dizisi gibi ek işleme özgü parametreleri alır <xref:System.AsyncCallback> ile uygulama durumu nesnesi son Parametrelerde **başlamak***OperationName* yöntem imzası.  
  
 **Begin***OperationName* döndürür denetim çağıran iş parçacığı hemen. Varsa **başlamak***OperationName* yöntemi özel durum oluşturur, zaman uyumsuz işlemi başlamadan önce özel durumlar. Varsa **başlamak***OperationName* yöntemi özel durum oluşturur, geri çağırma yöntemi çağrılamaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem bitiş  
 **Son***OperationName* yöntemi zaman uyumsuz işlemi sonlandırır *OperationName*. Dönüş değerini **son***OperationName* yöntemi zaman uyumlu kendisine karşılık gelen tarafından döndürülen aynı türde ve zaman uyumsuz işlemi özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi döndürür okunan bayt sayısı bir <xref:System.IO.FileStream> ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi döndürür bir <xref:System.Net.IPHostEntry> bir ana bilgisayar hakkında bilgi içeren nesne. **Son***OperationName* yöntemi herhangi sürüyor veya bildirilen yöntemi zaman uyumlu sürümünü imzada ref parametreler. Zaman uyumlu yöntemi parametrelerinden yanı sıra **son***OperationName* yöntemi de içeren bir <xref:System.IAsyncResult> parametresi. Arayanlar için karşılık gelen çağrı tarafından döndürülen örnek geçmesi gerekir **başlamak***OperationName*.  
  
 Zaman uyumsuz işlemi temsil varsa <xref:System.IAsyncResult> nesne ne zaman tamamlanmadı **son***OperationName* olarak adlandırılır, **son**  *OperationName* zaman uyumsuz işlemi tamamlanana kadar çağıran iş parçacığı engeller. Zaman uyumsuz işlemi tarafından oluşturulan özel durum **son***OperationName* yöntemi. Arama etkisini **son***OperationName* yöntemiyle birden çok kez aynı <xref:System.IAsyncResult> tanımlı değil. Benzer şekilde, çağırma **son***OperationName* yöntemi ile bir <xref:System.IAsyncResult> , değil döndürüldü ilgili Begin tarafından yöntemi de tanımlı değil.  
  
> [!NOTE]
>  Atma ya da tanımsız senaryoları için Implementers düşünmelisiniz <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Bu tasarım deseni Implementers ayarlayarak zaman uyumsuz işlemi tamamlandı çağıran bildir <xref:System.IAsyncResult.IsCompleted%2A> (belirtilmişse) zaman uyumsuz geri çağırma yöntemini çağırarak ve sinyal true olarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Uygulama geliştiricilerinin zaman uyumsuz işlem sonuçlarını erişmek için birkaç tasarım seçeneğiniz vardır. Doğru seçim olup uygulama işlemi tamamlanırken yürütebilir yönergeleri bağlıdır. Zaman uyumsuz işlem sonuçlarını alıncaya kadar uygulama herhangi bir ek iş gerçekleştirilemiyor, sonuçları kullanılabilir oluncaya kadar uygulama engellemelidir. Zaman uyumsuz bir işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Çağrı **son***OperationName* uygulamanın ana iş parçacığından işlemi kadar uygulamanın yürütülmesini engelleme tamamlanmıştır. Bu teknik gösteren örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir veya daha fazla işlem tamamlanana kadar blok uygulama yürütme için. Bu teknik gösteren örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlemi tamamlanırken engelleme gerekmez uygulamaları aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Yoklama işlemi tamamlanma durumunu denetleyerek için <xref:System.IAsyncResult.IsCompleted%2A> özelliği düzenli aralıklarla ve arama **son***OperationName* işlemi tamamlandığında. Bu teknik gösteren örnek için bkz: [için zaman uyumsuz bir işlem durumunu yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Kullanım bir <xref:System.AsyncCallback> işlemi tamamlandığında çağrılacak bir yöntem belirtmek için temsilci. Bu teknik gösteren örnek için bkz: [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
