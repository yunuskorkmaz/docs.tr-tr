---
title: Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 0cfc1d6d1d59dc74fcf5990abb0a9d980a83d7b0
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241805"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="0cf96-102">Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="0cf96-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="0cf96-103">Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-103">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="0cf96-104">[Await](../../../language-reference/operators/await.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="0cf96-105">Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.</span><span class="sxs-lookup"><span data-stu-id="0cf96-105">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="0cf96-106">Ancak, programın gerçekleştirmeye yönelik başka bir işi olması durumunda görevin tamamlanmasına bağlı olmaması durumunda görevi bekleyen görev oluşturmayı ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="0cf96-107">Bir görevi başlatma ve bekleme arasında başka görevler de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="0cf96-108">Ek görevler dolaylı olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="0cf96-109">Aşağıdaki program, üç zaman uyumsuz Web yüklemesi başlatır ve ardından bunların çağrıldıkları sırayla bekler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="0cf96-110">Programı çalıştırdığınızda, görevlerin Oluşturulma sırasında ve bekledikleri sırada her zaman bitmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0cf96-110">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="0cf96-111">Bunlar oluşturulduğunda çalışmaya başlar ve Yöntem await ifadelerine ulaşmadan önce bir veya daha fazla görev bitebilirler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-111">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cf96-112">Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="0cf96-113">Aynı anda birden çok görevi Başlatan başka bir örnek için, bkz. [Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="0cf96-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="0cf96-114">Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="0cf96-115">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0cf96-115">To set up the project</span></span>  
  
1. <span data-ttu-id="0cf96-116">WPF uygulaması ayarlamak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="0cf96-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="0cf96-117">[Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişmek](./walkthrough-accessing-the-web-by-using-async-and-await.md)için bu adımlarla ilgili ayrıntılı yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="0cf96-118">Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0cf96-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="0cf96-119">Düğmeyi adlandırın `startButton` ve metin kutusunu adlandırın `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="0cf96-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="0cf96-120">İçin bir başvuru ekleyin <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="0cf96-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="0cf96-121">MainWindow.xaml.cs dosyasında, için bir yönerge ekleyin `using` `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="0cf96-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="0cf96-122">Kodu eklemek için</span><span class="sxs-lookup"><span data-stu-id="0cf96-122">To add the code</span></span>  
  
1. <span data-ttu-id="0cf96-123">Tasarım penceresinde, MainWindow. xaml, `startButton_Click` MainWindow.xaml.cs içinde olay işleyicisini oluşturmak için düğmeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="0cf96-124">Aşağıdaki kodu kopyalayın ve `startButton_Click` MainWindow.xaml.cs içindeki gövdesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="0cf96-125">Kod, uygulamayı yönlendiren bir zaman uyumsuz yöntemini çağırır `CreateMultipleTasksAsync` .</span><span class="sxs-lookup"><span data-stu-id="0cf96-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="0cf96-126">Aşağıdaki destek yöntemlerini projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0cf96-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="0cf96-127">`ProcessURLAsync`<xref:System.Net.Http.HttpClient>bir Web sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="0cf96-128">Destek yöntemi, `ProcessURLAsync` ardından dizinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cf96-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="0cf96-129">`DisplayResults`her URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="0cf96-130">Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0cf96-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="0cf96-131">Aşağıdaki yöntemleri kopyalayın ve `startButton_Click` MainWindow.xaml.cs içindeki olay işleyicisinden sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="0cf96-132">Son olarak, `CreateMultipleTasksAsync` aşağıdaki adımları gerçekleştiren yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="0cf96-133">Yöntemi `HttpClient` , içindeki yöntemine erişmeniz gereken bir nesne bildirir <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="0cf96-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="0cf96-134">Yöntemi, türünde üç görev oluşturur ve başlatır <xref:System.Threading.Tasks.Task%601> , burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="0cf96-135">Her görev bittiğinde, `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="0cf96-136">Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0cf96-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="0cf96-137">Yöntemi her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="0cf96-138">Her `await` operatör, `CreateMultipleTasksAsync` beklelen görev tamamlanana kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="0cf96-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="0cf96-139">İşleci, her tamamlanan görevden öğesine yapılan çağrıdan döndürülen değeri de alır `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="0cf96-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="0cf96-140">Görevler tamamlandığında ve tamsayı değerleri alınırsa, yöntemi web sitelerinin uzunluklarını toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0cf96-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="0cf96-141">Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="0cf96-142">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0cf96-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="0cf96-143">Üç görevin her zaman aynı sırada bitmeyeceğini ve bunların tamamların oluşturulma sırası ve bekledikleri sıra olması gerektiğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0cf96-143">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cf96-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cf96-144">Example</span></span>  
 <span data-ttu-id="0cf96-145">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="0cf96-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cf96-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf96-146">See also</span></span>

- [<span data-ttu-id="0cf96-147">İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="0cf96-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="0cf96-148">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="0cf96-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="0cf96-149">Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)</span><span class="sxs-lookup"><span data-stu-id="0cf96-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
