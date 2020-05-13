---
title: Ortak dil çalışma zamanında tür iletme
description: Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir .NET derlemesine taşımanızı sağlar.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378590"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="91ddf-103">Ortak dil çalışma zamanında tür iletme</span><span class="sxs-lookup"><span data-stu-id="91ddf-103">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="91ddf-104">Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91ddf-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="91ddf-105">Örneğin, bir uygulamanın `Example` sınıfının *Utility. dll*adlı bir derlemede kullandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="91ddf-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="91ddf-106">*Utility. dll* ' nin geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfı başka bir derlemeye taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="91ddf-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="91ddf-107">*Utility* . dll ' nin eski sürümü *Utility. dll* ' nin yeni sürümü ve yardımcı bütünleştirilmiş kodu tarafından değiştirilirse, sınıfını kullanan uygulama, `Example` `Example` sınıfının yeni bir *Utility. dll*sürümünde konumlandıramadığı için başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="91ddf-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="91ddf-108">*Utility. dll* ' nin geliştiricileri `Example` , özniteliğini kullanarak, sınıfının isteklerini ileterek bunu önleyebilir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> .</span><span class="sxs-lookup"><span data-stu-id="91ddf-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="91ddf-109">Özniteliği, *Utility. dll*' nin yeni sürümüne uygulanmışsa, `Example` sınıfının istekleri artık sınıfı içeren derlemeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="91ddf-109">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="91ddf-110">Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="91ddf-110">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91ddf-111">.NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ddf-111">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="91ddf-112">Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="91ddf-112">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="91ddf-113">Yani, uygulama C# veya C++ dilinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="91ddf-113">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="91ddf-114">İleri türleri</span><span class="sxs-lookup"><span data-stu-id="91ddf-114">Forward types</span></span>  
 <span data-ttu-id="91ddf-115">Bir türü iletmek için dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="91ddf-115">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="91ddf-116">Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="91ddf-116">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="91ddf-117">Türünün bulunması için kullanıldığı derlemede, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşınan tür için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="91ddf-117">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="91ddf-118">Aşağıdaki kod, taşınan adlı bir tür için özniteliğini gösterir `Example` .</span><span class="sxs-lookup"><span data-stu-id="91ddf-118">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="91ddf-119">Artık türü içeren derlemeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="91ddf-119">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="91ddf-120">Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="91ddf-120">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="91ddf-121">Örneğin, komut satırından bir C# dosyası derlerken, türü içeren derlemeyi belirtmek için [-Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91ddf-121">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="91ddf-122">C++ ' da, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91ddf-122">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ddf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ddf-123">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="91ddf-124">Tür iletme (C++/CLı)</span><span class="sxs-lookup"><span data-stu-id="91ddf-124">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="91ddf-125">#using yönergesi</span><span class="sxs-lookup"><span data-stu-id="91ddf-125">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
