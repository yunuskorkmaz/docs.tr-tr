---
title: İş parçacığı havuzu (C#)
ms.date: 07/20/2015
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
ms.openlocfilehash: 42e1dcedc1897dc82bbd13f12882cbef6a5da4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pooling-c"></a>İş parçacığı havuzu (C#)
A *iş parçacığı havuzu* arka planda çeşitli görevleri gerçekleştirmek için kullanılan iş parçacıklarını koleksiyonudur. (Bkz [parçacıkları (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) arka plan bilgileri için.) Bu, birincil iş parçacığı diğer görevleri zaman uyumsuz olarak serbest bırakır.  
  
 İş parçacığı havuzları genellikle sunucu uygulamalarında görevli olduğu. Böylece istek zaman uyumsuz olarak birincil iş parçacığını bağlamadan veya izleyen istekleri işlemeyi geciktirme işlenebilen her gelen istek bir iş parçacığı için iş parçacığı havuzundan atanır.  
  
 Bir iş parçacığı havuzu, kendi görev tamamlandığında, bekleyen iş parçacıklarının kuyruğuna burada kullanılabilme döndürülür. Bu yeniden her görev için yeni bir iş parçacığı oluşturma maliyetini önlemek uygulamaları etkinleştirir.  
  
 İş parçacığı havuzları genellikle iş parçacığı sayısı üst sahiptir. Tüm iş parçacıkları meşgul ise, iş parçacıkları kullanılabilir duruma geldiğinde bunların hizmet verilebilir kadar ek görevler sıraya konur.  
  
 Kendi iş parçacığı havuzu uygulayabilirsiniz, ancak .NET Framework tarafından sunulan iş parçacığı havuzu kullanma daha kolaydır <xref:System.Threading.ThreadPool> sınıfı.  
  
 İş parçacığı havuzu ile çağrı <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> çalıştırmak istediğiniz bir temsilci yöntemiyle bir yordam ve C# iş parçacığı oluşturan ve yordamınız çalıştırır.  
  
## <a name="thread-pooling-example"></a>İş parçacığı havuzu örnek  
 Aşağıdaki örnek, iş parçacığı çeşitli görevleri başlatmak için havuzu nasıl kullanabileceğinizi gösterir.  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 İş parçacığı havuzu bir avantajı, bağımsız değişkenler görev yordama durumu nesnesinde geçirebilirsiniz olmasıdır. Çağırdığınız yordamı birden fazla bağımsız değişken gerektiriyorsa, bir yapının ya da sınıfının bir örneği çevirebilirsiniz bir `Object` veri türü.  
  
## <a name="thread-pool-parameters-and-return-values"></a>İş parçacığı havuzu parametreler ve dönüş değerleri  
 Bir iş parçacığı havuzu iş parçacığından değerler döndüren basit değildir. Değerler döndüren bir işlev çağrısında standart yolu için izin verilmiyor `Sub` yordamlar yalnızca tür iş parçacığı havuzu için sıraya yordamı içindir. Tek yönlü, parametreleri sağlamak ve değerleri olan parametreleri, dönüş değerleri kaydırma tarafından ve yöntemleri bir sarmalayıcı sınıfı açıklandığı gibi dönmek [parametreler ve dönüş değerleri (C#) birden çok iş parçacıklı yordamlar için](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 İsteğe bağlı kullanarak parametreleri sağlamak ve dönüş değerleri için daha kolay bir yoludur `ByVal` durumu nesne değişkeninin <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi. Bir sınıfın bir örneğine başvuru geçirmek için bu değişkeni kullanın, örnek üyeleri iş parçacığı havuzu iş parçacığı tarafından değiştirilebilir ve dönüş değerleri olarak kullanılır.  
  
 İlk bakışta değeri tarafından geçirilen bir değişkeni tarafından başvurulan nesne değiştirebileceğiniz belirgin olmayabilir. Yalnızca nesne başvurusu değeriyle geçtiğinden bunu yapabilirsiniz. Nesne başvurusu tarafından başvurulan nesne üyeleri değişiklik yaptığınızda, değişiklikler gerçek sınıf örneğine uygulanır.  
  
 Yapılar, durum nesneleri içinde değer döndürmek için kullanılamaz. Zaman uyumsuz işlem yaptığı değişiklikler yapıları değer türleri olduğundan, özgün yapısı üyeleri değiştirmeyin. Dönüş değerleri değil gerektiğinde parametreleri sağlamak amacıyla yapıları kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Nasıl yapılır: iş parçacığı havuzu (C#) kullanma](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [İş parçacığı (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Birden çok iş parçacıklı uygulamalar (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [İş parçacığı eşitleme (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
