---
title: (C#) zaman uyumsuz uygulamalarda yeniden girişi işleme
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: c641c217b01e820e9a68065b0a56277a656ccc25
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034474"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="19602-102">(C#) zaman uyumsuz uygulamalarda yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="19602-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="19602-103">Zaman uyumsuz kod uygulamanıza eklediğinizde, göz önünde bulundurun ve tamamlanmadan önce zaman uyumsuz bir işlem engellemelisiniz yeniden giriş muhtemelen önlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="19602-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="19602-104">Olasılıklarını tanımlamaz ve yönetmezseniz, beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="19602-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="19602-105">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="19602-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="19602-106">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="19602-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="19602-107">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="19602-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="19602-108">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="19602-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="19602-109">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="19602-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="19602-110">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="19602-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="19602-111">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="19602-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="19602-112">Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19602-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="19602-113">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="19602-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="19602-114">Bu konudaki örnekte, kullanıcıların seçim bir **Başlat** Web sitesi dizilerini indiren ve indirilen bayt toplam sayısını hesaplayan zaman uyumsuz bir uygulamayı başlatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="19602-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="19602-115">Zaman uyumlu bir sürümünü örneğin aynı şekilde bakılmaksızın İlk seferden sonra UI iş parçacığı bu olayları Uygulama çalışmayı sonlandırıncaya kadar yok sayar. çünkü, kaç kez bir kullanıcı düğmeyi yanıtlamayı ister.</span><span class="sxs-lookup"><span data-stu-id="19602-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="19602-116">Zaman uyumsuz bir uygulamada, ancak kullanıcı Arabirimi iş parçacığı yanıtlamaya devam eder ve zaman uyumsuz işlem tamamlanmadan önce yeniden.</span><span class="sxs-lookup"><span data-stu-id="19602-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="19602-117">Aşağıdaki örnek, beklenen gösterir. Kullanıcı seçtiğinde çıkış **Başlat** düğmesini yalnızca bir defa.</span><span class="sxs-lookup"><span data-stu-id="19602-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="19602-118">İndirilen Web sitelerinin bir listesiyle boyutunu bayt cinsinden her site görünür.</span><span class="sxs-lookup"><span data-stu-id="19602-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="19602-119">Toplam bayt sayısı sonda görünür.</span><span class="sxs-lookup"><span data-stu-id="19602-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="19602-120">Ancak kullanıcı düğmeyi birden fazla kez seçerse olay işleyicisi tekrarlanarak çağrılır ve indirme işlemini, her zaman reentered.</span><span class="sxs-lookup"><span data-stu-id="19602-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="19602-121">Sonuç olarak, birtakım zaman uyumsuz işlemler aynı anda çalışan, çıktı sonuçları karışır ve toplam bayt sayısı karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="19602-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="19602-122">Bu konunun sonuna kadar giderek bu çıkışı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19602-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="19602-123">Çözümü yerel bilgisayarınıza indirip WebsiteDownload projeyi daha sonra çalışan veya kendi projenizi oluşturmak için bu konunun sonunda kodu kullanarak kodla denemeler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19602-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="19602-124">Daha fazla bilgi ve yönergeler için bkz. [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="19602-124">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="19602-125">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="19602-125">Handling Reentrancy</span></span>  
 <span data-ttu-id="19602-126">Yolu, uygulamanızı yapmak için istediğinize bağlı olarak çeşitli yollardan yeniden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19602-126">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="19602-127">Bu konu aşağıdaki örnekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="19602-127">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="19602-128">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="19602-128">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="19602-129">Devre dışı **Başlat** böylece kullanıcı, kesme işlemi devam ederken düğmesi.</span><span class="sxs-lookup"><span data-stu-id="19602-129">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="19602-130">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="19602-130">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="19602-131">Kullanıcı seçtiğinde devam eden tüm işlemleri iptal **Başlat** yeniden düğmesini ve ardından let en son İstenen işleme devam edin.</span><span class="sxs-lookup"><span data-stu-id="19602-131">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="19602-132">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="19602-132">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="19602-133">Tüm istenen işlemlerin zaman uyumsuz olarak çalışır, ancak çıktı görünümünü koordine edecek her işlemin sonuçları birlikte ve sıralı görünür izin verir.</span><span class="sxs-lookup"><span data-stu-id="19602-133">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="19602-134">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="19602-134">Disable the Start Button</span></span>  
 <span data-ttu-id="19602-135">Engelleyebilirsiniz **Başlat** en üstündeki düğmesini devre dışı bırakarak işlem çalışırken `StartButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="19602-135">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="19602-136">İçinden düğmeyi ardından etkinleştirebileceğiniz bir `finally` böylece kullanıcılar uygulamayı yeniden çalıştırabilir işlem tamamlandığında engelleyin.</span><span class="sxs-lookup"><span data-stu-id="19602-136">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="19602-137">Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="19602-137">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="19602-138">Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="19602-138">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="19602-139">Proje adı disablestartbutton.</span><span class="sxs-lookup"><span data-stu-id="19602-139">The name of the project is DisableStartButton.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 <span data-ttu-id="19602-140">Değişikliklerin bir sonucu olarak düğme yanıt vermiyor ancak `AccessTheWebAsync` işlem reentered şekilde Web siteleri yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="19602-140">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="19602-141">İptal edip işlemi yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="19602-141">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="19602-142">Devre dışı bırakmak yerine **Başlat** düğmesini kullanabilirsiniz düğmeyi etkin tutabilirsiniz ancak, kullanıcı yeniden bu düğmeyi seçerse, zaten çalışıyor ve en son başlatılan işlemin devam izin işlemi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="19602-142">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="19602-143">İptal işlemleri hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="19602-143">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="19602-144">Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="19602-144">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="19602-145">Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="19602-145">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="19602-146">Projenin adı CancelAndRestart'tır.</span><span class="sxs-lookup"><span data-stu-id="19602-146">The name of the project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="19602-147">Bildirme bir <xref:System.Threading.CancellationTokenSource> değişken `cts`, tüm yöntemler için kapsam dahilinde olan.</span><span class="sxs-lookup"><span data-stu-id="19602-147">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="19602-148">İçinde `StartButton_Click`, bir işlemin zaten çalışıp çalışmadığını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="19602-148">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="19602-149">Varsa değerini `cts` olan boş, hiçbir işlem zaten etkin.</span><span class="sxs-lookup"><span data-stu-id="19602-149">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="19602-150">Değer null değilse, zaten çalışan işlemi iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="19602-150">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="19602-151">Ayarlama `cts` geçerli işlemi temsil eden farklı bir değer.</span><span class="sxs-lookup"><span data-stu-id="19602-151">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="19602-152">Sonunda `StartButton_Click`, geçerli işlem tamamlanır, bu nedenle ayarlayın `cts` null geri dönün.</span><span class="sxs-lookup"><span data-stu-id="19602-152">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="19602-153">Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="19602-153">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="19602-154">Eklentiler yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="19602-154">The additions are marked with asterisks.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 <span data-ttu-id="19602-155">İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="19602-155">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="19602-156">Öğesinden iptal belirtecini kabul etmek için bir parametre ekleyin `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="19602-156">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="19602-157">Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> ettiğinden Web sitelerini indirmek için yöntemi `GetAsync` kabul eden bir <xref:System.Threading.CancellationToken> bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="19602-157">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="19602-158">Çağırmadan önce `DisplayResults` her indirilebilir Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlemi iptal edildiğini doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="19602-158">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="19602-159">Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="19602-159">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 <span data-ttu-id="19602-160">Seçerseniz **Başlat** düğmesine birkaç kez bu uygulama çalışırken aşağıdaki çıktıya benzer sonuçlar üretmelidir.</span><span class="sxs-lookup"><span data-stu-id="19602-160">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="19602-161">Kısmi listelerini ortadan kaldırmak için ilk kod satırı açıklamadan çıkarın `StartButton_Click` kullanıcı her zaman metin kutusunu temizlemek için işlemi yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="19602-161">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="19602-162">Birden çok işlemi çalıştırın ve çıktıyı sıraya alın</span><span class="sxs-lookup"><span data-stu-id="19602-162">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="19602-163">Başka bir zaman uyumsuz işlemi kullanıcı her zaman uygulama başlatır, bu üçüncü örnek en karmaşık örnektir **Başlat** düğmesi ve tüm işlemler tamamlanmak üzere çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="19602-163">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="19602-164">Listeden Web siteleri tüm istenen işlemler zaman uyumsuz olarak yükleyin, ancak çıkış işlemlerden çıktılar ardışık olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="19602-164">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="19602-165">Diğer bir deyişle, gerçek indirme etkinliği, deki çıkışın gösterdiği gibi aralanmıştır [yeniden giriş tanıma](#BKMK_RecognizingReentrancy) gösterir, ancak her grup için sonuçların listesi ayrı ayrı sunulur.</span><span class="sxs-lookup"><span data-stu-id="19602-165">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="19602-166">İşlemleri genel paylaşım <xref:System.Threading.Tasks.Task>, `pendingWork`, görüntüleme işlemi için bir ağ geçidi olarak görev gören.</span><span class="sxs-lookup"><span data-stu-id="19602-166">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  

 <span data-ttu-id="19602-167">Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="19602-167">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="19602-168">Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="19602-168">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="19602-169">Proje QueueResults adıdır.</span><span class="sxs-lookup"><span data-stu-id="19602-169">The name of the project is QueueResults.</span></span>  
   
 <span data-ttu-id="19602-170">Aşağıdaki çıktı, kullanıcı seçtiğinde görülecek sonucu gösterir **Başlat** düğmesini yalnızca bir defa.</span><span class="sxs-lookup"><span data-stu-id="19602-170">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="19602-171">Harf etiketi A, sonucun ilk kez gösterir **Başlat** düğmesi seçilir.</span><span class="sxs-lookup"><span data-stu-id="19602-171">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="19602-172">Sayılar, yükleme hedefleri listesinde URL'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19602-172">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="19602-173">Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulama aşağıdaki satırlara benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="19602-173">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="19602-174">Bir kare ile başlayan bilgi satırları uygulamanın ilerleyişini (#) izleme oturum açın.</span><span class="sxs-lookup"><span data-stu-id="19602-174">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="19602-175">Grup A tamamlanmadan, ancak her grubun çıktısı ayrı görünür önce Grup B ve C başlatın.</span><span class="sxs-lookup"><span data-stu-id="19602-175">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="19602-176">Grup A için çıktıların tamamı ardından Grup B için çıktıların tamamı ve sonra tüm çıkış grubu c için ilk olarak, görünür Uygulama her zaman sırayla grupları görüntüler ve her bir grup için her zaman URL'leri URL'lerin listesinde görüntülenen sırayla tek tek Web siteleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19602-176">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="19602-177">Ancak, hangi indirmelerin gerçekte olduğu sırayı tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="19602-177">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="19602-178">Birden çok grup başlattıktan sonra oluşturdukları indirme görevlerinin tamamı etkindir.</span><span class="sxs-lookup"><span data-stu-id="19602-178">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="19602-179">Bu A-1 varsayamazsınız önce B-1 indirilir ve bu A-1 varsayamazsınız A-2 önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="19602-179">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="19602-180">Genel tanımlar</span><span class="sxs-lookup"><span data-stu-id="19602-180">Global Definitions</span></span>  
 <span data-ttu-id="19602-181">Örnek kod, tüm yöntemlerden görünen aşağıdaki iki genel bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="19602-181">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="19602-182">`Task` Değişken `pendingWork`, görüntüleme işlemini kesmesini ve herhangi bir grubu başka bir grubun görünen çalışmasını önler.</span><span class="sxs-lookup"><span data-stu-id="19602-182">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="19602-183">Karakter değişkeni `group`, sonuçların beklenen sırada göründüğünü doğrulamak üzere farklı gruplardan çıkış etiketler.</span><span class="sxs-lookup"><span data-stu-id="19602-183">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="19602-184">Tıklama olayı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="19602-184">The Click Event Handler</span></span>  
 <span data-ttu-id="19602-185">Olay işleyicisi `StartButton_Click`, her zaman kullanıcı Grup harfini artırır **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="19602-185">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="19602-186">Ardından işleyici çağrıları `AccessTheWebAsync` indirme işlemini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="19602-186">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="19602-187">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="19602-187">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="19602-188">Bu örnekte böler `AccessTheWebAsync` öğesini iki yöntem.</span><span class="sxs-lookup"><span data-stu-id="19602-188">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="19602-189">İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve ayarlar `pendingWork` görüntüleme işlemini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="19602-189">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="19602-190">Yöntemi, bir dil ile tümleşik sorgu (LINQ sorgusu) kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> tüm indirme görevlerini aynı anda başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="19602-190">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="19602-191">`AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her İndirmenin tamamlanmasını beklemek ve uzunluğunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="19602-191">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="19602-192">`FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="19602-192">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="19602-193">Değeri, görev önce başka bir işlem tarafından kesintiye engellediğini tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="19602-193">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="19602-194">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="19602-194">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="19602-195">Bu yöntemi izleyerek her birini bekler, karşıdan yüklenen Web sitesi uzunluğunu görüntülemek ve uzunluğu toplama ekleme bir gruptaki indirme görevlerini aracılığıyla geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="19602-195">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="19602-196">İlk deyimde `FinishOneGroupAsync` kullanan `pendingWork` yöntemin girilmesinin zaten içinde görüntüleme işlemini veya beklemede bir işlemle çakışmamasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="19602-196">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="19602-197">Bu tür bir işlem sürüyorsa, giriş işlemi kendi sırasını beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="19602-197">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
   
#### <a name="points-of-interest"></a><span data-ttu-id="19602-198">İlgi noktaları</span><span class="sxs-lookup"><span data-stu-id="19602-198">Points of Interest</span></span>  
 <span data-ttu-id="19602-199">Çıktıda pound işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklamak.</span><span class="sxs-lookup"><span data-stu-id="19602-199">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="19602-200">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="19602-200">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="19602-201">Bir grubu, bir önceki Grup çıktıyı görüntülerken, ancak görüntü önceki grubun çıktı görünümü kesintiye başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="19602-201">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="19602-202">`pendingWork` Görevi başlangıcında NULL'dur `FinishOneGroupAsync` Grup A için yalnızca ilk başlayan a.</span><span class="sxs-lookup"><span data-stu-id="19602-202">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="19602-203">Grup A taşınmadığından henüz tamamlanmamış bir await deyimindeki ulaştığında `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="19602-203">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="19602-204">Bu nedenle, Denetim öğesine dönmemiştir `AccessTheWebAsync`ve ilk atamaya `pendingWork` oluşmamıştır.</span><span class="sxs-lookup"><span data-stu-id="19602-204">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="19602-205">Her zaman aşağıdaki iki satır çıktıda birlikte görünür.</span><span class="sxs-lookup"><span data-stu-id="19602-205">The following two lines always appear together in the output.</span></span> <span data-ttu-id="19602-206">Kod bir grubun çalışmasını başlatma arasında hiçbir zaman kesintiye `StartButton_Click` ve grubun bir görev atama `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="19602-206">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="19602-207">Bir grubu girdikten sonra `StartButton_Click`, işlemi işlemi girinceye kadar await ifadesini tamamlamaz değil `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="19602-207">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="19602-208">Bu nedenle, başka bir işlem sırasında kod kesiminin denetimi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19602-208">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="19602-209">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="19602-209">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="19602-210">Örnek uygulamayı daha iyi anlamak için indirin, kendiniz derleyebilir veya uygulamayı gerçekleştirmeden, bu konunun sonunda kodu gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="19602-210">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19602-211">Bir veya daha yeni bilgisayarınızda yüklü örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19602-211">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="19602-212">Uygulamayı karşıdan yükleme</span><span class="sxs-lookup"><span data-stu-id="19602-212">Downloading the App</span></span>  
  
1.  <span data-ttu-id="19602-213">Sıkıştırılmış dosyayı indirin [zaman uyumsuz örneği: .NET Desktop uygulamaları'na yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="19602-213">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="19602-214">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="19602-214">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="19602-215">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="19602-215">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="19602-216">Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="19602-216">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="19602-217">İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz projenin kısayol menüsünü **StartUpProject olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="19602-217">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="19602-218">Oluşturun ve projeyi çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="19602-218">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="19602-219">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="19602-219">Building the App</span></span>  
 <span data-ttu-id="19602-220">Aşağıdaki bölümde, örnek bir WPF uygulaması olarak oluşturmak için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="19602-220">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="19602-221">Bir WPF uygulaması derlemek için</span><span class="sxs-lookup"><span data-stu-id="19602-221">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="19602-222">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="19602-222">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="19602-223">Menü çubuğunda, **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="19602-223">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="19602-224">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="19602-224">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="19602-225">İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#** ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="19602-225">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="19602-226">Proje türleri listesinde seçin **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="19602-226">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="19602-227">Projeyi adlandırın `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="19602-227">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="19602-228">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="19602-228">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="19602-229">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="19602-229">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="19602-230">Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="19602-230">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="19602-231">İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="19602-231">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
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
  
     <span data-ttu-id="19602-232">Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="19602-232">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="19602-233">İçin bir başvuru eklemeniz <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="19602-233">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="19602-234">İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="19602-234">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="19602-235">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="19602-235">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
  
    // Add the following using directives, and add a reference for System.Net.Http.  
    using System.Net.Http;  
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "https://msdn.microsoft.com/library/hh191443.aspx",  
                    "https://msdn.microsoft.com/library/aa578028.aspx",  
                    "https://msdn.microsoft.com/library/jj155761.aspx",  
                    "https://msdn.microsoft.com/library/hh290140.aspx",  
                    "https://msdn.microsoft.com/library/hh524395.aspx",  
                    "https://msdn.microsoft.com/library/ms404677.aspx",  
                    "https://msdn.microsoft.com",  
                    "https://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "https://".  
                var displayURL = url.Replace("https://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="19602-236">Programı çalıştırın ve ardından CTRL + F5 tuşlarına basın **Başlat** düğmesine birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="19602-236">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="19602-237">Değişikliklerini yapın [Başlat düğmesini devre dışı](#BKMK_DisableTheStartButton), [iptal edip işlemi yeniden](#BKMK_CancelAndRestart), veya [birden çok işlemi çalıştırın ve çıktıyı sıraya](#BKMK_RunMultipleOperations) yeniden giriş işlemek için.</span><span class="sxs-lookup"><span data-stu-id="19602-237">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19602-238">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19602-238">See Also</span></span>

- [<span data-ttu-id="19602-239">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="19602-239">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="19602-240">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="19602-240">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
