---
title: Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: 218e297d192d37d55ff391045342262d7bf66a0c
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875137"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)
İş parçacığı sınıfı Oluşturucu hiçbir bağımsız değişkeni alır ve hiçbir değer döndürmeyen bir yordam başvuru geçirilmelidir sağlayarak ve değerler döndüren bir çok iş parçacıklı uygulamada karmaşık olmasıdır. Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Çok iş parçacıklı yordamlar için parametreleri belirtin  
 Çok iş parçacıklı bir yöntem çağrısı için parametreleri sağlamak için en iyi yolu, hedef yöntemin bir sınıf içinde sarmalamak ve yeni iş parçacığı için parametre olarak hizmet verecek o sınıf için alanları tanımlayan sağlamaktır. Bu yaklaşımın avantajı, yeni bir iş parçacığı istediğiniz her seferinde, sınıfının yeni bir örneğini kendi parametrelerle oluşturabilirsiniz olmasıdır. Örneğin, aşağıdaki kodda gösterildiği gibi bir üçgen alanını hesaplayan bir işlevi olduğunu varsayalım:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve giriş parametresi gibi depolamak için alanları oluşturur:  
  
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
  
 Dikkat `TestArea` yordamı değerini denetlemez `Area` arama sonra alan `CalcArea` yöntemi. Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan çağırdıktan hemen sonra onay ayarlanacak garanti edilmez `Thread.Start`. Sonraki bölümde, dönüş değerleri çok iş parçacıklı yordamlar için daha iyi bir yolu anlatılmaktadır.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Çok iş parçacıklı yordamlar değerler döndüren  
 Ayrı iş parçacıkları üzerinde çalıştırılan yordamları değerleri döndürme yordamlar, İşlevler olamaz ve kullanamazsınız gerçeğiyle karmaşık `ByRef` bağımsız değişkenler. Dönüş değerleri için en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> dizilerinizi yönetmek ve görev tamamlandığında bir olay tetikleyebilir ve bir olay işleyicisi ile sonuçları işlemek için bileşen.  
  
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
  
 Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durumu nesne değişkeni <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. İş parçacığı Zamanlayıcı iş parçacıklarını durum nesnesi bu amaç için de destekler. İş parçacığı havuzu ve iş parçacığı zamanlayıcıları hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) ve [zamanlayıcılar](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [İş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [İş parçacığı eşitleme (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Olaylar](../../../../csharp/programming-guide/events/index.md)  
 [Çok iş parçacıklı uygulamalar (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Temsilciler](../../../../csharp/programming-guide/delegates/index.md)  
 [Bileşenlerinde çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
