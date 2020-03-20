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
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181146"
---
# <a name="securing-exception-handling"></a>Özel Durum İşleme Güvenliğini Sağlama
Visual C++ ve Visual Basic'te, bir filtre ifadesi yığının daha yukarısında herhangi bir **son** deyimi önce çalışır. Bu filtreyle ilişkili **catch** bloğu **son** deyimden sonra çalışır. Daha fazla bilgi için [bkz.](../../standard/exceptions/using-user-filtered-exception-handlers.md) Bu bölümde, bu siparişin güvenlik etkileri incelenir. Filtre deyimlerinin ve **son ifadelerin** çalışma sırasını gösteren aşağıdaki pseudocode örneğini göz önünde bulundurun.  
  
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
  
 Filtre **son** deyimi önce çalışır, böylece güvenlik sorunları diğer kodun yürütülmesi nin yararlanabileceği bir durum değişikliği yapan herhangi bir şey tarafından tanıtılabilir. Örnek:  
  
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
  
 Bu sözde kod, bir filtrenin yığından daha yüksek bir üste rasgele kod çalışmasına izin verir. Benzer bir etkiye sahip diğer işlemler örnekleri, başka bir kimliğin geçici olarak kimliğe bürünme, bazı güvenlik denetimini atlayan bir iç bayrak ayarı veya iş parçacığıyla ilişkili kültürü değiştirmektir. Önerilen çözüm, kodun değişikliklerini arayanların filtre bloklarından iş parçacığı durumuna yalıtmak için bir özel durum işleyicisi tanıtmaktır. Ancak, özel durum işleyicisinin düzgün bir şekilde tanıtılması veya bu sorunun giderilmemesi önemlidir. Aşağıdaki örnek, UI kültürünü değiştirir, ancak her türlü iş parçacığı durumu değişikliği benzer şekilde ortaya çıkabilir.  
  
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
  
 Bu durumda doğru düzeltme, varolan **try**/**bloğunu bir** **try**/**catch** bloğunda sarmaktır. Varolan **try**/**finally** bloğuna bir **yakalama atma** yan tümcesi girmek, aşağıdaki örnekte gösterildiği gibi sorunu çözmez.  
  
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
  
 **Bu, son** deyimi `FilterFunc` denetim alır önce çalışmadı, çünkü sorunu gidermez.  
  
 Aşağıdaki örnek, arayanların özel durum filtre blokları kadar bir özel durum sunmadan önce **son** yan tümcesinin yürütülmesini sağlayarak sorunu giderir.  
  
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
