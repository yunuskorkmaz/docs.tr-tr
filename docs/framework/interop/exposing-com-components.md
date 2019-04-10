---
title: COM Bileşenlerini .NET Framework'te Gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b7aa028afeaf4230ee079f0d4071a5cd6a21c65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320918"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="8cac1-102">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="8cac1-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="8cac1-103">Bu bölüm, yönetilen kod için varolan bir COM bileşeni kullanıma sunmak için gereken işlem özetler.</span><span class="sxs-lookup"><span data-stu-id="8cac1-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="8cac1-104">COM sunucuları, sıkı bir şekilde yazma hakkında ayrıntılar .NET Framework ile tümleştirmek için bkz: [birlikte çalışma için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8cac1-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="8cac1-105">Mevcut COM değerli kaynakları yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevi olarak bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="8cac1-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="8cac1-106">İdeal bir bileşeni olan birincil birlikte çalışma derlemesi ve sıkı bir şekilde COM tarafından uygulanan programlama standartlarına uyar</span><span class="sxs-lookup"><span data-stu-id="8cac1-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="8cac1-107">COM bileşenlerini .NET Framework'te göstermek için</span><span class="sxs-lookup"><span data-stu-id="8cac1-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="8cac1-108">[Bir tür kitaplığını derleme olarak içeri](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="8cac1-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="8cac1-109">Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türleri için meta verileri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8cac1-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="8cac1-110">COM türleri olarak meta veriler içe içeren bir derlemenin almak için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="8cac1-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="8cac1-111">[Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8cac1-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="8cac1-112">COM türlerini inceleyin, örnekleri etkinleştirmek ve herhangi bir yönetilen türü için yaptığınız gibi COM nesnesinin yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8cac1-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="8cac1-113">[Birlikte çalışma projesi derleme](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="8cac1-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="8cac1-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Birçok dilde uyumlu olan ortak dil belirtimi (dahil olmak üzere CLS), derleyiciler sağlar [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#ve C++.</span><span class="sxs-lookup"><span data-stu-id="8cac1-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4. <span data-ttu-id="8cac1-115">[Birlikte çalışma uygulamasını dağıtma](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="8cac1-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="8cac1-116">Birlikte çalışma uygulamaları olarak dağıtılan en iyi [tanımlayıcı adlı](../app-domains/strong-named-assemblies.md), genel derleme önbelleğinde derlemeleri imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="8cac1-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cac1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cac1-117">See also</span></span>

- [<span data-ttu-id="8cac1-118">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="8cac1-118">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="8cac1-119">Birlikte Çalışma için Tasarımla İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="8cac1-119">Design Considerations for Interoperation</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [<span data-ttu-id="8cac1-120">COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu</span><span class="sxs-lookup"><span data-stu-id="8cac1-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="8cac1-121">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="8cac1-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="8cac1-122">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="8cac1-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
