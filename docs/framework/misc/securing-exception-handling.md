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
ms.openlocfilehash: e0465f2eb6be61e161f5e6b8cadf629a53f11906
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215796"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="920fe-102">Özel Durum İşleme Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="920fe-102">Securing Exception Handling</span></span>
<span data-ttu-id="920fe-103">Görsel C++ ve Visual Basic, yığın üzerinde daha fazla bir filtre ifadesi herhangi bir **finally** ifadesiyle önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="920fe-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="920fe-104">Bu filtreyle ilişkili **catch** bloğu **finally** ifadesinden sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="920fe-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="920fe-105">Daha fazla bilgi için bkz. [Kullanıcı filtrelenmiş özel durumları kullanma](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="920fe-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="920fe-106">Bu bölümde, bu sıranın güvenlik etkileri incelenir.</span><span class="sxs-lookup"><span data-stu-id="920fe-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="920fe-107">Filter deyimlerinin ve **finally** deyimlerinin çalışacağı sırayı gösteren aşağıdaki sözde kod örneğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="920fe-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="920fe-108">Bu kod aşağıdakileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="920fe-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="920fe-109">Filtre **finally** ifadesinden önce çalışır, bu nedenle güvenlik sorunları diğer kodun yürütülmesinin avantajlarından faydalanarak bir durum değişikliği yapan herhangi bir şey tarafından tanıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="920fe-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="920fe-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="920fe-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="920fe-111">Bu sözde kod, bir filtrenin rastgele kod çalıştırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="920fe-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="920fe-112">Benzer bir etkiye sahip olacak diğer işlemlere örnek olarak, başka bir kimlik kimliğe bürünme, bazı güvenlik denetimini atlayan bir iç bayrak ayarlama veya iş parçacığıyla ilişkili kültürü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="920fe-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="920fe-113">Önerilen çözüm, kodun iş parçacığı durumuna çağıranların filtre blokları üzerinde yaptığı değişiklikleri yalıtmak için bir özel durum işleyicisi tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="920fe-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="920fe-114">Ancak, özel durum işleyicisinin doğru bir şekilde tanıtılmasından veya bu sorunun düzeltilmeyecek olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="920fe-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="920fe-115">Aşağıdaki örnek, UI kültürünü geçirir, ancak her türlü iş parçacığı durum değişikliği benzer şekilde açığa çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="920fe-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="920fe-116">Bu durumda doğru düzeltme, **try**/**catch** bloğunda var olan **TRY**/**finally** bloğunu sarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="920fe-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="920fe-117">Aşağıdaki örnekte gösterildiği gibi, var olan **try**/**finally** bloğunun bir **catch-throw** yan tümcesini sorunu çözmez.</span><span class="sxs-lookup"><span data-stu-id="920fe-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="920fe-118">Bu, `FilterFunc` denetimi almadan önce **finally** ifadesinin çalıştırılmadığı için sorunu çözmez.</span><span class="sxs-lookup"><span data-stu-id="920fe-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="920fe-119">Aşağıdaki örnek, çağıran özel durum filtre blokları için bir özel durum sunmadan önce **finally** yan tümcesinin yürütüldüğünü sağlayarak sorunu düzeltir.</span><span class="sxs-lookup"><span data-stu-id="920fe-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="920fe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="920fe-120">See also</span></span>

- [<span data-ttu-id="920fe-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="920fe-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
