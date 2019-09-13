---
title: Özel Durum İşleme Güvenliğini Sağlama
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 256d9c9b825081e3bcfafd6e0e09de825d046d20
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894549"
---
# <a name="securing-exception-handling"></a>Özel Durum İşleme Güvenliğini Sağlama
Görsel C++ ve Visual Basic, yığın üzerinde daha fazla bir filtre ifadesi herhangi bir **finally** ifadesiyle önce çalışır. Bu filtreyle ilişkili **catch** bloğu **finally** ifadesinden sonra çalışır. Daha fazla bilgi için bkz. [Kullanıcı filtrelenmiş özel durumları kullanma](../../standard/exceptions/using-user-filtered-exception-handlers.md). Bu bölümde, bu sıranın güvenlik etkileri incelenir. Filter deyimlerinin ve **finally** deyimlerinin çalışacağı sırayı gösteren aşağıdaki sözde kod örneğini göz önünde bulundurun.  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 Bu kod aşağıdakileri yazdırır.  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtre **finally** ifadesinden önce çalışır, bu nedenle güvenlik sorunları diğer kodun yürütülmesinin avantajlarından faydalanarak bir durum değişikliği yapan herhangi bir şey tarafından tanıtılamaz. Örneğin:  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 Bu sözde kod, bir filtrenin rastgele kod çalıştırmasına izin verir. Benzer bir etkiye sahip olacak diğer işlemlere örnek olarak, başka bir kimlik kimliğe bürünme, bazı güvenlik denetimini atlayan bir iç bayrak ayarlama veya iş parçacığıyla ilişkili kültürü değiştirme. Önerilen çözüm, kodun iş parçacığı durumuna çağıranların filtre blokları üzerinde yaptığı değişiklikleri yalıtmak için bir özel durum işleyicisi tanıtmaktır. Ancak, özel durum işleyicisinin doğru bir şekilde tanıtılmasından veya bu sorunun düzeltilmeyecek olması önemlidir. Aşağıdaki örnek, UI kültürünü geçirir, ancak her türlü iş parçacığı durum değişikliği benzer şekilde açığa çıkabilir.  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 Bu durumda doğru düzeltme, bir **TRY**/**catch** bloğunda var olan **TRY**/**finally** bloğunu sarmalıdır. Aşağıdaki örnekte gösterildiği gibi, var olan **TRY**/**finally** bloğunun içine bir **catch-throw** yan tümcesinin oluşturulması sorunu çözmemektedir.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 **Finally** deyimleri, `FilterFunc` almadan önce çalıştırılmadığından, bu sorunu çözmez.  
  
 Aşağıdaki örnek, çağıran özel durum filtre blokları için bir özel durum sunmadan önce **finally** yan tümcesinin yürütüldüğünü sağlayarak sorunu düzeltir.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
