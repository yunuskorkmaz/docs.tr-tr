---
title: 'Zaman uyumsuz programlama ile async ve await (C#)'
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Zaman uyumsuz programlama ile async ve await (C#)
Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.  
  
[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) basitleştirilmiş bir yaklaşım, .NET Framework 4.5 ve sonraki zaman uyumsuz desteği kullanan zaman uyumsuz programlama, .NET Core ve Windows çalışma zamanı kullanıma sunulmuştur. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.  
  
Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Zaman uyumsuz yanıt hızını artırır.  
 Faaliyetler engelleyen potansiyel olarak, web erişim gibi etkinlikler için önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik zaman uyumlu işlemde engellenirse uygulamanın tamamı beklemelidir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.  
  
 Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET ve Windows çalışma zamanı kaynaklarından listelenen API'lar, zaman uyumsuz programlamayı destekleyen yöntemler içerir.  
  
| Uygulama alanı    | Zaman uyumsuz yöntemler ile .NET türleri     | Zaman uyumsuz yöntemler ile Windows çalışma zamanı türleri  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Görüntülerle çalışma||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.  
  
 Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.  
  
 Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Zaman uyumsuz yöntemleri yazmak daha kolaydır  
 [Zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) ve [await](../../../../csharp/language-reference/keywords/await.md) sözcükler C# zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak neredeyse bir zaman uyumlu yöntem kolayca olarak zaman uyumsuz bir yöntem oluşturmak için .NET Framework, .NET Core veya Windows çalışma zamanı kaynakları kullanabilirsiniz. Kullanarak tanımladığınız zaman uyumsuz yöntemler `async` anahtar sözcüğü denir *zaman uyumsuz yöntemler*.  
  
 Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.  
  
 Windows Presentation Foundation (WPF) örnek dosyanın tamamını bu konunun sonunda bulabilirsiniz ve örneği indirebilirsiniz [zaman uyumsuz örneği: Örnek "zaman uyumsuz programlama ile Async ve Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    using (HttpClient client = new HttpClient())  
    {  
        // GetStringAsync returns a Task<string>. That means that when you await the  
        // task you'll get a string (urlContents).  
        Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
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
}  
```  
  
 Varsa `AccessTheWebAsync` arasında arama yapmak için bir iş içermiyorsa `GetStringAsync` ve tamamlanmasını bekleme çağırma ve aşağıdaki tek deyimde bekleme işlemlerini gerçekleştirerek kodunuzu basitleştirebilirsiniz.  
  
```csharp  
string urlContents = await client.GetStringAsync("https://docs.microsoft.com");  
```  
 
Aşağıdaki özellikler, önceki örneği neyin zaman uyumsuz hale getirdiğini özetler.  
  
-   Yöntem imzası içerir bir `async` değiştiricisi.  
  
-   Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.  
  
-   Dönüş türü aşağıdaki türlerden biridir:  
  
    -   <xref:System.Threading.Tasks.Task%601> yönteminizi işlenenin türü içeren bir dönüş ifadesi varsa `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> yönteminizi yok ya da işlenen içermeyen bir dönüş ifadesi varsa.  
  
    -   `void` zaman uyumsuz bir olay işleyici yazıyorsanız.  

    -   Sahip herhangi bir türü bir `GetAwaiter` yöntemi (C# 7. 0'dan itibaren).
  
     Daha fazla bilgi için [dönüş türleri ve parametreleri](#BKMK_ReturnTypesandParameters) bölümü.  
  
-   Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.  
  
 Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.  
  
 .NET Framework'ün önceki sürümlerindeki zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Zaman uyumsuz yöntemde neler  
 Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol gösterecektir.  
  
 ![Bir zamanuyumsuz program izleme](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir.  
  
1.  Bir olay işleyici çağırır ve bekler `AccessTheWebAsync` zaman uyumsuz yöntem.  
  
2.  `AccessTheWebAsync` oluşturur bir <xref:System.Net.Http.HttpClient> örneği ve çağrıları <xref:System.Net.Http.HttpClient.GetStringAsync%2A> dize olarak bir Web sitesinin içeriklerini karşıdan yüklemek için zaman uyumsuz yöntem.  
  
3.  İçinde bir şey `GetStringAsync` ilerlemesini engelleyen. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakların engellenmesini önlemek için `GetStringAsync` denetimi onu arayan verir `AccessTheWebAsync`.  
  
     `GetStringAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada `TResult` bir dizedir ve `AccessTheWebAsync` görevi atayan `getStringTask` değişkeni. Görev için yapılan çağrının devam eden işlemini temsil eden `GetStringAsync`, çalışma tamamlandığında gerçek dize değerini oluşturma taahhüdü ile.  
  
4.  Çünkü `getStringTask` henüz beklenmediği `AccessTheWebAsync` gelen nihai sonuca bağımlı olmayan diğer çalışmalar ile devam edebilir `GetStringAsync`. İş zaman uyumlu yönteme yapılan bir çağrıyla temsil edilir `DoIndependentWork`.  
  
5.  `DoIndependentWork` kendi iş ve arayanına dönen bir zaman uyumlu yöntemdir.  
  
6.  `AccessTheWebAsync` bir sonuç olmadan yapabileceği işleri dışında çalıştırıldı `getStringTask`. `AccessTheWebAsync` hesaplamak ve uzunluğu, indirilen dizenin, ancak yöntem döndürmek ister, yöntem dizeye sahip oluncaya kadar değeri hesaplamaz.  
  
     Bu nedenle, `AccessTheWebAsync` bir await işleci kullanarak ilerlemesini askıya alır ve çağıran yönteme denetimi elde etmek üzere kullandığı `AccessTheWebAsync`. `AccessTheWebAsync` döndürür bir `Task<int>` çağırana. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.  
  
    > [!NOTE]
    >  Varsa `GetStringAsync` (ve bu nedenle `getStringTask`) önce tamamlanırsa `AccessTheWebAsync` bekler, Denetim saklanır `AccessTheWebAsync`. Askıya alma ve daha sonra dönme gideri `AccessTheWebAsync` boşa gidecektir çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve `AccessTheWebSync` için nihai sonucu bekleme zorunluluğu yoktur.  
  
     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıranın sonucuna bağlı olmayan diğer işleri yapabilir `AccessTheWebAsync` sonucunda ortaya çıkan veya çağıranın bekleyen hemen beklemeye geçebilir.   Olay işleyicisi bekliyor `AccessTheWebAsync`, ve `AccessTheWebAsync` bekliyor `GetStringAsync`.  
  
7.  `GetStringAsync` tamamlandıktan ve bir dize sonucu üretir. Dize sonucu çağrısı tarafından döndürülen değil `GetStringAsync` beklediğiniz şekilde. (Yöntemin adım 3'te zaten bir görev döndürdüğünü unutmayın.) Bunun yerine, dize sonucu tamamlama yöntemini belirten bir görevde saklanır `getStringTask`. Await işleci sonuçtan alır `getStringTask`. Atama ifadesi alınan sonucu atar `urlContents`.  
  
8.  Zaman `AccessTheWebAsync` dize sonucu yöntem dize uzunluğunu hesaplayabilir. Ardından çalışmasına `AccessTheWebAsync` da tamamlanır ve bekleyen olay işleyicisi devam edebilir. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.    
Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.  
  
Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda (C#) denetim akışı](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> API zaman uyumsuz yöntemler  
 Yöntemleri gibi nerede bulacağınızı merak ediyor olabilirsiniz `GetStringAsync` asenkronize programlamayı destekleyen. .NET Core ve .NET Framework 4.5 veya üzeri ile çalışan birçok üye içerir `async` ve `await`. Bunları kendi dönüş türü ve üye adına eklenir "Async" soneki tarafından tanıyabilmesi <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Örneğin, `System.IO.Stream` sınıfı içeren yöntemler gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu metotları yanı sıra <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, ve <xref:System.IO.Stream.Write%2A>.  
  
 Windows çalışma zamanı ayrıca ile kullanabileceğiniz birçok yöntem içerir `async` ve `await` Windows uygulamalarında. Daha fazla bilgi için [parçacıkları ve zaman uyumsuz programlama](/windows/uwp/threading-async/) UWP geliştirme ve [zaman uyumsuz programlama (Windows Store apps)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) ve [hızlı başlangıç: Zaman uyumsuz API'leri çağırma C# veya Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) Windows çalışma zamanı'nın önceki sürümlerini kullanıyorsanız.  
  
##  <a name="BKMK_Threads"></a> İş parçacıkları  
Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Bir `await` beklenen görev çalışırken, zaman uyumsuz bir yöntem içinde deyim geçerli iş parçacığı engelleme değil. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.  
  
`async` Ve `await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> arka plan iş parçacığı, ancak arka plan CPU bağımlı iş taşımak için iş parçacığı kullanılabilir hale gelmesi için sonuçları bekleyen işlemler için yardımcı olmaz.  
  
Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Bu yaklaşım özellikle, daha iyi <xref:System.ComponentModel.BackgroundWorker> koda daha basit olduğundan ve yarış durumlarına karşı önlem gerekmez çünkü ben/Ç işlemleri için sınıf. İle birlikte <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodu, zaman uyumsuz programlama, daha iyi <xref:System.ComponentModel.BackgroundWorker> CPU'ya bağlı işlemler için zaman uyumsuz programlama, kodunuzu çalıştırılan koordinasyon ayrıntılarını ayırır çünkü `Task.Run` aktarır iş parçacığı havuzu.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async ve await  
 Kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi, aşağıdaki iki özelliği etkinleştirirsiniz.  
  
-   İşaretli zaman uyumsuz yöntem kullanabilirsiniz [await](../../../../csharp/language-reference/keywords/await.md) askıya alma noktaları belirlemek için. `await` İşleci derleyici beklenen zaman uyumsuz işlem tamamlanana kadar zaman uyumsuz yöntemin bu noktanın ilerisine devam edemeyeceğini bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.  
  
     Zaman uyumsuz bir yöntemin askıya alınması bir `await` ifade etmez yöntemden bir çıkış oluşturur ve `finally` blokları çalışmaz.  
  
-   İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.  
  
Bir zaman uyumsuz yöntem genelde bir veya daha çok tekrarı içeren bir `await` işleci, ancak olmaması `await` ifadeleri bir derleyici hatasına neden değil. Zaman uyumsuz bir yöntem kullanmıyorsa bir `await` zaman uyumlu bir yöntem olarak, yöntem, askıya alma noktası için işleç yürütür rağmen `async` değiştiricisi. Derleyici bu tür yöntemler için bir uyarı verir.  
  
 `async` ve `await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Dönüş türleri ve parametreleri  
Zaman uyumsuz bir yöntem genellikle döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Bir zaman uyumsuz yöntem içinde bir `await` işleci, başka bir zaman uyumsuz yöntemin çağrısından döndürülen göreve uygulanır.  
  
Belirttiğiniz <xref:System.Threading.Tasks.Task%601> yöntemi içeriyorsa, dönüş türü bir [dönüş](../../../../csharp/language-reference/keywords/return.md) türünde bir işlenen ifadesi `TResult`. 
  
Kullandığınız <xref:System.Threading.Tasks.Task> dönüş türünü yöntem herhangi bir dönüş deyimi içeriyorsa ya da bir işleç döndürmeyen bir return deyimi vardır.  

Koşuluyla türünü içeren C# 7.0 ile başlayarak, ayrıca diğer dönüş türleri, belirtebilirsiniz bir `GetAwaiter` yöntemi. <xref:System.Threading.Tasks.ValueTask%601> Böyle bir türü örneğidir. Kullanılabilir, [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet paketi.
  
 Aşağıdaki örnek, bildirme ve döndüren bir yöntem çağırmak nasıl gösterir. bir <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> GetTaskOfTResultAsync()  
{  
    int hours = 0;  
    await Task.Delay(0);  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to GetTaskOfTResultAsync  
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await GetTaskOfTResultAsync();  
  
// Signature specifies Task  
async Task GetTaskAsync()  
{  
    await Task.Delay(0);  
    // The method has no return statement.    
}  
  
// Calls to GetTaskAsync  
Task returnedTask = GetTaskAsync();  
await returnedTask;  
// or, in a single statement  
await GetTaskAsync();  
```  
  
Döndürülmüş her görev, devam eden bir çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumu hakkındaki bilgileri saklar ve sonunda, işlemden alınan nihai sonuca veya başarısız olursa işlemin neden olduğu bir özel duruma ilişkin bilgileri içerir.  
  
Zaman uyumsuz bir yöntem ayrıca olabilir bir `void` dönüş türü. Bu dönüş türü öncelikle olay işleyicilerini tanımlamak için kullanılan burada bir `void` dönüş türünün gerekli. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.  
  
Bir zaman uyumsuz yöntemin bir `void` dönüş türü beklenemez ve void döndüren bir yöntemi çağıran kişi yöntemin verdiği hiçbir özel durumu yakalayamaz.  
  
Zaman uyumsuz bir yöntem bildiremezsiniz [içinde](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir. Benzer şekilde, bir zaman uyumsuz yöntem dönüş değerleri ref olan yöntemleri çağırabilir olsa da başvuruya göre bir değer döndüremez. 
  
Daha fazla bilgi ve örnekler için bkz. [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [try-catch](../../../../csharp/language-reference/keywords/try-catch.md). 
  
Windows çalışma zamanı programlamada zaman uyumsuz API'leri görevlere benzeyen aşağıdaki dönüş türlerinden birine sahiptir:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, karşılık gelen <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, karşılık gelen <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Adlandırma kuralı  
Kural olarak, yaygın olarak beklenebilir türleri döndüren yöntemler (örneğin `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`) "Async" ile biten adlara sahip olmalıdır. Zaman uyumsuz bir işlem başlatın, ancak bir beklenebilir türü döndürmeyen yöntemleri adları "Async" ile bitemez, ancak bu yöntem değil döndürmesine veya bir işlemin sonucunu önermek için "Başlangıç", "Başlangıç" veya diğer bir fiil başlayabilir sahip olmamalıdır.
  
 Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, ortak olay işleyicileri gibi adlandırmamanız `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekleri (Visual Studio)  
  
|Başlık|Açıklama|Örnek|  
|-----------|-----------------|------------|  
|[İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örneği: İzlenecek yol erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Ekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önceki izlenecek. Kullanımını `WhenAll` tüm indirmeleri aynı anda başlatır.||  
|[Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örneği: Birden çok Web isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||  
|[Denetim akışı zaman uyumsuz programlarda (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Zaman uyumsuz örneği: Zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[(C#) Async uygulamanızda hassas ayar yapma](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> -   [Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[(C#) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Çalıştırıldığı sırada etkin bir zaman uyumsuz işlemin yeniden başlatıldığı durumların nasıl işleneceğini gösterir.||  
|[WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Görev türü .NET Framework ve Iasyncoperations arasında nasıl köprü oluşturulacağını gösterir [!INCLUDE[wrt](~/includes/wrt-md.md)] kullanabilirsiniz, böylece <xref:System.Threading.Tasks.Task.WhenAny%2A> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve WhenAny) arasında köprü oluşturma](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Zaman uyumsuz iptal: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma|Görev türü .NET Framework ve Iasyncoperations arasında nasıl köprü oluşturulacağını gösterir [!INCLUDE[wrt](~/includes/wrt-md.md)] kullanabilirsiniz, böylece <xref:System.Threading.CancellationTokenSource> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve iptal) arasında köprü oluşturma](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Zaman uyumsuz dosya erişimi için (C#) kullanma](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||  
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen dayanır <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türleri.||  
|[Kanal 9 üzerinde zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||  
  
##  <a name="BKMK_CompleteExample"></a> Tam örnek  
 Aşağıdaki kod, bu konuda bahsedilen Windows Presentation Foundation (WPF) uygulamasında MainWindow.xaml.cs dosyasıdır. İçinden örneği karşıdan yükleyebilirsiniz [zaman uyumsuz örneği: Örnek "zaman uyumsuz programlama ile Async ve Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
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
                $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            using (HttpClient client = new HttpClient())  
            {  
                    // GetStringAsync returns a Task<string>. That means that when you await the  
                    // task you'll get a string (urlContents).  
                    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
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
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 25035.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Zaman uyumsuz programlama](../../../../csharp/async.md)
- [Zaman uyumsuz genel bakış](../../../../standard/async.md)
