---
title: "Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 071e0aa916e4b3464c7c0cbff6596cabc6b67906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)
İş parçacığı sınıfı oluşturucusu bağımsız değişken almayan ve herhangi bir değer döndüren bir yordam için bir başvuru geçirilmelidir sağlayarak ve birden çok iş parçacıklı uygulamada değerler döndüren karmaşık olmasıdır. Aşağıdaki bölümlerde, parametrelerini ve dönüş değerleri yordamlardan ayrı iş parçacıklarına basit bazı yollarını gösterir.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Birden çok iş parçacıklı yordamlar için parametreleri belirtin  
 Birden çok iş parçacıklı yöntem çağrısı için parametreleri sağlamak için en iyi bir sınıfta hedef yöntemin sarmalayın ve üzerinde yeni bir iş parçacığı için parametre olarak hizmet verecektir o sınıfın alanlarını tanımlamak için yoludur. Bu yaklaşımın avantajı, yeni bir iş parçacığı başlatmak istediğiniz her zaman kendi parametrelerle sınıfının yeni bir örneğini oluşturmak ' dir. Örneğin, aşağıdaki kod olduğu gibi bir üçgen alanının hesaplar bir işlevi olduğunu varsayalım:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Saran bir sınıf yazabilirsiniz `CalcArea` işlev ve girdi parametresi şu şekilde depolamak için alanlar oluşturur:  
  
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
  
 Dikkat `TestArea` yordamı değerini denetlemez `Area` çağırdıktan sonra alan `CalcArea` yöntemi. Çünkü `CalcArea` ayrı bir iş parçacığı üzerinde çalışan `Area` alan hemen çağrıldıktan sonra işaretlerseniz ayarlanacak garanti edilmez `Thread.Start`. Sonraki bölümde, birden çok iş parçacıklı yordamlardan dönüş değerleri daha iyi bir yolu anlatılmaktadır.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Birden çok iş parçacıklı yordamlardan dönüş değerleri  
 Ayrı iş parçacıklarına çalıştırmak yordamları değerler döndürme yordamları işlevleri olamaz ve kullanamazsınız olgusu karmaşık `ByRef` bağımsız değişkenler. Dönüş değerleri yapmanın en kolay yolu kullanmaktır <xref:System.ComponentModel.BackgroundWorker> , iş parçacıkları yönetmek ve görev tamamlandığında, bir olayı ve bir olay işleyicisi sonuçlarıyla işlemek için bileşen.  
  
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
  
 Parametreleri sağlamak ve dönüş değerleri için iş parçacığı havuzu iş parçacıkları isteğe bağlı kullanarak `ByVal` durum nesnesi değişken <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. İş parçacığı-Zamanlayıcı iş parçacığı, bu amaç için bir durum nesnesi de destekler. İş parçacığı havuzu ve iş parçacığı zamanlayıcılar hakkında daha fazla bilgi için bkz: [iş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[iş parçacığı havuzu](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) ve [iş parçacığı zamanlayıcılar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [İş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Olayları](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Birden çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Bileşenleri çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
