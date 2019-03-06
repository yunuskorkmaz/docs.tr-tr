---
title: Zaman uyumsuz programlama ile Async ve Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Zaman uyumsuz programlama ile Async ve Await (Visual Basic)
Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.  
  
 Visual Studio 2012 basitleştirilmiş bir yaklaşım olan zaman uyumsuz destek .NET Framework 4.5 ve üzeri de olduğu gibi Windows çalışma zamanı kullanan zaman uyumsuz kullanıma sunmuştur. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.  
  
 Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.  
  
## <a name="BKMK_WhentoUseAsynchrony"></a> Zaman uyumsuz yanıt hızını artırır.  
 Zaman uyumsuzluk, uygulamanızın Web'e erişmesi gibi engelleme olasılığı bulunan faaliyetler için önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik zaman uyumlu işlemde engellenirse uygulamanın tamamı beklemelidir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.  
  
 Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET Framework 4.5 ve Windows çalışma zamanı kaynaklarından listelenen API'lar, zaman uyumsuz programlamayı destekleyen yöntemler içerir.  
  
|Uygulama alanı|Zaman uyumsuz yöntemler içeren API'leri destekleme|  
|----------------------|------------------------------------------------|  
|Web erişimi|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|  
|Dosyalarla çalışma|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|  
|Görüntülerle çalışma|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|  
|||  
  
 Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.  
  
 Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.  
  
 Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.  
  
