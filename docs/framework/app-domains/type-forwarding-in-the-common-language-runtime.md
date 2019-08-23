---
title: Ortak Dil Çalışma Zamanında Tür İletme
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921411"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="243a5-102">Ortak Dil Çalışma Zamanında Tür İletme</span><span class="sxs-lookup"><span data-stu-id="243a5-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="243a5-103">Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="243a5-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="243a5-104">Örneğin, bir uygulamanın `Example` sınıfını adlı `Utility.dll`bir derlemede kullandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="243a5-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="243a5-105">Geliştiriciler `Utility.dll` , derlemeyi yeniden düzenleme kararı verebilir ve süreçte, `Example` sınıfı başka bir derlemeye taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="243a5-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="243a5-106">Eski sürümü `Utility.dll` `Utility.dll` ve onun yardımcı derlemesi yeni sürümü ile değiştirilirse, sınıfını kullanan `Example` uygulama, `Example` sınıfının yeni sürümünde `Utility.dll`konumlandıramadığı için başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="243a5-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="243a5-107">' A ait `Utility.dll` geliştiriciler, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliğini kullanarak `Example` sınıfının isteklerini ileterek bunu önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="243a5-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="243a5-108">Özniteliği yeni sürümüne `Utility.dll`uygulanmışsa, `Example` sınıfı için istekler, artık sınıfını içeren derlemeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="243a5-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="243a5-109">Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="243a5-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="243a5-110">.NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="243a5-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="243a5-111">Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="243a5-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="243a5-112">Yani, uygulama veya C# C++içinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="243a5-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="243a5-113">İletme türleri</span><span class="sxs-lookup"><span data-stu-id="243a5-113">Forwarding Types</span></span>  
 <span data-ttu-id="243a5-114">Bir türü iletmek için dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="243a5-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="243a5-115">Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="243a5-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2. <span data-ttu-id="243a5-116">Türünün bulunması için kullanıldığı derlemede, taşınan tür için bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="243a5-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="243a5-117">Aşağıdaki kod, taşınan adlı `Example` bir tür için özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="243a5-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. <span data-ttu-id="243a5-118">Artık türü içeren derlemeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="243a5-118">Compile the assembly that now contains the type.</span></span>  
  
4. <span data-ttu-id="243a5-119">Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="243a5-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="243a5-120">Örneğin, komut satırından bir C# dosya derlerken, türü içeren derlemeyi belirtmek için [/Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="243a5-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="243a5-121">İçinde C++, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="243a5-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243a5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="243a5-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="243a5-123">Tür İletme (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="243a5-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="243a5-124">#using yönergesi</span><span class="sxs-lookup"><span data-stu-id="243a5-124">#using Directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
