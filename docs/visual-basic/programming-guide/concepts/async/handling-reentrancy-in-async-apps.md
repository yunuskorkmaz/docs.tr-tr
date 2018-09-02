---
title: (Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: b633e3cf9a499cd5f364692cd0461aed640fe54d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401896"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="1b179-102">(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="1b179-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="1b179-103">Zaman uyumsuz kod uygulamanıza eklediğinizde, göz önünde bulundurun ve tamamlanmadan önce zaman uyumsuz bir işlem engellemelisiniz yeniden giriş muhtemelen önlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b179-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="1b179-104">Olasılıklarını tanımlamaz ve yönetmezseniz, beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b179-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="1b179-105">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="1b179-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="1b179-106">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="1b179-106">Recognizing Reentrancy</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="1b179-107">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="1b179-107">Handling Reentrancy</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="1b179-108">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="1b179-108">Disable the Start Button</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="1b179-109">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="1b179-109">Cancel and Restart the Operation</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="1b179-110">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="1b179-110">Run Multiple Operations and Queue the Output</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="1b179-111">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1b179-111">Reviewing and Running the Example App</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="1b179-112">Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b179-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="1b179-113">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="1b179-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="1b179-114">Bu konudaki örnekte, kullanıcıların seçim bir **Başlat** Web sitesi dizilerini indiren ve indirilen bayt toplam sayısını hesaplayan zaman uyumsuz bir uygulamayı başlatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="1b179-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="1b179-115">Zaman uyumlu bir sürümünü örneğin aynı şekilde bakılmaksızın İlk seferden sonra UI iş parçacığı bu olayları Uygulama çalışmayı sonlandırıncaya kadar yok sayar. çünkü, kaç kez bir kullanıcı düğmeyi yanıtlamayı ister.</span><span class="sxs-lookup"><span data-stu-id="1b179-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="1b179-116">Zaman uyumsuz bir uygulamada, ancak kullanıcı Arabirimi iş parçacığı yanıtlamaya devam eder ve zaman uyumsuz işlem tamamlanmadan önce yeniden.</span><span class="sxs-lookup"><span data-stu-id="1b179-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="1b179-117">Aşağıdaki örnek, beklenen gösterir. Kullanıcı seçtiğinde çıkış **Başlat** düğmesini yalnızca bir defa.</span><span class="sxs-lookup"><span data-stu-id="1b179-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="1b179-118">İndirilen Web sitelerinin bir listesiyle boyutunu bayt cinsinden her site görünür.</span><span class="sxs-lookup"><span data-stu-id="1b179-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="1b179-119">Toplam bayt sayısı sonda görünür.</span><span class="sxs-lookup"><span data-stu-id="1b179-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="1b179-120">Ancak kullanıcı düğmeyi birden fazla kez seçerse olay işleyicisi tekrarlanarak çağrılır ve indirme işlemini, her zaman reentered.</span><span class="sxs-lookup"><span data-stu-id="1b179-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="1b179-121">Sonuç olarak, birtakım zaman uyumsuz işlemler aynı anda çalışan, çıktı sonuçları karışır ve toplam bayt sayısı karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="1b179-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="1b179-122">Bu konunun sonuna kadar giderek bu çıkışı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b179-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="1b179-123">Çözümü yerel bilgisayarınıza indirerek ve WebsiteDownload proje çalıştırarak kodla denemeler yapın ya da daha fazla bilgi ve yönergeler için kendi projenizi oluşturmak için bu konunun sonunda kodu kullanma tarafından [ Gözden geçirme ve örnek uygulamayı çalıştırma](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="1b179-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="1b179-124">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="1b179-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="1b179-125">Yolu, uygulamanızı yapmak için istediğinize bağlı olarak çeşitli yollardan yeniden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b179-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="1b179-126">Bu konu aşağıdaki örnekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="1b179-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="1b179-127">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="1b179-127">Disable the Start Button</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="1b179-128">Devre dışı **Başlat** böylece kullanıcı, kesme işlemi devam ederken düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1b179-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="1b179-129">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="1b179-129">Cancel and Restart the Operation</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="1b179-130">Kullanıcı seçtiğinde devam eden tüm işlemleri iptal **Başlat** yeniden düğmesini ve ardından let en son İstenen işleme devam edin.</span><span class="sxs-lookup"><span data-stu-id="1b179-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="1b179-131">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="1b179-131">Run Multiple Operations and Queue the Output</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="1b179-132">Tüm istenen işlemlerin zaman uyumsuz olarak çalışır, ancak çıktı görünümünü koordine edecek her işlemin sonuçları birlikte ve sıralı görünür izin verir.</span><span class="sxs-lookup"><span data-stu-id="1b179-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="1b179-133">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="1b179-133">Disable the Start Button</span></span>  
 <span data-ttu-id="1b179-134">Engelleyebilirsiniz **Başlat** en üstündeki düğmesini devre dışı bırakarak işlem çalışırken `StartButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1b179-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="1b179-135">İçinden düğmeyi ardından etkinleştirebileceğiniz bir `Finally` böylece kullanıcılar uygulamayı yeniden çalıştırabilir işlem tamamlandığında engelleyin.</span><span class="sxs-lookup"><span data-stu-id="1b179-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="1b179-136">Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b179-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="1b179-137">Bu konunun sonunda kodu değişiklikleri ekleyebilir veya bitmiş uygulamayı indirebilirsiniz [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="1b179-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="1b179-138">Proje adı disablestartbutton.</span><span class="sxs-lookup"><span data-stu-id="1b179-138">The project name is DisableStartButton.</span></span>  
  
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
  
 <span data-ttu-id="1b179-139">Değişikliklerin bir sonucu olarak düğme yanıt vermiyor ancak `AccessTheWebAsync` işlem reentered şekilde Web siteleri yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="1b179-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="1b179-140">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="1b179-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="1b179-141">Devre dışı bırakmak yerine **Başlat** düğmesini kullanabilirsiniz düğmeyi etkin tutabilirsiniz ancak, kullanıcı yeniden bu düğmeyi seçerse, zaten çalışıyor ve en son başlatılan işlemin devam izin işlemi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="1b179-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="1b179-142">İptal işlemleri hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="1b179-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="1b179-143">Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="1b179-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="1b179-144">Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="1b179-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="1b179-145">Bu projenin adı CancelAndRestart'tır.</span><span class="sxs-lookup"><span data-stu-id="1b179-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="1b179-146">Bildirme bir <xref:System.Threading.CancellationTokenSource> değişken `cts`, tüm yöntemler için kapsam dahilinde olan.</span><span class="sxs-lookup"><span data-stu-id="1b179-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="1b179-147">İçinde `StartButton_Click`, bir işlemin zaten çalışıp çalışmadığını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1b179-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="1b179-148">Varsa değerini `cts` olduğu `Nothing`, hiçbir işlem zaten etkin.</span><span class="sxs-lookup"><span data-stu-id="1b179-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="1b179-149">Değer yoksa `Nothing`, zaten çalışan işlemi iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1b179-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="1b179-150">Ayarlama `cts` geçerli işlemi temsil eden farklı bir değer.</span><span class="sxs-lookup"><span data-stu-id="1b179-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="1b179-151">Sonunda `StartButton_Click`, geçerli işlem tamamlanır, bu nedenle ayarlayın `cts` geri `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1b179-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="1b179-152">Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="1b179-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="1b179-153">Eklentiler yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="1b179-153">The additions are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="1b179-154">İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="1b179-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="1b179-155">Öğesinden iptal belirtecini kabul etmek için bir parametre ekleyin `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="1b179-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="1b179-156">Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> ettiğinden Web sitelerini indirmek için yöntemi `GetAsync` kabul eden bir <xref:System.Threading.CancellationToken> bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="1b179-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="1b179-157">Çağırmadan önce `DisplayResults` her indirilebilir Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlemi iptal edildiğini doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="1b179-158">Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b179-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="1b179-159">Seçerseniz **Başlat** düğmesine birkaç kez bu uygulama çalışırken aşağıdaki çıktıya benzer sonuçlar üretmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b179-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="1b179-160">Kısmi listelerini ortadan kaldırmak için ilk kod satırı açıklamadan çıkarın `StartButton_Click` kullanıcı her zaman metin kutusunu temizlemek için işlemi yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="1b179-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="1b179-161">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="1b179-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="1b179-162">Başka bir zaman uyumsuz işlemi kullanıcı her zaman uygulama başlatır, bu üçüncü örnek en karmaşık örnektir **Başlat** düğmesi ve tüm işlemler tamamlanmak üzere çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="1b179-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="1b179-163">Listeden Web siteleri tüm istenen işlemler zaman uyumsuz olarak yükleyin, ancak çıkış işlemlerden çıktılar ardışık olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="1b179-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="1b179-164">Diğer bir deyişle, gerçek indirme etkinliği, deki çıkışın gösterdiği gibi aralanmıştır [yeniden giriş tanıma](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) gösterir, ancak her grup için sonuçların listesi ayrı ayrı sunulur.</span><span class="sxs-lookup"><span data-stu-id="1b179-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="1b179-165">İşlemleri genel paylaşım <xref:System.Threading.Tasks.Task>, `pendingWork`, görüntüleme işlemi için bir ağ geçidi olarak görev gören.</span><span class="sxs-lookup"><span data-stu-id="1b179-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="1b179-166">Bu örnek koda değişiklikleri yapıştırarak çalıştırabilirsiniz [uygulama](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri takip edebilirsiniz [uygulamayı indirmeye](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirip QueueResults projesini'ı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-166">You can run this example by pasting the changes into the code in [Building the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="1b179-167">Aşağıdaki çıktı, kullanıcı seçtiğinde görülecek sonucu gösterir **Başlat** düğmesini yalnızca bir defa.</span><span class="sxs-lookup"><span data-stu-id="1b179-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="1b179-168">Harf etiketi A, sonucun ilk kez gösterir **Başlat** düğmesi seçilir.</span><span class="sxs-lookup"><span data-stu-id="1b179-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="1b179-169">Sayılar, yükleme hedefleri listesinde URL'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b179-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="1b179-170">Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulama aşağıdaki satırlara benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="1b179-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="1b179-171">Bir kare ile başlayan bilgi satırları uygulamanın ilerleyişini (#) izleme oturum açın.</span><span class="sxs-lookup"><span data-stu-id="1b179-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="1b179-172">Grup A tamamlanmadan, ancak her grubun çıktısı ayrı görünür önce Grup B ve C başlatın.</span><span class="sxs-lookup"><span data-stu-id="1b179-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="1b179-173">Grup A için çıktıların tamamı ardından Grup B için çıktıların tamamı ve sonra tüm çıkış grubu c için ilk olarak, görünür Uygulama her zaman sırayla grupları görüntüler ve her bir grup için her zaman URL'leri URL'lerin listesinde görüntülenen sırayla tek tek Web siteleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b179-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="1b179-174">Ancak, hangi indirmelerin gerçekte olduğu sırayı tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b179-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="1b179-175">Birden çok grup başlattıktan sonra oluşturdukları indirme görevlerinin tamamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="1b179-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="1b179-176">Bu A-1 varsayamazsınız önce B-1 indirilir ve bu A-1 varsayamazsınız A-2 önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1b179-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="1b179-177">Genel tanımlar</span><span class="sxs-lookup"><span data-stu-id="1b179-177">Global Definitions</span></span>  
 <span data-ttu-id="1b179-178">Örnek kod, tüm yöntemlerden görünen aşağıdaki iki genel bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="1b179-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="1b179-179">`Task` Değişken `pendingWork`, görüntüleme işlemini kesmesini ve herhangi bir grubu başka bir grubun görünen çalışmasını önler.</span><span class="sxs-lookup"><span data-stu-id="1b179-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="1b179-180">Karakter değişkeni `group`, sonuçların beklenen sırada göründüğünü doğrulamak üzere farklı gruplardan çıkış etiketler.</span><span class="sxs-lookup"><span data-stu-id="1b179-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="1b179-181">Tıklama olayı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="1b179-181">The Click Event Handler</span></span>  
 <span data-ttu-id="1b179-182">Olay işleyicisi `StartButton_Click`, her zaman kullanıcı Grup harfini artırır **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1b179-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="1b179-183">Ardından işleyici çağrıları `AccessTheWebAsync` indirme işlemini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
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
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="1b179-184">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b179-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="1b179-185">Bu örnekte böler `AccessTheWebAsync` öğesini iki yöntem.</span><span class="sxs-lookup"><span data-stu-id="1b179-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="1b179-186">İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve ayarlar `pendingWork` görüntüleme işlemini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="1b179-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="1b179-187">Yöntemi, bir dil ile tümleşik sorgu (LINQ sorgusu) kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> tüm indirme görevlerini aynı anda başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="1b179-188">`AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her İndirmenin tamamlanmasını beklemek ve uzunluğunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="1b179-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="1b179-189">`FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="1b179-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="1b179-190">Değeri, görev önce başka bir işlem tarafından kesintiye engellediğini tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b179-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
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
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="1b179-191">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b179-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="1b179-192">Bu yöntemi izleyerek her birini bekler, karşıdan yüklenen Web sitesi uzunluğunu görüntülemek ve uzunluğu toplama ekleme bir gruptaki indirme görevlerini aracılığıyla geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="1b179-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="1b179-193">İlk deyimde `FinishOneGroupAsync` kullanan `pendingWork` yöntemin girilmesinin zaten içinde görüntüleme işlemini veya beklemede bir işlemle çakışmamasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="1b179-194">Bu tür bir işlem sürüyorsa, giriş işlemi kendi sırasını beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="1b179-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
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
  
 <span data-ttu-id="1b179-195">Bu örnek koda değişiklikleri yapıştırarak çalıştırabilirsiniz [uygulama](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri takip edebilirsiniz [uygulamayı indirmeye](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirip QueueResults projesini'ı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1b179-195">You can run this example by pasting the changes into the code in [Building the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="1b179-196">İlgi noktaları</span><span class="sxs-lookup"><span data-stu-id="1b179-196">Points of Interest</span></span>  
 <span data-ttu-id="1b179-197">Çıktıda pound işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklamak.</span><span class="sxs-lookup"><span data-stu-id="1b179-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="1b179-198">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b179-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="1b179-199">Bir grubu, bir önceki Grup çıktıyı görüntülerken, ancak görüntü önceki grubun çıktı görünümü kesintiye başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b179-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="1b179-200">`pendingWork` Görev `Nothing` başlangıcında `FinishOneGroupAsync` Grup A için yalnızca ilk başlayan a.</span><span class="sxs-lookup"><span data-stu-id="1b179-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="1b179-201">Grup A taşınmadığından henüz tamamlanmamış bir await deyimindeki ulaştığında `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="1b179-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="1b179-202">Bu nedenle, Denetim öğesine dönmemiştir `AccessTheWebAsync`ve ilk atamaya `pendingWork` oluşmamıştır.</span><span class="sxs-lookup"><span data-stu-id="1b179-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="1b179-203">Her zaman aşağıdaki iki satır çıktıda birlikte görünür.</span><span class="sxs-lookup"><span data-stu-id="1b179-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="1b179-204">Kod bir grubun çalışmasını başlatma arasında hiçbir zaman kesintiye `StartButton_Click` ve grubun bir görev atama `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="1b179-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="1b179-205">Bir grubu girdikten sonra `StartButton_Click`, işlemi işlemi girinceye kadar await ifadesini tamamlamaz değil `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="1b179-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="1b179-206">Bu nedenle, başka bir işlem sırasında kod kesiminin denetimi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b179-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="1b179-207">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1b179-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="1b179-208">Örnek uygulamayı daha iyi anlamak için indirin, kendiniz derleyebilir veya uygulamayı gerçekleştirmeden, bu konunun sonunda kodu gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="1b179-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b179-209">Bir veya daha yeni bilgisayarınızda yüklü örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b179-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="1b179-210">Uygulamayı karşıdan yükleme</span><span class="sxs-lookup"><span data-stu-id="1b179-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="1b179-211">Sıkıştırılmış dosyayı indirin [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="1b179-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="1b179-212">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1b179-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="1b179-213">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="1b179-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="1b179-214">Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1b179-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="1b179-215">İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz projenin kısayol menüsünü **StartUpProject olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="1b179-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="1b179-216">Oluşturun ve projeyi çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="1b179-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="1b179-217">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b179-217">Building the App</span></span>  
 <span data-ttu-id="1b179-218">Aşağıdaki bölümde, örnek bir WPF uygulaması olarak oluşturmak için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b179-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="1b179-219">Bir WPF uygulaması derlemek için</span><span class="sxs-lookup"><span data-stu-id="1b179-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="1b179-220">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1b179-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1b179-221">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="1b179-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="1b179-222">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="1b179-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1b179-223">İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="1b179-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="1b179-224">Proje türleri listesinde seçin **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="1b179-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="1b179-225">Projeyi adlandırın `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1b179-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="1b179-226">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1b179-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="1b179-227">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1b179-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="1b179-228">Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="1b179-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="1b179-229">İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1b179-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="1b179-230">Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="1b179-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="1b179-231">İçin bir başvuru eklemeniz <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="1b179-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="1b179-232">İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="1b179-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="1b179-233">MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1b179-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
  
11. <span data-ttu-id="1b179-234">Programı çalıştırın ve ardından CTRL + F5 tuşlarına basın **Başlat** düğmesine birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="1b179-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="1b179-235">Değişikliklerini yapın [Başlat düğmesini devre dışı](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [iptal edip işlemi yeniden](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya [birden çok işlemi çalıştırın ve çıktıyı sıraya](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) yeniden giriş işlemek için.</span><span class="sxs-lookup"><span data-stu-id="1b179-235">Make the changes from [Disable the Start Button](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b179-236">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b179-236">See Also</span></span>  
 [<span data-ttu-id="1b179-237">İzlenecek yol: Async kullanarak Web'e erişme ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b179-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="1b179-238">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b179-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
