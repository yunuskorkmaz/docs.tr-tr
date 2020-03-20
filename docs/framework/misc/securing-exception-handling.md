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
# <a name="securing-exception-handling"></a><span data-ttu-id="36e78-102">Özel Durum İşleme Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="36e78-102">Securing Exception Handling</span></span>
<span data-ttu-id="36e78-103">Visual C++ ve Visual Basic'te, bir filtre ifadesi yığının daha yukarısında herhangi bir **son** deyimi önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="36e78-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="36e78-104">Bu filtreyle ilişkili **catch** bloğu **son** deyimden sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="36e78-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="36e78-105">Daha fazla bilgi için [bkz.](../../standard/exceptions/using-user-filtered-exception-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="36e78-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="36e78-106">Bu bölümde, bu siparişin güvenlik etkileri incelenir.</span><span class="sxs-lookup"><span data-stu-id="36e78-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="36e78-107">Filtre deyimlerinin ve **son ifadelerin** çalışma sırasını gösteren aşağıdaki pseudocode örneğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="36e78-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="36e78-108">Bu kod aşağıdakileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="36e78-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="36e78-109">Filtre **son** deyimi önce çalışır, böylece güvenlik sorunları diğer kodun yürütülmesi nin yararlanabileceği bir durum değişikliği yapan herhangi bir şey tarafından tanıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="36e78-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="36e78-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="36e78-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="36e78-111">Bu sözde kod, bir filtrenin yığından daha yüksek bir üste rasgele kod çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="36e78-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="36e78-112">Benzer bir etkiye sahip diğer işlemler örnekleri, başka bir kimliğin geçici olarak kimliğe bürünme, bazı güvenlik denetimini atlayan bir iç bayrak ayarı veya iş parçacığıyla ilişkili kültürü değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="36e78-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="36e78-113">Önerilen çözüm, kodun değişikliklerini arayanların filtre bloklarından iş parçacığı durumuna yalıtmak için bir özel durum işleyicisi tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="36e78-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="36e78-114">Ancak, özel durum işleyicisinin düzgün bir şekilde tanıtılması veya bu sorunun giderilmemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="36e78-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="36e78-115">Aşağıdaki örnek, UI kültürünü değiştirir, ancak her türlü iş parçacığı durumu değişikliği benzer şekilde ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="36e78-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="36e78-116">Bu durumda doğru düzeltme, varolan **try**/**bloğunu bir** **try**/**catch** bloğunda sarmaktır.</span><span class="sxs-lookup"><span data-stu-id="36e78-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="36e78-117">Varolan **try**/**finally** bloğuna bir **yakalama atma** yan tümcesi girmek, aşağıdaki örnekte gösterildiği gibi sorunu çözmez.</span><span class="sxs-lookup"><span data-stu-id="36e78-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="36e78-118">**Bu, son** deyimi `FilterFunc` denetim alır önce çalışmadı, çünkü sorunu gidermez.</span><span class="sxs-lookup"><span data-stu-id="36e78-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="36e78-119">Aşağıdaki örnek, arayanların özel durum filtre blokları kadar bir özel durum sunmadan önce **son** yan tümcesinin yürütülmesini sağlayarak sorunu giderir.</span><span class="sxs-lookup"><span data-stu-id="36e78-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36e78-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36e78-120">See also</span></span>

- [<span data-ttu-id="36e78-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="36e78-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
