---
title: Parametreler ve dönüş değerleri için birden çok iş parçacıklı yordamlar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 545da3e89d44c29c67784b5f01812d87350030c6
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874617"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="bfd9f-102">Parametreler ve dönüş değerleri için birden çok iş parçacıklı yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd9f-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="bfd9f-103">İş parçacığı sınıfı Oluşturucu hiçbir bağımsız değişkeni alır ve hiçbir değer döndürmeyen bir yordam başvuru geçirilmelidir sağlayarak ve değerler döndüren bir çok iş parçacıklı uygulamada karmaşık olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="bfd9f-104">Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="bfd9f-105">Çok iş parçacıklı yordamlar için parametreleri belirtin</span><span class="sxs-lookup"><span data-stu-id="bfd9f-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="bfd9f-106">Çok iş parçacıklı bir yöntem çağrısı için parametreleri sağlamak için en iyi yolu, hedef yöntemin bir sınıf içinde sarmalamak ve yeni iş parçacığı için parametre olarak hizmet verecek o sınıf için alanları tanımlayan sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="bfd9f-107">Bu yaklaşımın avantajı, yeni bir iş parçacığı istediğiniz her seferinde, sınıfının yeni bir örneğini kendi parametrelerle oluşturabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="bfd9f-108">Örneğin, aşağıdaki kodda gösterildiği gibi bir üçgen alanını hesaplayan bir işlevi olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="bfd9f-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="bfd9f-109">Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve giriş parametresi gibi depolamak için alanları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfd9f-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="bfd9f-110">Kullanılacak `AreaClass`, oluşturabileceğiniz bir `AreaClass` nesne ve ayarlama `Base` ve `Height` aşağıdaki kodda gösterildiği gibi özellikleri:</span><span class="sxs-lookup"><span data-stu-id="bfd9f-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 <span data-ttu-id="bfd9f-111">Dikkat `TestArea` yordamı değerini denetlemez `Area` arama sonra alan `CalcArea` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="bfd9f-112">Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan çağırdıktan hemen sonra onay ayarlanacak garanti edilmez `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="bfd9f-113">Sonraki bölümde, dönüş değerleri çok iş parçacıklı yordamlar için daha iyi bir yolu anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="bfd9f-114">Çok iş parçacıklı yordamlar değerler döndüren</span><span class="sxs-lookup"><span data-stu-id="bfd9f-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="bfd9f-115">Ayrı iş parçacıkları üzerinde çalıştırılan yordamları değerleri döndürme yordamlar, İşlevler olamaz ve kullanamazsınız gerçeğiyle karmaşık `ByRef` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="bfd9f-116">Dönüş değerleri için en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> dizilerinizi yönetmek ve görev tamamlandığında bir olay tetikleyebilir ve bir olay işleyicisi ile sonuçları işlemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="bfd9f-117">Aşağıdaki örnek, bir olay ayrı bir iş parçacığı üzerinde çalışan bir yordamdan yükselterek bir değer döndürür:</span><span class="sxs-lookup"><span data-stu-id="bfd9f-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 <span data-ttu-id="bfd9f-118">Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durumu nesne değişkeni <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="bfd9f-119">İş parçacığı Zamanlayıcı iş parçacıklarını durum nesnesi bu amaç için de destekler.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="bfd9f-120">İş parçacığı havuzu ve iş parçacığı zamanlayıcıları hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[iş parçacığı havuzu](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) ve [zamanlayıcılar](../../../../standard/threading/timers.md).</span><span class="sxs-lookup"><span data-stu-id="bfd9f-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Timers](../../../../standard/threading/timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd9f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfd9f-121">See Also</span></span>  
 [<span data-ttu-id="bfd9f-122">İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="bfd9f-122">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="bfd9f-123">İş parçacığı havuzu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd9f-123">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="bfd9f-124">İş parçacığı eşitleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd9f-124">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="bfd9f-125">Olaylar</span><span class="sxs-lookup"><span data-stu-id="bfd9f-125">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="bfd9f-126">Çok iş parçacıklı uygulamalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd9f-126">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="bfd9f-127">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="bfd9f-127">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="bfd9f-128">Bileşenlerinde çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="bfd9f-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
