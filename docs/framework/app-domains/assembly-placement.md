---
title: Derleme Yerleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119965"
---
# <a name="assembly-placement"></a><span data-ttu-id="49a32-102">Derleme Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="49a32-102">Assembly Placement</span></span>
<span data-ttu-id="49a32-103">Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz.</span><span class="sxs-lookup"><span data-stu-id="49a32-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="49a32-104">Bir yapılandırma dosyasındaki [ \<codebase> öğesini](../configure-apps/file-schema/runtime/codebase-element.md) kullanarak ortak dil çalışma zamanının bir derlemeyi aradığı yeri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49a32-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="49a32-105">Derleme tanımlayıcı bir ada sahip değilse, [ \<codebase> öğesi](../configure-apps/file-schema/runtime/codebase-element.md) kullanılarak belirtilen konum, uygulama dizini veya bir alt dizin ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="49a32-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="49a32-106">Derlemenin tanımlayıcı bir adı varsa, [ \<codebase> öğesi](../configure-apps/file-schema/runtime/codebase-element.md) bilgisayar üzerinde veya bir ağ üzerinde herhangi bir konumu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="49a32-106">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="49a32-107">Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="49a32-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="49a32-108">Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="49a32-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="49a32-109">COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="49a32-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a32-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49a32-110">See also</span></span>

- [<span data-ttu-id="49a32-111">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="49a32-111">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="49a32-112">Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="49a32-112">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="49a32-113">Yönetilmeyen kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="49a32-113">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="49a32-114">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="49a32-114">Assemblies in .NET</span></span>](index.md)
