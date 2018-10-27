---
title: 'Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: b366b43cf1c6114f02f026da25aeb5e30dc91c6f
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453430"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)
Yük oluşturulduğunda bir zaman uyumsuz yönteminde görevler oluşturulduklarında başlatılır. [Await](../../../../csharp/language-reference/keywords/await.md) işleci işlemenin devam edemediği görev tamamlanana kadar yöntem noktasındaki göreve uygulanır. Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklenir.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Ancak, görev öğesinin tamamlanmasına bağımlı değildir, programınızın gerçekleştirilecek başka işleri varsa, görevi bekleme işleminden görev oluşturma ayırabilirsiniz.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Bir görev başlatma ve bekleme arasında başka görevler başlatabilirsiniz. Ek görevler, örtülü olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulmaz.  
  
 Aşağıdaki program üç zaman uyumsuz web yüklemesini başlatır ve ardından bunları adlı sırayla bekler. Bu görev sırası, bunlar oluşturulan bekleniyor ve her zaman tamamlanmıyor programı çalıştırdığınızda dikkat edin. Oluşturuldukları ve yöntem bekleme ifadelerine ulaşmadan önce bir veya birkaç görev bitebilir çalışmaya başlayın.  
  
> [!NOTE]
>  Bu projeyi tamamlamak için Visual Studio 2012 veya üzeri ve .NET Framework 4.5 olmalıdır veya üzeri yüklü.  
  
 Aynı anda birden çok görevi başlatan başka bir örnek için bkz: [nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu örnekte kodunu indirebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Projeyi kurmak için  
  
1.  Bir WPF uygulaması ayarlamak için aşağıdaki adımları tamamlayın. İçinde bu adımlara ilişkin ayrıntılı yönergeleri bulabilirsiniz [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Bir metin kutusu ve bir düğmeyi içeren bir WPF uygulaması oluşturun. Düğmeyi adlandırın `startButton`ve metin kutusunu adlandırın `resultsTextBox`.  
  
    -   İçin bir başvuru eklemeniz <xref:System.Net.Http>.  
  
    -   MainWindow.xaml.cs dosyasında, ekleme bir `using` yönergesi `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Kod eklemek için  
  
1.  Tasarım penceresinde, MainWindow.xaml oluşturmak için düğmeyi çift tıklatın `startButton_Click` MainWindow.xaml.cs olay işleyicisi.  
  
2.  Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.cs içinde.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod, zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüleri.  
  
3.  Projeye şu destek yöntemlerini ekleyin:  
  
    -   `ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesinin içeriklerini karşıdan yüklemek için yöntemi. Destek yöntemi daha `ProcessURLAsync` ardından görüntüler ve dizinin uzunluğunu döndürür.  
  
    -   `DisplayResults` bayt sayısı, her bir URL için bayt dizisindeki görüntüler. Bu görüntüler gösterir her bir görevin indirmeyi bitirmesini.  
  
     Aşağıdaki yöntemleri kopyalayın ve sonra bunları yapıştırın `startButton_Click` MainWindow.xaml.cs olay işleyicisi.  
  
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
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
4.  Son olarak, yöntemi tanımlayan `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.  
  
    -   Yöntem bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.  
  
    -   Yöntemi oluşturur ve başlatır türünde üç görev <xref:System.Threading.Tasks.Task%601>burada `TResult` bir tamsayıdır. Her görev bittikçe `DisplayResults` görevin URL'sini ve karşıdan yüklenen içeriklerin uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçların görüntülenme sırasını bildirilmiş sırasından farklı olabilir.  
  
    -   Yöntem her görevin tamamlanmasını bekler. Her `await` işleci yürütmesini askıya alır `CreateMultipleTasksAsync` beklenen görev bitinceye kadar. İşleci ayrıca çağrısından dönen değer alır `ProcessURLAsync` her tamamlanan görevden.  
  
    -   Görevler tamamlandığında ve tamsayı değerleri alındığında, yöntem Web sitelerinin uzunluklarını toplar ve sonucu görüntüler.  
  
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
        resultsTextBox.Text +=  
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
    ```  
  
5.  Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
     Program üç görevin her zaman aynı sırada tamamlanmıyor ve hangi sıranın mutlaka, bunlar oluşturulan bekleniyor ve sırasını olmadığını doğrulamak için birkaç kez çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam örneği içermektedir.  
  
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
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
