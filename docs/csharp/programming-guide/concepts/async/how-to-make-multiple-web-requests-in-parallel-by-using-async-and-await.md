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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)
Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır. [Await](../../../language-reference/operators/await.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır. Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Ancak, programın gerçekleştirmeye yönelik başka bir işi olması durumunda görevin tamamlanmasına bağlı olmaması durumunda görevi bekleyen görev oluşturmayı ayırabilirsiniz.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Bir görevi başlatma ve bekleme arasında başka görevler de başlatabilirsiniz. Ek görevler dolaylı olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.  
  
 Aşağıdaki program, üç zaman uyumsuz Web yüklemesi başlatır ve ardından bunların çağrıldıkları sırayla bekler. Programı çalıştırdığınızda, görevlerin Oluşturulma sırasında ve bekledikleri sırada her zaman bitmediğine dikkat edin. Bunlar oluşturulduğunda çalışmaya başlar ve Yöntem await ifadelerine ulaşmadan önce bir veya daha fazla görev bitebilirler.  
  
> [!NOTE]
> Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.  
  
 Aynı anda birden çok görevi Başlatan başka bir örnek için, bkz. [Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.  
  
### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için  
  
1. WPF uygulaması ayarlamak için aşağıdaki adımları izleyin. [Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişmek](./walkthrough-accessing-the-web-by-using-async-and-await.md)için bu adımlarla ilgili ayrıntılı yönergeleri bulabilirsiniz.  
  
    - Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun. Düğmeyi adlandırın `startButton` ve metin kutusunu adlandırın `resultsTextBox` .  
  
    - İçin bir başvuru ekleyin <xref:System.Net.Http> .  
  
    - MainWindow.xaml.cs dosyasında, için bir yönerge ekleyin `using` `System.Net.Http` .  
  
### <a name="to-add-the-code"></a>Kodu eklemek için  
  
1. Tasarım penceresinde, MainWindow. xaml, `startButton_Click` MainWindow.xaml.cs içinde olay işleyicisini oluşturmak için düğmeye çift tıklayın.  
  
2. Aşağıdaki kodu kopyalayın ve `startButton_Click` MainWindow.xaml.cs içindeki gövdesine yapıştırın.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod, uygulamayı yönlendiren bir zaman uyumsuz yöntemini çağırır `CreateMultipleTasksAsync` .  
  
3. Aşağıdaki destek yöntemlerini projeye ekleyin:  
  
    - `ProcessURLAsync`<xref:System.Net.Http.HttpClient>bir Web sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır. Destek yöntemi, `ProcessURLAsync` ardından dizinin uzunluğunu görüntüler ve döndürür.  
  
    - `DisplayResults`her URL için bayt dizisindeki bayt sayısını görüntüler. Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.  
  
     Aşağıdaki yöntemleri kopyalayın ve `startButton_Click` MainWindow.xaml.cs içindeki olay işleyicisinden sonra yapıştırın.  
  
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
  
4. Son olarak, `CreateMultipleTasksAsync` aşağıdaki adımları gerçekleştiren yöntemi tanımlayın.  
  
    - Yöntemi `HttpClient` , içindeki yöntemine erişmeniz gereken bir nesne bildirir <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> `ProcessURLAsync` .  
  
    - Yöntemi, türünde üç görev oluşturur ve başlatır <xref:System.Threading.Tasks.Task%601> , burada `TResult` bir tamsayıdır. Her görev bittiğinde, `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.  
  
    - Yöntemi her görevin tamamlanmasını bekler. Her `await` operatör, `CreateMultipleTasksAsync` beklelen görev tamamlanana kadar yürütmeyi askıya alır. İşleci, her tamamlanan görevden öğesine yapılan çağrıdan döndürülen değeri de alır `ProcessURLAsync` .  
  
    - Görevler tamamlandığında ve tamsayı değerleri alınırsa, yöntemi web sitelerinin uzunluklarını toplar ve sonucu görüntüler.  
  
     Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.  
  
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
  
5. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.  
  
     Üç görevin her zaman aynı sırada bitmeyeceğini ve bunların tamamların oluşturulma sırası ve bekledikleri sıra olması gerektiğini doğrulamak için programı birkaç kez çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam örneği içerir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
- [Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
