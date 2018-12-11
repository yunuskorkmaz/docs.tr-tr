---
title: (Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: b1c56cb6d894dbcd9e70f06d7e5cd44b559b8cd4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148469"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="30db8-102">(Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="30db8-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>
<span data-ttu-id="30db8-103">Kullanarak bir süre sonra Zamanuyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> işlemin tamamlanmasını beklemek istemiyorsanız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="30db8-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="30db8-104">Bu yöntem tarafından belirlenen süre içinde tam olmayan herhangi bir ilişkili görevin iptalini zamanlar `CancelAfter` ifade.</span><span class="sxs-lookup"><span data-stu-id="30db8-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="30db8-105">Bu örnek içinde geliştirilen koda eklenir [zaman uyumsuz bir görev veya biri listeyi görevler (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Web sitesi listesini indirmek ve her birindeki içerik uzunluğunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="30db8-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30db8-106">Örnekleri çalıştırmak için Visual Studio 2012 veya sonraki sürümünü ve .NET Framework 4.5 olmalıdır veya daha sonra bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="30db8-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="30db8-107">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="30db8-107">Downloading the Example</span></span>  
 <span data-ttu-id="30db8-108">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanıza ince](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="30db8-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="30db8-109">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="30db8-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="30db8-110">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="30db8-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="30db8-111">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningVB için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="30db8-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="30db8-112">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAfterTime** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="30db8-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="30db8-113">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30db8-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="30db8-114">Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="30db8-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="30db8-115">Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="30db8-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="30db8-116">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.vb dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30db8-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="30db8-117">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="30db8-117">Building the Example</span></span>  
 <span data-ttu-id="30db8-118">Bu konudaki örnek içinde geliştirilen projeye ekler [zaman uyumsuz bir görev veya biri listeyi görevler (Visual Basic) iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Görevler listesini iptal etme.</span><span class="sxs-lookup"><span data-stu-id="30db8-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="30db8-119">Örnekte aynı Arabirim kullanılmaktadır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="30db8-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="30db8-120">Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelAListOfTasks** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="30db8-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="30db8-121">Bu konuda, değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="30db8-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="30db8-122">Görevleri iptal edildi olarak işaretlenmeden önceki süre üst sınırını belirtmek için bir çağrı ekleyin `CancelAfter` için `startButton_Click`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="30db8-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="30db8-123">Ayrıca, yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="30db8-123">The addition is marked with asterisks.</span></span>  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
        Await AccessTheWebAsync(cts.Token)  
        resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
    Catch ex As OperationCanceledException  
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
    Catch ex As Exception  
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
    End Try  
  
    ' Set the CancellationTokenSource to Nothing when the download is complete.  
    cts = Nothing  
End Sub  
```  
  
 <span data-ttu-id="30db8-124">Program çıkış tüm Web siteleri, hiçbir Web sitesi veya bazı web siteleri için çıktı gösterebildiğini doğrulamak için birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="30db8-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="30db8-125">Aşağıdaki çıktı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="30db8-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="30db8-126">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="30db8-126">Complete Example</span></span>  
 <span data-ttu-id="30db8-127">Aşağıdaki örnek için MainWindow.xaml.vb dosyanın tam metni kodudur.</span><span class="sxs-lookup"><span data-stu-id="30db8-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="30db8-128">Yıldız işaretleri, bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="30db8-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="30db8-129">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="30db8-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="30db8-130">Projeden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="30db8-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="30db8-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30db8-131">See Also</span></span>  
 [<span data-ttu-id="30db8-132">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30db8-132">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="30db8-133">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30db8-133">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="30db8-134">Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="30db8-134">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [<span data-ttu-id="30db8-135">(Visual Basic) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="30db8-135">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="30db8-136">Zaman uyumsuz örneği: Uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="30db8-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
