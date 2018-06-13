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
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)
İş parçacığı sınıfı oluşturucusu bağımsız değişken almayan ve herhangi bir değer döndüren bir yordam için bir başvuru geçirilmelidir sağlayarak ve birden çok iş parçacıklı uygulamada değerler döndüren karmaşık olmasıdır. Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Birden çok iş parçacıklı yordamlar için parametreleri belirtin  
 Birden çok iş parçacıklı yöntem çağrısı için parametreleri sağlamak için en iyi bir sınıfta hedef yöntemin sarmalayın ve üzerinde yeni bir iş parçacığı için parametre olarak hizmet verecektir o sınıfın alanlarını tanımlamak için yoludur. Bu yaklaşımın avantajı, yeni bir iş parçacığı başlatmak istediğiniz her zaman kendi parametrelerle sınıfının yeni bir örneğini oluşturmak ' dir. Örneğin, aşağıdaki kod olduğu gibi bir üçgen alanının hesaplar bir işlevi olduğunu varsayalım:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve girdi parametresi şu şekilde depolamak için alanlar oluşturur:  
  
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
  
 Kullanılacak `AreaClass`, oluşturabileceğiniz bir `AreaClass` nesne ve ayarlama `Base` ve `Height` aşağıdaki kodda gösterildiği gibi özellikleri:  
  
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
  
 Dikkat `TestArea` yordamı değerini denetlemez `Area` çağırdıktan sonra alan `CalcArea` yöntemi. Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan hemen çağrıldıktan sonra işaretlerseniz ayarlanacak garanti edilmez `Thread.Start`. Sonraki bölümde, birden çok iş parçacıklı yordamlardan dönüş değerleri daha iyi bir yolu anlatılmaktadır.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Birden çok iş parçacıklı yordamlardan dönüş değerleri  
 Ayrı iş parçacıklarına çalıştırmak yordamları değerler döndürme yordamları işlevleri olamaz ve kullanamazsınız olgusu karmaşık `ByRef` bağımsız değişkenler. Dönüş değerleri yapmanın en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> , iş parçacıkları yönetmek ve görev tamamlandığında, bir olayı ve bir olay işleyicisi sonuçlarıyla işlemek için bileşen.  
  
 Aşağıdaki örnek, bir olay ayrı bir iş parçacığı üzerinde çalışan bir yordamdan yükselterek bir değer döndürür:  
  
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
  
 Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durum nesnesi değişken <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. İş parçacığı-Zamanlayıcı iş parçacığı, bu amaç için bir durum nesnesi de destekler. İş parçacığı havuzu ve iş parçacığı zamanlayıcılar hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) ve [iş parçacığı zamanlayıcılar (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [İş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [İş parçacığı eşitleme (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Olaylar](../../../../csharp/programming-guide/events/index.md)  
 [Birden çok iş parçacıklı uygulamalar (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Temsilciler](../../../../csharp/programming-guide/delegates/index.md)  
 [Bileşenleri çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
