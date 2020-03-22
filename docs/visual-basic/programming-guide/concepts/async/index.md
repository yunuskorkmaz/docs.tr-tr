---
title: Async ve Await ile Zaman Uyumsuz Programlama
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: cbcdd48571855e168f563585088f1210eb6410eb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266501"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Async ve Await ile asynchronous programlama (Visual Basic)

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

Visual Studio 2012, .NET Framework 4.5 ve daha yüksek ve Windows Runtime'da eşzamanlı destekten yararlanan basitleştirilmiş bir yaklaşım, async programlama getirmiştir. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a>Async yanıt verme yeteneğini artırır

Zaman uyumsuzluk, uygulamanızın Web'e erişmesi gibi engelleme olasılığı bulunan faaliyetler için önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik zaman uyumlu işlemde engellenirse uygulamanın tamamı beklemelidir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET Framework 4.5 ve Windows Runtime'dan listelenen API'ler, async programlamayı destekleyen yöntemler içerir.

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

## <a name="async-methods-are-easier-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a>Async yöntemleri yazmak daha kolaydır

Visual Basic'teki [Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar kelimeleri async programlamanın kalbidir. Bu iki anahtar kelimeyi kullanarak, .NET Framework veya Windows Runtime'daki kaynakları kullanarak eşzamanlı bir yöntem oluşturduğunuz kadar kolay bir eşzamanlı yöntem oluşturabilirsiniz. Kullanarak `Async` tanımladığınız ve `Await` async yöntemleri olarak adlandırdığınız eşzamanlı yöntemler.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.

