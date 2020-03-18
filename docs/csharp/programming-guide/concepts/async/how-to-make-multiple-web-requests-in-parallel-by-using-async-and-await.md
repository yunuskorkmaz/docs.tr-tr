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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl
Async yönteminde, görevler oluşturulduklarında başlatılır. [Bekleme](../../../language-reference/operators/await.md) işleci, görev bitene kadar işlemenin devam edilemeyebildiği yöntemdeki noktada göreve uygulanır. Genellikle bir görev, aşağıdaki örnekte görüldüğü gibi, oluşturulduğu anda beklenilir.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Ancak, programınızın gerçekleştirmesi gereken ve görevin tamamlanmasına bağlı olmayan başka işleri varsa, görevi beklemekten görevi ayırabilirsiniz.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Bir görevi başlatmak ve beklemek arasında, diğer görevleri başlatabilirsiniz. Ek görevler örtülü olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.  
  
 Aşağıdaki program üç eşzamanlı web indirme başlar ve daha sonra çağrıldıkları sırada onları bekliyor. Programı çalıştırdığınızda, görevlerin her zaman oluşturuldukları ve beklendikleri sırada bitmediklerine dikkat edin. Oluşturulduklarında çalışmaya başlarlar ve yöntem bekleyen ifadelere ulaşmadan önce görevlerden biri veya birkaçı tamamlanabilir.  
  
> [!NOTE]
> Bu projeyi tamamlamak için Visual Studio 2012 veya üstü ve .NET Framework 4.5 veya daha yüksek bilgisayarınıza yüklü olması gerekir.  
  
 Aynı anda birden çok görevi başlatan başka bir örnek için, [Task.WhenAll (C#) kullanarak async walkthrough'u nasıl genişletirebilirsiniz.](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
  
 Bu örnek için kodu [Geliştirici Kodu Örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.  
  
### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için  
  
1. Bir WPF uygulaması ayarlamak için aşağıdaki adımları tamamlayın. [Walkthrough: Access ingsync kullanarak web'e erişim ve (C#) bekliyor.](./walkthrough-accessing-the-web-by-using-async-and-await.md)  
  
    - Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun. Düğmeyi `startButton`adlandırın ve metin `resultsTextBox`kutusunu adlandırın.  
  
    - Için <xref:System.Net.Http>bir başvuru ekleyin.  
  
    - MainWindow.xaml.cs dosyasında, `using` `System.Net.Http`için bir yönerge ekleyin.  
  
### <a name="to-add-the-code"></a>Kodu eklemek için  
  
1. Tasarım penceresinde, MainWindow.xaml, MainWindow.xaml.cs olay işleyicisi `startButton_Click` oluşturmak için düğmesini çift tıklatın.  
  
2. Aşağıdaki kodu kopyalayın ve MainWindow.xaml.cs'nin `startButton_Click` gövdesine yapıştırın.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod, `CreateMultipleTasksAsync`uygulamayı yönlendiren bir eşzamanlı yöntem çağırır.  
  
3. Projeye aşağıdaki destek yöntemlerini ekleyin:  
  
    - `ProcessURLAsync`bir <xref:System.Net.Http.HttpClient> web sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır. Destek yöntemi, `ProcessURLAsync` daha sonra dizinin uzunluğunu görüntüler ve döndürür.  
  
    - `DisplayResults`her URL için bayt dizisinde bayt sayısını görüntüler. Bu ekran, her görevin karşıdan yüklemeyi ne zaman tamamlarolduğunu gösterir.  
  
     Aşağıdaki yöntemleri kopyalayın ve MainWindow.xaml.cs `startButton_Click` olay işleyicisi sonra yapıştırın.  
  
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
  
4. Son olarak, `CreateMultipleTasksAsync`aşağıdaki adımları gerçekleştiren yöntemi tanımlayın.  
  
    - Yöntem, `ProcessURLAsync`'de `HttpClient` metne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> erişmeniz gereken bir nesneyi bildirir.  
  
    - Yöntem oluşturur ve bir <xref:System.Threading.Tasks.Task%601>karşıcı türü `TResult` , üç görev başlatır. Her görev sona `DisplayResults` ererken, görevin URL'sini ve indirilen içeriğin uzunluğunu görüntüler. Görevler eşzamanlı olarak çalıştığı için, sonuçların görüntülenme sırası, beyan edildikleri sırayla farklı olabilir.  
  
    - Yöntem, her görevin tamamlanmasını bekler. Her `await` işleç, `CreateMultipleTasksAsync` beklenen görev tamamlanana kadar yürütmeyi askıya adatır. İşletici ayrıca, tamamlanan her `ProcessURLAsync` görevden aramadan iade değerini de alır.  
  
    - Görevler tamamlandığında ve sonda değerleri alındığında, yöntem web sitelerinin uzunluklarını toplama gelir ve sonucu görüntüler.  
  
     Aşağıdaki yöntemi kopyalayın ve çözüme yapıştırın.  
  
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
  
5. Programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin.  
  
     Üç görevin her zaman aynı sırada tamamlanmadığını ve bitirdikleri sıranın oluşturuldukları ve beklendikleri sıra olmadığını doğrulamak için programı birkaç kez çalıştırın.  
  
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

- [Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
