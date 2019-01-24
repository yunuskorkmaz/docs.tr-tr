---
title: 'Nasıl yapılır: CLS olmayan özel yakalayın'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: f64a5de3c09b2f270d49a46ed4170c27483e17d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508402"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="812c4-102">Nasıl yapılır: CLS olmayan özel yakalayın</span><span class="sxs-lookup"><span data-stu-id="812c4-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="812c4-103">Bazı .NET dilleri dahil C + +/ CLI, öğesinden türetilen değil özel durumlar oluşturan nesneleri izin <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="812c4-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="812c4-104">Bu tür özel durumların adlı *CLS olmayan özel durumları* veya *olmayan özel durumları*.</span><span class="sxs-lookup"><span data-stu-id="812c4-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="812c4-105">C# ' de CLS olmayan özel durumları oluşturulamıyor, ancak iki yolla yakalayabilir:</span><span class="sxs-lookup"><span data-stu-id="812c4-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="812c4-106">İçinde bir `catch (RuntimeWrappedException e)` blok.</span><span class="sxs-lookup"><span data-stu-id="812c4-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="812c4-107">Varsayılan olarak, bir Visual C# Derleme CLS olmayan özel durumlar sarmalanmış özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="812c4-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="812c4-108">Üzerinden erişilen özgün özel erişime ihtiyacınız varsa, bu yöntemi kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="812c4-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="812c4-109">Bu konunun devamındaki yordamı, bu şekilde özel durumları yakalamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="812c4-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="812c4-110">Genel bir catch bloğu (bir catch bloğu olmadan bir özel durum türü belirtilmiş) içinde yerleştirildiğini sonra diğer tüm `catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="812c4-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="812c4-111">Yanıt olarak CLS olmayan özel durumları (örneğin, bir günlük dosyasına yazma) bir eylem gerçekleştirmek istediğiniz ve özel durum bilgilerine erişim gerekmez, bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="812c4-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="812c4-112">Varsayılan olarak, tüm özel durumları ortak dil çalışma zamanı sarmalar.</span><span class="sxs-lookup"><span data-stu-id="812c4-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="812c4-113">Bu davranışı devre dışı bırakmak için genellikle AssemblyInfo.cs dosyasında kodunuzda bu derleme düzeyi özniteliğini ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="812c4-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="812c4-114">CLS olmayan özel durum yakalamak için</span><span class="sxs-lookup"><span data-stu-id="812c4-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="812c4-115">İçinde bir `catch(RuntimeWrappedException e)` engelleme, özgün özel durum aracılığıyla erişim <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="812c4-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="812c4-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="812c4-116">Example</span></span>  
 <span data-ttu-id="812c4-117">Aşağıdaki örnek, C +'da yazılmış bir sınıf kitaplığından oluşturulan bir CLS olmayan özel durum yakalamak gösterilmektedir +/ CLI.</span><span class="sxs-lookup"><span data-stu-id="812c4-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="812c4-118">Bu örnekte, C# istemci kodu önceden oluşturulan özel durum türü olduğunu bilir, Not bir <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="812c4-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="812c4-119">Atayabilirsiniz <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği orijinal türe geri türü kodunuz içinden erişilebilir olduğu sürece.</span><span class="sxs-lookup"><span data-stu-id="812c4-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="812c4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="812c4-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="812c4-121">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="812c4-121">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
