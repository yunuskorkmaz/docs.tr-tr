---
title: 'Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b66d0a88864188d67aab19de67aaa857a06eaa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053162"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="f1c62-102">Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme</span><span class="sxs-lookup"><span data-stu-id="f1c62-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="f1c62-103">Bir uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="f1c62-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="f1c62-104">Önerilen yol `static` ,`Shared` sınıfının<xref:System.Reflection.Assembly?displayProperty=nameWithType> (Visual Basic) <xref:System.Reflection.Assembly.Load%2A> sınıfında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c62-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f1c62-105">Derlemelerin yüklenebilme diğer yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f1c62-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="f1c62-106">Sınıfının<xref:System.Reflection.Assembly> yöntemi, <xref:System.Reflection.Assembly.LoadFrom%2A> dosya konumu verilen bir derlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="f1c62-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="f1c62-107">Derlemeleri bu yöntemle yüklemek farklı bir yük bağlamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1c62-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="f1c62-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri bir derlemeyi yalnızca yansıma bağlamına yükler.</span><span class="sxs-lookup"><span data-stu-id="f1c62-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="f1c62-109">Bu içeriğe yüklenen derlemeler incelenebilir ancak yürütülmeyebilir, diğer platformları hedefleyen derlemelerin incelenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f1c62-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="f1c62-110">Bkz [. nasıl yapılır: Derlemeleri yalnızca yansıma bağlamına](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f1c62-110">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1c62-111">Yalnızca yansıma bağlamı .NET Framework sürüm 2,0 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="f1c62-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="f1c62-112"><xref:System.AppDomain.CreateInstance%2A> Sınıfının ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> gibi yöntemleri bir uygulama etki alanına derlemeler yükleyebilir. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="f1c62-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="f1c62-113"><xref:System.Type> Sınıfının <xref:System.Type.GetType%2A> yöntemi derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c62-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="f1c62-114"><xref:System.AppDomain?displayProperty=nameWithType> Sınıfının yöntemi derlemeleri yükleyebilir, ancak birincil olarak com birlikte çalışabilirlik için kullanılır. <xref:System.AppDomain.Load%2A></span><span class="sxs-lookup"><span data-stu-id="f1c62-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="f1c62-115">Derlemeleri, çağrıldığı uygulama etki alanından başka bir uygulama etki alanına yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1c62-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1c62-116">.NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez.</span><span class="sxs-lookup"><span data-stu-id="f1c62-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="f1c62-117">Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1c62-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="f1c62-118">Yüklenen derlemelerdeki tam zamanında (JıT) derlenmiş kodun uygulama etki alanları arasında paylaşılma şeklini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1c62-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="f1c62-119">Daha fazla bilgi için bkz. [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="f1c62-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1c62-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1c62-120">Example</span></span>  
 <span data-ttu-id="f1c62-121">Aşağıdaki kod, geçerli uygulama etki alanına "example. exe" veya "example. dll" adlı bir derlemeyi yükler, derlemeden adlı `Example` bir tür alır, bu tür için adlı `MethodA` parametresiz bir yöntemi alır ve yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="f1c62-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="f1c62-122">Yüklü bir derlemeden bilgi alma hakkında ayrıntılı bir tartışma için bkz. [dinamik olarak yükleme ve türleri kullanma](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="f1c62-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f1c62-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c62-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="f1c62-124">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="f1c62-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f1c62-125">Yansıma</span><span class="sxs-lookup"><span data-stu-id="f1c62-125">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="f1c62-126">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1c62-126">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="f1c62-127">Nasıl yapılır: Derlemeleri yalnızca yansıma Içeriğine yükle</span><span class="sxs-lookup"><span data-stu-id="f1c62-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="f1c62-128">Uygulama etki alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="f1c62-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
