---
title: CLS dışı özel durumu yakalama
description: CLS dışı bir özel durum yakalama hakkında bilgi edinin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: db723cb1e29181e9462c5b423c66cdf8de659259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178677"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="1a407-104">CLS dışı özel durumu yakalama</span><span class="sxs-lookup"><span data-stu-id="1a407-104">How to catch a non-CLS exception</span></span>

<span data-ttu-id="1a407-105">C++/CLı dahil bazı .NET dilleri, nesnelerin türetmeyen özel durumlar oluşturmasını sağlar <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="1a407-105">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="1a407-106">Bu tür özel durumlar *CLS dışı özel durumlar* veya *özel durumlar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1a407-106">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="1a407-107">C# dilinde CLS olmayan özel durumlar belirtemezsiniz, ancak bunları iki şekilde yakalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a407-107">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="1a407-108">Bir `catch (RuntimeWrappedException e)` blok içinde.</span><span class="sxs-lookup"><span data-stu-id="1a407-108">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="1a407-109">Varsayılan olarak, bir Visual C# derlemesi, CLS dışı özel durumları sarmalanmış özel durumlar olarak yakalar.</span><span class="sxs-lookup"><span data-stu-id="1a407-109">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="1a407-110">Bu yöntemi, özelliği aracılığıyla erişilebilen özgün özel duruma erişmeniz gerekiyorsa kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1a407-110">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1a407-111">Bu konu başlığında ilerleyen yordamda, özel durumların bu şekilde nasıl yakalanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a407-111">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="1a407-112">Genel bir catch bloğu içinde (özel durum türü belirtilmeden bir catch bloğu), diğer tüm bloklarından sonra konur `catch` .</span><span class="sxs-lookup"><span data-stu-id="1a407-112">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="1a407-113">CLS olmayan özel durumlara yanıt olarak bazı eylemler (örneğin, bir günlük dosyasına yazma) gerçekleştirmek istediğinizde ve özel durum bilgilerine erişmeniz gerekmiyorsa bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a407-113">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="1a407-114">Varsayılan olarak ortak dil çalışma zamanı tüm özel durumları sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="1a407-114">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="1a407-115">Bu davranışı devre dışı bırakmak için, bu derleme düzeyi özniteliğini kodunuzda, genellikle AssemblyInfo.cs dosyasında ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` .</span><span class="sxs-lookup"><span data-stu-id="1a407-115">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="1a407-116">CLS olmayan bir özel durumu yakalamak için</span><span class="sxs-lookup"><span data-stu-id="1a407-116">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="1a407-117">Bir `catch(RuntimeWrappedException e)` blok içinde, özelliği aracılığıyla özgün özel duruma erişin <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1a407-117">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a407-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a407-118">Example</span></span>  

 <span data-ttu-id="1a407-119">Aşağıdaki örnek, C++/CLIENDE yazılmış bir sınıf kitaplığından oluşturulan CLS olmayan bir özel durumun nasıl yakalanalınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a407-119">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="1a407-120">Bu örnekte, C# istemci kodunun, oluşturulmakta olan özel durum türünün bir olduğunu önceden öğrendiğine unutmayın <xref:System.String?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1a407-120">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a407-121"><xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>Bu tür, kodunuzun erişebileceği sürece özelliği özgün türünü geri çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a407-121">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a407-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a407-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="1a407-123">Özel durumlar ve özel durum Işleme</span><span class="sxs-lookup"><span data-stu-id="1a407-123">Exceptions and Exception Handling</span></span>](./index.md)
