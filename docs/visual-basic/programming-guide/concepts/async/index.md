---
title: Async ve Await ile Zaman Uyumsuz Programlama
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: b3ca0398936d257612b30828e3048797894ccc20
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163637"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Async ve await ile zaman uyumsuz programlama (Visual Basic)

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.

Visual Studio 2012, .NET Framework 4,5 ve üzeri, Windows Çalışma Zamanı ve ayrıca zaman uyumsuz destekten yararlanan, zaman uyumsuz bir yaklaşım getirmiştir. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.

Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.

## <a name="BKMK_WhentoUseAsynchrony"></a>Zaman uyumsuz, yanıt hızını geliştirir

Zaman uyumsuzluk, uygulamanızın Web'e erişmesi gibi engelleme olasılığı bulunan faaliyetler için önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik zaman uyumlu işlemde engellenirse uygulamanın tamamı beklemelidir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET Framework 4,5 ve Windows Çalışma Zamanı listelenen API 'Ler, zaman uyumsuz programlamayı destekleyen yöntemler içerir.

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

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Zaman uyumsuz yöntemlerin yazılması daha kolaydır

Visual Basic zaman [uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [await](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcükleri zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework veya Windows Çalışma Zamanı kaynaklarını kullanabilirsiniz. `Async` ve `Await` kullanarak tanımladığınız zaman uyumsuz yöntemler, zaman uyumsuz yöntemler olarak adlandırılır.

Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.

Bu konunun sonunda bir Windows Presentation Foundation (WPF) örnek dosyası bulabilirsiniz ve örneği [zaman uyumsuz örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/)indirebilirsiniz.

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

`AccessTheWebAsync`, çağırma `GetStringAsync` arasında yapamazsa ve tamamlanmasını beklerken, aşağıdaki tek deyime çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası bir `Async` değiştiricisi içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - Yönteminizin TResult türünde olan bir return ifadesine sahipse [görev (TResult)](xref:System.Threading.Tasks.Task%601) .
  - yönteminizin Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahipse <xref:System.Threading.Tasks.Task>.
  - Bir zaman uyumsuz olay işleyicisi yazıyorsanız [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) .

  Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki "Dönüş Türleri ve Parametreler" bölümüne bakın.

- Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.

.NET Framework önceki sürümlerinde zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

![Zaman uyumsuz bir programın izlenmesini gösteren diyagram.](./media/index/navigation-trace-async-program.png)

Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir:

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync` bir <xref:System.Net.Http.HttpClient> örneği oluşturur ve bir Web sitesinin içeriğini bir dize olarak indirmek için <xref:System.Net.Http.HttpClient.GetStringAsync%2A> zaman uyumsuz yöntemini çağırır.

3. `GetStringAsync` ilerleme durumunu askıya alan bir sorun oluşur. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemeyi önlemek için `GetStringAsync`, `AccessTheWebAsync`çağıranına denetim verir.

     `GetStringAsync`, TResult bir dize olduğu ve `AccessTheWebAsync` görevi `getStringTask` değişkenine atayan bir [görevi (TResult)](xref:System.Threading.Tasks.Task%601) döndürür. Görev, iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde `GetStringAsync`çağrısı için devam eden işlemi temsil eder.

4. `getStringTask` henüz beklenmediği için, `AccessTheWebAsync` `GetStringAsync`son sonucuna bağlı olmayan diğer çalışmalarla devam edebilir. Bu iş, zaman uyumlu Yöntem `DoIndependentWork`çağrısıyla temsil edilir.

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, `getStringTask`bir sonuç olmadan yapabilmeden iş dışında çalışıyor. `AccessTheWebAsync`, indirilen dizenin uzunluğunu hesaplamak ve döndürmek istiyor, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle, `AccessTheWebAsync` ilerlemesini askıya almak ve denetimi `AccessTheWebAsync`çağıran yönteme bırakmak için bir Await işleci kullanır. `AccessTheWebAsync`, çağırana bir `Task(Of Integer)` döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.

    > [!NOTE]
    > `GetStringAsync` (ve bu nedenle `getStringTask`) `AccessTheWebAsync` önünde beklediğinden denetim `AccessTheWebAsync`' de kalır. Çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve AccessTheWebSync 'in nihai sonucu beklemek zorunda olmaması durumunda `AccessTheWebAsync` için askıya alma ve sonra geri dönme gideri harcanacaktır.

     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Çağıran, sonucu beklemeden önce `AccessTheWebAsync` sonucu üzerinde bağlı olmayan başka işler, veya arayanın anında bekleme yapması istenebilir.   Olay işleyicisi `AccessTheWebAsync`bekliyor ve `AccessTheWebAsync` `GetStringAsync`bekliyor.

7. `GetStringAsync` tamamlanır ve bir dize sonucu üretir. Dize sonucu, `GetStringAsync` çağrısı tarafından, bekleneceğiniz şekilde döndürülmedi. (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu, yönteminin tamamlandığını temsil eden görevde saklanır `getStringTask`. Await işleci `getStringTask`sonucu alır. Atama ekstresi, alınan sonucu `urlContents`atar.

8. `AccessTheWebAsync` dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. `AccessTheWebAsync` çalışması da tamamlanır ve bekleyen olay işleyicisi de sürdürülür. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.

Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen `GetStringAsync` gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz. .NET Framework 4,5 veya üzeri, `Async` ve `Await`birlikte çalışan birçok üye içerir. Bu üyeleri, üye adına iliştirilmiş "Async" sonekine ve <xref:System.Threading.Tasks.Task> ya da görevin bir dönüş türüne [(TResult)](xref:System.Threading.Tasks.Task%601)göre tanıyabilirsiniz. Örneğin `System.IO.Stream` sınıfı, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu yöntemler <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>ve <xref:System.IO.Stream.Write%2A>gibi yöntemleri içerir.

Windows Çalışma Zamanı ayrıca Windows uygulamalarında `Async` ve `Await` ile kullanabileceğiniz birçok yöntem içerir. Daha fazla bilgi ve örnek yöntemler için bkz. [Visual Basic zaman uyumsuz C# API 'leri çağırma](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [zaman uyumsuz programlama (Windows çalışma zamanı uygulamalar)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))ve [WhenAny: .NET Framework ile Windows çalışma zamanı arasında köprü](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))oluşturma.

## <a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Zaman uyumsuz bir yöntemde `Await` ifadesi, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.

`Async` ve `Await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntemler kendi iş parçacığında çalışmadığından zaman uyumsuz metotlar çok iş parçacığı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> kullanabilirsiniz, ancak arka plan iş parçacığı yalnızca sonuçların kullanılabilir hale gelmesini bekleyen bir işlem konusunda yardımcı olmaz.

Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım g/ç ile bağlantılı işlemler için <xref:System.ComponentModel.BackgroundWorker> daha iyidir, çünkü kod basittir ve yarış koşullarına karşı koruma yapmanız gerekmez. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>ile birlikte zaman uyumsuz programlama, CPU 'ya bağlanan işlemler için <xref:System.ComponentModel.BackgroundWorker> daha iyidir, çünkü zaman uyumsuz programlama, kodunuzun iş parçacığı koduna `Task.Run` aktardığı işten kod çalıştırmanın koordinasyon ayrıntılarını ayırır.

## <a name="BKMK_AsyncandAwait"></a>Async ve await

Bir yöntemi [zaman](../../../../visual-basic/language-reference/modifiers/async.md) uyumsuz bir değiştirici kullanarak zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../../visual-basic/language-reference/operators/await-operator.md) kullanabilir. await işleci derleyiciye, beklenen zaman uyumsuz işlem tamamlanmadan zaman uyumsuz yöntemin bu noktanın ilerisine devam edemeyeceğini bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.

  Bir `Await` ifadesinde zaman uyumsuz bir yöntemin askıya alınması yöntemden bir çıkış oluşturmaz ve `Finally` blokları çalışmaz.

- İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.

Zaman uyumsuz bir yöntem, genellikle bir `Await` işlecinin bir veya daha fazla örneğini içerir, ancak `Await` ifadelerinin yokluğu bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma noktasını işaretlemek için `Await` işleci kullanmıyorsa, yöntem, `Async` değiştiriciye rağmen zaman uyumlu bir yöntem olarak yürütülür. Derleyici bu tür yöntemler için bir uyarı verir.

`Async` ve `Await` bağlamsal anahtar sözcüklerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

.NET Framework programlamada, zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> veya bir [görevi (TResult)](xref:System.Threading.Tasks.Task%601)döndürür. Zaman uyumsuz bir yöntem içinde, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve `Await` işleci uygulanır.

Yöntemi, `TResult`türünde bir işleneni belirten bir [Return](../../../../visual-basic/language-reference/statements/return-statement.md) bildirisi içeriyorsa, dönüş türü olarak [(TResult) görevi](xref:System.Threading.Tasks.Task%601) belirtirsiniz.

Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda dönüş türü olarak `Task` kullanırsınız.

Aşağıdaki örnek, bir [görevi (TResult)](xref:System.Threading.Tasks.Task%601) veya <xref:System.Threading.Tasks.Task>döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir:

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

Zaman uyumsuz bir yöntem de `Sub` yöntemi olabilir. Bu dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.

`Sub` yordam olan zaman uyumsuz bir yöntem beklenemez ve çağıran, yöntemin aldığı özel durumları yakalayamaz.

Zaman uyumsuz bir yöntem [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametreleri bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return Types (Visual Basic)](async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- [IAsyncOperation (Of TResult)](xref:Windows.Foundation.IAsyncOperation%601), [göreve (Of TResult)](xref:System.Threading.Tasks.Task%601) karşılık gelir
- <xref:System.Threading.Tasks.Task> karşılık gelen <xref:Windows.Foundation.IAsyncAction>
- [IAsyncActionWithProgress (Of TProgress)](xref:Windows.Foundation.IAsyncActionWithProgress%601)
- [IAsyncOperationWithProgress (Of TResult, TProgress)](xref:Windows.Foundation.IAsyncOperationWithProgress%602)

Daha fazla bilgi ve bir örnek için bkz. [ C# ' de zaman uyumsuz API 'leri çağırma veya Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kurala göre, bir `Async` değiştiricisine sahip yöntemlerin adlarına "Async" ekleyin.

Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, `Button1_Click`gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme yolu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki izlenecek yolu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ekler. `WhenAll` kullanımı, tüm indirmeleri aynı anda başlatır.||
|[Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Async örneği: zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)](fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> [zaman uyumsuz bir görevi veya görev listesini iptal - (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />zaman [uyumsuz görevleri bir süre sonra iptal - (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />[kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal - (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [birden çok zaman uyumsuz görev başlatın ve bunları tamamladıktan sonra işleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](handling-reentrancy-in-async-apps.md)|Çalışırken etkin bir zaman uyumsuz işlemin yeniden başlatılma durumlarının nasıl işleneceğini gösterir.||
|[WhenAny: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ile Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.CancellationTokenSource> kullanabilmeniz için, Windows Çalışma Zamanı .NET Framework ve IAsyncOperations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (Visual Basic)](using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Bu model <xref:System.Threading.Tasks.Task> ve [görev (Of TResult)](xref:System.Threading.Tasks.Task%601) türlerini temel alır.||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async+&type=All)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu konunun ele aldığı Windows Presentation Foundation (WPF) uygulamasındaki MainWindow. xaml. vb dosyasıdır. Örneği zaman uyumsuz [örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/)indirebilirsiniz.

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
