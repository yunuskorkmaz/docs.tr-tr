---
title: Async ve await ile zaman uyumsuz programlama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 9632ee7d275e6641bcd334aa12cded44920d2fda
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291662"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Async ve await ile zaman uyumsuz programlama (Visual Basic)

Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verebilirliğini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir, bu da yazma, hata ayıklama ve sürdürme işlemlerini zorlaştırır.

Visual Studio 2012, .NET Framework 4,5 ve üzeri, Windows Çalışma Zamanı ve ayrıca zaman uyumsuz destekten yararlanan, zaman uyumsuz bir yaklaşım getirmiştir. Derleyici, geliştiricinin yapması için kullandığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlamanın avantajlarından yararlanın ve bu da çabaların bir sonucudur.

Bu konu, zaman uyumsuz programlamanın ne zaman ve nasıl kullanılacağına dair bir genel bakış sağlar ve Ayrıntılar ve örnekler içeren destek konularına bağlantılar içerir.

## <a name="BKMK_WhentoUseAsynchrony"></a>Zaman uyumsuz, yanıt hızını geliştirir

Asynchrony, uygulamanızın Web 'e erişmesi gibi olası engelleme etkinlikleri için gereklidir. Bir web kaynağına erişim bazen yavaş veya geciktirilebilir. Bu tür bir etkinlik zaman uyumlu bir işlem içinde engellenirse, uygulamanın tamamının beklemesi gerekir. Zaman uyumsuz bir işlemde, uygulama, olası engelleme görevi tamamlanana kadar web kaynağına bağlı olmayan diğer çalışmalarla devam edebilir.

Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını artıran tipik bölgeler gösterilmektedir. .NET Framework 4,5 ve Windows Çalışma Zamanı listelenen API 'Ler, zaman uyumsuz programlamayı destekleyen yöntemler içerir.

