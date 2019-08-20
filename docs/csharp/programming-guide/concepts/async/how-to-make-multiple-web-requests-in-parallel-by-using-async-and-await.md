---
title: 'Nasıl yapılır: Async ve await (C#) kullanarak birden çok web isteğini paralel hale getirme'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 75425764ff9ce4f97aac147ced4c57bf1a10714b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595569"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Nasıl yapılır: Async ve await (C#) kullanarak birden çok web isteğini paralel hale getirme
Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır. [Await](../../../language-reference/keywords/await.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır. Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.  
  
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
>  Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.  
  
 Aynı anda birden çok görevi Başlatan başka bir örnek için bkz [. nasıl yapılır: Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)kullanarak zaman uyumsuz izlenecek yolu genişletin.  
  
 Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.  
  
### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için  
  
1. WPF uygulaması ayarlamak için aşağıdaki adımları izleyin. Bu adımlar [için ayrıntılı yönergeleri gözden geçirmede bulabilirsiniz: Async ve await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.  
  
    - Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun. Düğmeyi `startButton`adlandırın ve metin kutusunu `resultsTextBox`adlandırın.  
  
    - İçin <xref:System.Net.Http>bir başvuru ekleyin.  
  
    - MainWindow.xaml.cs dosyasında, için `using` `System.Net.Http`bir yönerge ekleyin.  
  
### <a name="to-add-the-code"></a>Kodu eklemek için  
  
1. Tasarım penceresinde, MainWindow. xaml, MainWindow.xaml.cs içinde `startButton_Click` olay işleyicisini oluşturmak için düğmeye çift tıklayın.  
  
2. Aşağıdaki kodu kopyalayın ve MainWindow.xaml.cs `startButton_Click` içindeki gövdesine yapıştırın.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod, uygulamayı yönlendiren bir zaman uyumsuz `CreateMultipleTasksAsync`yöntemini çağırır.  
  
3. Aşağıdaki destek yöntemlerini projeye ekleyin:  
  
    - `ProcessURLAsync`bir Web <xref:System.Net.Http.HttpClient> sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır. Destek yöntemi, `ProcessURLAsync` ardından dizinin uzunluğunu görüntüler ve döndürür.  
  
    - `DisplayResults`her URL için bayt dizisindeki bayt sayısını görüntüler. Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.  
  
     Aşağıdaki yöntemleri kopyalayın ve MainWindow.xaml.cs içindeki `startButton_Click` olay işleyicisinden sonra yapıştırın.  
  
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
  
4. Son olarak, aşağıdaki `CreateMultipleTasksAsync`adımları gerçekleştiren yöntemi tanımlayın.  
  
    - Yöntemi, içindeki `HttpClient` <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemine`ProcessURLAsync`erişmeniz gereken bir nesne bildirir.  
  
    - Yöntemi, türünde <xref:System.Threading.Tasks.Task%601>üç görev oluşturur ve başlatır, burada `TResult` bir tamsayıdır. Her görev bittiğinde, `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.  
  
    - Yöntemi her görevin tamamlanmasını bekler. Her `await` operatör, beklelen `CreateMultipleTasksAsync` görev tamamlanana kadar yürütmeyi askıya alır. İşleci, her tamamlanan görevden öğesine `ProcessURLAsync` yapılan çağrıdan döndürülen değeri de alır.  
  
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

- [İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)
- [Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
