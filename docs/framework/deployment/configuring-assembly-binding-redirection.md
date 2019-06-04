---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5df468b87c62f454f6a42fa7a80d92e5ec199fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873736"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="755b7-102">Derleme Bağlama Yönlendirmesini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="755b7-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="755b7-103">Varsayılan olarak, uygulamalar, uygulama derlemek için kullanılan çalışma zamanı sürümü ile birlikte .NET Framework derlemeleri kümesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="755b7-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="755b7-104">Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvurularının nasıl belirli bir .NET sürümünü yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Framework derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="755b7-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="755b7-105">İsteğe bağlı bu öznitelik, bir .NET Framework sürüm numarası geçerli hangi sürüm olduğunu belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="755b7-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="755b7-106">Hayır ise **appliesTo** özniteliği belirtilirse,  **\<assemblyBinding >** öğe tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="755b7-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="755b7-107">**AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 tarafından göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="755b7-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="755b7-108">Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="755b7-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="755b7-109">Kullanım **appliesTo** belirli bir çalışma zamanı sürümünü derleme bağlama yeniden yönlendirme sınırlamak için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="755b7-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="755b7-110">Örneğin, derleme için bir .NET Framework sürüm 1.0 derleme bağlamasına yönlendirmek için aşağıdaki XML kodunu uygulama yapılandırma dosyanızda verilebilir.</span><span class="sxs-lookup"><span data-stu-id="755b7-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="755b7-111">**\<AssemblyBinding >** sipariş duyarlı öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="755b7-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="755b7-112">Herhangi bir .NET Framework sürüm 1.1 derlemeler için derleme bağlama yönlendirme bilgisini ardından herhangi bir .NET Framework sürüm 1.0 derlemeler için derleme bağlama yönlendirme bilgisini ilk olarak girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="755b7-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="755b7-113">Son olarak, kullanılmayan tüm .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yönlendirme bilgisini girin **appliesTo** özniteliği ve bu nedenle tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="755b7-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="755b7-114">Yeniden yönlendirme bir çakışma olması durumunda, yapılandırma dosyasındaki eşleşen ilk yönlendirme cümlesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="755b7-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="755b7-115">Örneğin, .NET Framework sürüm 1.0 derlemesine bir başvuru ve başka bir başvuru bir .NET Framework sürüm 1.1 derlemesine yönlendirmek için aşağıdaki sözde kod gösterilen yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="755b7-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="755b7-116">Yapılandırma Dosyası Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="755b7-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="755b7-117">Uygulama etki alanı oluşturulduğunda ve kodu, uygulama etki alanına yükler, çalışma zamanı yapılandırma dosyalarını bir kez ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="755b7-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="755b7-118">Ortak dil çalışma zamanı, giriş yoksayarak bir yapılandırma dosyası hatalarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="755b7-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="755b7-119">Hatalı biçimlendirilmiş XML içeriyorsa, çalışma zamanı, tüm yapılandırma dosyası yok sayar.</span><span class="sxs-lookup"><span data-stu-id="755b7-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="755b7-120">Geçersiz XML için yalnızca geçersiz bölümlere göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="755b7-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="755b7-121">Derleme bağlama yeniden yönlendirmeleri gerçekleşen olup olmadığını bir yapılandırma dosyası belirleyerek kullanılıp kullanılmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755b7-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="755b7-122">Kullanım [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) hangi derlemelerin yüklenen görmek için.</span><span class="sxs-lookup"><span data-stu-id="755b7-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="755b7-123">Tüm derleme bağlamalarını öğrenmek için bir giriş ayarlamak **ForceLog** kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="755b7-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755b7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="755b7-124">See also</span></span>

- [<span data-ttu-id="755b7-125">Nasıl yapılır: Otomatik bağlama yeniden yönlendirmesini devre dışı bırakma ve etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="755b7-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
