---
title: Zaman uyumsuz programlama ile Async ve Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: 0f30dbeafa8fcac0ebfd76496721f1455b20048b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Zaman uyumsuz programlama ile Async ve Await (Visual Basic)
Zaman uyumsuz programlama kullanarak performans sorunlarını önleyebilir ve uygulamanızın genel yanıt verme becerisini geliştirebilirsiniz. Ancak, zaman uyumsuz uygulamalar yazmaya yönelik geleneksel teknikler karmaşık olabilir ve bu nedenle yazılmaları, hataların ayıklanması ve bakım yapılması zorlaşabilir.  
  
 Visual Studio 2012 basitleştirilmiş bir yaklaşım, .NET Framework 4.5 ve daha yüksek zaman uyumsuz desteği de olduğu gibi Windows çalışma zamanı yararlanan, zaman uyumsuz programlama sunmuştur. Derleyici, normalde geliştiricinin yaptığı zor işi yapar ve uygulamanız zaman uyumlu koda benzer bir mantıksal yapıyı korur. Sonuç olarak, zaman uyumsuz programlama avantajlarının tamamını çok daha az çaba harcayarak elde edebilirsiniz.  
  
 Bu konu zaman uyumsuz programlamanın ne zaman ve nasıl kullanılması gerektiği hakkında genel bakış içerir ve ayrıntılar ve örnekler içeren destek konularına bağlantılar sunar.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> Zaman uyumsuz yanıt hızını artırır  
 Zaman uyumsuzluk, uygulamanızın Web'e erişmesi gibi engelleme olasılığı bulunan faaliyetler için önemlidir. Web kaynağına erişim bazen yavaş veya gecikmeli olabilir. Böyle bir etkinlik zaman uyumlu işlemde engellenirse uygulamanın tamamı beklemelidir. Uygulama, zaman uyumsuz bir işlemde olası engelleme görevi sona erinceye kadar web kaynağına bağlı olmayan diğer işlerle devam eder.  
  
 Aşağıdaki tabloda, zaman uyumsuz programlamanın yanıt verme hızını geliştirdiği genel alanlar gösterilmektedir. .NET Framework 4.5 ve Windows çalışma zamanı listelenen API'lerden zaman uyumsuz programlama desteği yöntemleri içerir.  
  
