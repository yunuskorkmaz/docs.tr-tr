---
title: COM Bileşenlerini .NET Framework'te Gösterme
description: COM bileşenlerini .NET 'e gösterme sürecini öğrenin. COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerlidir.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 459ba7ffed2e4f6c458f89a63b2baa37180d270d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620852"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="ec3b7-104">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="ec3b7-104">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="ec3b7-105">Bu bölümde, mevcut bir COM bileşenini yönetilen koda göstermek için gereken işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="ec3b7-106">.NET Framework ile sıkı bir şekilde tümleştirilen COM sunucularının yazılmasına ilişkin ayrıntılar için bkz. [Interoperation Için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="ec3b7-107">Mevcut COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerli kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="ec3b7-108">İdeal bir bileşen bir birincil birlikte çalışma derlemesine sahiptir ve COM tarafından uygulanan programlama standartlarına sıkı bir şekilde uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="ec3b7-109">COM bileşenlerini .NET Framework kullanıma sunmak için</span><span class="sxs-lookup"><span data-stu-id="ec3b7-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="ec3b7-110">[Bir tür kitaplığını derleme olarak Içeri aktarın](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="ec3b7-111">Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türler için meta veriler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="ec3b7-112">Meta veri olarak içeri aktarılan COM türlerini içeren bir derlemeyi almanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="ec3b7-113">[Yönetilen KODDA com türlerini kullanın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-113">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="ec3b7-114">Com türlerini inceleyebilir, örnekleri etkinleştirebilir ve COM nesnesi üzerinde yöntemleri herhangi bir yönetilen tür için yaptığınız şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="ec3b7-115">[Birlikte çalışabilirlik projesi derleyin](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="ec3b7-116">Windows SDK, Visual Basic, C# ve C++ dahil olmak üzere ortak dil belirtimi (CLS) ile uyumlu birkaç dil için derleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="ec3b7-117">[Birlikte çalışabilirlik uygulaması dağıtın](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="ec3b7-118">Birlikte çalışma uygulamaları, genel derleme önbelleğinde [tanımlayıcı adlı](../../standard/assembly/strong-named.md), imzalanmış derlemeler olarak en iyi şekilde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3b7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-119">See also</span></span>

- [<span data-ttu-id="ec3b7-120">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="ec3b7-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="ec3b7-121">[Birlikte çalışabilirlik için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ec3b7-121">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="ec3b7-122">COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu</span><span class="sxs-lookup"><span data-stu-id="ec3b7-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="ec3b7-123">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="ec3b7-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="ec3b7-124">Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="ec3b7-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