## <a name="BKMK_HowtoWriteanAsyncMethod"></a> Zaman uyumsuz yöntemleri yazmak daha kolaydır  
 [Zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await](../../../../visual-basic/language-reference/modifiers/async.md) sözcükler Visual Basic'te zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak neredeyse bir zaman uyumlu yöntem kolayca olarak zaman uyumsuz bir yöntem oluşturmak için .NET Framework veya Windows çalışma zamanı kaynakları kullanabilirsiniz. Kullanarak tanımladığınız zaman uyumsuz yöntemler `Async` ve `Await` zaman uyumsuz yöntemler olarak adlandırılır.  
  
 Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.  
  
 Windows Presentation Foundation (WPF) örnek dosyanın tamamını bu konunun sonunda bulabilirsiniz ve örneği indirebilirsiniz [zaman uyumsuz örneği: Örnek "zaman uyumsuz programlama ile Async ve Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Three things to note in the signature:  
'  - The method has an Async modifier.   
'  - The return type is Task or Task(Of T). (See "Return Types" section.)  
'    Here, it is Task(Of Integer) because the return statement returns an integer.  
'  - The method name ends in "Async."  
Async Function AccessTheWebAsync() As Task(Of Integer)  
  
    ' You need to add a reference to System.Net.Http to declare client.  
    Dim client As HttpClient = New HttpClient()  
  
    ' GetStringAsync returns a Task(Of String). That means that when you await the  
    ' task you'll get a string (urlContents).  
    Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
  
    ' You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork()  
  
    ' The Await operator suspends AccessTheWebAsync.  
    '  - AccessTheWebAsync can't continue until getStringTask is complete.  
    '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    '  - Control resumes here when getStringTask is complete.   
    '  - The Await operator then retrieves the string result from getStringTask.  
    Dim urlContents As String = Await getStringTask  
  
    ' The return statement specifies an integer result.  
    ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    Return urlContents.Length  
End Function  
```  
  
 Varsa `AccessTheWebAsync` arasında arama yapmak için bir iş içermiyorsa `GetStringAsync` ve tamamlanmasını bekleme çağırma ve aşağıdaki tek deyimde bekleme işlemlerini gerçekleştirerek kodunuzu basitleştirebilirsiniz.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Aşağıdaki özellikler, önceki örneği neyin zaman uyumsuz hale getirdiğini özetler.  
  
-   Yöntem imzası içerir bir `Async` değiştiricisi.  
  
-   Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.  
  
-   Dönüş türü aşağıdaki türlerden biridir:  
  
    -   <xref:System.Threading.Tasks.Task%601> yönteminizin, TResult türünde işlenen içeren bir dönüş ifadesi varsa.  
  
    -   <xref:System.Threading.Tasks.Task> yönteminizi yok ya da işlenen içermeyen bir dönüş ifadesi varsa.  
  
    -   [Alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) zaman uyumsuz bir olay işleyici yazıyorsanız.  
  
     Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki "Dönüş Türleri ve Parametreler" bölümüne bakın.  
  
-   Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.  
  
 Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.  
  
 .NET Framework'ün önceki sürümlerindeki zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Zaman uyumsuz yöntemde neler  
 Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol gösterecektir.  
  
 ![Bir zamanuyumsuz program izleme](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir.  
  
1.  Bir olay işleyici çağırır ve bekler `AccessTheWebAsync` zaman uyumsuz yöntem.  
  
2.  `AccessTheWebAsync` oluşturur bir <xref:System.Net.Http.HttpClient> örneği ve çağrıları <xref:System.Net.Http.HttpClient.GetStringAsync%2A> dize olarak bir Web sitesinin içeriklerini karşıdan yüklemek için zaman uyumsuz yöntem.  
  
3.  İçinde bir şey `GetStringAsync` ilerlemesini engelleyen. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakların engellenmesini önlemek için `GetStringAsync` denetimi onu arayan verir `AccessTheWebAsync`.  
  
     `GetStringAsync` döndürür bir <xref:System.Threading.Tasks.Task%601> burada TResult bir dizedir ve `AccessTheWebAsync` görevi atayan `getStringTask` değişkeni. Görev için yapılan çağrının devam eden işlemini temsil eden `GetStringAsync`, çalışma tamamlandığında gerçek dize değerini oluşturma taahhüdü ile.  
  
4.  Çünkü `getStringTask` henüz beklenmediği `AccessTheWebAsync` gelen nihai sonuca bağımlı olmayan diğer çalışmalar ile devam edebilir `GetStringAsync`. İş zaman uyumlu yönteme yapılan bir çağrıyla temsil edilir `DoIndependentWork`.  
  
5.  `DoIndependentWork` kendi iş ve arayanına dönen bir zaman uyumlu yöntemdir.  
  
6.  `AccessTheWebAsync` bir sonuç olmadan yapabileceği işleri dışında çalıştırıldı `getStringTask`. `AccessTheWebAsync` hesaplamak ve uzunluğu, indirilen dizenin, ancak yöntem döndürmek ister, yöntem dizeye sahip oluncaya kadar değeri hesaplamaz.  
  
     Bu nedenle, `AccessTheWebAsync` bir await işleci kullanarak ilerlemesini askıya alır ve çağıran yönteme denetimi elde etmek üzere kullandığı `AccessTheWebAsync`. `AccessTheWebAsync` döndürür bir `Task<int>` (`Task(Of Integer)` Visual Basic'te) çağırana. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.  
  
    > [!NOTE]
    >  Varsa `GetStringAsync` (ve bu nedenle `getStringTask`) önce tamamlanırsa `AccessTheWebAsync` bekler, Denetim saklanır `AccessTheWebAsync`. Askıya alma ve daha sonra dönme gideri `AccessTheWebAsync` boşa gidecektir çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve accessthewebsync yoksa için nihai sonucu bekleme.  
  
     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıranın sonucuna bağlı olmayan diğer işleri yapabilir `AccessTheWebAsync` sonucunda ortaya çıkan veya çağıranın bekleyen hemen beklemeye geçebilir.   Olay işleyicisi bekliyor `AccessTheWebAsync`, ve `AccessTheWebAsync` bekliyor `GetStringAsync`.  
  
7.  `GetStringAsync` tamamlandıktan ve bir dize sonucu üretir. Dize sonucu çağrısı tarafından döndürülen değil `GetStringAsync` beklediğiniz şekilde. (Yöntemin adım 3'te zaten bir görev döndürdüğünü unutmayın.) Bunun yerine, dize sonucu tamamlama yöntemini belirten bir görevde saklanır `getStringTask`. Await işleci sonuçtan alır `getStringTask`. Atama ifadesi alınan sonucu atar `urlContents`.  
  
8.  Zaman `AccessTheWebAsync` dize sonucu yöntem dize uzunluğunu hesaplayabilir. Ardından çalışmasına `AccessTheWebAsync` da tamamlanır ve bekleyen olay işleyicisi devam edebilir. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.  
  
 Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.  
  
 Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="BKMK_APIAsyncMethods"></a> Zaman uyumsuz API yöntemleri  
 Yöntemleri gibi nerede bulacağınızı merak ediyor olabilirsiniz `GetStringAsync` asenkronize programlamayı destekleyen. .NET Framework 4.5 veya üzeri ile çalışan birçok üye içerir `Async` ve `Await`. Bu üyeleri, üye adı ve dönüş türüne bağlı "Async" ekinden <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Örneğin, `System.IO.Stream` sınıfı içeren yöntemler gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu metotları yanı sıra <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, ve <xref:System.IO.Stream.Write%2A>.  
  
 Windows çalışma zamanı ayrıca ile kullanabileceğiniz birçok yöntem içerir `Async` ve `Await` Windows uygulamalarında. Daha fazla bilgi ve örnek yöntemler için bkz. [zaman uyumsuz API'leri çağırma C# veya Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [zaman uyumsuz programlama (Windows çalışma zamanı uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), ve [WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).  
  
## <a name="BKMK_Threads"></a> İş parçacıkları  
 Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Bir `Await` beklenen görev çalışırken, zaman uyumsuz bir yöntem içinde deyim geçerli iş parçacığı engelleme değil. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.  
  
 `Async` Ve `Await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> arka plan iş parçacığı, ancak arka plan CPU bağımlı iş taşımak için iş parçacığı kullanılabilir hale gelmesi için sonuçları bekleyen işlemler için yardımcı olmaz.  
  
 Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Bu yaklaşım özellikle, daha iyi <xref:System.ComponentModel.BackgroundWorker> miyim/Ç işlemleri kod daha basit olduğundan ve koruma sağlamak yoksa yarış durumlarına karşı için. İle birlikte <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, zaman uyumsuz programlama, daha iyi <xref:System.ComponentModel.BackgroundWorker> CPU'ya bağlı işlemler için zaman uyumsuz programlama, kodunuzu çalıştırılan koordinasyon ayrıntılarını ayırır çünkü `Task.Run` havuzuna aktarılan işten.  
  
## <a name="BKMK_AsyncandAwait"></a> Async ve Await  
 Kullanarak bir yöntemin zaman uyumsuz bir yöntem olduğunu belirtirseniz bir [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi, aşağıdaki iki özelliği etkinleştirirsiniz.  
  
-   İşaretli zaman uyumsuz yöntem kullanabilirsiniz [Await](../../../../visual-basic/language-reference/operators/await-operator.md) askıya alma noktaları belirlemek için. await işleci derleyiciye, beklenen zaman uyumsuz işlem tamamlanmadan zaman uyumsuz yöntemin bu noktanın ilerisine devam edemeyeceğini bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.  
  
     Zaman uyumsuz bir yöntemin askıya alınması bir `Await` ifade etmez yöntemden bir çıkış oluşturur ve `Finally` blokları çalışmaz.  
  
-   İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.  
  
 Bir zaman uyumsuz yöntem genelde bir veya daha çok tekrarı içeren bir `Await` işleci, ancak olmaması `Await` ifadeleri bir derleyici hatasına neden değil. Zaman uyumsuz bir yöntem kullanmıyorsa bir `Await` zaman uyumlu bir yöntem olarak, yöntem, askıya alma noktası için işleç yürütür rağmen `Async` değiştiricisi. Derleyici bu tür yöntemler için bir uyarı verir.  
  
 `Async` ve `Await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:  
  
-   [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
## <a name="BKMK_ReturnTypesandParameters"></a> Dönüş türleri ve parametreleri  
 .NET Framework programlamada bir zaman uyumsuz yöntem genellikle döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Bir zaman uyumsuz yöntem içinde bir `Await` işleci, başka bir zaman uyumsuz yöntemin çağrısından döndürülen göreve uygulanır.  
  
 Belirttiğiniz <xref:System.Threading.Tasks.Task%601> yöntemi içeriyorsa, dönüş türü bir [dönüş](../../../../visual-basic/language-reference/statements/return-statement.md) türünde bir işlenen ifadesi `TResult`.  
  
 Kullandığınız `Task` dönüş türünü yöntem herhangi bir dönüş deyimi içeriyorsa ya da bir işleç döndürmeyen bir return deyimi vardır.  
  
 Aşağıdaki örnek, bildirme ve döndüren bir yöntem çağırmak nasıl gösterir. bir <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.  
  
```vb  
' Signature specifies Task(Of Integer)  
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)  
  
    Dim hours As Integer  
    ' . . .  
    ' Return statement specifies an integer result.  
    Return hours  
End Function  
  
' Calls to TaskOfTResult_MethodAsync  
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()  
Dim intResult As Integer = Await returnedTaskTResult  
' or, in a single statement  
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()  
  
' Signature specifies Task  
Async Function Task_MethodAsync() As Task  
  
    ' . . .  
    ' The method has no return statement.  
End Function  
  
' Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync()  
Await returnedTask  
' or, in a single statement  
Await Task_MethodAsync()  
```  
  
 Döndürülmüş her görev, devam eden bir çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumu hakkındaki bilgileri saklar ve sonunda, işlemden alınan nihai sonuca veya başarısız olursa işlemin neden olduğu bir özel duruma ilişkin bilgileri içerir.  
  
 Zaman uyumsuz bir yöntem ayrıca olabilir bir `Sub` yöntemi. Bu dönüş türü, bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için öncelikle kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.  
  
 Zaman uyumsuz bir yöntem bu bir `Sub` yordamı beklenemez ve çağıran yöntemin oluşturduğu hiçbir özel durumu yakalayamaz.  
  
 Zaman uyumsuz bir yöntem bildiremezsiniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametreleri, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir.  
  
 Daha fazla bilgi ve örnekler için bkz. [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Windows çalışma zamanı programlamada zaman uyumsuz API'leri görevlere benzeyen aşağıdaki dönüş türlerinden birine sahiptir:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, karşılık gelen <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, karşılık gelen <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
  
 Daha fazla bilgi ve örnek için bkz. [C# veya Visual Basic'te zaman uyumsuz API'leri çağırma](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).  
  
## <a name="BKMK_NamingConvention"></a> Adlandırma kuralı  
 Kural gereği, içeren yöntemlerin adlarına "Async" ekleme bir `Async` değiştiricisi.  
  
 Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, ortak olay işleyicileri gibi adlandırmamanız `Button1_Click`.  
  
## <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekleri (Visual Studio)  
  
|Başlık|Açıklama|Örnek|  
|-----------|-----------------|------------|  
|[İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örneği: İzlenecek yol erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Ekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önceki izlenecek. Kullanımını `WhenAll` tüm indirmeleri aynı anda başlatır.||  
|[Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örneği: Birden çok Web isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||  
|[Zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Zaman uyumsuz örneği: Zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[(Visual Basic) Async uygulamanızda hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> -   [Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [(Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Çalıştırıldığı sırada etkin bir zaman uyumsuz işlemin yeniden başlatıldığı durumların nasıl işleneceğini gösterir.||  
|[WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Görev türü .NET Framework ve Iasyncoperations arasında nasıl köprü oluşturulacağını gösterir [!INCLUDE[wrt](~/includes/wrt-md.md)] kullanabilirsiniz, böylece <xref:System.Threading.Tasks.Task.WhenAny%2A> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve WhenAny) arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|  
|Zaman uyumsuz iptal: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma|Görev türü .NET Framework ve Iasyncoperations arasında nasıl köprü oluşturulacağını gösterir [!INCLUDE[wrt](~/includes/wrt-md.md)] kullanabilirsiniz, böylece <xref:System.Threading.CancellationTokenSource> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve iptal) arasında köprü oluşturma](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[(Visual Basic) dosya erişimi için Async kullanma](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||  
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen dayanır <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türleri.||  
|[Kanal 9 üzerinde zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async+&type=All)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||  
  
## <a name="BKMK_CompleteExample"></a> Tam örnek  
 Aşağıdaki kod, bu konuda bahsedilen Windows Presentation Foundation (WPF) uygulamasında MainWindow.xaml.vb dosyasıdır. İçinden örneği karşıdan yükleyebilirsiniz [zaman uyumsuz örneği: Örnek "zaman uyumsuz programlama ile Async ve Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```vb  
' Add an Imports statement and a reference for System.Net.Http  
Imports System.Net.Http  
  
Class MainWindow  
  
    ' Mark the event handler with async so you can use Await in it.  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Call and await separately.  
        'Task<int> getLengthTask = AccessTheWebAsync();  
        '' You can do independent work here.  
        'int contentLength = await getLengthTask;  
  
        Dim contentLength As Integer = Await AccessTheWebAsync()  
  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
    End Sub  
  
    ' Three things to note in the signature:  
    '  - The method has an Async modifier.   
    '  - The return type is Task or Task(Of T). (See "Return Types" section.)  
    '    Here, it is Task(Of Integer) because the return statement returns an integer.  
    '  - The method name ends in "Async."  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' You need to add a reference to System.Net.Http to declare client.  
        Dim client As HttpClient = New HttpClient()  
  
        ' GetStringAsync returns a Task(Of String). That means that when you await the  
        ' task you'll get a string (urlContents).  
        Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
  
        ' You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork()  
  
        ' The Await operator suspends AccessTheWebAsync.  
        '  - AccessTheWebAsync can't continue until getStringTask is complete.  
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        '  - Control resumes here when getStringTask is complete.   
        '  - The Await operator then retrieves the string result from getStringTask.  
        Dim urlContents As String = Await getStringTask  
  
        ' The return statement specifies an integer result.  
        ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        Return urlContents.Length  
    End Function  
  
    Sub DoIndependentWork()  
        ResultsTextBox.Text &= "Working . . . . . . ." & vbCrLf  
    End Sub  
End Class  
  
' Sample Output:  
  
' Working . . . . . . .  
  
' Length of the downloaded string: 41763.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
