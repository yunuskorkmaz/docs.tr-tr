---
title: "İş parçacığı havuzu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a>İş parçacığı havuzu (Visual Basic)
A *iş parçacığı havuzu* arka planda çeşitli görevleri gerçekleştirmek için kullanılan iş parçacıklarını koleksiyonudur. (Bkz [parçacıkları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) arka plan bilgileri için.) Bu, birincil iş parçacığı diğer görevleri zaman uyumsuz olarak serbest bırakır.  
  
 İş parçacığı havuzları genellikle sunucu uygulamalarında görevli olduğu. Böylece istek zaman uyumsuz olarak birincil iş parçacığını bağlamadan veya izleyen istekleri işlemeyi geciktirme işlenebilen her gelen istek bir iş parçacığı için iş parçacığı havuzundan atanır.  
  
 Bir iş parçacığı havuzu, kendi görev tamamlandığında, bekleyen iş parçacıklarının kuyruğuna burada kullanılabilme döndürülür. Bu yeniden her görev için yeni bir iş parçacığı oluşturma maliyetini önlemek uygulamaları etkinleştirir.  
  
 İş parçacığı havuzları genellikle iş parçacığı sayısı üst sahiptir. Tüm iş parçacıkları meşgul ise, iş parçacıkları kullanılabilir duruma geldiğinde bunların hizmet verilebilir kadar ek görevler sıraya konur.  
  
 Kendi iş parçacığı havuzu uygulayabilirsiniz, ancak .NET Framework tarafından sunulan iş parçacığı havuzu kullanma daha kolaydır <xref:System.Threading.ThreadPool> sınıfı.  
  
 İş parçacığı havuzu ile çağrı <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> çalıştırmak istediğiniz bir temsilci yöntemiyle bir yordam ve Visual Basic iş parçacığı oluşturan ve yordamınız çalıştırır.  
  
## <a name="thread-pooling-example"></a>İş parçacığı havuzu örnek  
 Aşağıdaki örnek, iş parçacığı çeşitli görevleri başlatmak için havuzu nasıl kullanabileceğinizi gösterir.  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 İş parçacığı havuzu bir avantajı, bağımsız değişkenler görev yordama durumu nesnesinde geçirebilirsiniz olmasıdır. Çağırdığınız yordamı birden fazla bağımsız değişken gerektiriyorsa, bir yapının ya da sınıfının bir örneği çevirebilirsiniz bir `Object` veri türü.  
  
## <a name="thread-pool-parameters-and-return-values"></a>İş parçacığı havuzu parametreler ve dönüş değerleri  
 Bir iş parçacığı havuzu iş parçacığından değerler döndüren basit değildir. Değerler döndüren bir işlev çağrısında standart yolu için izin verilmiyor `Sub` yordamlar yalnızca tür iş parçacığı havuzu için sıraya yordamı içindir. Tek yönlü, parametreleri sağlamak ve değerleri olan parametreleri, dönüş değerleri kaydırma tarafından ve yöntemleri bir sarmalayıcı sınıfı açıklandığı gibi dönmek [parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 İsteğe bağlı kullanarak parametreleri sağlamak ve dönüş değerleri için bir easer yoludur `ByVal` durumu nesne değişkeninin <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. Bir sınıfın bir örneğine başvuru geçirmek için bu değişkeni kullanın, örnek üyeleri iş parçacığı havuzu iş parçacığı tarafından değiştirilebilir ve dönüş değerleri olarak kullanılır.  
  
 İlk bakışta değeri tarafından geçirilen bir değişkeni tarafından başvurulan nesne değiştirebileceğiniz belirgin olmayabilir. Yalnızca nesne başvurusu değeriyle geçtiğinden bunu yapabilirsiniz. Nesne başvurusu tarafından başvurulan nesne üyeleri değişiklik yaptığınızda, değişiklikler gerçek sınıf örneğine uygulanır.  
  
 Yapılar, durum nesneleri içinde değer döndürmek için kullanılamaz. Zaman uyumsuz işlem yaptığı değişiklikler yapıları değer türleri olduğundan, özgün yapısı üyeleri değiştirmeyin. Dönüş değerleri değil gerektiğinde parametreleri sağlamak amacıyla yapıları kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [İş parçacığı oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Birden çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
