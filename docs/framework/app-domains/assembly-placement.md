---
title: Derleme Yerleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971633"
---
# <a name="assembly-placement"></a><span data-ttu-id="47799-102">Derleme Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="47799-102">Assembly Placement</span></span>
<span data-ttu-id="47799-103">Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz.</span><span class="sxs-lookup"><span data-stu-id="47799-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="47799-104">Bir yapılandırma dosyasındaki [ \<codebase > öğesini](../../framework/configure-apps/file-schema/runtime/codebase-element.md) kullanarak ortak dil çalışma zamanının bir derlemeyi aradığı yeri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47799-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="47799-105">Derleme tanımlayıcı bir ada sahip değilse, [ \<codebase > öğesi](../../framework/configure-apps/file-schema/runtime/codebase-element.md) kullanılarak belirtilen konum, uygulama dizini veya bir alt dizin ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="47799-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="47799-106">Derlemenin tanımlayıcı bir adı varsa, [ \<codebase > öğesi](../../framework/configure-apps/file-schema/runtime/codebase-element.md) bilgisayar üzerinde veya bir ağ üzerinde herhangi bir konumu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="47799-106">If the assembly has a strong name, the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="47799-107">Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="47799-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="47799-108">Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="47799-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="47799-109">COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="47799-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47799-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47799-110">See also</span></span>

- [<span data-ttu-id="47799-111">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="47799-111">How the Runtime Locates Assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="47799-112">Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47799-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="47799-113">Yönetilmeyen kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="47799-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="47799-114">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="47799-114">Assemblies in .NET</span></span>](index.md)
