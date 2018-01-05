---
title: "Özel Durum İşleme Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a><span data-ttu-id="c57bb-102">Özel Durum İşleme Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="c57bb-102">Securing Exception Handling</span></span>
<span data-ttu-id="c57bb-103">Visual C++ ve Visual Basic'te yığın yukarı daha fazla filtre ifadesi önce çalışır **son** deyimi.</span><span class="sxs-lookup"><span data-stu-id="c57bb-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="c57bb-104">**Catch** blok ile ilişkili sonra bu filtre çalışan **son** deyimi.</span><span class="sxs-lookup"><span data-stu-id="c57bb-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="c57bb-105">Daha fazla bilgi için bkz: [Using User-Filtered özel durumları](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="c57bb-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="c57bb-106">Bu bölümde, bu sırada güvenlik etkilerini inceler.</span><span class="sxs-lookup"><span data-stu-id="c57bb-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="c57bb-107">Hangi filtre ifadesini sırayla gösterilmektedir aşağıdaki sahte kod örneği göz önünde bulundurun ve **son** deyimleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c57bb-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="c57bb-108">Bu kod aşağıdakileri yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="c57bb-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="c57bb-109">Filtre öncesinde çalışan **son** güvenlik sorunları diğer kod yürütmeyi avantajı burada ele geçirebilir değiştirme durumu sağlayan şey tanıtılabilir şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="c57bb-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="c57bb-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c57bb-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="c57bb-111">Bu sahte kod yığını rastgele bir kodu çalıştırmak için daha yüksek bir filtre izin verir.</span><span class="sxs-lookup"><span data-stu-id="c57bb-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="c57bb-112">İş parçacığı ile ilişkilendirilmiş kültürü değiştirme veya diğer örnekler geçici kimliğe bürünme başka bir kimlik, bazı güvenlik denetimi atlayan bir iç bayrağı ayarlama işlemlerinin benzer bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c57bb-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="c57bb-113">Önerilen çözüm kodun değişiklikler iş parçacığı durumu arayanlar filtre bloklarından ayırmak için bir özel durum işleyici uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="c57bb-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="c57bb-114">Ancak, özel durum işleyici düzgün bir şekilde uygulanması önemlidir veya bu sorun değil düzeltilecektir.</span><span class="sxs-lookup"><span data-stu-id="c57bb-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="c57bb-115">Aşağıdaki örnek UI kültürü geçer, ancak her türlü iş parçacığı durumu değişikliği benzer şekilde açığa çıkabileceği.</span><span class="sxs-lookup"><span data-stu-id="c57bb-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="c57bb-116">Varolan kaydırmak için bu durumda durumda doğru düzeltme **deneyin**/**son** engelleyin bir **deneyin**/**catch** Blok.</span><span class="sxs-lookup"><span data-stu-id="c57bb-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="c57bb-117">Yalnızca Tanıtımı bir **catch throw** varolan INTO yan tümcesinin **deneyin**/**son** bloğu değil düzeltme sorun aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c57bb-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c57bb-118">Bu sorunu nedeniyle gideremiyor **son** deyimi önce çalıştırılacak `FilterFunc` denetim alır.</span><span class="sxs-lookup"><span data-stu-id="c57bb-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="c57bb-119">Aşağıdaki örnek, sağlayarak sorunu giderir **son** yan tümcesi yürütülebilir bir özel durum arayanlar özel durum filtresi bloklarını yukarı sunmadan önce.</span><span class="sxs-lookup"><span data-stu-id="c57bb-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c57bb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c57bb-120">See Also</span></span>  
 [<span data-ttu-id="c57bb-121">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c57bb-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
