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
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametreler ve dönüş değerleri için birden çok iş parçacıklı yordamlar (Visual Basic)
İş parçacığı sınıfı Oluşturucu hiçbir bağımsız değişkeni alır ve hiçbir değer döndürmeyen bir yordam başvuru geçirilmelidir sağlayarak ve değerler döndüren bir çok iş parçacıklı uygulamada karmaşık olmasıdır. Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Çok iş parçacıklı yordamlar için parametreleri belirtin  
 Çok iş parçacıklı bir yöntem çağrısı için parametreleri sağlamak için en iyi yolu, hedef yöntemin bir sınıf içinde sarmalamak ve yeni iş parçacığı için parametre olarak hizmet verecek o sınıf için alanları tanımlayan sağlamaktır. Bu yaklaşımın avantajı, yeni bir iş parçacığı istediğiniz her seferinde, sınıfının yeni bir örneğini kendi parametrelerle oluşturabilirsiniz olmasıdır. Örneğin, aşağıdaki kodda gösterildiği gibi bir üçgen alanını hesaplayan bir işlevi olduğunu varsayalım:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve giriş parametresi gibi depolamak için alanları oluşturur:  
  
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
  
 Kullanılacak `AreaClass`, oluşturabileceğiniz bir `AreaClass` nesne ve ayarlama `Base` ve `Height` aşağıdaki kodda gösterildiği gibi özellikleri:  
  
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
  
 Dikkat `TestArea` yordamı değerini denetlemez `Area` arama sonra alan `CalcArea` yöntemi. Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan çağırdıktan hemen sonra onay ayarlanacak garanti edilmez `Thread.Start`. Sonraki bölümde, dönüş değerleri çok iş parçacıklı yordamlar için daha iyi bir yolu anlatılmaktadır.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Çok iş parçacıklı yordamlar değerler döndüren  
 Ayrı iş parçacıkları üzerinde çalıştırılan yordamları değerleri döndürme yordamlar, İşlevler olamaz ve kullanamazsınız gerçeğiyle karmaşık `ByRef` bağımsız değişkenler. Dönüş değerleri için en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> dizilerinizi yönetmek ve görev tamamlandığında bir olay tetikleyebilir ve bir olay işleyicisi ile sonuçları işlemek için bileşen.  
  
 Aşağıdaki örnek, bir olay ayrı bir iş parçacığı üzerinde çalışan bir yordamdan yükselterek bir değer döndürür:  
  
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
  
 Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durumu nesne değişkeni <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. İş parçacığı Zamanlayıcı iş parçacıklarını durum nesnesi bu amaç için de destekler. İş parçacığı havuzu ve iş parçacığı zamanlayıcıları hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[iş parçacığı havuzu](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) ve [zamanlayıcılar](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [İş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Bileşenlerinde çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
