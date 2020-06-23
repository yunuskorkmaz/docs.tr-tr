---
title: 'Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme'
description: .NET 'teki bir uygulama etki alanına derlemeler yüklemeyi öğrenin. Önerilen yol, System. Reflection. Assembly içinde statik (veya paylaşılan) yükleme yöntemini kullanmaktır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104751"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="8c093-104">Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme</span><span class="sxs-lookup"><span data-stu-id="8c093-104">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="8c093-105">Bir uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="8c093-105">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="8c093-106">Önerilen yol, `static` `Shared` sınıfının (Visual Basic) <xref:System.Reflection.Assembly.Load%2A> sınıfında kullanılır <xref:System.Reflection.Assembly?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8c093-106">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8c093-107">Derlemelerin yüklenebilme diğer yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8c093-107">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="8c093-108"><xref:System.Reflection.Assembly.LoadFrom%2A>Sınıfının yöntemi, <xref:System.Reflection.Assembly> dosya konumu verilen bir derlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="8c093-108">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="8c093-109">Derlemeleri bu yöntemle yüklemek farklı bir yük bağlamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c093-109">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="8c093-110"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri bir derlemeyi yalnızca yansıma bağlamına yükler.</span><span class="sxs-lookup"><span data-stu-id="8c093-110">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="8c093-111">Bu içeriğe yüklenen derlemeler incelenebilir ancak yürütülmeyebilir, diğer platformları hedefleyen derlemelerin incelenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8c093-111">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="8c093-112">Bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="8c093-112">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c093-113">Yalnızca yansıma bağlamı .NET Framework sürüm 2,0 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="8c093-113">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="8c093-114"><xref:System.AppDomain.CreateInstance%2A>Sınıfının ve gibi yöntemleri <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> bir uygulama etki alanına derlemeler yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8c093-114">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="8c093-115"><xref:System.Type.GetType%2A> <xref:System.Type> Sınıfının yöntemi derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8c093-115">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="8c093-116"><xref:System.AppDomain.Load%2A> <xref:System.AppDomain?displayProperty=nameWithType> Sınıfının yöntemi derlemeleri yükleyebilir, ancak BIRINCIL olarak com birlikte çalışabilirlik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c093-116">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="8c093-117">Derlemeleri, çağrıldığı uygulama etki alanından başka bir uygulama etki alanına yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c093-117">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c093-118">.NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez.</span><span class="sxs-lookup"><span data-stu-id="8c093-118">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="8c093-119">Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8c093-119">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="8c093-120">Yüklenen derlemelerdeki tam zamanında (JıT) derlenmiş kodun uygulama etki alanları arasında paylaşılma şeklini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c093-120">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="8c093-121">Daha fazla bilgi için bkz. [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="8c093-121">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c093-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c093-122">Example</span></span>  
 <span data-ttu-id="8c093-123">Aşağıdaki kod, geçerli uygulama etki alanına "example.exe" veya "example.dll" adlı bir derlemeyi yükler, derlemeden adlı bir tür alır, `Example` Bu tür için adlı parametresiz bir yöntemi alır `MethodA` ve yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="8c093-123">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="8c093-124">Yüklü bir derlemeden bilgi alma hakkında ayrıntılı bir tartışma için bkz. [dinamik olarak yükleme ve türleri kullanma](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="8c093-124">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8c093-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c093-125">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="8c093-126">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="8c093-126">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="8c093-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8c093-127">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="8c093-128">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8c093-128">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="8c093-129">Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme</span><span class="sxs-lookup"><span data-stu-id="8c093-129">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="8c093-130">Uygulama Etki Alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="8c093-130">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
