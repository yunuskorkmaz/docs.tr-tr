---
title: COM Bileşenlerini .NET Framework'te Gösterme
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e17c0b8c3676bb632c9b45af0577708c98446967
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="2c012-102">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="2c012-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="2c012-103">Bu bölümde, yönetilen kod için var olan bir COM bileşeni kullanıma sunmak için gereken işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c012-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="2c012-104">COM sunucuları bu sıkı bir şekilde yazma hakkında ayrıntılar .NET Framework ile tümleştirmek için bkz: [birlikte çalışma için tasarım değerlendirmeleri](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2c012-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span></span>
  
 <span data-ttu-id="2c012-105">Var olan COM bileşenlerini değerli yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevselliği olarak kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="2c012-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="2c012-106">İdeal bir bileşen birincil birlikte çalışma derlemesi vardır ve COM tarafından uygulanan programlama standartlara sıkıca uyumlu</span><span class="sxs-lookup"><span data-stu-id="2c012-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="2c012-107">COM bileşenlerini .NET Framework'te kullanıma sunmak için</span><span class="sxs-lookup"><span data-stu-id="2c012-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="2c012-108">[Tür kitaplığını derleme olarak içeri aktarma](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="2c012-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="2c012-109">Ortak dil çalışma zamanı meta veri COM türleri dahil olmak üzere tüm türleri için gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2c012-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="2c012-110">Meta veri içeri COM türlerini içeren bir derlemenin almak için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="2c012-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="2c012-111">[Yönetilen kodda COM türlerini oluşturabilir](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2c012-111">[Create COM types in managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
     <span data-ttu-id="2c012-112">COM türlerini inceleyin, örnekleri etkinleştirin ve COM nesnesinin yöntemlerde, herhangi bir yönetilen türü için aynı şekilde çağırır.</span><span class="sxs-lookup"><span data-stu-id="2c012-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="2c012-113">[Birlikte çalışma projesi derleme](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="2c012-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="2c012-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Çeşitli diller uyumlu ile ortak dil belirtimi (de dahil olmak üzere CLS), derleyicileri sağlayan [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++.</span><span class="sxs-lookup"><span data-stu-id="2c012-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="2c012-115">[Birlikte çalışma uygulamasını dağıtma](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="2c012-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="2c012-116">Birlikte çalışma uygulamaları olarak en iyi dağıtıldığı [tanımlayıcı adlı](../app-domains/strong-named-assemblies.md), genel derleme önbelleğinde imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="2c012-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c012-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c012-117">See Also</span></span>  
 [<span data-ttu-id="2c012-118">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="2c012-118">Interoperating with Unmanaged Code</span></span>](index.md)  
 <span data-ttu-id="2c012-119">[Birlikte çalışma için tasarım konuları](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2c012-119">[Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span></span>  
 [<span data-ttu-id="2c012-120">COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu</span><span class="sxs-lookup"><span data-stu-id="2c012-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="2c012-121">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="2c012-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="2c012-122">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="2c012-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
