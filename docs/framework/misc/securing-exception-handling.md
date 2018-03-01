---
title: "Özel Durum İşleme Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a>Özel Durum İşleme Güvenliğini Sağlama
Visual C++ ve Visual Basic'te yığın yukarı daha fazla filtre ifadesi önce çalışır **son** deyimi. **Catch** blok ile ilişkili sonra bu filtre çalışan **son** deyimi. Daha fazla bilgi için bkz: [Using User-Filtered özel durumları](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Bu bölümde, bu sırada güvenlik etkilerini inceler. Hangi filtre ifadesini sırayla gösterilmektedir aşağıdaki sahte kod örneği göz önünde bulundurun ve **son** deyimleri çalıştırın.  
  
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
  
 Bu kod aşağıdakileri yazdırılır.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtre öncesinde çalışan **son** güvenlik sorunları diğer kod yürütmeyi avantajı burada ele geçirebilir değiştirme durumu sağlayan şey tanıtılabilir şekilde deyimi. Örneğin:  
  
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
  
 Bu sahte kod yığını rastgele bir kodu çalıştırmak için daha yüksek bir filtre izin verir. İş parçacığı ile ilişkilendirilmiş kültürü değiştirme veya diğer örnekler geçici kimliğe bürünme başka bir kimlik, bazı güvenlik denetimi atlayan bir iç bayrağı ayarlama işlemlerinin benzer bir etkisi yoktur. Önerilen çözüm kodun değişiklikler iş parçacığı durumu arayanlar filtre bloklarından ayırmak için bir özel durum işleyici uygulamaktır. Ancak, özel durum işleyici düzgün bir şekilde uygulanması önemlidir veya bu sorun değil düzeltilecektir. Aşağıdaki örnek UI kültürü geçer, ancak her türlü iş parçacığı durumu değişikliği benzer şekilde açığa çıkabileceği.  
  
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
  
 Varolan kaydırmak için bu durumda durumda doğru düzeltme **deneyin**/**son** engelleyin bir **deneyin**/**catch** Blok. Yalnızca Tanıtımı bir **catch throw** varolan INTO yan tümcesinin **deneyin**/**son** bloğu değil düzeltme sorun aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Bu sorunu nedeniyle gideremiyor **son** deyimi önce çalıştırılacak `FilterFunc` denetim alır.  
  
 Aşağıdaki örnek, sağlayarak sorunu giderir **son** yan tümcesi yürütülebilir bir özel durum arayanlar özel durum filtresi bloklarını yukarı sunmadan önce.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
