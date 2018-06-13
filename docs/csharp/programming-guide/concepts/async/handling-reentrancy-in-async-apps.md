---
title: Zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: f2b43bd982b7dcd1f4641ae55f95595d14d70b0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339767"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="00d72-102">Zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="00d72-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="00d72-103">Zaman uyumsuz kodu, uygulamanızda eklediğinizde göz önünde bulundurun ve büyük olasılıkla, tamamlanmadan önce zaman uyumsuz bir işlem yeniden girme için başvuruyor yeniden giriş önlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="00d72-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="00d72-104">Tanımlamak ve yeniden giriş olasılıklarını işlemek yok, beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="00d72-105">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="00d72-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="00d72-106">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="00d72-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="00d72-107">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="00d72-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="00d72-108">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="00d72-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="00d72-109">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="00d72-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="00d72-110">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="00d72-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="00d72-111">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="00d72-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="00d72-112">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="00d72-113">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="00d72-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="00d72-114">Bu konudaki örnek kullanıcıları seçin bir **Başlat** bir dizi Web siteleri yükler ve yüklenen bayt sayısı toplam hesaplar zaman uyumsuz bir uygulamayı başlatmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="00d72-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="00d72-115">Örnek zaman uyumlu bir sürümü aynı şekilde bakılmaksızın ilk kez sonra kullanıcı Arabirimi iş parçacığı çalışan uygulama sonlanana kadar bu olayları yoksayar çünkü kaç kez bir kullanıcı düğmesini seçer. yanıt.</span><span class="sxs-lookup"><span data-stu-id="00d72-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="00d72-116">Zaman uyumsuz bir uygulamada ancak, kullanıcı Arabirimi iş parçacığı yanıt vermeye devam eder ve onu tamamlanmadan önce zaman uyumsuz işlemi yeniden girmeniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="00d72-117">Aşağıdaki örnek, beklenen gösterir kullanıcı seçtiğinde çıktı **Başlat** yalnızca bir kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="00d72-118">Her sitenin bayt cinsinden boyutu ile indirilen Web siteleri listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00d72-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="00d72-119">Toplam bayt sayısı sonunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00d72-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="00d72-120">Ancak, kullanıcı düğmesi birden çok kez seçerse, olay işleyici tekrar çağrılır ve indirme işlemini her seferinde reentered.</span><span class="sxs-lookup"><span data-stu-id="00d72-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="00d72-121">Sonuç olarak, birkaç zaman uyumsuz işlemler aynı anda çalıştırıyorsanız, çıktısı sonuçlara interleaves ve toplam bayt sayısı karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="00d72-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="00d72-122">Bu konuda sonuna kaydırarak bu çıkışı üretir kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="00d72-123">Çözüm, yerel bilgisayarınıza indirip WebsiteDownload proje çalıştıran veya kendi projesi oluşturmak için bu konunun sonunda kodu kullanarak koduyla deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="00d72-124">Daha fazla bilgi ve yönergeler için bkz: [gözden geçirme ve örnek uygulamayı çalıştıran](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="00d72-124">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="00d72-125">Yeniden girişi işleme</span><span class="sxs-lookup"><span data-stu-id="00d72-125">Handling Reentrancy</span></span>  
 <span data-ttu-id="00d72-126">Yeniden giriş yapmak için uygulamanızın istediğinize bağlı olarak yolları, çeşitli işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-126">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="00d72-127">Bu konuda aşağıdaki örnekler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="00d72-127">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="00d72-128">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="00d72-128">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="00d72-129">Devre dışı **Başlat** böylece kullanıcı onu kesme işlemi çalışırken düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-129">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="00d72-130">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="00d72-130">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="00d72-131">Kullanıcı seçtiğinde hala çalıştıran herhangi bir işlem iptal **Başlat** yeniden düğmesine ve ardından let en yakın zamanda istenen işlem devam edin.</span><span class="sxs-lookup"><span data-stu-id="00d72-131">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="00d72-132">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="00d72-132">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="00d72-133">Tüm işlemlerini zaman uyumsuz olarak çalıştırın, ancak her işlemi sonuçlarından birlikte ve sırada görünmesini sağlayacak şekilde çıkış görüntüsünü koordine etmek için istenen izin verir.</span><span class="sxs-lookup"><span data-stu-id="00d72-133">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="00d72-134">Başlat düğmesi devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="00d72-134">Disable the Start Button</span></span>  
 <span data-ttu-id="00d72-135">Engelleyebilir **Başlat** en üstündeki düğmesi devre dışı bırakarak bir işlem devam ederken düğmesini `StartButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="00d72-135">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="00d72-136">İçinden düğmesini sonra etkinleştirebileceğiniz bir `finally` engelleme kullanıcıların uygulamayı yeniden çalıştırabilmeniz için işlem sona erdiğinde.</span><span class="sxs-lookup"><span data-stu-id="00d72-136">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="00d72-137">Bu senaryonun kurulumunu yapmak için aşağıdaki sağlanan temel kod değişiklik [gözden geçirme ve örnek uygulamayı çalıştıran](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="00d72-137">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="00d72-138">Tamamlanan uygulama aynı zamanda indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="00d72-138">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="00d72-139">Proje DisableStartButton adıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-139">The name of the project is DisableStartButton.</span></span>  
  
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
  
 <span data-ttu-id="00d72-140">Değişikliklerin sonucu olarak, düğme yanıt vermiyor sırada `AccessTheWebAsync` işlemi girilmesi edilemez şekilde Web siteleri yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="00d72-140">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="00d72-141">İptal edin ve işlemi yeniden deneyin</span><span class="sxs-lookup"><span data-stu-id="00d72-141">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="00d72-142">Devre dışı bırakma yerine **Başlat** düğmesini kullanabilirsiniz düğmesi etkin tutmak ancak, kullanıcı bu düğme yeniden seçerse zaten çalışan ve en son başlatılan işlemin devam etmesine izin vermek işlemi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="00d72-142">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="00d72-143">İptal etme hakkında daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="00d72-143">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="00d72-144">Bu senaryonun kurulumunu yapmak için aşağıdaki sağlanan temel kod değişiklik [gözden geçirme ve örnek uygulamayı çalıştıran](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="00d72-144">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="00d72-145">Tamamlanan uygulama aynı zamanda indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="00d72-145">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="00d72-146">Proje CancelAndRestart adıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-146">The name of the project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="00d72-147">Bildirme bir <xref:System.Threading.CancellationTokenSource> değişkeni, `cts`, kapsamdaki tüm yöntemleri için olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-147">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="00d72-148">İçinde `StartButton_Click`, bir işlemi zaten devam ettiğinden olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="00d72-148">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="00d72-149">Varsa değerini `cts` olan null, hiçbir zaten etkin bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="00d72-149">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="00d72-150">Değer null değilse, zaten çalışıyor işlemi iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="00d72-150">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="00d72-151">Ayarlama `cts` için geçerli işlem temsil eden farklı bir değer.</span><span class="sxs-lookup"><span data-stu-id="00d72-151">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="00d72-152">Sonunda `StartButton_Click`, geçerli işlemi tamamlandığında, böylece değerini ayarlayın `cts` null dön.</span><span class="sxs-lookup"><span data-stu-id="00d72-152">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="00d72-153">Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="00d72-153">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="00d72-154">Eklemeleri yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="00d72-154">The additions are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="00d72-155">İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="00d72-155">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="00d72-156">Gelen iptal belirteci kabul etmek için bir parametre eklemek `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="00d72-156">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="00d72-157">Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> çünkü Web sitelerini yüklemeye yöntemi `GetAsync` kabul bir <xref:System.Threading.CancellationToken> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="00d72-157">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="00d72-158">Çağırmadan önce `DisplayResults` indirilen her Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlem iptal edildi değiştirilmediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-158">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="00d72-159">Aşağıdaki kod yıldız işaretiyle işaretli bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="00d72-159">The following code shows these changes, which are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="00d72-160">Seçerseniz **Başlat** birkaç kez düğmesini bu uygulama çalışırken, aşağıdaki çıkış benzer sonuçlar üretmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00d72-160">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="00d72-161">Kısmi listeleri ortadan kaldırmak için ilk kod satırı açıklamadan kaldırmasına `StartButton_Click` kullanıcı işlemi yeniden her zaman metin kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="00d72-161">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="00d72-162">Birden çok işlemleri çalıştırın ve çıkış sırası</span><span class="sxs-lookup"><span data-stu-id="00d72-162">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="00d72-163">Uygulama başka bir zaman uyumsuz işlemi kullanıcının seçtiği her zaman başlatır, bu üçüncü en karmaşık örneğidir **Başlat** düğmesi ve tüm işlemleri tamamlanıncaya kadar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="00d72-163">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="00d72-164">Listeden Web sitelerini istenen tüm işlemleri zaman uyumsuz olarak indirebilir, ancak işlem çıkışı sıralı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="00d72-164">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="00d72-165">Diğer bir deyişle, gerçek indirme etkinliği, çıktı olarak araya eklemeli [algılamayı yeniden giriş](#BKMK_RecognizingReentrancy) gösterir, ancak her grup için sonuçlardan sunulur ayrı olarak.</span><span class="sxs-lookup"><span data-stu-id="00d72-165">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="00d72-166">Operations genel paylaşmak <xref:System.Threading.Tasks.Task>, `pendingWork`, hangi görüntü işlemi için bir ağ geçidi olarak hizmet verir.</span><span class="sxs-lookup"><span data-stu-id="00d72-166">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  

 <span data-ttu-id="00d72-167">Bu senaryonun kurulumunu yapmak için aşağıdaki sağlanan temel kod değişiklik [gözden geçirme ve örnek uygulamayı çalıştıran](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="00d72-167">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="00d72-168">Tamamlanan uygulama aynı zamanda indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="00d72-168">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="00d72-169">Proje QueueResults adıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-169">The name of the project is QueueResults.</span></span>  
   
 <span data-ttu-id="00d72-170">Kullanıcı seçtiğinde sonuç aşağıdaki çıktı gösterir **Başlat** yalnızca bir kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-170">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="00d72-171">Harf etiketi, A, sonuç ilk saati gösterir **Başlat** düğmesi seçilidir.</span><span class="sxs-lookup"><span data-stu-id="00d72-171">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="00d72-172">Sayıları URL'leri sırasını indirme hedefler listesinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="00d72-172">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="00d72-173">Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulamanın aşağıdaki satırları benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="00d72-173">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="00d72-174">Kare ile başlayan bilgi satırları (#) izleme uygulama ilerlemesini oturum açın.</span><span class="sxs-lookup"><span data-stu-id="00d72-174">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="00d72-175">Grup B ve C gruba tamamlandı, ancak her grup için çıktı ayrı olarak görünür önce başlatın.</span><span class="sxs-lookup"><span data-stu-id="00d72-175">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="00d72-176">Grup a tüm çıktı ardından B grubu için tüm çıkış ve ardından tüm çıktı grubu c için ilk olarak, görünür Uygulama her zaman sıraya göre grupları görüntüler ve her grup için her zaman tek tek Web siteleri hakkında bilgi URL'leri URL'leri listede sırada görüntüler.</span><span class="sxs-lookup"><span data-stu-id="00d72-176">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="00d72-177">Ancak, indirmeleri gerçekten durum meydana sipariş tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="00d72-177">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="00d72-178">Birden çok grubu başlatıldıktan sonra oluşturdukları indirme tüm etkin görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="00d72-178">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="00d72-179">Bu A-1 varsayın olamaz B-1 önce indirilir ve o A-1 varsayın olamaz A-2 önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="00d72-179">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="00d72-180">Genel tanımları</span><span class="sxs-lookup"><span data-stu-id="00d72-180">Global Definitions</span></span>  
 <span data-ttu-id="00d72-181">Örnek kod tüm yöntemleri görünür olan aşağıdaki iki genel bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="00d72-181">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="00d72-182">`Task` Değişkeni `pendingWork`, görüntüleme işlemini denetleyen ve herhangi bir grubu başka bir grubun görüntü işlemi önler.</span><span class="sxs-lookup"><span data-stu-id="00d72-182">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="00d72-183">Karakter değişkeni `group`, sonuçları beklenen sırada göründüğünü doğrulamak için farklı gruplar çıktısını etiketler.</span><span class="sxs-lookup"><span data-stu-id="00d72-183">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="00d72-184">Click olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="00d72-184">The Click Event Handler</span></span>  
 <span data-ttu-id="00d72-185">Olay işleyicisi `StartButton_Click`, kullanıcının seçtiği her defasında grup harf artırır **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="00d72-185">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="00d72-186">Ardından işleyicisi çağrılarını `AccessTheWebAsync` indirme işlemi çalıştıramadı.</span><span class="sxs-lookup"><span data-stu-id="00d72-186">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
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
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="00d72-187">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="00d72-187">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="00d72-188">Bu örnek böler `AccessTheWebAsync` iki yöntemlerde.</span><span class="sxs-lookup"><span data-stu-id="00d72-188">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="00d72-189">İlk yöntem `AccessTheWebAsync`, bir grup için tüm yükleme görevleri başlatır ve ayarlayan `pendingWork` görüntüleme işlemini kontrol eden.</span><span class="sxs-lookup"><span data-stu-id="00d72-189">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="00d72-190">Bir dil ile tümleşik sorgu (LINQ sorgusu) yöntemini kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> aynı anda tüm yükleme görevleri başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="00d72-190">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="00d72-191">`AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her indirme tamamlanmasını bekler ve uzunluğu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="00d72-191">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="00d72-192">`FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="00d72-192">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="00d72-193">Görev tamamlanmadan önce değer kesinti başka bir işlem tarafından engellediğini.</span><span class="sxs-lookup"><span data-stu-id="00d72-193">That value prevents interruption by another operation before the task is complete.</span></span>  
  
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
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="00d72-194">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="00d72-194">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="00d72-195">Bu yöntem, gruptaki her biri bekleniyor, indirilen Web sitesi uzunluğu görüntüleyerek ve toplam uzunluğu ekleyerek, indirme görevleri boyunca geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="00d72-195">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="00d72-196">İlk ifade, `FinishOneGroupAsync` kullanan `pendingWork` yöntemi girme zaten görüntü işleminde veya, zaten bekleyen bir işlem ile engellemez emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="00d72-196">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="00d72-197">Böyle bir işlem devam ediyor, kendi dönüş girme işlemi beklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00d72-197">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
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
  
   
#### <a name="points-of-interest"></a><span data-ttu-id="00d72-198">İlgilenilen noktaları</span><span class="sxs-lookup"><span data-stu-id="00d72-198">Points of Interest</span></span>  
 <span data-ttu-id="00d72-199">Bu örnek nasıl çalıştığını çıktıda pound işareti (#) ile başlayan bilgi satırları açıklayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-199">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="00d72-200">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="00d72-200">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="00d72-201">Bir grup, bir önceki Grup çıktısını görüntüleme, ancak önceki grubun çıkış görüntüsünü kesintiye değil başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-201">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="00d72-202">`pendingWork` Görev null başlangıcında `FinishOneGroupAsync` yalnızca Grup A, başlatılan ilk.</span><span class="sxs-lookup"><span data-stu-id="00d72-202">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="00d72-203">Grup A kurmadı henüz tamamlanmamış bir bekleme ifade ulaştığında `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="00d72-203">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="00d72-204">Bu nedenle, denetim için döndürülen kurmadı `AccessTheWebAsync`ve ilk atama `pendingWork` oluştu kurmadı.</span><span class="sxs-lookup"><span data-stu-id="00d72-204">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="00d72-205">Aşağıdaki iki satırı birlikte her zaman çıkışında görünür.</span><span class="sxs-lookup"><span data-stu-id="00d72-205">The following two lines always appear together in the output.</span></span> <span data-ttu-id="00d72-206">Kod bir grubun işlemi başlatılıyor arasında hiçbir zaman kesintiye `StartButton_Click` ve bir görev için grubunun atama `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="00d72-206">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="00d72-207">Bir grup girdikten sonra `StartButton_Click`, işlemi işlemi girene kadar bir bekleme ifade işlemini tamamlamazsa `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="00d72-207">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="00d72-208">Bu nedenle, başka bir işlem denetimi, kod kesimi sırasında kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-208">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="00d72-209">Gözden geçirme ve örnek uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="00d72-209">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="00d72-210">Örnek uygulama daha iyi anlamak için indirir, kendiniz oluşturabilir veya uygulama uygulamadan bu konunun sonunda kodu gözden.</span><span class="sxs-lookup"><span data-stu-id="00d72-210">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00d72-211">Örnek bir Windows Presentation Foundation (WPF) masaüstü uygulaması çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="00d72-211">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="00d72-212">Uygulama indiriliyor</span><span class="sxs-lookup"><span data-stu-id="00d72-212">Downloading the App</span></span>  
  
1.  <span data-ttu-id="00d72-213">Sıkıştırılmış dosya indirme [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="00d72-213">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="00d72-214">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="00d72-214">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="00d72-215">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="00d72-215">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="00d72-216">Açılmış örnek kodu içeren klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="00d72-216">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="00d72-217">İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz proje için kısayol menüsünü açın **StartUpProject ayarlamak**.</span><span class="sxs-lookup"><span data-stu-id="00d72-217">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="00d72-218">CTRL + F5 anahtarları projesini derlemeyi ve çalıştırmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="00d72-218">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="00d72-219">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="00d72-219">Building the App</span></span>  
 <span data-ttu-id="00d72-220">Aşağıdaki bölümde, örnek olarak bir WPF uygulaması oluşturmak için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="00d72-220">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="00d72-221">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="00d72-221">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="00d72-222">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="00d72-222">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="00d72-223">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="00d72-223">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="00d72-224">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="00d72-224">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="00d72-225">İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#**, genişletin ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="00d72-225">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="00d72-226">Proje türleri listesinden seçip **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="00d72-226">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="00d72-227">Proje adı `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="00d72-227">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="00d72-228">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="00d72-228">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="00d72-229">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="00d72-229">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="00d72-230">Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="00d72-230">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="00d72-231">İçinde **XAML** görüntülemek MainWindow.xaml, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="00d72-231">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="00d72-232">Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.</span><span class="sxs-lookup"><span data-stu-id="00d72-232">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="00d72-233">İçin bir başvuru ekleyin <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="00d72-233">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="00d72-234">İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="00d72-234">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="00d72-235">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="00d72-235">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="00d72-236">Programını çalıştırın ve ardından seçmek için CTRL + F5 anahtarlar **Başlat** birkaç kez düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-236">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="00d72-237">Öğesinden değişiklikler yapmak [Başlat düğmesi devre dışı](#BKMK_DisableTheStartButton), [iptal edin ve işlemi yeniden](#BKMK_CancelAndRestart), veya [birden çok işlemler çalıştırın ve çıkış sırası](#BKMK_RunMultipleOperations) yeniden giriş işlemek için.</span><span class="sxs-lookup"><span data-stu-id="00d72-237">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d72-238">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00d72-238">See Also</span></span>  
 [<span data-ttu-id="00d72-239">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="00d72-239">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="00d72-240">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="00d72-240">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
