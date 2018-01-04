---
title: "Derleme Bağlama Yönlendirmesini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b53673d1ddb1de7fed087b4c5cb125e50f11b918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="c9c97-102">Derleme Bağlama Yönlendirmesini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9c97-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="c9c97-103">Varsayılan olarak, uygulamaların uygulama derlemek için kullanılan çalışma zamanı sürümü ile birlikte gelen .NET Framework derlemeler kümesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9c97-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="c9c97-104">Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvuruları .NET belirli bir sürümüne yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Framework'te derleme.</span><span class="sxs-lookup"><span data-stu-id="c9c97-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="c9c97-105">Bu isteğe bağlı öznitelik uygulandığı hangi sürüm belirtmek için bir .NET Framework sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9c97-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="c9c97-106">Öyle değilse **appliesTo** özniteliği belirtilirse  **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c9c97-107">**AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="c9c97-108">Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c9c97-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9c97-109">Kullanım **appliesTo** Derleme bağlaması yeniden yönlendirme çalışma zamanının belirli bir sürüme sınırlamak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c9c97-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="c9c97-110">Örneğin, derleme için bir .NET Framework sürüm 1.0 Derleme bağlaması yeniden yönlendirme için uygulama yapılandırma dosyasında aşağıdaki XML kodunu içermesi.</span><span class="sxs-lookup"><span data-stu-id="c9c97-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="c9c97-111"> **\<AssemblyBinding >** sipariş duyarlı öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="c9c97-112">Derleme bağlaması yeniden yönlendirme bilgilerini tüm .NET Framework sürüm 1.1 derlemeler için arkasından Derleme bağlaması yeniden yönlendirme bilgilerini tüm .NET Framework sürüm 1.0 derlemeler için ilk olarak, girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="c9c97-113">Son olarak, Derleme bağlaması yeniden yönlendirme bilgilerini kullanmayan tüm .NET Framework derleme yeniden yönlendirme için girin **appliesTo** özniteliği ve bu nedenle, .NET Framework'ün tüm sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="c9c97-114">Yeniden yönlendirme bir çakışma durumunda ilk eşleşen yeniden yönlendirme deyiminde yapılandırma dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9c97-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="c9c97-115">Örneğin, bir .NET Framework sürüm 1.0 derleme bir başvuru ve bir .NET Framework sürüm 1.1 derleme başka bir başvuru yeniden yönlendirmek için aşağıdaki yarı kodu içinde gösterilen düzeni kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c9c97-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="c9c97-116">Yapılandırma Dosyası Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c9c97-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="c9c97-117">Uygulama etki alanı oluşturulduğunda ve o uygulama etki alanına kod yükler çalışma zamanı yapılandırma dosyalarını bir kez ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="c9c97-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="c9c97-118">Ortak dil çalışma zamanı, giriş yoksayılıyor tarafından bir yapılandırma dosyasına hatalarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="c9c97-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="c9c97-119">Hatalı biçimlendirilmiş XML içeriyorsa, çalışma zamanı tüm yapılandırma dosyası yok sayar.</span><span class="sxs-lookup"><span data-stu-id="c9c97-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="c9c97-120">Geçersiz XML için yalnızca geçersiz bölüm göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c9c97-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="c9c97-121">Derleme bağlama yeniden yönlendirmeleri yaşanan olup olmadığını bir yapılandırma dosyası belirleyerek kullanılmakta olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c97-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="c9c97-122">Kullanım [Derleme bağlaması Günlük Görüntüleyici (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) hangi derlemelerin yüklü görmek için.</span><span class="sxs-lookup"><span data-stu-id="c9c97-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="c9c97-123">Tüm derleme bağlamalar görmek için bir girişi ayarlayın **ForceLog** kayıt defterinde.</span><span class="sxs-lookup"><span data-stu-id="c9c97-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c97-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c97-124">See Also</span></span>  
 [<span data-ttu-id="c9c97-125">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="c9c97-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