|Uygulama alanı|Zaman uyumsuz yöntemler içeren API'leri destekleme|  
|----------------------|------------------------------------------------|  
|Web erişimi|<xref:System.Net.Http.HttpClient>, [SyndicationClient](http://go.microsoft.com/fwlink/p/?LinkId=259441)|  
|Dosyalarla çalışma|[StorageFile](http://go.microsoft.com/fwlink/p/?LinkId=248220), <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|  
|Görüntülerle çalışma|[MediaCapture](http://go.microsoft.com/fwlink/p/?LinkId=261839), [BitmapEncoder](http://go.microsoft.com/fwlink/p/?LinkId=261840), [BitmapDecoder](http://go.microsoft.com/fwlink/p/?LinkId=261841)|  
|WCF programlama|[Zaman Uyumlu ve Zaman Uyumsuz İşlemler](http://go.microsoft.com/fwlink/p/?LinkID=192382)|  
|||  
  
 Tüm kullanıcı arabirimi ilişkili faaliyetler genellikle tek bir iş parçacığını paylaştığından, zaman uyumsuzluğun kullanıcı arabirimi iş parçacığına erişen uygulamalar için özellikle önem taşıdığı kanıtlanmıştır. Herhangi bir işlem zaman uyumlu bir uygulamada engellenirse, tümü engellenir. Uygulamanız yanıt vermiyordur ve bunu uygulamanın beklediği değil de başarısız olduğu şeklinde yorumlayabilirsiniz.  
  
 Zaman uyumsuz yöntemleri kullandığınızda, uygulama arabirime yanıt vermeye devam eder. Bir pencereyi yeniden boyutlandırabilir veya simge durumuna küçültebilir ya da bitmesini beklemek istemiyorsanız kapatabilirsiniz.  
  
 Zaman uyumsuz tabanlı yaklaşım otomatik bir iletimin eşdeğerini, zaman uyumsuz işlemler tasarlarken seçebileceğiniz seçenekler listesine ekler. Diğer bir deyişle, geleneksel zaman uyumsuz programlamanın tüm avantajlarından yararlanabilirsiniz, buna rağmen geliştiricinin daha az çaba sarf etmesi gerekir.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Zaman uyumsuz yöntemleri yazma kolaydır  
 [Zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [bekleme](../../../../visual-basic/language-reference/modifiers/async.md) sözcükler Visual Basic'te zaman uyumsuz programlama Kalp. Bu iki anahtar sözcükleri kullanarak zaman uyumsuz bir yöntem olarak zaman uyumlu bir yöntem oluşturma gibi kolayca neredeyse oluşturmak için .NET Framework veya Windows çalışma zamanı kaynakları kullanabilirsiniz. Kullanarak tanımladığınız zaman uyumsuz yöntemleri `Async` ve `Await` zaman uyumsuz yöntemleri olarak adlandırılır.  
  
 Aşağıdaki örnekte zaman uyumsuz bir yöntem gösterilmektedir. Kodda yer alan hemen hemen her şey size tamamen tanıdık gelmiş olmalıdır. Açıklamalar, zaman uyumsuzluğu eklemek için oluşturduğunuz özellikleri çağırır.  
  
 Bu konunun sonunda eksiksiz bir Windows Presentation Foundation (WPF) örnek dosyasını bulabilirsiniz ve örnekten indirebilirsiniz [zaman uyumsuz örnek: "Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme" örnekten](http://go.microsoft.com/fwlink/?LinkID=261549).  
  
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
    Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
 Varsa `AccessTheWebAsync` arasında arama yapmak için herhangi bir iş yok `GetStringAsync` ve bunun tamamlanmasını bekleyen, çağırarak ve aşağıdaki tek deyiminde bekleyen kodunuzu basitleştirebilirsiniz.  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 Aşağıdaki özellikler, önceki örneği neyin zaman uyumsuz hale getirdiğini özetler.  
  
-   Yöntem imzası içeren bir `Async` değiştiricisi.  
  
-   Zaman uyumsuz yöntemin adı kurala göre "Async" soneki ile sona erer.  
  
-   Dönüş türü aşağıdaki türlerden biridir:  
  
    -   <xref:System.Threading.Tasks.Task%601> yönteminizi varsa işleneni olan bir return deyimi TResult yazın.  
  
    -   <xref:System.Threading.Tasks.Task> yönteminizi dönüş deyimi yok veya hiçbir işleneni olan bir return deyimi içeriyor  
  
    -   [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) zaman uyumsuz olay işleyicisi yazıyorsanız.  
  
     Daha fazla bilgi için bu konunun ilerleyen kısımlarındaki "Dönüş Türleri ve Parametreler" bölümüne bakın.  
  
-   Yöntem, genellikle beklenen zaman uyumsuz işlem tamamlanana kadar devam edemediği bir noktayı işaretleyen en az bir await ifadesi içerir. Bu sırada yöntem askıya alınır ve denetim yöntemi arayana döner. Bu konunun sonraki bölümünde askıya alma noktasında neler olduğu gösterilmektedir.  
  
 Zaman uyumsuz yöntemlerde ne yapmak istediğinizi belirtmek için sağlanan anahtar sözcükleri ve türleri kullanırsınız ve denetim, askıya alınan bir yöntemde await noktasına geldiğinde olması gerekenlerin izlenmesi dahil olmak üzere geri kalan işlemleri derleyici yapar. Döngüler ve özel durum işleme gibi bazı rutin işlemlerin geleneksel zaman uyumsuz kodla yapılması zor olabilir. Zaman uyumsuz bir yöntemde, bu öğeleri olabildiğince zaman uyumlu çözümde yazarsınız ve sorun çözülür.  
  
 .NET Framework'ün önceki sürümlerinde asynchrony hakkında daha fazla bilgi için bkz: [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](http://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Bir zaman uyumsuz yöntem ne olur?  
 Zaman uyumsuz programlama ile ilgili olarak anlamanız gereken en önemli şey, denetim akışının yöntemden yönteme nasıl geçtiğidir. Aşağıdaki diyagram işlem boyunca size yol gösterecektir.  
  
 ![Zaman uyumsuz program izleme](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Diyagramdaki sayılar aşağıdaki adımlara karşılık gelir.  
  
1.  Olay işleyici çağırır ve bekler `AccessTheWebAsync` async yöntemi.  
  
2.  `AccessTheWebAsync` oluşturur bir <xref:System.Net.Http.HttpClient> örneği ve çağrıları <xref:System.Net.Http.HttpClient.GetStringAsync%2A> dize olarak bir Web sitesi içeriğini indirmek için zaman uyumsuz yöntem.  
  
3.  İçinde bir şey `GetStringAsync` , ilerleme durumunu askıya alır. Bir web sitesinin indirmesini veya başka bir engelleyen etkinliği beklemesi gerekebilir. Kaynakları engellemekten kaçınacak şekilde `GetStringAsync` çağırıcısına, Denetim verir `AccessTheWebAsync`.  
  
     `GetStringAsync` döndüren bir <xref:System.Threading.Tasks.Task%601> TResult bir dize olduğu ve `AccessTheWebAsync` görevi atar `getStringTask` değişkeni. Görev çağrısı için devam eden işlemi temsil eden `GetStringAsync`, iş tamamlandığında, gerçek dize değeri üretmek için taahhüdü ile.  
  
4.  Çünkü `getStringTask` henüz beklemenin kurmadı `AccessTheWebAsync` Nihai sonuç bağımlı değil diğer iş devam edebilirsiniz `GetStringAsync`. Çalışma zaman uyumlu yöntemine bir çağrı tarafından temsil edilen `DoIndependentWork`.  
  
5.  `DoIndependentWork` kendi çalışır ve çağırıcısına döndüren bir zaman uyumlu yöntemidir.  
  
6.  `AccessTheWebAsync` bir sonuç kümesinden olmadan yapabilirsiniz İş dışı çalıştırıldı `getStringTask`. `AccessTheWebAsync` dize yöntemi olana kadar sonraki istediği hesaplamak ve indirilen dize ancak yöntemi uzunluğu dönmek için bu değeri hesaplanamıyor.  
  
     Bu nedenle, `AccessTheWebAsync` ilerleme durumunu askıya alma ve çağrılan yöntemi için denetimi elde etmek üzere bir bekleme işlecini kullanan `AccessTheWebAsync`. `AccessTheWebAsync` döndüren bir `Task<int>` (`Task(Of Integer)` Visual Basic'te) çağırana. Görev, indirilen dizenin uzunluğu olan bir tamsayı sonucu verecek bir taahhüdü temsil eder.  
  
    > [!NOTE]
    >  Varsa `GetStringAsync` (ve bu nedenle `getStringTask`) önce tamamlandıktan `AccessTheWebAsync` , Denetim kalırken bekler `AccessTheWebAsync`. Askıya alma ve sonra dönme gider `AccessTheWebAsync` varsa küçülttüğü iyi bir şekilde çağrılan zaman uyumsuz işlemi (`getStringTask`) zaten tamamlandı ve AccessTheWebSync nihai sonucu için beklemesi gerekmez.  
  
     Arayanın içinde (bu örnekte olay işleyicisi), işleme düzeni devam eder. Arayan sonucundan bağımlı değil diğer iş yapabilecek `AccessTheWebAsync` önce sonucunda ortaya çıkan veya arayan bekleyen hemen beklemek.   Olay işleyicisi bekliyor `AccessTheWebAsync`, ve `AccessTheWebAsync` bekliyor `GetStringAsync`.  
  
7.  `GetStringAsync` tamamlandıktan ve bir dizi sonuç üretir. Dize sonucu çağrısı tarafından döndürülen değil `GetStringAsync` beklediğiniz şekilde. (Yöntem 3. adımda zaten bir görev döndürülen unutmayın.) Bunun yerine, dize sonucu yöntemi tamamlanmasından temsil eden görev depolanan `getStringTask`. Bekleme işleci sonucundan alır `getStringTask`. Alınan sonucu atama deyimi atar `urlContents`.  
  
8.  Zaman `AccessTheWebAsync` dize sonuçta yöntemi dize uzunluğu hesaplayabilirsiniz. Ardından çalışmanın `AccessTheWebAsync` de tamamlandıktan ve bekleme olay işleyicisi devam edebilirsiniz. Konunun sonundaki tam örnekte olay işleyicisinin uzunluk sonucundaki değeri aldığını ve yazdığını onaylayabilirsiniz.  
  
 Zaman uyumsuz programlama konusunda yeniyseniz, zaman uyumlu ve zaman uyumsuz davranış arasındaki farkları değerlendirmek için bir dakikanızı ayırın. Zaman uyumlu yöntem, işi tamamlandığında döndürür (5. adım), ancak zaman uyumsuz bir yöntem işi askıya alındığında görev değeri döndürür (3 ve 6. adım). Zaman uyumsuz yöntem çalışmasını tamamladığında görev tamamlandı olarak işaretlenir ve varsa sonuç görevde depolanır.  
  
 Denetim akışı hakkında daha fazla bilgi için bkz: [(Visual Basic) zaman uyumsuz programlarda denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> API zaman uyumsuz yöntemleri  
 Yöntemleri gibi nerede bulacağını merak ediyor olabilirsiniz `GetStringAsync` Bu destek zaman uyumsuz programlama. .NET Framework 4.5 veya üstü çalışmak çok sayıda üye içeren `Async` ve `Await`. Üye adı ve dönüş türü bağlı "Zaman uyumsuz" soneki göre bu üyeler tanıyabilmesi <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Örneğin, `System.IO.Stream` sınıfı yöntemleri gibi içerir <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> zaman uyumlu yöntemleri yanında <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, ve <xref:System.IO.Stream.Write%2A>.  
  
 Windows çalışma zamanı ile birlikte kullanabileceğiniz birçok yöntem de içeren `Async` ve `Await` Windows uygulamalarında. Daha fazla bilgi ve örnek yöntemleri için bkz: [hızlı başlangıç: zaman uyumsuz programlama için bekleme işlecini kullanarak](http://go.microsoft.com/fwlink/?LinkId=248545), [zaman uyumsuz programlama (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/?LinkId=259592), ve [WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx).  
  
##  <a name="BKMK_Threads"></a> İş parçacıkları  
 Zaman uyumsuz yöntemlerin engelleyici olmayan işlemler olmaları amaçlanmıştır. Bir `Await` awaited Görev yürütülürken, bir zaman uyumsuz yöntem ifadesinde geçerli iş parçacığının engelleme değil. Bunun yerine ifade, yöntemin geri kalanını yöntemin devamı olarak imzalar ve denetimi zaman uyumsuz yöntemi arayan kişiye verir.  
  
 `Async` Ve `Await` anahtar sözcükleri oluşturulacak ek iş parçacığı neden yoktur. Zaman uyumsuz yöntem kendi iş parçacığı üzerinde çalışmadığı için zaman uyumsuz yöntemler çoklu iş parçacığı kullanımı gerektirmez. Yöntem geçerli eşitleme kapsamının üzerinde çalışır ve yalnızca yöntem etkin olduğunda iş parçacığındaki zamanı kullanır. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> arka plan iş parçacığı, ancak bir arka plan için CPU bağımlı iş taşımak için iş parçacığı kullanılabilir hale gelmesi için sonuçları yalnızca bekleyen bir işlem yardımcı değil.  
  
 Zaman uyumsuz programlamaya zaman uyumsuz yaklaşım, hemen hemen her durumda varolan yaklaşımlara tercih edilir. Bu yaklaşım özellikle, daha iyi <xref:System.ComponentModel.BackgroundWorker> için g/Ç işlemleri kod basittir ve koruma gerekmez çünkü karşı koşullar izler. İle birlikte <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, zaman uyumsuz programlama daha iyi <xref:System.ComponentModel.BackgroundWorker> CPU bağımlı işlemler için zaman uyumsuz programlama işten kodunuzu çalıştıran koordinasyon ayrıntılarını ayırdığından `Task.Run` aktarımları için iş parçacığı havuzu.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async ve Await  
 Bir yöntemi kullanarak bir zaman uyumsuz yöntem olup belirtirseniz bir [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi, aşağıdaki iki özelliklerini etkinleştirin.  
  
-   İşaretlenen zaman uyumsuz yöntem kullanabilirsiniz [bekleme](../../../../visual-basic/language-reference/operators/await-operator.md) askıya noktalarını belirlemek için. await işleci derleyiciye, beklenen zaman uyumsuz işlem tamamlanmadan zaman uyumsuz yöntemin bu noktanın ilerisine devam edemeyeceğini bildirir. Bu sırada denetim, zaman uyumsuz yönteminin arayanına döner.  
  
     Bir zaman uyumsuz yöntem ertelenmesi bir `Await` ifadesi yönteminden bir çıkış niteliğinde değildir ve `Finally` blokları çalıştırma.  
  
-   İşaretli zaman uyumsuz yöntem, kendisinin çağırdığı yöntemler tarafından bekleniyor olabilir.  
  
 Zaman uyumsuz yöntem genellikle bir veya daha fazla oluşumu içeren bir `Await` işleci ancak olmaması `Await` ifadeleri derleyici hatası neden değil. Zaman uyumsuz yöntem kullanmıyorsa bir `Await` bir askıya alma, yöntemi olarak işaretle işleci yürüten bir zaman uyumlu yöntemi yaptığı gibi rağmen `Async` değiştiricisi. Derleyici bu tür yöntemler için bir uyarı verir.  
  
 `Async` ve `Await` bağlamsal anahtar sözcükler. Daha fazla bilgi ve örnek için aşağıdaki konulara bakın:  
  
-   [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Dönüş türleri ve parametreleri  
 .NET Framework programlamada bir zaman uyumsuz yöntem genellikle döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Zaman uyumsuz yöntem içinde bir `Await` işleci, başka bir zaman uyumsuz yöntem çağrısından döndürülen bir görev için uygulanır.  
  
 Belirttiğiniz <xref:System.Threading.Tasks.Task%601> yöntemi içeriyorsa, dönüş türü olarak bir [dönmek](../../../../visual-basic/language-reference/statements/return-statement.md) tür işleneni belirtir deyimi `TResult`.  
  
 Kullandığınız `Task` yöntemin dönüş deyimi yok veya işleneni döndürmez bir dönüş ifadesi içeriyor, dönüş türü.  
  
 Aşağıdaki örnek, nasıl bildirme ve döndüren bir yöntem çağrısı gösterir bir <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.  
  
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
  
 Async yöntemi de olabilir bir `Sub` yöntemi. Bu dönüş türü, dönüş türü gerekli olduğu öncelikle olay işleyicileri tanımlamak için kullanılır. Zaman uyumsuz olay işleyicileri, genellikle zaman uyumsuz programlar için başlangıç noktası olarak hizmet eder.  
  
 Zaman uyumsuz yöntem bu bir `Sub` yordamı olamaz beklemenin ve arayan yöntemi atar tüm özel durumları yakalamak olamaz.  
  
 Async yöntemi bildiremezsiniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametreleri, ancak yöntem bu tür parametrelerine sahip yöntemleri çağırabilirsiniz.  
  
 Daha fazla bilgi ve örnekler için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Zaman uyumsuz yöntemleri özel durumlarını yakalama hakkında daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Windows çalışma zamanı programlama zaman uyumsuz API'leri görevlere benzer aşağıdaki dönüş türlerinden birini vardır:  
  
-   [IAsyncOperation](http://go.microsoft.com/fwlink/p/?LinkId=261896), hangi karşılık gelir <xref:System.Threading.Tasks.Task%601>  
  
-   [IAsyncAction](http://go.microsoft.com/fwlink/p/?LinkId=261897), hangi karşılık gelir <xref:System.Threading.Tasks.Task>  
  
-   [IAsyncActionWithProgress](http://go.microsoft.com/fwlink/p/?LinkId=261898)  
  
-   [IAsyncOperationWithProgress](http://go.microsoft.com/fwlink/p/?LinkID=259454)  
  
 Daha fazla bilgi ve bir örnek için bkz: [hızlı başlangıç: zaman uyumsuz programlama için bekleme işlecini kullanarak](http://go.microsoft.com/fwlink/p/?LinkId=248545).  
  
##  <a name="BKMK_NamingConvention"></a> Adlandırma kuralları  
 Kurala göre sahip yöntemleri adlarına "Zaman uyumsuz" append bir `Async` değiştiricisi.  
  
 Bir olay, taban sınıf veya arabirim sözleşmesi farklı bir ad öneriyorsa kuralı yoksayabilirsiniz. Örneğin, ortak olay işleyicileri gibi yeniden adlandırmadan döndürmemelidir `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> İlgili Konular ve örnekleri (Visual Studio)  
  
|Başlık|Açıklama|Örnek|  
|-----------|-----------------|------------|  
|[İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Zaman uyumlu bir WPF çözümünü zaman uyumsuz bir WPF çözümüne nasıl dönüştüreceğinizi gösterir. Uygulama bir dizi web sitesi indirir.|[Zaman uyumsuz örnek: Web gözden geçirme erişme](http://go.microsoft.com/fwlink/p/?LinkID=255191&clcid=0x409)|  
|[Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Ekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önceki kılavuzu için. Kullanımını `WhenAll` aynı anda tüm indirmeleri başlatır.||  
|[Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Nasıl aynı anda birkaç görevi başlatacağınızı gösterir.|[Zaman uyumsuz örnek: Birden çok Web isteğini paralel hale](http://go.microsoft.com/fwlink/p/?LinkID=254906&clcid=0x409)|  
|[Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Zaman uyumsuz yöntemlerin döndürebileceği türleri gösterir ve her türün ne zaman uygun olduğunu açıklar.||  
|[(Visual Basic) zaman uyumsuz programlarda denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Ayrıntılı olarak birbirini izleyenler aracılığıyla denetim akışını izler ve zaman uyumsuz bir program ifadesi bekler.|[Zaman uyumsuz örnek: Zaman uyumsuz programlarda denetim akışı](http://go.microsoft.com/fwlink/p/?LinkID=255285&clcid=0x409)|  
|[Async uygulamanızda (Visual Basic) hassas ayar yapma](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Zaman uyumsuz çözümünüze aşağıdaki işlevin nasıl ekleneceğini gösterir:<br /><br /> -   [Zaman uyumsuz görevi veya görev (Visual Basic) listesi iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Bir süre (Visual Basic) sonra zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Zaman uyumsuz örnek: İnce uygulamanızı ayarlama](http://go.microsoft.com/fwlink/p/?LinkID=255046&clcid=0x409)|  
|[(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Çalıştırıldığı sırada etkin bir zaman uyumsuz işlemin yeniden başlatıldığı durumların nasıl işleneceğini gösterir.||  
|[WhenAny: .NET Framework ve Windows çalışma zamanı arasında köprü oluşturma](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)|.NET Framework'teki görev türleri ve IAsyncOperations içinde arasında köprü gösterilmektedir [!INCLUDE[wrt](~/includes/wrt-md.md)] , kullanabilmesi için <xref:System.Threading.Tasks.Task.WhenAny%2A> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask ve WhenAny) arasında köprü oluşturma](http://go.microsoft.com/fwlink/p/?LinkID=260638)|  
|Zaman Uyumsuz İptal: .NET Framework ve Windows Çalışma Zamanı arasında köprü oluşturma|.NET Framework'teki görev türleri ve IAsyncOperations içinde arasında köprü gösterilmektedir [!INCLUDE[wrt](~/includes/wrt-md.md)] , kullanabilmesi için <xref:System.Threading.CancellationTokenSource> ile bir [!INCLUDE[wrt](~/includes/wrt-md.md)] yöntemi.|[Zaman uyumsuz örneği: .NET ve Windows çalışma zamanı (AsTask & İptal) arasında köprü oluşturma](http://go.microsoft.com/fwlink/p/?LinkId=263004)|  
|[(Visual Basic) dosya erişimi için Async kullanma](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Dosyalara erişmek için zaman uyumsuz yöntemin ve await işlecinin kullanılmasına ilişkin avantajları listeler ve gösterir.||  
|[Görev Tabanlı Zaman Uyumsuz Desen (TAP)](http://msdn.microsoft.com/library/8cef1fcf-6f9f-417c-b21f-3fd8bac75007)|.NET Framework'te zaman uyumsuzluk için yeni bir düzen açıklar. Desen dayanır <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> türleri.||  
|[Zaman uyumsuz videolar kanalda 9](http://go.microsoft.com/fwlink/p/?LinkID=267466)|Zaman uyumsuz programlama hakkında çeşitli videoların bağlantılarını sağlar.||  
  
##  <a name="BKMK_CompleteExample"></a> Tam örnek  
 Aşağıdaki kod, bu konuda ele alınmıştır Windows Presentation Foundation (WPF) uygulamadan MainWindow.xaml.vb dosyasıdır. Örnekten indirebilirsiniz [zaman uyumsuz örnek: "Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme" örnekten](http://go.microsoft.com/fwlink/p/?LinkID=261549).  
  
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
        Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)
