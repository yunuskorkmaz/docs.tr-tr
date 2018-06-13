---
title: 'Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: e3e94c6ba475a56b5a2b7069eac1f1bbe45498c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337762"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="ec566-102">Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)</span><span class="sxs-lookup"><span data-stu-id="ec566-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="ec566-103">Bir zaman uyumsuz yönteminde oluşturuldukları görevleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ec566-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="ec566-104">[Await](../../../../csharp/language-reference/keywords/await.md) işleci, burada işleme devam edemiyor görevi tamamlanana kadar yöntemi bir noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ec566-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="ec566-105">Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklemenin.</span><span class="sxs-lookup"><span data-stu-id="ec566-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="ec566-106">Ancak, görev tamamlama sonrasında bağımlı değil programınızın gerçekleştirmek için diğer iş varsa, görev bekleniyor gelen görev oluşturma ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec566-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="ec566-107">Bir görev başlatma ve onu bekleyen arasında diğer görevleri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec566-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="ec566-108">Ek görevler örtük olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ec566-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="ec566-109">Aşağıdaki programı üç zaman uyumsuz web yüklemeleri başlatır ve ardından bunları adlı sırada bekler.</span><span class="sxs-lookup"><span data-stu-id="ec566-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="ec566-110">Bildirim, görevler, bunlar oluşturulan beklemenin ve sırayla her zaman son verme programı, çalıştırdığınızda.</span><span class="sxs-lookup"><span data-stu-id="ec566-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="ec566-111">Bunlar, oluşturuldukları ve bekleme ifadeleri yöntemi erişmeden önce bir veya daha fazla görevleri son çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="ec566-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec566-112">Bu proje tamamlamak için Visual Studio 2012 veya sonraki sürümlerini ve .NET Framework 4.5 olmalıdır veya üstü yüklü.</span><span class="sxs-lookup"><span data-stu-id="ec566-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="ec566-113">Aynı anda birden çok görevi başlatan başka bir örnek için bkz: [nasıl yapılır: Task.WhenAll kullanarak (C#) tarafından izlenecek zaman uyumsuz genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="ec566-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="ec566-114">Bu örnekte kodunu indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="ec566-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="ec566-115">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ec566-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="ec566-116">WPF uygulamayı kurmak için aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="ec566-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="ec566-117">Ayrıntılı yönergeler için bu adımları bulabilirsiniz [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ec566-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="ec566-118">Bir düğmeyi ve bir metin kutusu içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec566-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="ec566-119">Düğme adının `startButton`ve metin kutusunun adı `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="ec566-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="ec566-120">İçin bir başvuru ekleyin <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="ec566-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="ec566-121">MainWindow.xaml.cs dosyasına ekleyin bir `using` için yönerge `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="ec566-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="ec566-122">Kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="ec566-122">To add the code</span></span>  
  
1.  <span data-ttu-id="ec566-123">Tasarım penceresinde MainWindow.xaml, oluşturmak için düğmesini çift `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ec566-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="ec566-124">Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.cs içinde.</span><span class="sxs-lookup"><span data-stu-id="ec566-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="ec566-125">Kod zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüler.</span><span class="sxs-lookup"><span data-stu-id="ec566-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="ec566-126">Aşağıdaki destek yöntemlerden projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ec566-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="ec566-127">`ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesi içeriğini indirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ec566-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="ec566-128">Destek yöntemi `ProcessURLAsync` ardından görüntüler ve dizi uzunluğu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec566-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="ec566-129">`DisplayResults` bayt sayısını bayt dizisi, her URL için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec566-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="ec566-130">Bu görüntüler gösterir indirme her görev tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="ec566-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="ec566-131">Aşağıdaki yöntemlerden kopyalayabilir ve sonra yapıştırabilirsiniz `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ec566-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
4.  <span data-ttu-id="ec566-132">Son olarak, yöntemi tanımlayın `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ec566-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="ec566-133">Yöntem bildiren bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec566-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="ec566-134">Yöntem oluşturur ve üç görev türü başlatır <xref:System.Threading.Tasks.Task%601>, burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="ec566-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="ec566-135">Her görev bitirdiğinde `DisplayResults` görevin URL ve indirilen içeriği uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec566-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="ec566-136">Görevler zaman uyumsuz olarak çalıştığından, sonuçları görünme sırasını bildirilen siparişte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec566-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="ec566-137">Yöntemi, her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ec566-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="ec566-138">Her `await` işleci askıya yürütülmesi `CreateMultipleTasksAsync` awaited görevi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="ec566-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="ec566-139">Operatör çağrısı dönüş değerini de alır `ProcessURLAsync` tamamlanan her görev.</span><span class="sxs-lookup"><span data-stu-id="ec566-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="ec566-140">Tamamlanan görevler ve tamsayı değerlerini alınan yöntemi Web sitelerinin uzunlukları toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec566-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="ec566-141">Aşağıdaki yöntem kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec566-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
            ProcessURLAsync("http://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text +=  
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
    ```  
  
5.  <span data-ttu-id="ec566-142">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ec566-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ec566-143">Program, üç görev her zaman aynı sırada son yok ve hangi son siparişin, bunlar oluşturulan beklemenin sırada mutlaka olmadığından emin doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec566-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec566-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec566-144">Example</span></span>  
 <span data-ttu-id="ec566-145">Aşağıdaki kod, tam örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="ec566-145">The following code contains the full example.</span></span>  
  
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
                ProcessURLAsync("http://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec566-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec566-146">See Also</span></span>  
 [<span data-ttu-id="ec566-147">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="ec566-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="ec566-148">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="ec566-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="ec566-149">Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme</span><span class="sxs-lookup"><span data-stu-id="ec566-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
