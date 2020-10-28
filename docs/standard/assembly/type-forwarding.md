---
title: Ortak dil çalışma zamanında tür iletme
description: Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir .NET derlemesine taşımanızı sağlar.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687666"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="34bfa-103">Ortak dil çalışma zamanında tür iletme</span><span class="sxs-lookup"><span data-stu-id="34bfa-103">Type forwarding in the common language runtime</span></span>

<span data-ttu-id="34bfa-104">Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="34bfa-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="34bfa-105">Örneğin, bir uygulamanın `Example` sınıfı *Utility.dll* adlı bir derlemede kullandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="34bfa-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll* .</span></span> <span data-ttu-id="34bfa-106">*Utility.dll* geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfı başka bir derlemeye taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="34bfa-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="34bfa-107">*Utility.dll* eski sürümü *Utility.dll* yeni sürümü ve yardımcı bütünleştirilmiş kodu ile değiştirilirse, sınıfı kullanan uygulama, `Example` `Example` sınıfı yeni *Utility.dll* sürümünde konumlandıramadığından başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="34bfa-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll* .</span></span>  
  
 <span data-ttu-id="34bfa-108">*Utility.dll* geliştiricileri `Example` , özniteliğini kullanarak sınıfının isteklerini ileterek bunu önleyebilir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> .</span><span class="sxs-lookup"><span data-stu-id="34bfa-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="34bfa-109">Öznitelik *Utility.dll* yeni sürümüne uygulanmışsa, sınıfı için istekler, `Example` artık sınıfı içeren derlemeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="34bfa-109">If the attribute has been applied to the new version of *Utility.dll* , requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="34bfa-110">Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="34bfa-110">The existing application continues to function normally, without recompilation.</span></span>

## <a name="forward-a-type"></a><span data-ttu-id="34bfa-111">Bir tür ilet</span><span class="sxs-lookup"><span data-stu-id="34bfa-111">Forward a type</span></span>

 <span data-ttu-id="34bfa-112">Bir türü iletmek için dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="34bfa-112">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="34bfa-113">Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="34bfa-113">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="34bfa-114">Türünün bulunması için kullanıldığı derlemede, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşınan tür için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="34bfa-114">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="34bfa-115">Aşağıdaki kod, taşınan adlı bir tür için özniteliğini gösterir `Example` .</span><span class="sxs-lookup"><span data-stu-id="34bfa-115">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="34bfa-116">Artık türü içeren derlemeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="34bfa-116">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="34bfa-117">Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="34bfa-117">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="34bfa-118">Örneğin, komut satırından bir C# dosyası derlerken, türü içeren derlemeyi belirtmek için [-Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="34bfa-118">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="34bfa-119">C++ ' da, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="34bfa-119">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34bfa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34bfa-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="34bfa-121">Tür iletme (C++/CLı)</span><span class="sxs-lookup"><span data-stu-id="34bfa-121">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="34bfa-122">#using yönergesi</span><span class="sxs-lookup"><span data-stu-id="34bfa-122">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
