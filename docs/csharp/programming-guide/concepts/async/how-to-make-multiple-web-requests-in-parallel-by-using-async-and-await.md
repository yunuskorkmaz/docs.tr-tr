---
title: 'Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: c8f1c9a134af2139f3dd0d76614b1f719b4d453c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547650"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="5e09c-102">Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5e09c-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="5e09c-103">Yük oluşturulduğunda bir zaman uyumsuz yönteminde görevler oluşturulduklarında başlatılır.</span><span class="sxs-lookup"><span data-stu-id="5e09c-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="5e09c-104">[Await](../../../../csharp/language-reference/keywords/await.md) işleci işlemenin devam edemediği görev tamamlanana kadar yöntem noktasındaki göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e09c-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="5e09c-105">Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklenir.</span><span class="sxs-lookup"><span data-stu-id="5e09c-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="5e09c-106">Ancak, görev öğesinin tamamlanmasına bağımlı değildir, programınızın gerçekleştirilecek başka işleri varsa, görevi bekleme işleminden görev oluşturma ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e09c-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="5e09c-107">Bir görev başlatma ve bekleme arasında başka görevler başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e09c-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="5e09c-108">Ek görevler, örtülü olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="5e09c-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="5e09c-109">Aşağıdaki program üç zaman uyumsuz web yüklemesini başlatır ve ardından bunları adlı sırayla bekler.</span><span class="sxs-lookup"><span data-stu-id="5e09c-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="5e09c-110">Bu görev sırası, bunlar oluşturulan bekleniyor ve her zaman tamamlanmıyor programı çalıştırdığınızda dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5e09c-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="5e09c-111">Oluşturuldukları ve yöntem bekleme ifadelerine ulaşmadan önce bir veya birkaç görev bitebilir çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="5e09c-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e09c-112">Bu projeyi tamamlamak için Visual Studio 2012 veya üzeri ve .NET Framework 4.5 olmalıdır veya üzeri yüklü.</span><span class="sxs-lookup"><span data-stu-id="5e09c-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="5e09c-113">Aynı anda birden çok görevi başlatan başka bir örnek için bkz [nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="5e09c-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="5e09c-114">Bu örnekte kodunu indirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="5e09c-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="5e09c-115">Projeyi kurmak için</span><span class="sxs-lookup"><span data-stu-id="5e09c-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="5e09c-116">Bir WPF uygulaması ayarlamak için aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="5e09c-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="5e09c-117">İçinde bu adımlara ilişkin ayrıntılı yönergeleri bulabilirsiniz [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5e09c-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="5e09c-118">Bir metin kutusu ve bir düğmeyi içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e09c-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="5e09c-119">Düğmeyi adlandırın `startButton`ve metin kutusunu adlandırın `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="5e09c-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="5e09c-120">İçin bir başvuru eklemeniz <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="5e09c-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="5e09c-121">MainWindow.xaml.cs dosyasında, ekleme bir `using` yönergesi `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="5e09c-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="5e09c-122">Kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="5e09c-122">To add the code</span></span>  
  
1.  <span data-ttu-id="5e09c-123">Tasarım penceresinde, MainWindow.xaml oluşturmak için düğmeyi çift tıklatın `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5e09c-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="5e09c-124">Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.cs içinde.</span><span class="sxs-lookup"><span data-stu-id="5e09c-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="5e09c-125">Kod, zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüleri.</span><span class="sxs-lookup"><span data-stu-id="5e09c-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="5e09c-126">Projeye şu destek yöntemlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5e09c-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="5e09c-127">`ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesinin içeriklerini karşıdan yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5e09c-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="5e09c-128">Destek yöntemi daha `ProcessURLAsync` ardından görüntüler ve dizinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e09c-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="5e09c-129">`DisplayResults` bayt sayısı, her bir URL için bayt dizisindeki görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e09c-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="5e09c-130">Bu görüntüler gösterir her bir görevin indirmeyi bitirmesini.</span><span class="sxs-lookup"><span data-stu-id="5e09c-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="5e09c-131">Aşağıdaki yöntemleri kopyalayın ve sonra bunları yapıştırın `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5e09c-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4.  <span data-ttu-id="5e09c-132">Son olarak, yöntemi tanımlayan `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e09c-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="5e09c-133">Yöntem bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="5e09c-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="5e09c-134">Yöntemi oluşturur ve başlatır türünde üç görev <xref:System.Threading.Tasks.Task%601>burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="5e09c-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="5e09c-135">Her görev bittikçe `DisplayResults` görevin URL'sini ve karşıdan yüklenen içeriklerin uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e09c-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="5e09c-136">Görevler zaman uyumsuz olarak çalıştığından, sonuçların görüntülenme sırasını bildirilmiş sırasından farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e09c-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="5e09c-137">Yöntem her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="5e09c-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="5e09c-138">Her `await` işleci yürütmesini askıya alır `CreateMultipleTasksAsync` beklenen görev bitinceye kadar.</span><span class="sxs-lookup"><span data-stu-id="5e09c-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="5e09c-139">İşleci ayrıca çağrısından dönen değer alır `ProcessURLAsync` her tamamlanan görevden.</span><span class="sxs-lookup"><span data-stu-id="5e09c-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="5e09c-140">Görevler tamamlandığında ve tamsayı değerleri alındığında, yöntem Web sitelerinin uzunluklarını toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e09c-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="5e09c-141">Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="5e09c-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5.  <span data-ttu-id="5e09c-142">Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5e09c-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="5e09c-143">Program üç görevin her zaman aynı sırada tamamlanmıyor ve hangi sıranın mutlaka, bunlar oluşturulan bekleniyor ve sırasını olmadığını doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5e09c-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e09c-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e09c-144">Example</span></span>  
 <span data-ttu-id="5e09c-145">Aşağıdaki kod tam örneği içermektedir.</span><span class="sxs-lookup"><span data-stu-id="5e09c-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e09c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e09c-146">See also</span></span>

- [<span data-ttu-id="5e09c-147">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5e09c-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="5e09c-148">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5e09c-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="5e09c-149">Nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)</span><span class="sxs-lookup"><span data-stu-id="5e09c-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
