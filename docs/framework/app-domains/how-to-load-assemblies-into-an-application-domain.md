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
ms.openlocfilehash: fd6f14f89d143edd03f8b5d028ec84315b2f2e97
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886545"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="1bf71-102">Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme</span><span class="sxs-lookup"><span data-stu-id="1bf71-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="1bf71-103">Uygulama etki alanına bir derlemeyi yüklemek için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1bf71-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="1bf71-104">Kullanmak için önerilen yoldur `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.Load%2A> yöntemi <xref:System.Reflection.Assembly?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1bf71-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1bf71-105">Derlemeleri yüklenebilir diğer yolları:</span><span class="sxs-lookup"><span data-stu-id="1bf71-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="1bf71-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Yöntemi <xref:System.Reflection.Assembly> sınıfı, dosya konumu verilen bir derleme yükler.</span><span class="sxs-lookup"><span data-stu-id="1bf71-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="1bf71-107">Bu yöntemle derlemeler yüklemek, farklı yükleme bağlamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bf71-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="1bf71-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri salt yansıma bağlamına bir derlemeyi yüklemek.</span><span class="sxs-lookup"><span data-stu-id="1bf71-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="1bf71-109">Bu bağlamı yüklenen derlemeler incelenir, ancak yürütülmedi, diğer platformları hedefleyen derlemeleri incelenmesi izin verme.</span><span class="sxs-lookup"><span data-stu-id="1bf71-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="1bf71-110">Bkz: [nasıl yapılır: salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="1bf71-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bf71-111">Yalnızca yansıma bağlamı, .NET Framework 2.0 sürümünde yenidir.</span><span class="sxs-lookup"><span data-stu-id="1bf71-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="1bf71-112">Yöntemler gibi <xref:System.AppDomain.CreateInstance%2A> ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> , <xref:System.AppDomain> sınıfı, bir uygulama etki alanına derlemeler yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1bf71-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="1bf71-113"><xref:System.Type.GetType%2A> Yöntemi <xref:System.Type> sınıfı derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1bf71-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="1bf71-114"><xref:System.AppDomain.Load%2A> Yöntemi <xref:System.AppDomain?displayProperty=nameWithType> sınıfı derlemeleri yükleyebilirsiniz ancak öncelikle COM birlikte çalışabilirlik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bf71-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="1bf71-115">İçinden çağrıldığı uygulama etki alanından başka bir uygulama etki alanına derlemeler yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf71-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bf71-116">.NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklü çalışma zamanı daha yüksek bir sürüm numarasına sahip .NET Framework sürümü ile derlenen bütünleştirilmiş yüklemez.</span><span class="sxs-lookup"><span data-stu-id="1bf71-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="1bf71-117">Bu sürüm numarasının büyük ve küçük bileşenleri birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1bf71-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="1bf71-118">Uygulama etki alanları arasında paylaşılan just-in-time (JIT) derlenmiş kodunun yüklenen derlemelerin yolu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf71-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="1bf71-119">Daha fazla bilgi için [uygulama etki alanları ve derlemeler](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span><span class="sxs-lookup"><span data-stu-id="1bf71-119">For more information, see [Application Domains and Assemblies](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf71-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf71-120">Example</span></span>  
 <span data-ttu-id="1bf71-121">Aşağıdaki kod yüklerini geçerli uygulama etki alanına "example.exe" veya "example.dll" adlı bir derleme adlı bir tür alır `Example` adlı bir parametresiz yöntemin, derlemenin alır `MethodA` , yazın ve yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="1bf71-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="1bf71-122">Kapsamlı bir açıklama yüklenen derlemeden bilgi edinme hakkında bilgi için bkz: [dinamik olarak yükleme ve türleri kullanarak](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="1bf71-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf71-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf71-123">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [<span data-ttu-id="1bf71-124">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="1bf71-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="1bf71-125">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1bf71-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="1bf71-126">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1bf71-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 [<span data-ttu-id="1bf71-127">Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme</span><span class="sxs-lookup"><span data-stu-id="1bf71-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [<span data-ttu-id="1bf71-128">Uygulama Etki Alanları ve Derlemeler</span><span class="sxs-lookup"><span data-stu-id="1bf71-128">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
