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
ms.openlocfilehash: c560e2c5858de67442ccbcd18c8f92b142cc178d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119902"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="22028-102">Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme</span><span class="sxs-lookup"><span data-stu-id="22028-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="22028-103">Bir uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="22028-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="22028-104">Önerilen `static` yol,`Shared` <xref:System.Reflection.Assembly.Load%2A> <xref:System.Reflection.Assembly?displayProperty=nameWithType> sınıfının (Visual Basic) sınıfında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22028-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="22028-105">Derlemelerin yüklenebilme diğer yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="22028-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="22028-106"><xref:System.Reflection.Assembly> Sınıfının yöntemi, <xref:System.Reflection.Assembly.LoadFrom%2A> dosya konumu verilen bir derlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="22028-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="22028-107">Derlemeleri bu yöntemle yüklemek farklı bir yük bağlamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="22028-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="22028-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri bir derlemeyi yalnızca yansıma bağlamına yükler.</span><span class="sxs-lookup"><span data-stu-id="22028-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="22028-109">Bu içeriğe yüklenen derlemeler incelenebilir ancak yürütülmeyebilir, diğer platformları hedefleyen derlemelerin incelenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="22028-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="22028-110">Bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="22028-110">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22028-111">Yalnızca yansıma bağlamı .NET Framework sürüm 2,0 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="22028-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="22028-112"><xref:System.AppDomain> Sınıfının <xref:System.AppDomain.CreateInstance%2A> ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> gibi yöntemleri bir uygulama etki alanına derlemeler yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="22028-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="22028-113"><xref:System.Type> Sınıfının <xref:System.Type.GetType%2A> yöntemi derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="22028-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="22028-114"><xref:System.AppDomain?displayProperty=nameWithType> Sınıfının <xref:System.AppDomain.Load%2A> yöntemi derlemeleri yükleyebilir, ancak birincil olarak com birlikte çalışabilirlik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22028-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="22028-115">Derlemeleri, çağrıldığı uygulama etki alanından başka bir uygulama etki alanına yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="22028-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22028-116">.NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez.</span><span class="sxs-lookup"><span data-stu-id="22028-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="22028-117">Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="22028-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="22028-118">Yüklenen derlemelerdeki tam zamanında (JıT) derlenmiş kodun uygulama etki alanları arasında paylaşılma şeklini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22028-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="22028-119">Daha fazla bilgi için bkz. [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="22028-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22028-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="22028-120">Example</span></span>  
 <span data-ttu-id="22028-121">Aşağıdaki kod, geçerli uygulama etki alanına "example. exe" veya "example. dll" adlı bir derlemeyi yükler, derlemeden adlı `Example` bir tür alır, bu tür için adlı `MethodA` parametresiz bir yöntemi alır ve yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="22028-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="22028-122">Yüklü bir derlemeden bilgi alma hakkında ayrıntılı bir tartışma için bkz. [dinamik olarak yükleme ve türleri kullanma](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="22028-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="22028-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22028-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="22028-124">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="22028-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="22028-125">Yansıma</span><span class="sxs-lookup"><span data-stu-id="22028-125">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="22028-126">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="22028-126">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="22028-127">Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme</span><span class="sxs-lookup"><span data-stu-id="22028-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="22028-128">Uygulama Etki Alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="22028-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