|Uygulama alanı|Zaman uyumsuz yöntemler içeren API 'Leri destekleme|
|----------------------|------------------------------------------------|
|Web erişimi|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|
|Dosyalarla çalışma|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|
|Görüntülerle çalışma|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|WCF programlama|[Zaman uyumlu ve zaman uyumsuz Işlemler](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Kullanıcı arabirimi ile ilgili tüm etkinlikler genellikle tek bir iş parçacığını paylaştığından, asynchrony, özellikle UI iş parçacığına erişen uygulamalar için değerlidir. Zaman uyumlu bir uygulamada herhangi bir işlem engellenirse, tümü engellenir. Uygulamanız yanıt vermeyi durduruyor ve bunun yerine bekleme süresi sona erdiğinde, bunun başarısız olduğunu de iptal edebilirsiniz.

Zaman uyumsuz yöntemler kullandığınızda, uygulama kullanıcı arabirimine yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da işlemin bitmesini beklemek istemiyorsanız uygulamayı kapatabilirsiniz.

Zaman uyumsuz tabanlı yaklaşım, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine otomatik bir iletimin eşdeğerini ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarını, ancak geliştiriciden çok daha az çaba elde edersiniz.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Zaman uyumsuz yöntemlerin yazılması daha kolaydır

Visual Basic zaman [uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [await](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcükleri zaman uyumsuz programlamanın kalbidir. Bu iki anahtar sözcüğü kullanarak, bir zaman uyumlu Yöntem oluştururken neredeyse kolayca zaman uyumsuz bir yöntem oluşturmak için .NET Framework veya Windows Çalışma Zamanı kaynaklarını kullanabilirsiniz. @No__t-0 ve `Await` kullanarak tanımladığınız zaman uyumsuz yöntemler, zaman uyumsuz yöntemler olarak adlandırılır.

Aşağıdaki örnek bir zaman uyumsuz yöntemi gösterir. Koddaki neredeyse her şey size tamamen tanıdık gelmelidir. Yorumlar, asynchrony oluşturmak için eklediğiniz özellikleri çağırır.

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

@No__t-0 ' ı çağırarak `GetStringAsync` arasında yapamazsa ve tamamlanmasını beklerken, aşağıdaki tek bildirimde çağırarak ve bekleyen kodunuzu basitleştirebilirsiniz.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

 Aşağıdaki özellikler, önceki örneği nasıl zaman uyumsuz bir yöntem yaptığını özetler:

- Yöntem imzası `Async` değiştiricisi içerir.
- Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.
- Dönüş türü aşağıdaki türlerden biridir:

  - <xref:System.Threading.Tasks.Task%601> ' ın işlenenin TResult türünde olduğu bir return bildirisi varsa.
  - <xref:System.Threading.Tasks.Task> ' ın Return bildirisi yoksa veya işleneni olmayan bir return ifadesine sahipse.
  - Bir zaman uyumsuz olay işleyicisi yazıyorsanız [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) .

  Daha fazla bilgi için bu konunun devamındaki "dönüş türleri ve parametreleri" başlığına bakın.

- Yöntemi genellikle beklenen zaman uyumsuz işlem tamamlanana kadar yöntemin devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim metodun çağıranına döner. Bu konunun sonraki bölümünde, askıya alma noktasında neler olduğu gösterilmektedir.

Zaman uyumsuz yöntemlerde, ne yapmak istediğinizi belirtmek için sunulan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına döndüğünde ne olması gerektiğini izlemek de dahil olmak üzere, geri kalanı yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodda işlenmesi zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri, zaman uyumlu bir çözümde yaptığınız kadar çok yazarsınız ve sorun çözülür.

.NET Framework önceki sürümlerinde zaman uyumsuzluğu hakkında daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Zaman uyumsuz bir yöntemde ne olur?

Zaman uyumsuz programlamada anlaşılması gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagramda süreç boyunca size yol gösterir:

![Zaman uyumsuz bir programın izlenmesini gösteren diyagram.](./media/index/navigation-trace-async-program.png)

Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir:

1. Bir olay işleyicisi, `AccessTheWebAsync` zaman uyumsuz yöntemini çağırır ve bekler.

2. `AccessTheWebAsync` bir <xref:System.Net.Http.HttpClient> örneği oluşturur ve bir Web sitesinin içeriğini bir dize olarak indirmek için <xref:System.Net.Http.HttpClient.GetStringAsync%2A> zaman uyumsuz yöntemini çağırır.

3. @No__t-0 ' da, ilerleme durumunu askıya alan bir sorun oluşur. Belki de bir Web sitesinin indirilmesinin veya başka bir engelleme etkinliğinin beklemesi gerekir. @No__t-0, kaynak engellemeyi önlemek için, `AccessTheWebAsync` ' e yönelik denetim verir.

     `GetStringAsync`, TResult bir dize olduğunda bir <xref:System.Threading.Tasks.Task%601> döndürür ve `AccessTheWebAsync` görevi `getStringTask` değişkenine atar. Görev, iş tamamlandığında gerçek bir dize değeri üretme taahhüdünde `GetStringAsync` ' a yapılan çağrı için devam eden işlemi temsil eder.

4. @No__t-0 henüz beklenmediği için, `AccessTheWebAsync` `GetStringAsync` ' den nihai sonuca bağlı olmayan diğer çalışmalarla devam edebilir. Bu iş, zaman uyumlu yöntem çağrısıyla temsil edilir `DoIndependentWork`.

5. `DoIndependentWork`, işini yapan ve çağırana döndüren zaman uyumlu bir yöntemdir.

6. `AccessTheWebAsync`, `getStringTask` ' den bir sonuç olmadan yapabilmeden iş dışında çalışıyor. `AccessTheWebAsync` ' dan sonra indirilen dizenin uzunluğunu hesaplamak ve döndürmek ister, ancak yöntem dizeye gelinceye kadar bu değeri hesaplayamaz.

     Bu nedenle, `AccessTheWebAsync` ' ın ilerlemesini askıya almak ve denetimi `AccessTheWebAsync` ' i çağıran yönteme getirmek için bir Await işleci kullanır. `AccessTheWebAsync`, arayana bir `Task<int>` (`Task(Of Integer)` Visual Basic) döndürür. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu üretmek için bir Promise 'yi temsil eder.

    > [!NOTE]
    > @No__t-0 (ve bu nedenle `getStringTask`) `AccessTheWebAsync` ' den önce tamamlandıktan sonra, denetim `AccessTheWebAsync` ' te kalır. Çağrılan zaman uyumsuz işlem (`getStringTask`) zaten tamamlanmışsa ve AccessTheWebSync 'in nihai sonucu beklemek zorunda olmaması halinde `AccessTheWebAsync` ' a geri alma ve döndürme gideri harcanacaktır.

     Çağıranın içinde (Bu örnekteki olay işleyicisi), işleme deseninin devam etmesi gerekir. Çağıran, sonucu beklemeden önce `AccessTheWebAsync` ' dan sonuca bağlı olmayan başka işler, ya da çağıranın anında bekleme yapması istenebilir.   Olay işleyicisi `AccessTheWebAsync` ' ı bekliyor ve `AccessTheWebAsync` `GetStringAsync` ' i bekliyor.

7. `GetStringAsync` tamamlanır ve bir dize sonucu üretir. Dize sonucu, bekleneceğiniz şekilde `GetStringAsync` ' a çağrı tarafından döndürülmedi. (Metodun adım 3 ' te bir görevi zaten döndürdüğünü unutmayın.) Bunun yerine, dize sonucu yöntemin tamamlanmasını temsil eden görevde saklanır, `getStringTask`. Await işleci `getStringTask` ' dan sonucu alır. Atama ekstresi alınan sonucu `urlContents` ' a atar.

8. @No__t-0 ' ın dize sonucu olduğunda, yöntemi dizenin uzunluğunu hesaplayabilir. @No__t-0 ' ın çalışması da tamamlanır ve bekleyen olay işleyicisi sürdürülebilirler. Konunun sonundaki tam örnekte olay işleyicisinin, uzunluk sonucunun değerini aldığını ve yazdırmasını doğrulayabilirsiniz.

Zaman uyumsuz programlama için yeni bir işlem yapıyorsanız, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkı göz önünde bulundurmanız gereken bir dakika bekleyin. Zaman uyumlu bir yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem iş askıya alındığında bir görev değeri döndürür (adım 3 ve 6). Zaman uyumsuz yöntem işini en sonunda tamamladığında, görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.

Denetim akışı hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>API zaman uyumsuz yöntemleri

Zaman uyumsuz programlamayı destekleyen `GetStringAsync` gibi yöntemlerin nerede bulunacağını merak ediyor olabilirsiniz. .NET Framework 4,5 veya üzeri, `Async` ve `Await` ile çalışan birçok üye içerir. Bu üyeleri üye adına iliştirilmiş "Async" sonekine ve <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> dönüş türüne göre tanıyabilirsiniz. Örneğin `System.IO.Stream` sınıfı, zaman uyumlu yöntemler <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> ve <xref:System.IO.Stream.Write%2A> gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> ve <xref:System.IO.Stream.WriteAsync%2A> gibi yöntemler içerir.

Windows Çalışma Zamanı Ayrıca, Windows uygulamalarında `Async` ve `Await` ile kullanabileceğiniz birçok yöntem içerir. Daha fazla bilgi ve örnek yöntemler için bkz. [Visual Basic zaman uyumsuz C# API 'leri çağırma](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [zaman uyumsuz programlama (Windows çalışma zamanı uygulamalar)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10))ve [WhenAny: .NET Framework ile Windows çalışma zamanı arasında köprü](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))oluşturma.

## <a name="BKMK_Threads"></a>Akışları

Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olması amaçlanmıştır. Zaman uyumsuz bir yöntemde `Await` ifadesi, beklenen görev çalışırken geçerli iş parçacığını engellemez. Bunun yerine ifade, yöntemin geri kalanını devam olarak imzalar ve denetimi zaman uyumsuz yöntemi çağırana döndürür.

@No__t-0 ve `Await` anahtar sözcükleri ek iş parçacıklarının oluşturulmasına neden olmaz. Zaman uyumsuz yöntemler kendi iş parçacığında çalışmadığından zaman uyumsuz metotlar çok iş parçacığı gerektirmez. Yöntemi geçerli eşitleme bağlamında çalışır ve yalnızca Yöntem etkin olduğunda iş parçacığı üzerinde zaman kullanır. CPU 'ya bağlanan işi arka plan iş parçacığına taşımak için <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> ' ı kullanabilirsiniz, ancak arka plan iş parçacığı sonuçların kullanılabilir hale gelmesini bekleyen bir işlemle ilgili yardım etmez.

Zaman uyumsuz programlama için zaman uyumsuz tabanlı yaklaşım neredeyse her durumda varolan yaklaşımlara tercih edilir. Özellikle, bu yaklaşım g/ç ile bağlantılı işlemler için <xref:System.ComponentModel.BackgroundWorker> ' dan daha iyidir ve kod daha basittir ve yarış koşullarına karşı koruma yapmanız gerekmez. Zaman uyumsuz programlama, <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> ' ı kullanarak, CPU 'ya bağlanan işlemler için <xref:System.ComponentModel.BackgroundWorker> ' den daha iyidir, çünkü Async programlama, kodunuzun iş parçacığı adına `Task.Run` aktarımı olan işten kod çalıştırmanın koordinasyon ayrıntılarını ayırır.

## <a name="BKMK_AsyncandAwait"></a>Async ve await

Bir yöntemi [zaman](../../../../visual-basic/language-reference/modifiers/async.md) uyumsuz bir değiştirici kullanarak zaman uyumsuz bir yöntem olduğunu belirtirseniz, aşağıdaki iki özelliği etkinleştirirsiniz.

- İşaretlenen zaman uyumsuz yöntem, askıya alma noktaları belirlemek için [await](../../../../visual-basic/language-reference/operators/await-operator.md) kullanabilir. Await işleci derleyiciye zaman uyumsuz yöntemin, beklenen zaman uyumsuz işlem tamamlanana kadar bu noktanın ötesine devam edemeyeceğini söyler. Bu sırada denetim, zaman uyumsuz yöntemi çağırana döner.

  Bir `Await` ifadesinde zaman uyumsuz bir yöntemin askıya alınması yöntemden bir çıkış oluşturmaz ve `Finally` blokları çalışmaz.

- İşaretlenen zaman uyumsuz yöntem kendisini çağıran yöntemler tarafından beklemiş olabilir.

Zaman uyumsuz bir yöntem genellikle `Await` işlecinin bir veya daha fazla örneğini içerir, ancak `Await` ifadelerinin yokluğu bir derleyici hatasına neden olmaz. Zaman uyumsuz bir yöntem, askıya alma noktasını işaretlemek için `Await` işleci kullanmıyorsa, yöntem, `Async` değiştiricisine rağmen zaman uyumlu bir yöntem olarak yürütülür. Derleyici bu tür yöntemler için bir uyarı verir.

`Async` ve `Await` bağlamsal anahtar kelimelerdir. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:

- [Eş](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await Işleci](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Dönüş türleri ve parametreleri

.NET Framework programlamada, zaman uyumsuz bir yöntem genellikle bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndürür. Zaman uyumsuz bir yöntemin içinde, başka bir zaman uyumsuz metoda yapılan çağrıdan döndürülen bir göreve `Await` işleci uygulanır.

Yöntem, `TResult` türünde bir işleneni belirten bir [dönüş](../../../../visual-basic/language-reference/statements/return-statement.md) açıklaması içeriyorsa, dönüş türü olarak <xref:System.Threading.Tasks.Task%601> belirtirsiniz.

Metodun Return ifadesine sahip olmaması veya bir işleneni döndürmeyen bir return ifadesine sahip olması durumunda, dönüş türü olarak `Task` kullanırsınız.

Aşağıdaki örnek, <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task> döndüren bir yöntemi nasıl bildirmenizi ve çağırakullanacağınızı gösterir:

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

Döndürülen her görev devam eden çalışmayı temsil eder. Bir görev, zaman uyumsuz işlemin durumuyla ilgili bilgileri ve sonunda işlemin son sonucunu ya da işlemin başarılı olmazsa yaptığı özel durumu kapsar.

Zaman uyumsuz bir yöntem de `Sub` yöntemi olabilir. Bu dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri genellikle zaman uyumsuz programlar için başlangıç noktası olarak görev yapar.

@No__t-0 yordam olan zaman uyumsuz bir yöntem beklenemez ve çağıran, yöntemin aldığı özel durumları yakalayabilir.

Zaman uyumsuz bir yöntem [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametreleri bildiremez, ancak yöntem bu parametrelere sahip yöntemleri çağırabilir.

Daha fazla bilgi ve örnek için bkz. [Async Return Types (Visual Basic)](async-return-types.md). Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Windows Çalışma Zamanı programlamadaki zaman uyumsuz API 'Ler, görevlerle benzer olan aşağıdaki dönüş türlerinden birine sahiptir:

- <xref:Windows.Foundation.IAsyncOperation%601>, <xref:System.Threading.Tasks.Task%601> ' e karşılık gelir
- <xref:Windows.Foundation.IAsyncAction>, <xref:System.Threading.Tasks.Task> ' e karşılık gelir
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

Daha fazla bilgi ve bir örnek için bkz. [ C# ' de zaman uyumsuz API 'leri çağırma veya Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a>Adlandırma kuralı

Kurala göre, "Async" öğesini `Async` değiştiricisine sahip yöntemlerin adlarına ekleyin.

Bir olay, temel sınıf veya arabirim sözleşmesinin farklı bir ad önerdiği kuralı yoksayabilirsiniz. Örneğin, `Button1_Click` gibi yaygın olay işleyicilerini yeniden adlandırmamanız gerekir.

## <a name="BKMK_RelatedTopics"></a>İlgili konular ve örnekler (Visual Studio)

|Başlık|Açıklama|Örnek|
|-----------|-----------------|------------|
|[İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünün zaman uyumsuz bir WPF çözümüne nasıl dönüştürüleceğini gösterir. Uygulama bir dizi Web sitesi indirir.|[Zaman uyumsuz örnek: Web 'e erişme yolu](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Önceki izlenecek yol için <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ekler. @No__t-0 kullanımı, tüm indirmeleri aynı anda başlatır.||
|[Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Aynı anda birkaç görevi nasıl başlatabileceğinizi gösterir.|[Zaman uyumsuz örnek: birden çok Web Isteğini paralel hale getirme](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün uygun olduğu zaman bunu açıklar.||
|[Zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md)|Bir zaman uyumsuz programdaki bir bekleme ifadeleriyle denetim akışını ayrıntılı olarak izler.|[Async örneği: zaman uyumsuz programlarda denetim akışı](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)](fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevlerin nasıl ekleneceğini gösterir:<br /><br /> - [zaman uyumsuz bir görevi veya görev listesini Iptal etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [bir süre sonra zaman uyumsuz görevleri Iptal et (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [bir süre tamamlandıktan sonra kalan zaman uyumsuz görevleri Iptal et (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa işleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](handling-reentrancy-in-async-apps.md)|Çalışırken etkin bir zaman uyumsuz işlemin yeniden başlatılma durumlarının nasıl işleneceğini gösterir.||
|[WhenAny: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> kullanabilmeniz için, .NET Framework ve ıasyncoWindows çalışma zamanı Perations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ile Windows Çalışma Zamanı arasında köprü oluşturma (AsTask ve WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Zaman uyumsuz Iptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|Bir Windows Çalışma Zamanı yöntemiyle <xref:System.Threading.CancellationTokenSource> kullanabilmeniz için, .NET Framework ve ıasyncoWindows çalışma zamanı Perations içindeki görev türleri arasında nasıl köprü oluşturulacağını gösterir.|[Zaman uyumsuz örnek: .NET ve Windows Çalışma Zamanı arasında köprü oluşturma (AsTask & Iptali)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Dosya erişimi için Async Kullanma (Visual Basic)](using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz ve await kullanmanın avantajlarını listeler ve gösterir.||
|[Görev tabanlı zaman uyumsuz model (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|.NET Framework zaman uyumsuzluğu için yeni bir model tanımlar. Bu model <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türlerini temel alır.||
|[Channel 9 ' da zaman uyumsuz videolar](https://channel9.msdn.com/search?term=async+&type=All)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||

## <a name="BKMK_CompleteExample"></a>Örnek Tamam

Aşağıdaki kod, bu konunun ele aldığı Windows Presentation Foundation (WPF) uygulamasındaki MainWindow. xaml. vb dosyasıdır. Örneği zaman uyumsuz [örnek: "Async ve await Ile zaman uyumsuz programlama" kaynağından](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/)indirebilirsiniz.

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Await Işleci](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Eş](../../../../visual-basic/language-reference/modifiers/async.md)
