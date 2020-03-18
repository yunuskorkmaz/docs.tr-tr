---
title: Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 9f7420113d4af83d7d057b772af307bd8d4bcc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169955"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="79452-102">Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl</span><span class="sxs-lookup"><span data-stu-id="79452-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="79452-103">Async yönteminde, görevler oluşturulduklarında başlatılır.</span><span class="sxs-lookup"><span data-stu-id="79452-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="79452-104">[Bekleme](../../../language-reference/operators/await.md) işleci, görev bitene kadar işlemenin devam edilemeyebildiği yöntemdeki noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="79452-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="79452-105">Genellikle bir görev, aşağıdaki örnekte görüldüğü gibi, oluşturulduğu anda beklenilir.</span><span class="sxs-lookup"><span data-stu-id="79452-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="79452-106">Ancak, programınızın gerçekleştirmesi gereken ve görevin tamamlanmasına bağlı olmayan başka işleri varsa, görevi beklemekten görevi ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79452-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="79452-107">Bir görevi başlatmak ve beklemek arasında, diğer görevleri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79452-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="79452-108">Ek görevler örtülü olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="79452-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="79452-109">Aşağıdaki program üç eşzamanlı web indirme başlar ve daha sonra çağrıldıkları sırada onları bekliyor.</span><span class="sxs-lookup"><span data-stu-id="79452-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="79452-110">Programı çalıştırdığınızda, görevlerin her zaman oluşturuldukları ve beklendikleri sırada bitmediklerine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="79452-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="79452-111">Oluşturulduklarında çalışmaya başlarlar ve yöntem bekleyen ifadelere ulaşmadan önce görevlerden biri veya birkaçı tamamlanabilir.</span><span class="sxs-lookup"><span data-stu-id="79452-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79452-112">Bu projeyi tamamlamak için Visual Studio 2012 veya üstü ve .NET Framework 4.5 veya daha yüksek bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79452-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="79452-113">Aynı anda birden çok görevi başlatan başka bir örnek için, [Task.WhenAll (C#) kullanarak async walkthrough'u nasıl genişletirebilirsiniz.](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span><span class="sxs-lookup"><span data-stu-id="79452-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="79452-114">Bu örnek için kodu [Geliştirici Kodu Örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79452-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="79452-115">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="79452-115">To set up the project</span></span>  
  
1. <span data-ttu-id="79452-116">Bir WPF uygulaması ayarlamak için aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="79452-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="79452-117">[Walkthrough: Access ingsync kullanarak web'e erişim ve (C#) bekliyor.](./walkthrough-accessing-the-web-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="79452-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="79452-118">Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="79452-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="79452-119">Düğmeyi `startButton`adlandırın ve metin `resultsTextBox`kutusunu adlandırın.</span><span class="sxs-lookup"><span data-stu-id="79452-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="79452-120">Için <xref:System.Net.Http>bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79452-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="79452-121">MainWindow.xaml.cs dosyasında, `using` `System.Net.Http`için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79452-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="79452-122">Kodu eklemek için</span><span class="sxs-lookup"><span data-stu-id="79452-122">To add the code</span></span>  
  
1. <span data-ttu-id="79452-123">Tasarım penceresinde, MainWindow.xaml, MainWindow.xaml.cs olay işleyicisi `startButton_Click` oluşturmak için düğmesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="79452-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="79452-124">Aşağıdaki kodu kopyalayın ve MainWindow.xaml.cs'nin `startButton_Click` gövdesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="79452-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="79452-125">Kod, `CreateMultipleTasksAsync`uygulamayı yönlendiren bir eşzamanlı yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="79452-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="79452-126">Projeye aşağıdaki destek yöntemlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="79452-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="79452-127">`ProcessURLAsync`bir <xref:System.Net.Http.HttpClient> web sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="79452-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="79452-128">Destek yöntemi, `ProcessURLAsync` daha sonra dizinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="79452-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="79452-129">`DisplayResults`her URL için bayt dizisinde bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79452-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="79452-130">Bu ekran, her görevin karşıdan yüklemeyi ne zaman tamamlarolduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="79452-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="79452-131">Aşağıdaki yöntemleri kopyalayın ve MainWindow.xaml.cs `startButton_Click` olay işleyicisi sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="79452-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="79452-132">Son olarak, `CreateMultipleTasksAsync`aşağıdaki adımları gerçekleştiren yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="79452-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="79452-133">Yöntem, `ProcessURLAsync`'de `HttpClient` metne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> erişmeniz gereken bir nesneyi bildirir.</span><span class="sxs-lookup"><span data-stu-id="79452-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="79452-134">Yöntem oluşturur ve bir <xref:System.Threading.Tasks.Task%601>karşıcı türü `TResult` , üç görev başlatır.</span><span class="sxs-lookup"><span data-stu-id="79452-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="79452-135">Her görev sona `DisplayResults` ererken, görevin URL'sini ve indirilen içeriğin uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79452-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="79452-136">Görevler eşzamanlı olarak çalıştığı için, sonuçların görüntülenme sırası, beyan edildikleri sırayla farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="79452-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="79452-137">Yöntem, her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="79452-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="79452-138">Her `await` işleç, `CreateMultipleTasksAsync` beklenen görev tamamlanana kadar yürütmeyi askıya adatır.</span><span class="sxs-lookup"><span data-stu-id="79452-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="79452-139">İşletici ayrıca, tamamlanan her `ProcessURLAsync` görevden aramadan iade değerini de alır.</span><span class="sxs-lookup"><span data-stu-id="79452-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="79452-140">Görevler tamamlandığında ve sonda değerleri alındığında, yöntem web sitelerinin uzunluklarını toplama gelir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79452-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="79452-141">Aşağıdaki yöntemi kopyalayın ve çözüme yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="79452-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults
        // displays its length.  
        Task<int> download1 =
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="79452-142">Programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="79452-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="79452-143">Üç görevin her zaman aynı sırada tamamlanmadığını ve bitirdikleri sıranın oluşturuldukları ve beklendikleri sıra olmadığını doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="79452-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79452-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="79452-144">Example</span></span>  
 <span data-ttu-id="79452-145">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="79452-145">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults
            // displays its length.  
            Task<int> download1 =
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="79452-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79452-146">See also</span></span>

- [<span data-ttu-id="79452-147">Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="79452-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="79452-148">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="79452-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="79452-149">Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir</span><span class="sxs-lookup"><span data-stu-id="79452-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
