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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173686"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="59c95-102">Özel Durum İşleme Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="59c95-102">Securing Exception Handling</span></span>
<span data-ttu-id="59c95-103">Visual C++ ve Visual Basic'te yığınına daha fazla filtre ifadesi önce çalışan **son** deyimi.</span><span class="sxs-lookup"><span data-stu-id="59c95-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="59c95-104">**Catch** blok ile ilişkili filtre sonra çalışan **son** deyimi.</span><span class="sxs-lookup"><span data-stu-id="59c95-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="59c95-105">Daha fazla bilgi için [Using User-Filtered özel durumları](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="59c95-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="59c95-106">Bu bölümde, bu sırada güvenlik etkilerini inceler.</span><span class="sxs-lookup"><span data-stu-id="59c95-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="59c95-107">Filtre ifadeleri hangi sırayla gösteren aşağıdaki sözde kod örneği göz önünde bulundurun ve **son** deyimleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59c95-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="59c95-108">Bu kod aşağıdaki yazdırır.</span><span class="sxs-lookup"><span data-stu-id="59c95-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="59c95-109">Filtre öncesinde çalışan **son** güvenlik sorunları diğer kod yürütmeyi avantajı burada ele geçirebilir değiştirme bir duruma yaptığı şey tanıtılmak şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="59c95-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="59c95-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="59c95-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="59c95-111">Bu sözde kod yığınına rasgele kodu çalıştırmak için daha yüksek bir filtre izin verir.</span><span class="sxs-lookup"><span data-stu-id="59c95-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="59c95-112">Diğer örnekler bazı güvenlik denetimini atladığından bir iç bayrak ayarlandığında, başka bir kimlik geçici kimliğe bürünme benzer bir etkisi olmaz işlemleri veya iş parçacığıyla ilişkilendirilmiş kültürü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="59c95-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="59c95-113">Kod değişiklikleri için iş parçacığı durumu çağıranlar filtre bloklarından yalıtmak için bir özel durum işleyicisi tanıtmak için önerilen çözümdür bakın.</span><span class="sxs-lookup"><span data-stu-id="59c95-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="59c95-114">Ancak, özel durum işleyicisi düzgün tanıtılmak önemlidir veya bu sorun değil düzeltilecektir.</span><span class="sxs-lookup"><span data-stu-id="59c95-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="59c95-115">Aşağıdaki örnek kullanıcı Arabirimi kültürünü geçer, ancak herhangi bir türden iş parçacığı durumu değişikliği benzer şekilde sunulabilir.</span><span class="sxs-lookup"><span data-stu-id="59c95-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="59c95-116">Doğru düzeltmeyi bu durumda varolan sarmaktır **deneyin**/**son** engelleyin bir **deneyin**/**catch** Blok.</span><span class="sxs-lookup"><span data-stu-id="59c95-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="59c95-117">Yalnızca Giriş bir **catch throw** varolan INTO yan **deneyin**/**son** blok değil düzeltme sorun aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="59c95-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="59c95-118">Bu sorun nedeniyle düzeltmemeyi **son** deyimi önce çalıştırılacak `FilterFunc` denetimi alır.</span><span class="sxs-lookup"><span data-stu-id="59c95-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="59c95-119">Aşağıdaki örnek, sağlayarak sorunu düzeltir **son** yan tümcesi yürütülen sunmadan önce bir özel durum çağıranlar özel durum filtresi bloklarını ayarlama.</span><span class="sxs-lookup"><span data-stu-id="59c95-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59c95-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59c95-120">See also</span></span>

- [<span data-ttu-id="59c95-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="59c95-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
