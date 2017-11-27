---
title: "try-catch (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 753beb554796ad0aa2c5e15c715240453de9a3e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="try-catch-c-reference"></a>try-catch (C# Başvurusu)
Try-catch deyimi oluşan bir `try` blok izlenen bir veya daha fazla tarafından `catch` yan tümceleri farklı özel durumlar için işleyiciler belirleyin.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum, ortak dil çalışma zamanı (CLR) arar `catch` bu özel durumu işler deyimi. Şu anda yürütülen yöntemi gibi içermiyorsa, bir `catch` engellemek, CLR bakar ve benzeri çağrı yığını yukarı geçerli yöntemi çağrılan yöntemi. Öyle değilse `catch` blok bulunursa, ardından CLR kullanıcıya bir işlenmeyen özel durum iletisi görüntüler ve programın yürütülmesi durdurulur.  
  
 `try` Blok özel durumuna neden olabilir korunmuş kodunu içerir. Blok, bir özel durum veya başarıyla tamamlanıncaya kadar yürütülür. Örneğin, aşağıdaki cast denemesi bir `null` nesnesini başlatır <xref:System.NullReferenceException> özel durum:  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 Ancak `catch` yan tümcesi kullanılabilir bağımsız değişkenler herhangi bir özel durum türü yakalamak için bu kullanımı önerilmez. Genel olarak, yalnızca nasıl kurtarılır bildiğiniz bu özel durumları yakalamak. Bu nedenle, her zaman türetilmiş bir nesne bağımsız değişkeni belirtmeniz <xref:System.Exception?displayProperty=nameWithType> örneğin:  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 Birden fazla özel kullanmak da mümkündür `catch` yan tümcesinde aynı try-catch deyimi. Bu durumda, sırasını `catch` yan tümceleri önemlidir çünkü `catch` yan tümceleri sırayla inceledi. Daha fazla özel durum daha az yayına önce yakalar. Böylece daha sonra bir blok hiç üst sınırına, catch blokları siparişi derleyici bir hata oluşturur.  
  
 Kullanarak `catch` bağımsız değişkenleri olan istediğiniz işlemek için özel durumlar için filtre uygulamak için bir yolu.  Daha fazla uygulayacağınıza karar vermek için özel durum inceler bir koşul ifadesi de kullanabilirsiniz.  Koşul ifadesi false değeri döndürülürse, bir işleyici aramaya devam eder.  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 Özel durum filtreleri yakalama ve filtreleri yaralanmadığı türde yığını bıraktığınızdan (aşağıda anlatıldığı) yeniden atma tercih edilir.  Bir sonraki işleyici yığın dökümleri, burada özel durum ilk olarak, bunu işlenemezse yalnızca en son yer yerine geldiğini görebilirsiniz.  Özel durum filtre ifadeleri yaygın kullanımı günlüğü.  Her zaman, bunları işlemek ve yeniden oluşturulması gerekmeden ilerledikçe özel durumları günlüğe kaydetmek bir oturum için de çıkarır false değerini döndürür koşul işlev oluşturabilirsiniz.  
  
 A [throw](../../../csharp/language-reference/keywords/throw.md) deyimi içinde kullanılabilir bir `catch` tarafından yakalanan özel durum yeniden throw blok `catch` deyimi. Aşağıdaki örnekte kaynak bilgilerini ayıklar bir <xref:System.IO.IOException> özel durum ve ardından üst yöntemi özel durum oluşturur.  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 Bunun tek istisnası yakalamak ve farklı bir özel durum. Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi iç özel durum olarak yakalanan özel durum belirtin.  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 Belirtilen bir koşul true olduğunda aşağıdaki örnekte gösterildiği gibi aynı zamanda bir özel durum yeniden atabilirsiniz.  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 Gelen içinde bir `try` engellemek, okuduğunuzu bildirilen değişkenlerini Başlat. Aksi takdirde, bloğun yürütme tamamlanmadan önce bir özel durum meydana gelebilir. Örneğin, aşağıdaki kod örneğinde, değişkenin içinde `n` içinde başlatılan `try` bloğu. Bu değişken dışında kullanma girişimi `try` engelleyin `Write(n)` deyimi derleyici hatası üretir.  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 Catch hakkında daha fazla bilgi için bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
