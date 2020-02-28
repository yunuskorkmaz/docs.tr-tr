---
title: Ortak dil çalışma zamanında tür iletme
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160371"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="7354c-102">Ortak dil çalışma zamanında tür iletme</span><span class="sxs-lookup"><span data-stu-id="7354c-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="7354c-103">Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7354c-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="7354c-104">Örneğin, bir uygulamanın *Utility. dll*adlı bir derlemede `Example` sınıfını kullandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7354c-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="7354c-105">*Utility. dll* ' nin geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfını başka bir derlemeye taşıyabilirler.</span><span class="sxs-lookup"><span data-stu-id="7354c-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="7354c-106">*Utility. dll* ' nin eski sürümü *Utility. dll* ' nin yeni sürümü ve yardımcı bütünleştirilmiş kodu tarafından değiştirilirse, `Example` sınıfını kullanan uygulama, *yardımcı program. dll*' nin yeni sürümünde `Example` sınıfını bulamadığından başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7354c-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="7354c-107">*Utility. dll* ' nin geliştiricileri, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliğini kullanarak `Example` sınıfı için istekleri ileterek bundan kaçınabilir.</span><span class="sxs-lookup"><span data-stu-id="7354c-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="7354c-108">Özniteliği, *Utility. dll*' nin yeni sürümüne uygulanmışsa, `Example` sınıfına yönelik istekler, artık sınıfı içeren derlemeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="7354c-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="7354c-109">Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="7354c-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7354c-110">.NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7354c-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="7354c-111">Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7354c-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="7354c-112">Yani, uygulama veya C# C++içinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7354c-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="7354c-113">İleri türleri</span><span class="sxs-lookup"><span data-stu-id="7354c-113">Forward types</span></span>  
 <span data-ttu-id="7354c-114">Bir türü iletmek için dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="7354c-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="7354c-115">Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="7354c-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="7354c-116">Türün bulunması için kullanıldığı derlemede, taşınan tür için bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7354c-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="7354c-117">Aşağıdaki kod, taşınan `Example` adlı bir tür için özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7354c-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="7354c-118">Artık türü içeren derlemeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="7354c-118">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="7354c-119">Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="7354c-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="7354c-120">Örneğin, komut satırından bir C# dosya derlerken, türü içeren derlemeyi belirtmek için [-Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7354c-120">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="7354c-121">İçinde C++, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7354c-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7354c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7354c-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="7354c-123">Tür iletme (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="7354c-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="7354c-124">#using yönergesi</span><span class="sxs-lookup"><span data-stu-id="7354c-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
