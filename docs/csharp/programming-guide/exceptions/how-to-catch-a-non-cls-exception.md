---
title: CLS dışı özel durumu yakalama
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346272"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="a1279-102">CLS dışı özel durumu yakalama</span><span class="sxs-lookup"><span data-stu-id="a1279-102">How to catch a non-CLS exception</span></span>
<span data-ttu-id="a1279-103">C++/CLI dahil olmak üzere bazı .NET dilleri, nesnelerin <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="a1279-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="a1279-104">Bu tür özel *durumlar, CLS dışı özel durumlar* veya Özel Durumlar *olarak*adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a1279-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="a1279-105">C#'da CLS dışı özel durumlar atamazsınız, ancak bunları iki şekilde yakalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1279-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="a1279-106">Bir `catch (RuntimeWrappedException e)` blok içinde.</span><span class="sxs-lookup"><span data-stu-id="a1279-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="a1279-107">Varsayılan olarak, Visual C# derlemesi CLS olmayan özel durumları sarılmış özel durumlar olarak yakalar.</span><span class="sxs-lookup"><span data-stu-id="a1279-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="a1279-108"><xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Özellik üzerinden erişilebilen özgün özel durum özelliğine erişmeniz gerekiyorsa bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1279-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a1279-109">Bu konunun ilerleyen sonraki yordamı, özel durumların bu şekilde nasıl yakaılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1279-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="a1279-110">Genel bir catch bloğu içinde (bir istisna türü belirtilmeden bir `catch` catch blok) tüm diğer bloklar sonra konur.</span><span class="sxs-lookup"><span data-stu-id="a1279-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="a1279-111">CLS dışı özel durumlara yanıt olarak bazı eylem (günlük dosyasına yazma gibi) gerçekleştirmek istediğinizde bu yöntemi kullanın ve özel durum bilgilerine erişmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a1279-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="a1279-112">Varsayılan olarak ortak dil çalışma süresi tüm özel durumları sarar.</span><span class="sxs-lookup"><span data-stu-id="a1279-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="a1279-113">Bu davranışı devre dışı katmak için, genellikle AssemblyInfo.cs dosyasında bu derleme `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`düzeyi özniteliğini kodunuza ekleyin: .</span><span class="sxs-lookup"><span data-stu-id="a1279-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="a1279-114">CLS olmayan bir özel durum yakalamak için</span><span class="sxs-lookup"><span data-stu-id="a1279-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="a1279-115">Bir `catch(RuntimeWrappedException e)` blok içinde, özellik üzerinden <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> orijinal özel durum erişin.</span><span class="sxs-lookup"><span data-stu-id="a1279-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1279-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1279-116">Example</span></span>  
 <span data-ttu-id="a1279-117">Aşağıdaki örnek, C++/CLI ile yazılmış bir sınıf kitaplığından atılan CLS olmayan bir özel durum nasıl yakalandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1279-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="a1279-118">Bu örnekte, C# istemci kodu atılan özel durum türünün <xref:System.String?displayProperty=nameWithType>bir . olduğunu önceden bildiğini unutmayın</span><span class="sxs-lookup"><span data-stu-id="a1279-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1279-119">Bu türe <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> kodunuzdan erişilebildiği sürece özelliği özgün türünü geri atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1279-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="a1279-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1279-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="a1279-121">Özel Durumlar ve Özel Durum Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a1279-121">Exceptions and Exception Handling</span></span>](./index.md)