## <a name="exceptions-in-async-methods"></a>Zaman uyumsuz yöntemler özel durumlar  
 Bir zaman uyumsuz yöntem olarak işaretlenmiş bir [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştirici ve genellikle bir içeriyor ya da daha fazla ifadeler veya deyimleri bekler. Bir bekleme ifade geçerlidir [bekleme](../../../csharp/language-reference/keywords/await.md) işleci bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.  
  
 Ulaştığında denetlemek bir `await` awaited görevi tamamlanana kadar zaman uyumsuz yönteminde yöntemi ediyor askıya alınır. Görev tamamlandığında, yürütme yönteminde devam edebilirsiniz. Daha fazla bilgi için bkz: [zaman uyumsuz programlama ile zaman uyumsuz ve bekleme](../../../csharp/programming-guide/concepts/async/index.md) ve [zaman uyumsuz programlarda denetim akışı](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Tamamlanan görevin hangi `await` uygulanan görev döndüren yöntemi işlenmeyen bir özel durum nedeniyle hatalı bir durumda olabilir. Görev bekleyen bir özel durum oluşturur. Onu döndüren zaman uyumsuz işlemi iptal edilirse bir görevi iptal edilmiş durumda da düşebilir. İptal edilen bir görevin bekleyen oluşturur bir `OperationCanceledException`. Zaman uyumsuz bir işlem iptal etme hakkında daha fazla bilgi için bkz: [Fine-Tuning uygulamanız zaman uyumsuz](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Özel durum yakalamak için görev await bir `try` engelleme ve özel durum ilişkili catch `catch` bloğu. Örneğin, "Örnek" bölümüne bakın.  
  
 Zaman uyumsuz beklemenin yönteminde oluştuğundan, birden fazla özel bir görev hatalı bir durumda olabilir. Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Bu tür bir görev await, yalnızca bir özel durum yakalandı ve hangi özel durumu yakalandı tahmin edilemez. Örneğin, "Örnek" bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `try` bloğu için bir çağrı içerir `ProcessString` yöntemi bir özel durum neden olabilir. `catch` Yan tümcesi yalnızca ekranda bir ileti görüntüler özel durum işleyici içeriyor. Zaman `throw` deyimi çağrılır içinde `MyMethod`, sistem arar `catch` deyimi ve iletiyi görüntüler `Exception caught`.  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki catch bloklarını kullanılır ve önce geliyorsa, en özel durum yakalandı.  
  
 En az belirli özel durumu yakalamak için throw deyimi içinde değiştirebilirsiniz `ProcessString` aşağıdaki ifadesiyle: `throw new Exception()`.  
  
 En az özgü catch bloğu ilk örnekte yerleştirirseniz, aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel durum işleme için zaman uyumsuz yöntemleri gösterilmektedir. Zaman uyumsuz görev oluşturur bir özel durum çekmek için koyun `await` ifadesinde bir `try` engelleme ve catch özel durum bir `catch` bloğu.  
  
 Açıklamadan çıkarın `throw new Exception` özel durum işleme göstermek için örnekte satır. Görevin `IsFaulted` özelliği ayarlanmış `True`, görevin `Exception.InnerException` özelliği, özel durumu ayarlanır ve özel durumun yakalandığı `catch` bloğu.  
  
 Açıklamadan çıkarın `throw new OperationCancelledException` satır zaman uyumsuz bir işlem iptal ettiğinizde ne olacağını gösterir. Görevin `IsCanceled` özelliği ayarlanmış `true`, ve özel durumun yakalandığı `catch` bloğu. Bu örnek için görev 's uygulanmaz bazı koşullarda `IsFaulted` özelliği ayarlanmış `true` ve `IsCanceled` ayarlanır `false`.  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok görev birden çok özel durumları burada sonuçlanabilir özel durum işleme gösterilmektedir. `try` Blok bekler yapılan bir çağrı tarafından döndürülen görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. WhenAll uygulandığı üç görevler tamamlandığında tam bir görevdir.  
  
 Her biri üç görev bir özel durum oluşur. `catch` Blok tekrarlanan bulunan özel durumlar aracılığıyla `Exception.InnerExceptions` özellik tarafından döndürülen görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [deneyin, throw ve catch deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Özel durum işleme deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [Nasıl yapılır: açıkça özel durumlar oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