Bu konunun sonunda eksiksiz bir Windows Presentation Foundation (WPF) örnek dosyasını bulabilir ve Örneği [Async Sample'dan indirebilirsiniz: "Async ve Await ile Asynchronous Programming" örneğinden.](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/)

```vb
' Three things to note about writing an Async Function:
'  - The function has an Async modifier.
'  - Its return type is Task or Task(Of T). (See "Return Types" section.)
'  - As a matter of convention, its name ends in "Async".
Async Function AccessTheWebAsync() As Task(Of Integer)
    Using client As New HttpClient()
        ' Call and await separately.
        '  - AccessTheWebAsync can do other things while GetStringAsync is also running.
        '  - getStringTask stores the task we get from the call to GetStringAsync.
        '  - Task(Of String) means it is a task which returns a String when it is done.
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://docs.microsoft.com/dotnet")
        ' You can do other work here that doesn't rely on the string from GetStringAsync.
        DoIndependentWork()
        ' The Await operator suspends AccessTheWebAsync.
        '  - AccessTheWebAsync does not continue until getStringTask is complete.
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
        '  - Control resumes here when getStringTask is complete.
        '  - The Await operator then retrieves the String result from getStringTask.
        Dim urlContents As String = Await getStringTask
        ' The Return statement specifies an Integer result.
        ' A method which awaits AccessTheWebAsync receives the Length value.
        Return urlContents.Length

    End Using

End Function
```

`AccessTheWebAsync` Arama `GetStringAsync` yapmakla tamamlanmasını beklemek arasında yapabileceği herhangi bir iş yoksa, aşağıdaki tek ifadede arayarak ve bekleyerek kodunuzu basitleştirebilirsiniz.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Aşağıdaki özellikler, önceki örneği bir async yöntemi yapan şeyi özetler:

- Yöntem imzası bir `Async` değiştirici içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - [Görev (TResult)](xref:System.Threading.Tasks.Task%601) yönteminizde operand tresult türüne sahip bir iade deyimi varsa.
  - <xref:System.Threading.Tasks.Task>yönteminizde iade beyanı yoksa veya operand'ı olmayan bir iade beyanı varsa.
  - Bir async olay işleyicisi yazıyorsanız [alt.](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)

  Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki "Dönüş Türleri ve Parametreler" bölümüne bakın.

- Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

.NET Framework'ün önceki sürümlerinde eşzamanlılık hakkında daha fazla bilgi için [TPL ve Traditional .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md)bölümüne bakın.

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Async yönteminde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol açar:

![Bir async programının izini gösteren diyagram.](./media/index/navigation-trace-async-program.png)

Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir:

1. Bir olay işleyicisi `AccessTheWebAsync` çağırır ve async yöntemini bekler.

2. `AccessTheWebAsync`bir <xref:System.Net.Http.HttpClient> örnek oluşturur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2A> bir web sitesinin içeriğini dize olarak indirmek için eşzamanlı yöntemi çağırır.

3. İlerlemesini `GetStringAsync` askıya alan bir şey olur. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek `GetStringAsync` için, denetimi arayana verir. `AccessTheWebAsync`

     `GetStringAsync`TResult'In bir dize olduğu bir [Görev (TResult)](xref:System.Threading.Tasks.Task%601) döndürür ve `AccessTheWebAsync` görevi `getStringTask` değişkene atar. Görev, çalışma tamamlandığında gerçek bir `GetStringAsync`dize değeri oluşturma taahhüdüyle, çağrı için devam eden işlemi temsil eder.

4. Çünkü `getStringTask` henüz beklenmedi, `AccessTheWebAsync` nihai sonucuna bağlı olmayan diğer çalışmalarla devam `GetStringAsync`edebilir. Bu çalışma senkron yönteme `DoIndependentWork`yapılan bir çağrı yla temsil edilir.

5. `DoIndependentWork`işini yapan ve arayana geri dönen eşzamanlı bir yöntemdir.

6. `AccessTheWebAsync`bir sonuç olmadan yapabileceği iş tükendi `getStringTask`. `AccessTheWebAsync`sonraki, indirilen dize uzunluğunu hesaplamak ve döndürmek istiyor, ancak yöntem dize olana kadar bu değeri hesaplayamaz.

     Bu `AccessTheWebAsync` nedenle, ilerlemesini askıya almak ve '. `AccessTheWebAsync` `AccessTheWebAsync`arayana `Task(Of Integer)` bir döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > (ve `GetStringAsync` bu `getStringTask`nedenle) `AccessTheWebAsync` beklemeden önce tamamlanırsa, `AccessTheWebAsync`denetim . Çağrılan asynchronous işlemi ( `AccessTheWebAsync` `getStringTask`) zaten tamamlanmış ve AccessTheWebSync nihai sonucu beklemek zorunda değildir askıya alma ve daha sonra dönen gider boşa olacaktır.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Arayan, bu sonucu beklemeden önce elde edilen `AccessTheWebAsync` sonuca bağlı olmayan başka işler yapabilir veya arayan hemen bekleyebilir.   Olay işleyicisi `AccessTheWebAsync`bekliyor `AccessTheWebAsync` ve bekliyor. `GetStringAsync`

7. `GetStringAsync`tamamlar ve bir dize sonucu üretir. Dize sonucu, beklediğiniz şekilde `GetStringAsync` çağrıyla döndürülemez. (Yöntemin 3. adımda bir görevi zaten döndürettiğini unutmayın.) Bunun yerine, dize sonucu yöntemin tamamlanmasını temsil eden `getStringTask`görevde depolanır. Bekleme işleci sonucu ' `getStringTask`dan alır. Atama deyimi, alınan sonucu ' `urlContents`ya .

8. Dize sonucu olduğunda, `AccessTheWebAsync` yöntem dize uzunluğunu hesaplayabilirsiniz. Sonra iş `AccessTheWebAsync` de tamamlanır ve bekleyen olay işleyicisi devam edebilirsiniz. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.

Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi [için, Async Programlarında Denetim Akışı (Visual Basic)](control-flow-in-async-programs.md)bakın.

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a>API Async Yöntemleri

Bu tür async programlama gibi `GetStringAsync` yöntemleri nerede bulacağınızı merak ediyor olabilirsiniz. .NET Framework 4.5 veya üstü, birlikte `Async` `Await`çalışan ve . Bu üyeleri, üye adına ve bir dönüş türüne <xref:System.Threading.Tasks.Task> veya [Görev(TResult)](xref:System.Threading.Tasks.Task%601)ekilen "Async" sonekiyle tanıyabilirsiniz. `System.IO.Stream` Örneğin, <xref:System.IO.Stream.CopyToAsync%2A>sınıf , , <xref:System.IO.Stream.ReadAsync%2A>ve <xref:System.IO.Stream.WriteAsync%2A> senkron yöntemlerin <xref:System.IO.Stream.CopyTo%2A>yanı sıra <xref:System.IO.Stream.Read%2A>, <xref:System.IO.Stream.Write%2A>ve .

Windows Runtime, Windows uygulamalarında `Async` ve `Await` windows uygulamalarında kullanabileceğiniz birçok yöntem de içerir. Daha fazla bilgi ve örnek yöntem için C# veya Visual Basic, [Asynchronous programming (Windows Runtime uygulamaları)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))ve [WhenAny: .NET Framework ve Windows Runtime arasında köprü leme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))de dahil olmak üzere [asynchronous API'leri arayın.](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic)

## <a name="threads"></a><a name="BKMK_Threads"></a>Iş parçacığı

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Async `Await` yöntemindeki bir ifade, beklenen görev çalışırken geçerli iş parçacığı engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

Anahtar `Async` `Await` kelimeler ek iş parçacıkları oluşturulmasına neden olmaz. Async yöntemi kendi iş parçacığı üzerinde çalışmadığından, async yöntemleri çoklu iş parçacığı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. CPU'ya <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> bağlı çalışmayı arka plan iş parçacığına taşımak için kullanabilirsiniz, ancak arka plan iş parçacığı, sonuçların kullanılabilir olmasını bekleyen bir işleme yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Kod daha basit olduğundan <xref:System.ComponentModel.BackgroundWorker> ve yarış koşullarına karşı korumanız gerekmediği için, bu yaklaşım G/Ç'ye bağlı işlemlerden daha iyidir. Async <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>programlama, kodunuzu çalıştırmanın <xref:System.ComponentModel.BackgroundWorker> koordinasyon ayrıntılarını iş parçacığı havuzuna `Task.Run` aktaran işten ayırdığından, async programlama ile birlikte CPU'ya bağlı işlemlerden daha iyidir.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a>Async ve Await

Bir yöntemin [Async](../../../../visual-basic/language-reference/modifiers/async.md) değiştirici kullanarak bir async yöntemi olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirin.

- İşaretli async yöntemi süspansiyon noktalarını belirlemek için [Bekle'yi](../../../../visual-basic/language-reference/operators/await-operator.md) kullanabilir. await işleci derleyiciye, beklenen zaman uyumsuz işlem tamamlanmadan zaman uyumsuz yöntemin bu noktanın ilerisine devam edemeyeceğini bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

  Bir `Await` ifadede bir async yönteminin askıya alınması yöntemden çıkış `Finally` anlamına gelmez ve bloklar çalışmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Async yöntemi genellikle bir `Await` işleç bir veya daha fazla `Await` oluşumları içerir, ancak ifadelerin yokluğu derleyici hatasına neden olmaz. Bir async yöntemi bir süspansiyon `Await` noktası işaretlemek için bir işleç kullanmıyorsa, yöntem `Async` değiştirici rağmen, senkron bir yöntem olarak yürütür. Derleyici bu tür yöntemler için bir uyarı verir.

`Async`ve `Await` bağlamsal anahtar kelimelerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [Zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a>İade türleri ve parametreleri

.NET Framework programlamada, bir async yöntemi <xref:System.Threading.Tasks.Task> genellikle bir veya bir [Görev(TResult)](xref:System.Threading.Tasks.Task%601)döndürür. Bir async yöntemi `Await` içinde, bir işleç başka bir async yöntemiiçin bir çağrı döndürülen bir göreve uygulanır.

Yöntem, bir operand türü `TResult`belirten bir [İade](../../../../visual-basic/language-reference/statements/return-statement.md) deyimi içeriyorsa, İade türü olarak [Görev(Sonuç)](xref:System.Threading.Tasks.Task%601) belirtirsiniz.

Yöntemin `Task` iade deyimi yoksa veya bir operand döndürmeyen bir iade deyimi varsa, iade türü olarak kullanırsınız.

Aşağıdaki örnek, bir [Görevi (TResult)](xref:System.Threading.Tasks.Task%601) veya bir <xref:System.Threading.Tasks.Task>yöntemi nasıl beyan ettiğinizi ve adlandırdığınızı gösterir:

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

Bir async yöntemi de `Sub` bir yöntem olabilir. Bu iade türü, öncelikle bir dönüş türü gerekli olay işleyicileri tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

Yordam olan bir async `Sub` yöntemi beklenebilir ve arayan yöntematar herhangi bir özel durum yakalayamıyor.

Bir async yöntemi [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametrelerini bildiremez, ancak yöntem bu tür parametrelere sahip yöntemleri çağırabilir.

Daha fazla bilgi ve örnekler [için, Bkz. Async İade Türleri (Visual Basic)](async-return-types.md). Özel durumları async yöntemleriyle nasıl yakalayacakları hakkında daha fazla bilgi için [bkz. Yakalamak... Son Olarak İfade](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Windows Runtime programlamadaki eşzamanlı API'ler, görevlere benzer aşağıdaki iade türlerinden birine sahiptir:

- [Görev (TResult)](xref:System.Threading.Tasks.Task%601) karşılık gelen [IAsyncOperation(TResult)](xref:Windows.Foundation.IAsyncOperation%601)
- <xref:Windows.Foundation.IAsyncAction>, hangi karşılık gelir<xref:System.Threading.Tasks.Task>
- [IAsyncActionWithProgress(TProgress Of)](xref:Windows.Foundation.IAsyncActionWithProgress%601)
- [IAsyncOperationWithProgress(Sonuç, Tprogress)](xref:Windows.Foundation.IAsyncOperationWithProgress%602)

Daha fazla bilgi ve örnek için [C# veya Visual Basic'te asynchronous API'leri arayın.](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic)

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Sözleşmeye göre, "Async"i `Async` değiştirici olan yöntemlerin adlarına eklersiniz.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, '. gibi `Button1_Click`ortak olay işleyicileri yeniden adlandırmamalısınız.

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[Walkthrough: Async ve Await (Visual Basic) kullanarak Web'e erişim](walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Async Örnek: Web Walkthrough erişim](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Nasıl Yapılır: Task.WhenAll'ı Kullanarak Async Walkthrough'u genişletin (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> gözden geçirimi ekler. Tüm indirmeleri aynı anda başlatır. `WhenAll`||
|[Nasıl Yapılır: Async ve Await (Visual Basic) kullanarak Paralel Olarak Birden Çok Web İsteği Yapma](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Async Örnek: Paralel Olarak Birden Çok Web İsteği Yapma](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Async İade Türleri (Visual Basic)](async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Async Programlarında Kontrol Akışı (Visual Basic)](control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Async Örnek: Async Programlarında Kontrol Akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Async Uygulamanızda İnce Ayar (Visual Basic)](fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> - [Bir Async Görevi veya Görev Listesini İptal Etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Bir Süre Sonra Async Görevlerini İptal Etme (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Birden Çok Async Görevi Başlatın ve Tamamladıkları Gibi İşleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Async Örnek: Uygulamanızı İyi Ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Async Apps 'da Reentrancy Işleme (Visual Basic)](handling-reentrancy-in-async-apps.md)|Etkin bir eşzamanlı işlemin çalışırken yeniden başlatıldığu servis taleplerini gösterir.||
|[WhenAny: .NET Framework ve Windows Runtime arasında köprü kurma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Windows Runtime yöntemiyle kullanabilmeniz <xref:System.Threading.Tasks.Task.WhenAny%2A> için Windows Runtime'daki .NET Framework ve IAsyncOperations'taki Görev türleri arasında nasıl köprü kurkullanılacağını gösterir.|[Async Örnek: .NET ve Windows Runtime (AsTask ve WhenAny) arasında köprüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Windows Runtime yöntemiyle kullanabilmeniz <xref:System.Threading.CancellationTokenSource> için Windows Runtime'daki .NET Framework ve IAsyncOperations'taki Görev türleri arasında nasıl köprü kurkullanılacağını gösterir.|[Async Örnek: .NET ve Windows Runtime arasında köprüleme (AsTask & İptal)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya Erişimi için Async kullanma (Visual Basic)](using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen, Görev <xref:System.Threading.Tasks.Task> [(TResult)](xref:System.Threading.Tasks.Task%601) türlerine dayanır.||
|[Kanal 9'da Async Videoları](https://channel9.msdn.com/search?term=async+&type=All)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="complete-example"></a><a name="BKMK_CompleteExample"></a>Tam Örnek

Aşağıdaki kod, bu konunun tartıştığı Windows Sunu Temeli (WPF) uygulamasından Gelen MainWindow.xaml.vb dosyasıdır. Örneği [Async Sample'dan indirebilirsiniz: "Async ve Await ile Asynchronous Programming" örneğinden.](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/)

[!code-vb[async](~/samples/snippets/standard/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md)
