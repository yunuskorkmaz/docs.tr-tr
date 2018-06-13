---
title: Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: e27f8e67ff03260e1d13fa633064efc2059e6bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340222"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="f2216-102">Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)</span><span class="sxs-lookup"><span data-stu-id="f2216-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="f2216-103">İş parçacığı sınıfı oluşturucusu bağımsız değişken almayan ve herhangi bir değer döndüren bir yordam için bir başvuru geçirilmelidir sağlayarak ve birden çok iş parçacıklı uygulamada değerler döndüren karmaşık olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2216-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="f2216-104">Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2216-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="f2216-105">Birden çok iş parçacıklı yordamlar için parametreleri belirtin</span><span class="sxs-lookup"><span data-stu-id="f2216-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="f2216-106">Birden çok iş parçacıklı yöntem çağrısı için parametreleri sağlamak için en iyi bir sınıfta hedef yöntemin sarmalayın ve üzerinde yeni bir iş parçacığı için parametre olarak hizmet verecektir o sınıfın alanlarını tanımlamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="f2216-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="f2216-107">Bu yaklaşımın avantajı, yeni bir iş parçacığı başlatmak istediğiniz her zaman kendi parametrelerle sınıfının yeni bir örneğini oluşturmak ' dir.</span><span class="sxs-lookup"><span data-stu-id="f2216-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="f2216-108">Örneğin, aşağıdaki kod olduğu gibi bir üçgen alanının hesaplar bir işlevi olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="f2216-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="f2216-109">Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve girdi parametresi şu şekilde depolamak için alanlar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f2216-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="f2216-110">Kullanılacak `AreaClass`, oluşturabileceğiniz bir `AreaClass` nesne ve ayarlama `Base` ve `Height` aşağıdaki kodda gösterildiği gibi özellikleri:</span><span class="sxs-lookup"><span data-stu-id="f2216-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 <span data-ttu-id="f2216-111">Dikkat `TestArea` yordamı değerini denetlemez `Area` çağırdıktan sonra alan `CalcArea` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2216-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="f2216-112">Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan hemen çağrıldıktan sonra işaretlerseniz ayarlanacak garanti edilmez `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="f2216-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="f2216-113">Sonraki bölümde, birden çok iş parçacıklı yordamlardan dönüş değerleri daha iyi bir yolu anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2216-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="f2216-114">Birden çok iş parçacıklı yordamlardan dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="f2216-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="f2216-115">Ayrı iş parçacıklarına çalıştırmak yordamları değerler döndürme yordamları işlevleri olamaz ve kullanamazsınız olgusu karmaşık `ByRef` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="f2216-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="f2216-116">Dönüş değerleri yapmanın en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> , iş parçacıkları yönetmek ve görev tamamlandığında, bir olayı ve bir olay işleyicisi sonuçlarıyla işlemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="f2216-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="f2216-117">Aşağıdaki örnek, bir olay ayrı bir iş parçacığı üzerinde çalışan bir yordamdan yükselterek bir değer döndürür:</span><span class="sxs-lookup"><span data-stu-id="f2216-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 <span data-ttu-id="f2216-118">Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durum nesnesi değişken <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2216-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="f2216-119">İş parçacığı-Zamanlayıcı iş parçacığı, bu amaç için bir durum nesnesi de destekler.</span><span class="sxs-lookup"><span data-stu-id="f2216-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="f2216-120">İş parçacığı havuzu ve iş parçacığı zamanlayıcılar hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) ve [iş parçacığı zamanlayıcılar (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="f2216-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Thread Timers (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2216-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2216-121">See Also</span></span>  
 [<span data-ttu-id="f2216-122">İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="f2216-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="f2216-123">İş parçacığı havuzu (C#)</span><span class="sxs-lookup"><span data-stu-id="f2216-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="f2216-124">İş parçacığı eşitleme (C#)</span><span class="sxs-lookup"><span data-stu-id="f2216-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="f2216-125">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f2216-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="f2216-126">Birden çok iş parçacıklı uygulamalar (C#)</span><span class="sxs-lookup"><span data-stu-id="f2216-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="f2216-127">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f2216-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="f2216-128">Bileşenleri çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="f2216-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
