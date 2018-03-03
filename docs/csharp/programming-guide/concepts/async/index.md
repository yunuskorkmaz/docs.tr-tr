---
title: Zaman uyumsuz programlama ile async ve await (C#)
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 501a11f1bc6118e647cc414f4b83a14f6b41a37d
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Zaman uyumsuz programlama ile async ve await (C#)
Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.  
  
[C# 5](../../../whats-new/index.md#previous-versions) basitleştirilmiş bir yaklaşım, .NET Framework 4.5 ve daha yüksek zaman uyumsuz destek kullanan zaman uyumsuz programlama, .NET Core ve Windows çalışma zamanı sunmuştur. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.  
  
Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Zaman uyumsuz yanıt hızını artırır  
 Asynchrony, büyük olasılıkla, gibi web erişimi engelliyor etkinlikler için gereklidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Bu tür bir etkinlik zaman uyumlu bir işlemde engellenirse, tüm uygulama beklemeniz gerekir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.  
  
 Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET ve Windows çalışma zamanı listelenen API'lerden zaman uyumsuz programlama desteği yöntemleri içerir.  
  
| Uygulama alanı    | Zaman uyumsuz yöntemleri ile .NET türleri     | Zaman uyumsuz yöntemleri ile Windows çalışma zamanı türleri  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Görüntülerle çalışma||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.  
  
 Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.  
  
 Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Zaman uyumsuz yöntemleri yazma kolaydır  
 [Zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) ve [await](../../../../csharp/language-reference/keywords/await.md) C# anahtar sözcükler zaman uyumsuz programlama Kalp. Bu iki anahtar sözcükleri kullanarak zaman uyumsuz bir yöntem olarak zaman uyumlu bir yöntem oluşturma gibi kolayca neredeyse oluşturmak için .NET Framework, .NET Core ya da Windows çalışma zamanı kaynakları kullanabilir. Kullanarak tanımladığınız zaman uyumsuz yöntemleri `async` anahtar sözcüğü denir *zaman uyumsuz yöntemleri*.  
  
 Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.  
  
 Bu konunun sonunda eksiksiz bir Windows Presentation Foundation (WPF) örnek dosyasını bulabilirsiniz ve örnekten indirebilirsiniz [zaman uyumsuz örnek: "Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme" örnekten](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
    // You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork();  
  
    // The await operator suspends AccessTheWebAsync.  
    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    //  - Control resumes here when getStringTask is complete.   
    //  - The await operator then retrieves the string result from getStringTask.  
    string urlContents = await getStringTask;  
  
    // The return statement specifies an integer result.  
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    return urlContents.Length;  
}  
```  
  
 Varsa `AccessTheWebAsync` arasında arama yapmak için herhangi bir iş yok `GetStringAsync` ve bunun tamamlanmasını bekleyen, çağırarak ve aşağıdaki tek deyiminde bekleyen kodunuzu basitleştirebilirsiniz.  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
Aşağıdaki özellikler, önceki örneği neyin zaman uyumsuz hale getirdiğini özetler.  
  
-   Yöntem imzası içeren bir `async` değiştiricisi.  
  
-   Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.  
  
-   Dönüş türü aşağıdaki türlerden biridir:  
  
    -   <xref:System.Threading.Tasks.Task%601> yönteminizi işlenenin türü olan bir return deyimi olup olmadığını `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> yönteminizi dönüş deyimi yok veya hiçbir işleneni olan bir return deyimi içeriyor  
  
    -   `void` zaman uyumsuz olay işleyicisi yazıyorsanız.  

    -   Sahip herhangi bir türü bir `GetAwaiter` yöntemi (C# 7 ile başlayan).
  
     Daha fazla bilgi için bkz: [dönüş türü ve parametreler](#BKMK_ReturnTypesandParameters) bölümü.  
  
-   Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.  
  
 Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.  
  
 .NET Framework'ün önceki sürümlerinde asynchrony hakkında daha fazla bilgi için bkz: [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Bir zaman uyumsuz yöntem ne olur?  
 Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol gösterecektir.  
  
 ![Zaman uyumsuz program izleme](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir.  
  
1.  Olay işleyici çağırır ve bekler `AccessTheWebAsync` async yöntemi.  
  
2.  `AccessTheWebAsync` oluşturur bir <xref:System.Net.Http.HttpClient> örneği ve çağrıları <xref:System.Net.Http.HttpClient.GetStringAsync%2A> dize olarak bir Web sitesi içeriğini indirmek için zaman uyumsuz yöntem.  
  
3.  İçinde bir şey `GetStringAsync` , ilerleme durumunu askıya alır. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemekten kaçınacak şekilde `GetStringAsync` çağırıcısına, Denetim verir `AccessTheWebAsync`.  
  
     `GetStringAsync` döndüren bir <xref:System.Threading.Tasks.Task%601> nerede `TResult` bir dizedir ve `AccessTheWebAsync` görevi atar `getStringTask` değişkeni. Görev çağrısı için devam eden işlemi temsil eden `GetStringAsync`, iş tamamlandığında, gerçek dize değeri üretmek için taahhüdü ile.  
  
4.  Çünkü `getStringTask` henüz beklemenin kurmadı `AccessTheWebAsync` Nihai sonuç bağımlı değil diğer iş devam edebilirsiniz `GetStringAsync`. Çalışma zaman uyumlu yöntemine bir çağrı tarafından temsil edilen `DoIndependentWork`.  
  
5.  `DoIndependentWork` kendi çalışır ve çağırıcısına döndüren bir zaman uyumlu yöntemidir.  
  
6.  `AccessTheWebAsync` bir sonuç kümesinden olmadan yapabilirsiniz İş dışı çalıştırıldı `getStringTask`. `AccessTheWebAsync` dize yöntemi olana kadar sonraki istediği hesaplamak ve indirilen dize ancak yöntemi uzunluğu dönmek için bu değeri hesaplanamıyor.  
  
     Bu nedenle, `AccessTheWebAsync` ilerleme durumunu askıya alma ve çağrılan yöntemi için denetimi elde etmek üzere bir bekleme işlecini kullanan `AccessTheWebAsync`. `AccessTheWebAsync` döndüren bir `Task<int>` çağırana. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.  
  
    > [!NOTE]
    >  Varsa `GetStringAsync` (ve bu nedenle `getStringTask`) önce tamamlandıktan `AccessTheWebAsync` , Denetim kalırken bekler `AccessTheWebAsync`. Askıya alma ve sonra dönme gider `AccessTheWebAsync` varsa küçülttüğü iyi bir şekilde çağrılan zaman uyumsuz işlemi (`getStringTask`) zaten tamamlandı ve `AccessTheWebSync` son için beklemek zorunda değildir.  
  
     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Arayan sonucundan bağımlı değil diğer iş yapabilecek `AccessTheWebAsync` önce sonucunda ortaya çıkan veya arayan bekleyen hemen beklemek.   Olay işleyicisi bekliyor `AccessTheWebAsync`, ve `AccessTheWebAsync` bekliyor `GetStringAsync`.  
  
7.  `GetStringAsync` tamamlandıktan ve bir dizi sonuç üretir. Dize sonucu çağrısı tarafından döndürülen değil `GetStringAsync` beklediğiniz şekilde. (Yöntem 3. adımda zaten bir görev döndürülen unutmayın.) Bunun yerine, dize sonucu yöntemi tamamlanmasından temsil eden görev depolanan `getStringTask`. Bekleme işleci sonucundan alır `getStringTask`. Alınan sonucu atama deyimi atar `urlContents`.  
  
8.  Zaman `AccessTheWebAsync` dize sonuçta yöntemi dize uzunluğu hesaplayabilirsiniz. Ardından çalışmanın `AccessTheWebAsync` de tamamlandıktan ve bekleme olay işleyicisi devam edebilirsiniz. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.    
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.  
  
Denetim akışı hakkında daha fazla bilgi için bkz: [(C#) zaman uyumsuz programlarda denetim akışı](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> API zaman uyumsuz yöntemleri  
 Yöntemleri gibi nerede bulacağını merak ediyor olabilirsiniz `GetStringAsync` Bu destek zaman uyumsuz programlama. .NET Core ve .NET Framework 4.5 veya üstü çalışmak çok sayıda üye içeren `async` ve `await`. Bunları kendi dönüş türü ve üye ada eklenir "Zaman uyumsuz" soneki tarafından tanıyabilmesi <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Örneğin, `System.IO.Stream` sınıfı yöntemleri gibi içerir <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu yöntemleri yanında <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, ve <xref:System.IO.Stream.Write%2A>.  
  
 Windows çalışma zamanı ile birlikte kullanabileceğiniz birçok yöntem de içeren `async` ve `await` Windows uygulamalarında. Daha fazla bilgi için bkz: [parçacıkları ve zaman uyumsuz programlama](/windows/uwp/threading-async/) UWP geliştirme ve [zaman uyumsuz programlama (Windows mağazası uygulamaları)](/previous-versions/windows/apps/hh464924(v=win.10)) ve [hızlı başlangıç: zaman uyumsuz API'ları C# ' ta çağırma veya Visual Basic](/previous-versions/windows/apps/hh452713(v=win.10)) Windows çalışma zamanı'nın önceki sürümlerini kullanır.  
  
##  <a name="BKMK_Threads"></a> İş parçacıkları  
Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Bir `await` awaited Görev yürütülürken, bir zaman uyumsuz yöntem ifadesinde geçerli iş parçacığının engelleme değil. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.  
  
`async` Ve `await` anahtar sözcükleri oluşturulacak ek iş parçacığı neden yoktur. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> arka plan iş parçacığı, ancak bir arka plan için CPU bağımlı iş taşımak için iş parçacığı kullanılabilir hale gelmesi için sonuçları yalnızca bekleyen bir işlem yardımcı değil.  
  
Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu daha iyi yaklaşımdır <xref:System.ComponentModel.BackgroundWorker> sınıf g/ç işlemleri için kodu daha basit olduğundan ve yarış durumları karşı koruma sağlamak zorunda değilsiniz. İle birlikte <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi, zaman uyumsuz programlama daha iyi <xref:System.ComponentModel.BackgroundWorker> CPU bağımlı işlemler için zaman uyumsuz programlama işten kodunuzu çalıştıran koordinasyon ayrıntılarını ayırdığından `Task.Run` aktarır iş parçacığı havuzu.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async ve await  
 Bir yöntemi kullanarak bir zaman uyumsuz yöntem olup belirtirseniz [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi, aşağıdaki iki özelliklerini etkinleştirin.  
  
-   İşaretlenen zaman uyumsuz yöntem kullanabilirsiniz [await](../../../../csharp/language-reference/keywords/await.md) askıya noktalarını belirlemek için. `await` İşleci söyler derleyici awaited zaman uyumsuz işlem tamamlanana kadar zaman uyumsuz yöntem o noktadan devam edemiyor. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.  
  
     Bir zaman uyumsuz yöntem ertelenmesi bir `await` ifadesi yönteminden bir çıkış niteliğinde değildir ve `finally` blokları çalıştırma.  
  
-   İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.  
  
Zaman uyumsuz yöntem genellikle bir veya daha fazla oluşumu içeren bir `await` işleci ancak olmaması `await` ifadeleri derleyici hatası neden değil. Zaman uyumsuz yöntem kullanmıyorsa bir `await` bir askıya alma, yöntemi olarak işaretle işleci yürüten bir zaman uyumlu yöntemi yaptığı gibi rağmen `async` değiştiricisi. Derleyici bu tür yöntemler için bir uyarı verir.  
  
 `async` ve `await` bağlamsal anahtar sözcükler. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Dönüş türleri ve parametreleri  
Bir zaman uyumsuz yöntem genellikle döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Zaman uyumsuz yöntem içinde bir `await` işleci, başka bir zaman uyumsuz yöntem çağrısından döndürülen bir görev için uygulanır.  
  
Belirttiğiniz <xref:System.Threading.Tasks.Task%601> yöntemi içeriyorsa, dönüş türü olarak bir [dönmek](../../../../csharp/language-reference/keywords/return.md) tür işleneni belirtir deyimi `TResult`. 
  
Kullandığınız <xref:System.Threading.Tasks.Task> yöntemin dönüş deyimi yok veya işleneni döndürmez bir dönüş ifadesi içeriyor, dönüş türü.  

Bu türü içeren koşuluyla, C# 7 ile başlayarak, ayrıca herhangi diğer dönüş türü, belirtebilirsiniz bir `GetAwaiter` yöntemi. <xref:System.Threading.Tasks.ValueTask%601> Bu tür bir türde bir örnektir. İçinde kullanılabilir [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketi.
  
 Aşağıdaki örnek, nasıl bildirme ve döndüren bir yöntem çağrısı gösterir bir <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
```  
  
Döndürülmüş her görev, devam eden bir çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumu hakkındaki bilgileri saklar ve sonunda, işlemden alınan nihai sonuca veya başarısız olursa işlemin neden olduğu bir özel duruma ilişkin bilgileri içerir.  
  
Async yöntemi de sahip olabilir bir `void` dönüş türü. Bu dönüş türü öncelikle olay işleyicileri tanımlamak için kullanılan burada bir `void` dönüş türü gerekli. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.  
  
İçeren bir zaman uyumsuz yöntem bir `void` türü olamaz beklemenin ve void döndüren bir yöntem arayan yöntemi atar tüm özel durumları yakalamak olamaz döndürür.  
  
Async yöntemi bildiremezsiniz [ref](../../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../../csharp/language-reference/keywords/out.md) parametreleri, ancak yöntem bu tür parametrelerine sahip yöntemleri çağırabilirsiniz. Benzer şekilde, dönüş değerleri ref yöntemleriyle çağırabilirsiniz rağmen bir zaman uyumsuz yöntem başvuruya göre bir değer döndüremiyor. 
  
Daha fazla bilgi ve örnekler için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Zaman uyumsuz yöntemleri özel durumlarını yakalama hakkında daha fazla bilgi için bkz: [try-catch](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Windows çalışma zamanı programlama zaman uyumsuz API'leri görevlere benzer aşağıdaki dönüş türlerinden birini vardır:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, hangi karşılık gelir <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, hangi karşılık gelir <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Adlandırma kuralları  
 Kurala göre sahip yöntemleri adlarına "Zaman uyumsuz" append bir `async` değiştiricisi.  
  
 Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, ortak olay işleyicileri gibi yeniden adlandırmadan döndürmemelidir `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekleri (Visual Studio)  
  
|Başlık|Açıklama|Örnek|  
|-----------|-----------------|------------|  
|[İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web gözden geçirme erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Ekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önceki kılavuzu için. Kullanımını `WhenAll` aynı anda tüm indirmeleri başlatır.||  
|[Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: Birden çok Web isteğini paralel hale](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||  
|[Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> -   [Zaman uyumsuz görevi veya görev (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Çalıştırıldığı sırada etkin bir zaman uyumsuz işlemin yeniden başlatıldığı durumların nasıl işleneceğini gösterir.||  
|[WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|.NET Framework'teki görev türleri ve IAsyncOperations içinde arasında köprü gösterilmektedir [!INCLUDE[wrt](~/includes/wrt-md.md)] , kullanabilmesi için <xref:System.Threading.Tasks.Task.WhenAny%2A> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve WhenAny) arasında köprü oluşturma](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|.NET Framework'teki görev türleri ve IAsyncOperations içinde arasında köprü gösterilmektedir [!INCLUDE[wrt](~/includes/wrt-md.md)] , kullanabilmesi için <xref:System.Threading.CancellationTokenSource> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask & İptal) arasında köprü oluşturma](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Dosya erişimi için (C#) Async kullanma](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||  
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen dayanır <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türleri.||  
|[Zaman uyumsuz videolar kanalda 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||  
  
##  <a name="BKMK_CompleteExample"></a> Tam örnek  
 Aşağıdaki kod, bu konuda ele alınmıştır Windows Presentation Foundation (WPF) uygulamadan MainWindow.xaml.cs dosyasıdır. Örnekten indirebilirsiniz [zaman uyumsuz örnek: "Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme" örnekten](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
            // You can do work here that doesn't rely on the string from GetStringAsync.  
            DoIndependentWork();  
  
            // The await operator suspends AccessTheWebAsync.  
            //  - AccessTheWebAsync can't continue until getStringTask is complete.  
            //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
            //  - Control resumes here when getStringTask is complete.   
            //  - The await operator then retrieves the string result from getStringTask.  
            string urlContents = await getStringTask;  
  
            // The return statement specifies an integer result.  
            // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
            return urlContents.Length;  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [async](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Zaman uyumsuz programlama](../../../../csharp/async.md)  
 [Zaman uyumsuz genel bakış](../../../../standard/async.md)  
