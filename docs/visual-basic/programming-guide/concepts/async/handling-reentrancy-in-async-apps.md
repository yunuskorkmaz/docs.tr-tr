---
title: (Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c2f80eb8a0fbc655143ca02ead5f6f46f102918
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="358ba-102">(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="358ba-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="358ba-103">Zaman uyumsuz kodu, uygulamanızda eklediğinizde göz önünde bulundurun ve büyük olasılıkla, tamamlanmadan önce zaman uyumsuz bir işlem yeniden girme için başvuruyor yeniden giriş önlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="358ba-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="358ba-104">Tanımlamak ve yeniden giriş olasılıklarını işlemek yok, beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="358ba-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="358ba-105">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="358ba-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="358ba-106">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="358ba-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="358ba-107">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="358ba-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="358ba-108">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="358ba-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="358ba-109">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="358ba-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="358ba-110">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="358ba-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="358ba-111">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="358ba-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="358ba-112">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="358ba-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="358ba-113">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="358ba-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="358ba-114">Bu konudaki örnek kullanıcıları seçin bir **Başlat** bir dizi Web siteleri yükler ve yüklenen bayt sayısı toplam hesaplar zaman uyumsuz bir uygulamayı başlatmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="358ba-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="358ba-115">Örnek zaman uyumlu bir sürümü aynı şekilde bakılmaksızın ilk kez sonra kullanıcı Arabirimi iş parçacığı çalışan uygulama sonlanana kadar bu olayları yoksayar çünkü kaç kez bir kullanıcı düğmesini seçer. yanıt.</span><span class="sxs-lookup"><span data-stu-id="358ba-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="358ba-116">Zaman uyumsuz bir uygulamada ancak, kullanıcı Arabirimi iş parçacığı yanıt vermeye devam eder ve onu tamamlanmadan önce zaman uyumsuz işlemi yeniden girmeniz.</span><span class="sxs-lookup"><span data-stu-id="358ba-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="358ba-117">Aşağıdaki örnek, beklenen gösterir kullanıcı seçtiğinde çıktı **Başlat** yalnızca bir kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="358ba-118">Her sitenin bayt cinsinden boyutu ile indirilen Web siteleri listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="358ba-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="358ba-119">Toplam bayt sayısı sonunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="358ba-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="358ba-120">Ancak, kullanıcı düğmesi birden çok kez seçerse, olay işleyici tekrar çağrılır ve indirme işlemini her seferinde reentered.</span><span class="sxs-lookup"><span data-stu-id="358ba-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="358ba-121">Sonuç olarak, birkaç zaman uyumsuz işlemler aynı anda çalıştırıyorsanız, çıktısı sonuçlara interleaves ve toplam bayt sayısı karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="358ba-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="358ba-122">Bu konuda sonuna kaydırarak bu çıkışı üretir kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358ba-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="358ba-123">Yerel bilgisayarınıza çözümü indirme ve WebsiteDownload proje çalıştıran koduyla denemek ya da daha fazla bilgi ve yönergeler için kendi projesi oluşturmak için bu konunun sonunda kodu kullanarak tarafından bkz [ Gözden geçirme ve örnek uygulamayı çalıştıran](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="358ba-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="358ba-124">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="358ba-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="358ba-125">Yeniden giriş yapmak için uygulamanızın istediğinize bağlı olarak yolları, çeşitli işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="358ba-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="358ba-126">Bu konuda aşağıdaki örnekler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="358ba-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="358ba-127">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="358ba-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="358ba-128">Devre dışı **Başlat** böylece kullanıcı onu kesme işlemi çalışırken düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="358ba-129">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="358ba-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="358ba-130">Kullanıcı seçtiğinde hala çalıştıran herhangi bir işlem iptal **Başlat** yeniden düğmesine ve ardından let en yakın zamanda istenen işlem devam edin.</span><span class="sxs-lookup"><span data-stu-id="358ba-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="358ba-131">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="358ba-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="358ba-132">Tüm işlemlerini zaman uyumsuz olarak çalıştırın, ancak her işlemi sonuçlarından birlikte ve sırada görünmesini sağlayacak şekilde çıkış görüntüsünü koordine etmek için istenen izin verir.</span><span class="sxs-lookup"><span data-stu-id="358ba-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="358ba-133">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="358ba-133">Disable the Start Button</span></span>  
 <span data-ttu-id="358ba-134">Engelleyebilir **Başlat** en üstündeki düğmesi devre dışı bırakarak bir işlem devam ederken düğmesini `StartButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="358ba-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="358ba-135">İçinden düğmesini sonra etkinleştirebileceğiniz bir `Finally` engelleme kullanıcıların uygulamayı yeniden çalıştırabilmeniz için işlem sona erdiğinde.</span><span class="sxs-lookup"><span data-stu-id="358ba-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="358ba-136">Aşağıdaki kod yıldız işaretiyle işaretli bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358ba-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="358ba-137">Bu konunun sonunda kod değişiklikleri ekleyebilirsiniz veya tamamlanmış uygulamadan indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="358ba-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="358ba-138">Proje adı DisableStartButton ' dir.</span><span class="sxs-lookup"><span data-stu-id="358ba-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="358ba-139">Değişikliklerin sonucu olarak, düğme yanıt vermiyor sırada `AccessTheWebAsync` işlemi girilmesi edilemez şekilde Web siteleri yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="358ba-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="358ba-140">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="358ba-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="358ba-141">Devre dışı bırakma yerine **Başlat** düğmesini kullanabilirsiniz düğmesi etkin tutmak ancak, kullanıcı bu düğme yeniden seçerse zaten çalışan ve en son başlatılan işlemin devam etmesine izin vermek işlemi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="358ba-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="358ba-142">İptal etme hakkında daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="358ba-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="358ba-143">Bu senaryonun kurulumunu yapmak için aşağıdaki sağlanan temel kod değişiklik [gözden geçirme ve örnek uygulamayı çalıştıran](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="358ba-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="358ba-144">Tamamlanan uygulama aynı zamanda indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="358ba-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="358ba-145">Bu proje CancelAndRestart adıdır.</span><span class="sxs-lookup"><span data-stu-id="358ba-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="358ba-146">Bildirme bir <xref:System.Threading.CancellationTokenSource> değişkeni, `cts`, kapsamdaki tüm yöntemleri için olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="358ba-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="358ba-147">İçinde `StartButton_Click`, bir işlemi zaten devam ettiğinden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="358ba-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="358ba-148">Varsa değerini `cts` olan `Nothing`, hiçbir işlem zaten etkin.</span><span class="sxs-lookup"><span data-stu-id="358ba-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="358ba-149">Değer yoksa `Nothing`, zaten çalışıyor işlemi iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="358ba-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="358ba-150">Ayarlama `cts` için geçerli işlem temsil eden farklı bir değer.</span><span class="sxs-lookup"><span data-stu-id="358ba-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="358ba-151">Sonunda `StartButton_Click`, geçerli işlemi tamamlandığında, böylece değerini ayarlayın `cts` geri `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="358ba-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="358ba-152">Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="358ba-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="358ba-153">Eklemeleri yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="358ba-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="358ba-154">İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="358ba-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="358ba-155">Gelen iptal belirteci kabul etmek için bir parametre eklemek `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="358ba-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="358ba-156">Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> çünkü Web sitelerini yüklemeye yöntemi `GetAsync` kabul bir <xref:System.Threading.CancellationToken> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="358ba-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="358ba-157">Çağırmadan önce `DisplayResults` indirilen her Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlem iptal edildi değiştirilmediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="358ba-158">Aşağıdaki kod yıldız işaretiyle işaretli bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358ba-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="358ba-159">Seçerseniz **Başlat** birkaç kez düğmesini bu uygulama çalışırken, aşağıdaki çıkış benzer sonuçlar üretmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="358ba-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="358ba-160">Kısmi listeleri ortadan kaldırmak için ilk kod satırı açıklamadan kaldırmasına `StartButton_Click` kullanıcı işlemi yeniden her zaman metin kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="358ba-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="358ba-161">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="358ba-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="358ba-162">Uygulama başka bir zaman uyumsuz işlemi kullanıcının seçtiği her zaman başlatır, bu üçüncü en karmaşık örneğidir **Başlat** düğmesi ve tüm işlemleri tamamlanıncaya kadar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="358ba-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="358ba-163">Listeden Web sitelerini istenen tüm işlemleri zaman uyumsuz olarak indirebilir, ancak işlem çıkışı sıralı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="358ba-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="358ba-164">Diğer bir deyişle, gerçek indirme etkinliği, çıktı olarak araya eklemeli [algılamayı yeniden giriş](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) gösterir, ancak her grup için sonuçlardan sunulur ayrı olarak.</span><span class="sxs-lookup"><span data-stu-id="358ba-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="358ba-165">Operations genel paylaşmak <xref:System.Threading.Tasks.Task>, `pendingWork`, hangi görüntü işlemi için bir ağ geçidi olarak hizmet verir.</span><span class="sxs-lookup"><span data-stu-id="358ba-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="358ba-166">Bu örnek kodda içine değişiklikleri yapıştırılarak çalıştırabilirsiniz [uygulaması oluşturmaya](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri izleyin [uygulaması indiriliyor](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirmek ve ardından QueueResults proje çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="358ba-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="358ba-167">Kullanıcı seçtiğinde sonuç aşağıdaki çıktı gösterir **Başlat** yalnızca bir kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="358ba-168">Harf etiketi, A, sonuç ilk saati gösterir **Başlat** düğmesi seçilidir.</span><span class="sxs-lookup"><span data-stu-id="358ba-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="358ba-169">Sayıları URL'leri sırasını indirme hedefler listesinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="358ba-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="358ba-170">Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulamanın aşağıdaki satırları benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="358ba-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="358ba-171">Kare ile başlayan bilgi satırları (#) izleme uygulama ilerlemesini oturum açın.</span><span class="sxs-lookup"><span data-stu-id="358ba-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="358ba-172">Grup B ve C gruba tamamlandı, ancak her grup için çıktı ayrı olarak görünür önce başlatın.</span><span class="sxs-lookup"><span data-stu-id="358ba-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="358ba-173">Grup a tüm çıktı ardından B grubu için tüm çıkış ve ardından tüm çıktı grubu c için ilk olarak, görünür Uygulama her zaman sıraya göre grupları görüntüler ve her grup için her zaman tek tek Web siteleri hakkında bilgi URL'leri URL'leri listede sırada görüntüler.</span><span class="sxs-lookup"><span data-stu-id="358ba-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="358ba-174">Ancak, indirmeleri gerçekten durum meydana sipariş tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="358ba-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="358ba-175">Birden çok grubu başlatıldıktan sonra oluşturdukları indirme tüm etkin görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="358ba-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="358ba-176">Bu A-1 varsayın olamaz B-1 önce indirilir ve o A-1 varsayın olamaz A-2 önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="358ba-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="358ba-177">Genel tanımları</span><span class="sxs-lookup"><span data-stu-id="358ba-177">Global Definitions</span></span>  
 <span data-ttu-id="358ba-178">Örnek kod tüm yöntemleri görünür olan aşağıdaki iki genel bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="358ba-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="358ba-179">`Task` Değişkeni `pendingWork`, görüntüleme işlemini denetleyen ve herhangi bir grubu başka bir grubun görüntü işlemi önler.</span><span class="sxs-lookup"><span data-stu-id="358ba-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="358ba-180">Karakter değişkeni `group`, sonuçları beklenen sırada göründüğünü doğrulamak için farklı gruplar çıktısını etiketler.</span><span class="sxs-lookup"><span data-stu-id="358ba-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="358ba-181">Click olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="358ba-181">The Click Event Handler</span></span>  
 <span data-ttu-id="358ba-182">Olay işleyicisi `StartButton_Click`, kullanıcının seçtiği her defasında grup harf artırır **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="358ba-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="358ba-183">Ardından işleyicisi çağrılarını `AccessTheWebAsync` indirme işlemi çalıştıramadı.</span><span class="sxs-lookup"><span data-stu-id="358ba-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="358ba-184">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="358ba-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="358ba-185">Bu örnek böler `AccessTheWebAsync` iki yöntemlerde.</span><span class="sxs-lookup"><span data-stu-id="358ba-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="358ba-186">İlk yöntem `AccessTheWebAsync`, bir grup için tüm yükleme görevleri başlatır ve ayarlayan `pendingWork` görüntüleme işlemini kontrol eden.</span><span class="sxs-lookup"><span data-stu-id="358ba-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="358ba-187">Bir dil ile tümleşik sorgu (LINQ sorgusu) yöntemini kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> aynı anda tüm yükleme görevleri başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="358ba-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="358ba-188">`AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her indirme tamamlanmasını bekler ve uzunluğu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="358ba-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="358ba-189">`FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="358ba-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="358ba-190">Görev tamamlanmadan önce değer kesinti başka bir işlem tarafından engellediğini.</span><span class="sxs-lookup"><span data-stu-id="358ba-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="358ba-191">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="358ba-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="358ba-192">Bu yöntem, gruptaki her biri bekleniyor, indirilen Web sitesi uzunluğu görüntüleyerek ve toplam uzunluğu ekleyerek, indirme görevleri boyunca geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="358ba-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="358ba-193">İlk ifade, `FinishOneGroupAsync` kullanan `pendingWork` yöntemi girme zaten görüntü işleminde veya, zaten bekleyen bir işlem ile engellemez emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="358ba-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="358ba-194">Böyle bir işlem devam ediyor, kendi dönüş girme işlemi beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="358ba-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="358ba-195">Bu örnek kodda içine değişiklikleri yapıştırılarak çalıştırabilirsiniz [uygulaması oluşturmaya](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri izleyin [uygulaması indiriliyor](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirmek ve ardından QueueResults proje çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="358ba-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="358ba-196">İlgilenilen noktaları</span><span class="sxs-lookup"><span data-stu-id="358ba-196">Points of Interest</span></span>  
 <span data-ttu-id="358ba-197">Bu örnek nasıl çalıştığını çıktıda pound işareti (#) ile başlayan bilgi satırları açıklayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="358ba-198">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358ba-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="358ba-199">Bir grup, bir önceki Grup çıktısını görüntüleme, ancak önceki grubun çıkış görüntüsünü kesintiye değil başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="358ba-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="358ba-200">`pendingWork` Görev `Nothing` başlangıcında `FinishOneGroupAsync` yalnızca Grup A, başlatılan ilk.</span><span class="sxs-lookup"><span data-stu-id="358ba-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="358ba-201">Grup A kurmadı henüz tamamlanmamış bir bekleme ifade ulaştığında `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="358ba-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="358ba-202">Bu nedenle, denetim için döndürülen kurmadı `AccessTheWebAsync`ve ilk atama `pendingWork` oluştu kurmadı.</span><span class="sxs-lookup"><span data-stu-id="358ba-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="358ba-203">Aşağıdaki iki satırı birlikte her zaman çıkışında görünür.</span><span class="sxs-lookup"><span data-stu-id="358ba-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="358ba-204">Kod bir grubun işlemi başlatılıyor arasında hiçbir zaman kesintiye `StartButton_Click` ve bir görev için grubunun atama `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="358ba-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="358ba-205">Bir grup girdikten sonra `StartButton_Click`, işlemi işlemi girene kadar bir bekleme ifade işlemini tamamlamazsa `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="358ba-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="358ba-206">Bu nedenle, başka bir işlem denetimi, kod kesimi sırasında kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="358ba-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="358ba-207">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="358ba-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="358ba-208">Örnek uygulama daha iyi anlamak için indirir, kendiniz oluşturabilir veya uygulama uygulamadan bu konunun sonunda kodu gözden.</span><span class="sxs-lookup"><span data-stu-id="358ba-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="358ba-209">Örnek bir Windows Presentation Foundation (WPF) masaüstü uygulaması çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="358ba-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="358ba-210">Uygulama indiriliyor</span><span class="sxs-lookup"><span data-stu-id="358ba-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="358ba-211">Sıkıştırılmış dosya indirme [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="358ba-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="358ba-212">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="358ba-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="358ba-213">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="358ba-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="358ba-214">Açılmış örnek kodu içeren klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="358ba-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="358ba-215">İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz proje için kısayol menüsünü açın **StartUpProject ayarlamak**.</span><span class="sxs-lookup"><span data-stu-id="358ba-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="358ba-216">CTRL + F5 anahtarları projesini derlemeyi ve çalıştırmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="358ba-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="358ba-217">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="358ba-217">Building the App</span></span>  
 <span data-ttu-id="358ba-218">Aşağıdaki bölümde, örnek olarak bir WPF uygulaması oluşturmak için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="358ba-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="358ba-219">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="358ba-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="358ba-220">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="358ba-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="358ba-221">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="358ba-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="358ba-222">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="358ba-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="358ba-223">İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**, genişletin ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="358ba-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="358ba-224">Proje türleri listesinden seçip **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="358ba-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="358ba-225">Proje adı `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="358ba-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="358ba-226">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="358ba-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="358ba-227">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="358ba-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="358ba-228">Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="358ba-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="358ba-229">İçinde **XAML** görüntülemek MainWindow.xaml, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="358ba-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="358ba-230">Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="358ba-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="358ba-231">İçin bir başvuru ekleyin <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="358ba-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="358ba-232">İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="358ba-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="358ba-233">MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="358ba-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="358ba-234">Programını çalıştırın ve ardından seçmek için CTRL + F5 anahtarlar **Başlat** birkaç kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="358ba-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="358ba-235">Öğesinden değişiklikler yapmak [Başlat düğmesi devre dışı](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [iptal edin ve işlemi yeniden](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya [birden çok işlemler çalıştırın ve çıkış sırası](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) yeniden giriş işlemek için.</span><span class="sxs-lookup"><span data-stu-id="358ba-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358ba-236">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="358ba-236">See Also</span></span>  
 [<span data-ttu-id="358ba-237">İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="358ba-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="358ba-238">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="358ba-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
