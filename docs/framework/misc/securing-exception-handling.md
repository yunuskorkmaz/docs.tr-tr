---
title: Özel Durum İşleme Güvenliğini Sağlama
description: .NET kodunda özel durum işlemeyi güvenli hale getirme konusuna bakın. TRY, Except, catch ve finally deyimleri varsa kodun çalıştığı sırayı gözden geçirin.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: 73597f83d7236cd48a18a891c987b4f5d7e1723d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309046"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="0787e-104">Özel Durum İşleme Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="0787e-104">Securing Exception Handling</span></span>
<span data-ttu-id="0787e-105">Visual C++ ve Visual Basic içinde, yığın üzerinde daha fazla bir filtre ifadesi herhangi bir ifadeden önce çalışır `finally` .</span><span class="sxs-lookup"><span data-stu-id="0787e-105">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any `finally` statement.</span></span> <span data-ttu-id="0787e-106">Bu filtreyle ilişkili **catch** bloğu `finally` deyimden sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="0787e-106">The **catch** block associated with that filter runs after the `finally` statement.</span></span> <span data-ttu-id="0787e-107">Daha fazla bilgi için bkz. [Kullanıcı filtrelenmiş özel durumları kullanma](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="0787e-107">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="0787e-108">Bu bölümde, bu sıranın güvenlik etkileri incelenir.</span><span class="sxs-lookup"><span data-stu-id="0787e-108">This section examines the security implications of this order.</span></span> <span data-ttu-id="0787e-109">Filtre deyimlerinin ve deyimlerinin çalışacağı sırayı gösteren aşağıdaki sözde kod örneğini göz önünde bulundurun `finally` .</span><span class="sxs-lookup"><span data-stu-id="0787e-109">Consider the following pseudocode example that illustrates the order in which filter statements and `finally` statements run.</span></span>  
  
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
  
 <span data-ttu-id="0787e-110">Bu kod aşağıdakileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0787e-110">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="0787e-111">Filtre deyimden önce çalışır `finally` , bu nedenle güvenlik sorunları diğer kodun yürütülmesinin avantajlarından faydalanabilen bir durum değişikliği yapan herhangi bir şey tarafından tanıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="0787e-111">The filter runs before the `finally` statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="0787e-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0787e-112">For example:</span></span>  
  
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
  
 <span data-ttu-id="0787e-113">Bu sözde kod, bir filtrenin rastgele kod çalıştırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0787e-113">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="0787e-114">Benzer bir etkiye sahip olacak diğer işlemlere örnek olarak, başka bir kimlik kimliğe bürünme, bazı güvenlik denetimini atlayan bir iç bayrak ayarlama veya iş parçacığıyla ilişkili kültürü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="0787e-114">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="0787e-115">Önerilen çözüm, kodun iş parçacığı durumuna çağıranların filtre blokları üzerinde yaptığı değişiklikleri yalıtmak için bir özel durum işleyicisi tanıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="0787e-115">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="0787e-116">Ancak, özel durum işleyicisini doğru bir şekilde tanıtmak önemlidir veya bu sorun düzeltilmez.</span><span class="sxs-lookup"><span data-stu-id="0787e-116">However, it's important to properly introduce the exception handler or this problem won't be fixed.</span></span> <span data-ttu-id="0787e-117">Aşağıdaki örnek, UI kültürünü geçirir, ancak her türlü iş parçacığı durum değişikliği benzer şekilde açığa çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="0787e-117">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="0787e-118">Bu durumda doğru düzeltme, **try** / bir **TRY**catch bloğunda var olan TRY**finally** bloğunu sarmalıdır / **catch** .</span><span class="sxs-lookup"><span data-stu-id="0787e-118">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="0787e-119">Aşağıdaki örnekte gösterildiği gibi, var olan **TRY**finally bloğunun içine bir **catch-throw** yan tümcesinin oluşturulması / **finally** sorunu çözmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0787e-119">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0787e-120">Bu, `finally` bildirim, almadan önce çalıştırılmadığından sorunu çözmez `FilterFunc` .</span><span class="sxs-lookup"><span data-stu-id="0787e-120">This does not fix the problem because the `finally` statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="0787e-121">Aşağıdaki örnek, `finally` çağıran özel durum filtre blokları için bir özel durum sunmadan önce yan tümcesinin yürütülmesini sağlayarak sorunu düzeltir.</span><span class="sxs-lookup"><span data-stu-id="0787e-121">The following example fixes the problem by ensuring that the `finally` clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0787e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0787e-122">See also</span></span>

- [<span data-ttu-id="0787e-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0787e-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
