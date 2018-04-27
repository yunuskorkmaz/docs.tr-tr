---
title: 'Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5647fc8501afe2a4bf74739fd8efd4e6b74559a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="9bdc2-102">Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="9bdc2-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="9bdc2-103">C + dahil olmak üzere bazı .NET dillerini +/ CLI, nesnelerin öğesinden türetilen olmayan özel durumlar oluşturma izin <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="9bdc2-104">Bu tür özel durumlar olarak adlandırılan *CLS olmayan özel durumları* veya *özel durumları olmayan*.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="9bdc2-105">Visual C# ' CLS olmayan özel durumları atılamıyor, ancak iki yolla catch:</span><span class="sxs-lookup"><span data-stu-id="9bdc2-105">In Visual C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="9bdc2-106">İçinde bir `catch (Exception e)` olarak engelleme bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="9bdc2-107">Varsayılan olarak, bir Visual C# derleme Sarmalanan özel durumlar olarak CLS olmayan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="9bdc2-108">Üzerinden erişilen özgün özel erişmesi gerekiyorsa bu yöntemi kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="9bdc2-109">Bu konunun devamındaki yordamı bu şekilde özel durumlarını yakalama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="9bdc2-110">Bir genel catch bloğu (catch bloğu bir özel durum türü belirtilmiş olmadan) içinde put sonra bir `catch (Exception)` veya `catch (Exception e)` bloğu.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="9bdc2-111">Özel durum bilgilerini erişimi gerekmez ve yanıt CLS olmayan özel durumlar olarak (örneğin, bir günlük dosyasına yazılırken) bazı eylemler gerçekleştirme istediğinizde bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="9bdc2-112">Varsayılan olarak, tüm özel durumları ortak dil çalışma zamanı sarmalar.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="9bdc2-113">Bu davranışı devre dışı bırakmak için genellikle AssemblyInfo.cs dosyasında kodunuzu bu derleme düzeyi özniteliğini ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="9bdc2-114">CLS olmayan özel durumu yakalamak için</span><span class="sxs-lookup"><span data-stu-id="9bdc2-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="9bdc2-115">İçinde bir `catch(Exception e) block`, kullanın `as` test etmek için anahtar sözcüğü olup olmadığını `e` atanabilecek bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="9bdc2-116">Orijinal özel durumu ile erişim <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bdc2-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="9bdc2-117">Example</span></span>  
 <span data-ttu-id="9bdc2-118">Aşağıdaki örnekte yazılan C + sınıf kitaplığı'ndan oluşturulan bir CLS olmayan özel catch gösterilmektedir +/ CLR.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="9bdc2-119">Bu örnekte, Visual C# istemci kodu önceden oluşturulan özel durum türü olduğunu bilir olduğunu unutmayın bir <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-119">Note that in this example, the Visual C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9bdc2-120">Cast <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özellik türü kodunuzdan erişilebilir olduğu sürece özgün türüne yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="9bdc2-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bdc2-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="9bdc2-122">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="9bdc2-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
