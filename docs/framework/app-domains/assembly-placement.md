---
title: "Derleme Yerleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c92ff8102cefbe6dcf89cfd8ddc636f0fc638b8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-placement"></a><span data-ttu-id="f3b09-102">Derleme Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="f3b09-102">Assembly Placement</span></span>
<span data-ttu-id="f3b09-103">Çoğu .NET Framework uygulaması için, uygulamayı oluşturan derlemeleri uygulama dizininde, uygulama dizininin bir alt dizininde veya genel derleme önbelleğinde (derleme paylaşılıyorsa) bulursunuz.</span><span class="sxs-lookup"><span data-stu-id="f3b09-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="f3b09-104">Ortak dil çalışma zamanı kullanarak bir derleme için burada görünür kılabilirsiniz [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="f3b09-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="f3b09-105">Derleme kullanarak belirtilen konumda bir güçlü ad yoksa [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) uygulama dizini veya bir alt sınırlı.</span><span class="sxs-lookup"><span data-stu-id="f3b09-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="f3b09-106">Derleme güçlü bir ada sahipse [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) bilgisayarda veya ağ üzerindeki herhangi bir konumu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3b09-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="f3b09-107">Yönetilmeyen kod veya COM ile birlikte çalışma uygulamaları için derleme bulurken de benzer kurallar geçerlidir: Derleme birden çok uygulama tarafından paylaşılacaksa, genel derleme önbelleğine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3b09-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="f3b09-108">Yönetilmeyen kodla kullanılan derlemeler, bir tür kitaplığı olarak dışarı aktarılmalı ve kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3b09-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="f3b09-109">COM ile birlikte çalışma tarafından kullanılan derlemeler kataloğa kaydedilmelidir, ancak bazı durumlarda bu kayıt otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f3b09-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b09-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3b09-110">See Also</span></span>  
 [<span data-ttu-id="f3b09-111">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="f3b09-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="f3b09-112">Uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f3b09-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="f3b09-113">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="f3b09-113">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="f3b09-114">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="f3b09-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
