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
ms.openlocfilehash: 9945b66f9d9fcdfb075bd48f5f56f30f2fdf7712
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="5443c-102">Ortak Dil Çalışma Zamanında Tür İletme</span><span class="sxs-lookup"><span data-stu-id="5443c-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="5443c-103">Tür iletme özgün derleme kullanan uygulamaları yeniden derlemenize gerek kalmadan başka bir derlemeye türü taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5443c-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="5443c-104">Örneğin, bir uygulama kullandığını varsayın `Example` adlı bir derleme sınıfında `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="5443c-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="5443c-105">Geliştiriciler `Utility.dll` derleme yeniden düzenlemeniz karar verebilirsiniz ve bunlar işlemde taşıma `Example` başka bir derleme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5443c-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="5443c-106">Varsa eski sürümünü `Utility.dll` yeni sürümü tarafından değiştirilir `Utility.dll` yardımcı derleme, uygulamayı kullanan ve `Example` sınıfı başarısız konumunu belirleyemediği için `Example` yeni sürümünü sınıfında `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="5443c-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="5443c-107">Geliştiriciler `Utility.dll` bu istekleri ileterek önleyebilirsiniz `Example` sınıfı, kullanarak <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5443c-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="5443c-108">Öznitelik'ın yeni sürümüne uygulanıp uygulanmadığını `Utility.dll`, için istekleri `Example` sınıfı şimdi sınıfı içeren derlemeye iletilir.</span><span class="sxs-lookup"><span data-stu-id="5443c-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="5443c-109">Var olan uygulamaya yeniden derlenmek normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="5443c-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5443c-110">.NET Framework sürüm 2. 0'da, Visual Basic'te yazılmış derlemelerden türler iletemez.</span><span class="sxs-lookup"><span data-stu-id="5443c-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="5443c-111">Ancak, Visual Basic ile yazılmış bir uygulama iletilen türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5443c-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="5443c-112">Diğer bir deyişle, C# veya C++ kodlanmış bütünleştirilmiş uygulama kullanıyorsa ve bu derleme türünden başka bir derlemeye iletilir, Visual Basic uygulama iletilen türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5443c-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="5443c-113">İletme türleri</span><span class="sxs-lookup"><span data-stu-id="5443c-113">Forwarding Types</span></span>  
 <span data-ttu-id="5443c-114">Bir tür iletme gereken dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="5443c-114">There are four steps to forwarding a type:</span></span>  
  
1.  <span data-ttu-id="5443c-115">Kaynak kodu türü için özgün derlemeden hedef derlemeye taşıyın.</span><span class="sxs-lookup"><span data-stu-id="5443c-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2.  <span data-ttu-id="5443c-116">Türü kullanıldığı yer almasını derlemede eklemek bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşınmış türü için.</span><span class="sxs-lookup"><span data-stu-id="5443c-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="5443c-117">Aşağıdaki kod adlı tür özniteliğini gösterir `Example` , taşındı.</span><span class="sxs-lookup"><span data-stu-id="5443c-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  <span data-ttu-id="5443c-118">Şimdi türünü içeren bütünleştirilmiş kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="5443c-118">Compile the assembly that now contains the type.</span></span>  
  
4.  <span data-ttu-id="5443c-119">Türü artık türünü içeren bütünleştirilmiş başvuru yer almasını kullanıldığı derleme yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="5443c-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="5443c-120">Örneğin, C# dosyasına komut satırından derleme ise kullanın [/Reference (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) türünü içeren bütünleştirilmiş kodun belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5443c-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="5443c-121">C++'ta kullanmak [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) türünü içeren bütünleştirilmiş kodun belirtmek için kaynak dosyasında yönergesi.</span><span class="sxs-lookup"><span data-stu-id="5443c-121">In C++, use the [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5443c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5443c-122">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [<span data-ttu-id="5443c-123">Tür İletme (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="5443c-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)  
 [<span data-ttu-id="5443c-124">#using yönergesi</span><span class="sxs-lookup"><span data-stu-id="5443c-124">#using Directive</span></span>](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
