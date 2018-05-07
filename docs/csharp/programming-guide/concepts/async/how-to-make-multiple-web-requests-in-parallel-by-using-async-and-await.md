---
title: 'Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: e3e94c6ba475a56b5a2b7069eac1f1bbe45498c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)
Bir zaman uyumsuz yönteminde oluşturuldukları görevleri başlatılır. [Await](../../../../csharp/language-reference/keywords/await.md) işleci, burada işleme devam edemiyor görevi tamamlanana kadar yöntemi bir noktada göreve uygulanır. Genellikle, aşağıdaki örnekte gösterildiği gibi oluşturulduktan hemen sonra bir görev beklemenin.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Ancak, görev tamamlama sonrasında bağımlı değil programınızın gerçekleştirmek için diğer iş varsa, görev bekleniyor gelen görev oluşturma ayırabilirsiniz.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Bir görev başlatma ve onu bekleyen arasında diğer görevleri başlatabilirsiniz. Ek görevler örtük olarak paralel olarak çalışır, ancak hiçbir ek iş parçacığı oluşturulur.  
  
 Aşağıdaki programı üç zaman uyumsuz web yüklemeleri başlatır ve ardından bunları adlı sırada bekler. Bildirim, görevler, bunlar oluşturulan beklemenin ve sırayla her zaman son verme programı, çalıştırdığınızda. Bunlar, oluşturuldukları ve bekleme ifadeleri yöntemi erişmeden önce bir veya daha fazla görevleri son çalışmaya başlar.  
  
> [!NOTE]
>  Bu proje tamamlamak için Visual Studio 2012 veya sonraki sürümlerini ve .NET Framework 4.5 olmalıdır veya üstü yüklü.  
  
 Aynı anda birden çok görevi başlatan başka bir örnek için bkz: [nasıl yapılır: Task.WhenAll kullanarak (C#) tarafından izlenecek zaman uyumsuz genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu örnekte kodunu indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Projeyi ayarlamak için  
  
1.  WPF uygulamayı kurmak için aşağıdaki adımları tamamlayın. Ayrıntılı yönergeler için bu adımları bulabilirsiniz [izlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Bir düğmeyi ve bir metin kutusu içeren bir WPF uygulaması oluşturun. Düğme adının `startButton`ve metin kutusunun adı `resultsTextBox`.  
  
    -   İçin bir başvuru ekleyin <xref:System.Net.Http>.  
  
    -   MainWindow.xaml.cs dosyasına ekleyin bir `using` için yönerge `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Kod eklemek için  
  
1.  Tasarım penceresinde MainWindow.xaml, oluşturmak için düğmesini çift `startButton_Click` MainWindow.xaml.cs olay işleyicisi.  
  
2.  Aşağıdaki kodu kopyalayın ve gövdesine yapıştırın `startButton_Click` MainWindow.xaml.cs içinde.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod zaman uyumsuz bir yöntem çağırır `CreateMultipleTasksAsync`, uygulama sürücüler.  
  
3.  Aşağıdaki destek yöntemlerden projenize ekleyin:  
  
    -   `ProcessURLAsync` kullanan bir <xref:System.Net.Http.HttpClient> bir bayt dizisi olarak bir Web sitesi içeriğini indirmek için yöntem. Destek yöntemi `ProcessURLAsync` ardından görüntüler ve dizi uzunluğu döndürür.  
  
    -   `DisplayResults` bayt sayısını bayt dizisi, her URL için görüntüler. Bu görüntüler gösterir indirme her görev tamamlandığında.  
  
     Aşağıdaki yöntemlerden kopyalayabilir ve sonra yapıştırabilirsiniz `startButton_Click` MainWindow.xaml.cs olay işleyicisi.  
  
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
  
4.  Son olarak, yöntemi tanımlayın `CreateMultipleTasksAsync`, aşağıdaki adımları gerçekleştirir.  
  
    -   Yöntem bildiren bir `HttpClient` yöntemi erişimi için gereken nesne <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> içinde `ProcessURLAsync`.  
  
    -   Yöntem oluşturur ve üç görev türü başlatır <xref:System.Threading.Tasks.Task%601>, burada `TResult` bir tamsayıdır. Her görev bitirdiğinde `DisplayResults` görevin URL ve indirilen içeriği uzunluğunu görüntüler. Görevler zaman uyumsuz olarak çalıştığından, sonuçları görünme sırasını bildirilen siparişte farklı olabilir.  
  
    -   Yöntemi, her görevin tamamlanmasını bekler. Her `await` işleci askıya yürütülmesi `CreateMultipleTasksAsync` awaited görevi tamamlanana kadar. Operatör çağrısı dönüş değerini de alır `ProcessURLAsync` tamamlanan her görev.  
  
    -   Tamamlanan görevler ve tamsayı değerlerini alınan yöntemi Web sitelerinin uzunlukları toplar ve sonucu görüntüler.  
  
     Aşağıdaki yöntem kopyalayın ve çözümünüze yapıştırın.  
  
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
  
5.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Program, üç görev her zaman aynı sırada son yok ve hangi son siparişin, bunlar oluşturulan beklemenin sırada mutlaka olmadığından emin doğrulamak için birkaç kez çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam örnek içerir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
