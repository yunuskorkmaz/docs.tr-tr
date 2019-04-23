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
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173686"
---
# <a name="securing-exception-handling"></a>Özel Durum İşleme Güvenliğini Sağlama
Visual C++ ve Visual Basic'te yığınına daha fazla filtre ifadesi önce çalışan **son** deyimi. **Catch** blok ile ilişkili filtre sonra çalışan **son** deyimi. Daha fazla bilgi için [Using User-Filtered özel durumları](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Bu bölümde, bu sırada güvenlik etkilerini inceler. Filtre ifadeleri hangi sırayla gösteren aşağıdaki sözde kod örneği göz önünde bulundurun ve **son** deyimleri çalıştırın.  
  
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
  
 Bu kod aşağıdaki yazdırır.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtre öncesinde çalışan **son** güvenlik sorunları diğer kod yürütmeyi avantajı burada ele geçirebilir değiştirme bir duruma yaptığı şey tanıtılmak şekilde deyimi. Örneğin:  
  
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
  
 Bu sözde kod yığınına rasgele kodu çalıştırmak için daha yüksek bir filtre izin verir. Diğer örnekler bazı güvenlik denetimini atladığından bir iç bayrak ayarlandığında, başka bir kimlik geçici kimliğe bürünme benzer bir etkisi olmaz işlemleri veya iş parçacığıyla ilişkilendirilmiş kültürü değiştirme. Kod değişiklikleri için iş parçacığı durumu çağıranlar filtre bloklarından yalıtmak için bir özel durum işleyicisi tanıtmak için önerilen çözümdür bakın. Ancak, özel durum işleyicisi düzgün tanıtılmak önemlidir veya bu sorun değil düzeltilecektir. Aşağıdaki örnek kullanıcı Arabirimi kültürünü geçer, ancak herhangi bir türden iş parçacığı durumu değişikliği benzer şekilde sunulabilir.  
  
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
  
 Doğru düzeltmeyi bu durumda varolan sarmaktır **deneyin**/**son** engelleyin bir **deneyin**/**catch** Blok. Yalnızca Giriş bir **catch throw** varolan INTO yan **deneyin**/**son** blok değil düzeltme sorun aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Bu sorun nedeniyle düzeltmemeyi **son** deyimi önce çalıştırılacak `FilterFunc` denetimi alır.  
  
 Aşağıdaki örnek, sağlayarak sorunu düzeltir **son** yan tümcesi yürütülen sunmadan önce bir özel durum çağıranlar özel durum filtresi bloklarını ayarlama.  
  
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

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
