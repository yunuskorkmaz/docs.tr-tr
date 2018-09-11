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
ms.openlocfilehash: 5cd2fa6219f39a8506d865d85e1ce5f84d22a92f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269039"
---
# <a name="asynchronous-programming-model-apm"></a>Zaman Uyumsuz Programlama Modeli (APM)
Kullanan zaman uyumsuz bir işlem <xref:System.IAsyncResult> tasarım deseni adlı iki yöntem uygulanan **başlangıç ** * OperationName* ve **son ** * OperationName* başlar ve zaman uyumsuz bitiş işlem *OperationName* sırasıyla. Örneğin, <xref:System.IO.FileStream> sağlar sınıfını <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.EndRead%2A> bayt bir dosyadan zaman uyumsuz olarak okumak için yöntemleri. Bu yöntemlerin zaman uyumsuz bir sürümüne uygulamak <xref:System.IO.FileStream.Read%2A> yöntemi.  
  
> [!NOTE]
>  .NET Framework 4 ile başlayarak, görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar. Daha fazla bilgi için [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Çağırdıktan sonra **başlamak ** * OperationName*, bir uygulama zaman uyumsuz işlemi gerçekleştirilirken farklı bir iş parçacığı üzerinde yönergeleri çağıran iş parçacığında yürütme devam eder. Her çağrı için **başlamak ** * OperationName*, uygulama da çağırmalıdır **son ** * OperationName* işlemi sonuçları elde etmek için.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlangıcı  
 **Başlamak ** * OperationName* yöntemi zaman uyumsuz işlemi başlar *OperationName* ve uygulayan bir nesne döndürür <xref:System.IAsyncResult> arabirimi. <xref:System.IAsyncResult> nesneler zaman uyumsuz bir işlem hakkında bilgi depolar. Aşağıdaki tabloda, zaman uyumsuz bir işlem hakkında bilgi gösterir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Zaman uyumsuz işlemi hakkında bilgi içeren bir isteğe bağlı bir uygulamaya özgü nesne.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> zaman uyumsuz işlem tamamlanana kadar uygulamanın yürütülmesini engellemek için kullanılabilir.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|İş parçacığı üzerinde tamamlanan zaman uyumsuz işlem çağırmak için kullanılan olup olmadığını belirten bir değer **başlamak ** * OperationName* ayrı bir Tamamlanıyor yerine <xref:System.Threading.ThreadPool> iş parçacığı.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Zaman uyumsuz işlem tamamlanıp tamamlanmadığını belirten bir değer.|  
  
 A **başlamak ** * OperationName* yöntemi değere veya başvuruya göre geçirilen yöntemi zaman uyumlu sürümünü imzada bildirilen parametreleri alır. Out Parametreleri herhangi olmayan parçası **başlamak ** * OperationName* yöntem imzası. **Başlamak ** * OperationName* yöntem imzası da iki ek parametreler içerir. Bunlardan ilki tanımlayan bir <xref:System.AsyncCallback> zaman uyumsuz işlem tamamlandığında çağrılan bir yönteme başvuran temsilci. Çağıranın belirtebilirsiniz `null` (`Nothing` Visual Basic'te) işlemi tamamlandıktan sonra çağrılan bir yöntem istemiyorsa. İkinci ek parametre kullanıcı tanımlı bir nesnedir. Bu nesne, uygulamaya özel durum bilgilerini zaman uyumsuz işlem tamamlandığında çağrılan yönteme geçirmek için kullanılabilir. Varsa bir **başlamak ** * OperationName* yöntemi bir dosyadan okunan bayt depolamak için bir bayt dizisi gibi ek işleme özgü parametreleri alır <xref:System.AsyncCallback> ile uygulama durumu nesnesi son parametrelerinde **Başlamak ** * OperationName* yöntem imzası.  
  
 **Begin ** * OperationName* döndürür denetim çağıran iş parçacığı hemen. Varsa **başlamak ** * OperationName* yöntemi özel durum oluşturur, zaman uyumsuz işlemi başlamadan önce özel durumlar. Varsa **başlamak ** * OperationName* yöntemi özel durum oluşturur, geri çağırma yöntemi çağrılamaz.  
  
## <a name="ending-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem bitiş  
 **Son ** * OperationName* yöntemi zaman uyumsuz işlemi sonlandırır *OperationName*. Dönüş değerini **son ** * OperationName* yöntemi zaman uyumlu kendisine karşılık gelen tarafından döndürülen aynı türde ve zaman uyumsuz işlemi özeldir. Örneğin, <xref:System.IO.FileStream.EndRead%2A> yöntemi okunan bayt sayısını döndüren bir <xref:System.IO.FileStream> ve <xref:System.Net.Dns.EndGetHostByName%2A> yöntemi döndürür bir <xref:System.Net.IPHostEntry> bir konak bilgisayar hakkında bilgi içeren nesne. **Son ** * OperationName* yöntemi herhangi sürüyor veya bildirilen yöntemi zaman uyumlu sürümünü imzada ref parametreler. Zaman uyumlu yöntemi parametrelerinden yanı sıra **son ** * OperationName* yöntemi de içeren bir <xref:System.IAsyncResult> parametresi. Arayanlar için karşılık gelen çağrı tarafından döndürülen örnek geçmesi gerekir **başlamak ** * OperationName*.  
  
 Zaman uyumsuz işlemi temsil varsa <xref:System.IAsyncResult> nesne ne zaman tamamlanmadı **son ** * OperationName* olarak adlandırılır, **son ** * OperationName* çağıran iş parçacığı kadar engeller zaman uyumsuz işlemi tamamlanır. Zaman uyumsuz işlemi tarafından oluşturulan özel durum **son ** * OperationName* yöntemi. Arama etkisini **son ** * OperationName* yöntemiyle birden çok kez aynı <xref:System.IAsyncResult> tanımlı değil. Benzer şekilde, çağırma **son ** * OperationName* yöntemi ile bir <xref:System.IAsyncResult> , değil döndürüldü ilgili Begin tarafından yöntemi de tanımlı değil.  
  
> [!NOTE]
>  Özel durum atma uygulayıcılar ya da tanımlanmamış senaryoları için düşünmelisiniz <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Uygulayıcılar, bu tasarım deseni ayarlayarak zaman uyumsuz işlemi tamamlandı. çağıranın bildir <xref:System.IAsyncResult.IsCompleted%2A> (belirtilmişse) zaman uyumsuz geri çağırma yöntemini çağırarak ve sinyal true olarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Uygulama geliştiricileri, zaman uyumsuz işlemin sonuçları erişmek için çeşitli tasarım seçenekleri sahiptir. Uygulama işlemi tamamlanırken yürütebilir yönergeleri olup doğru seçim bağlıdır. Zaman uyumsuz işlemin sonuçları alana kadar bir uygulama herhangi bir ek çalışma gerçekleştiremiyorsanız sonuçları kullanılabilir olana kadar uygulamayı engellemeniz gerekir. Zaman uyumsuz işlem tamamlanana kadar engellemek için aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Çağrı **son ** * OperationName* uygulamanın ana iş parçacığından işlemi kadar uygulamanın yürütülmesini engelleme tamamlanmıştır. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulama yürütmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> için bir veya daha fazla işlem tamamlanana kadar uygulamanın yürütülmesini engelleme. Bu teknik gösteren bir örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz işlemi tamamlanırken engellemek için gerekmeyen uygulamalar aşağıdaki yaklaşımlardan birini kullanabilirsiniz:  
  
-   Yoklama işlemi tamamlanma durumunu denetleyerek için <xref:System.IAsyncResult.IsCompleted%2A> özelliği düzenli aralıklarla ve arama **son ** * OperationName* işlemi tamamlandığında. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemin durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Kullanım bir <xref:System.AsyncCallback> işlemi tamamlandığında çağrılacak bir yöntem belirtmek için temsilci. Bu teknik gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
