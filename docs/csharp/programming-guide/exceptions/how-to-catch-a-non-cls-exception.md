---
title: 'Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: d0ba212610372a89c2a3b4c6a249c6d8a02fa507
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590290"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="ac04a-102">Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ac04a-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="ac04a-103">/CLI dahil C++bazı .NET dilleri, nesnelerin türetmeyen <xref:System.Exception>özel durumlar oluşturması için izin verir.</span><span class="sxs-lookup"><span data-stu-id="ac04a-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="ac04a-104">Bu tür özel durumlar *CLS dışı özel durumlar* veya *özel durumlar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ac04a-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="ac04a-105">İçinde C# CLS olmayan özel durumlar belirtemezsiniz, ancak bunları iki şekilde yakalayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac04a-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="ac04a-106">Bir `catch (RuntimeWrappedException e)` blok içinde.</span><span class="sxs-lookup"><span data-stu-id="ac04a-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="ac04a-107">Varsayılan olarak, bir görsel C# derleme CLS olmayan özel durumları sarmalanmış özel durumlar olarak yakalar.</span><span class="sxs-lookup"><span data-stu-id="ac04a-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="ac04a-108">Bu yöntemi, <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla erişilebilen özgün özel duruma erişmeniz gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac04a-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ac04a-109">Bu konu başlığında ilerleyen yordamda, özel durumların bu şekilde nasıl yakalanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac04a-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="ac04a-110">Genel bir catch bloğu içinde (özel durum türü belirtilmeden bir catch bloğu), diğer `catch` tüm bloklarından sonra konur.</span><span class="sxs-lookup"><span data-stu-id="ac04a-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="ac04a-111">CLS olmayan özel durumlara yanıt olarak bazı eylemler (örneğin, bir günlük dosyasına yazma) gerçekleştirmek istediğinizde ve özel durum bilgilerine erişmeniz gerekmiyorsa bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac04a-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="ac04a-112">Varsayılan olarak ortak dil çalışma zamanı tüm özel durumları sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="ac04a-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="ac04a-113">Bu davranışı devre dışı bırakmak için, bu derleme düzeyi özniteliğini kodunuzda, genellikle AssemblyInfo.cs dosyasında ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="ac04a-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="ac04a-114">CLS olmayan bir özel durumu yakalamak için</span><span class="sxs-lookup"><span data-stu-id="ac04a-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="ac04a-115">Bir `catch(RuntimeWrappedException e)` blok içinde, <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla özgün özel duruma erişin.</span><span class="sxs-lookup"><span data-stu-id="ac04a-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac04a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac04a-116">Example</span></span>  
 <span data-ttu-id="ac04a-117">Aşağıdaki örnek,/Cliende C++yazılmış bir sınıf KITAPLıĞıNDAN oluşturulan CLS olmayan bir özel durumun nasıl yakalanalınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac04a-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="ac04a-118">Bu örnekte, C# istemci kodunun, oluşturulmakta olan özel durum türünün bir <xref:System.String?displayProperty=nameWithType>olduğunu önceden öğrendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ac04a-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac04a-119">Bu tür, kodunuzun <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> erişebileceği sürece özelliği özgün türünü geri çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac04a-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac04a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac04a-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="ac04a-121">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ac04a-121">Exceptions and Exception Handling</span></span>](./index.md)
