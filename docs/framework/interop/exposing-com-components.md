---
title: COM Bileşenlerini .NET Framework'te Gösterme
description: COM bileşenlerini .NET 'e gösterme sürecini öğrenin. COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerlidir.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 34dda58d9513874169927164706fafdd95e8ed84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554188"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="a1dc1-104">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="a1dc1-104">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="a1dc1-105">Bu bölümde, mevcut bir COM bileşenini yönetilen koda göstermek için gereken işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="a1dc1-106">.NET Framework ile sıkı bir şekilde tümleştirilen COM sunucularının yazılmasına ilişkin ayrıntılar için bkz. [Interoperation Için tasarım konuları](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a1dc1-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="a1dc1-107">Mevcut COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerli kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="a1dc1-108">İdeal bir bileşen bir birincil birlikte çalışma derlemesine sahiptir ve COM tarafından uygulanan programlama standartlarına sıkı bir şekilde uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="a1dc1-109">COM bileşenlerini .NET Framework kullanıma sunmak için</span><span class="sxs-lookup"><span data-stu-id="a1dc1-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="a1dc1-110">[Bir tür kitaplığını derleme olarak Içeri aktarın](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a1dc1-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="a1dc1-111">Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türler için meta veriler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="a1dc1-112">Meta veri olarak içeri aktarılan COM türlerini içeren bir derlemeyi almanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="a1dc1-113">[Yönetilen KODDA com türlerini kullanın](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a1dc1-113">[Use COM types in managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="a1dc1-114">Com türlerini inceleyebilir, örnekleri etkinleştirebilir ve COM nesnesi üzerinde yöntemleri herhangi bir yönetilen tür için yaptığınız şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="a1dc1-115">[Birlikte çalışabilirlik projesi derleyin](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="a1dc1-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="a1dc1-116">Windows SDK, Visual Basic, C# ve C++ dahil olmak üzere ortak dil belirtimi (CLS) ile uyumlu birkaç dil için derleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="a1dc1-117">[Birlikte çalışabilirlik uygulaması dağıtın](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="a1dc1-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="a1dc1-118">Birlikte çalışma uygulamaları, genel derleme önbelleğinde [tanımlayıcı adlı](../../standard/assembly/strong-named.md), imzalanmış derlemeler olarak en iyi şekilde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dc1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1dc1-119">See also</span></span>

- [<span data-ttu-id="a1dc1-120">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="a1dc1-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="a1dc1-121">[Birlikte çalışabilirlik için tasarım konuları](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a1dc1-121">[Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="a1dc1-122">COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu</span><span class="sxs-lookup"><span data-stu-id="a1dc1-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="a1dc1-123">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="a1dc1-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="a1dc1-124">Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="a1dc1-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
