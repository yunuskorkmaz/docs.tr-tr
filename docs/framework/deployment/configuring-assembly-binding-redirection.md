---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181692"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="d8b3a-102">Derleme Bağlama Yönlendirmesini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d8b3a-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="d8b3a-103">Varsayılan olarak, uygulamalar, uygulamayı derlemek için kullanılan çalışma zamanı sürümüyle birlikte gönderilen .NET Framework derlemeleri kümesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="d8b3a-104">Derleme bağlama başvurularını .NET Framework derlemelerinin belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasındaki [ \<>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğesini bağlama **özniteliğini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="d8b3a-105">Bu isteğe bağlı öznitelik, hangi sürüme uygulandığını belirtmek için bir .NET Framework sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="d8b3a-106">Hiçbir **öznitelik** belirtilmemişse, \*\* \<derlemeBağlama>\*\* öğesi .NET Framework'ün tüm sürümlerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d8b3a-107">**AapplyTo** özniteliği .NET Framework sürüm 1.1'de tanıtıldı; .NET Framework sürüm 1.0 tarafından yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="d8b3a-108">Bu, .NET Framework sürüm 1.0 kullanılırken tüm \*\* \<derlemebağlayıcı>\*\* öğelerinin **uygulandığı** anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8b3a-109">Derleme bağlama yeniden yönlendirmesini çalışma zamanının belirli bir sürümüyle sınırlamak için **applyTo** özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="d8b3a-110">Örneğin, bir .NET Framework sürüm 1.0 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="d8b3a-111">\*\* \<DerlemeBağlama>\*\* elemanları siparişe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="d8b3a-112">Önce .NET Framework sürüm 1.0 derlemeleri için derleme bağlama yeniden yönlendirme bilgilerini girmeniz, ardından da herhangi bir .NET Framework sürüm 1.1 derlemeleri için derleme bağlama yeniden yönlendirme bilgileri girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="d8b3a-113">Son olarak, **geçerliliği** kullanmayan ve bu nedenle .NET Framework'ün tüm sürümleriiçin geçerli olan herhangi bir .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="d8b3a-114">Yeniden yönlendirmede bir çakışma olması durumunda, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="d8b3a-115">Örneğin, bir başvuruyu .NET Framework sürüm 1.0 derlemesine ve başka bir başvuruyu bir .NET Framework sürüm 1.1 derlemesine yönlendirmek için aşağıdaki pseudocode'da gösterilen deseni kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="d8b3a-116">Yapılandırma Dosyası Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d8b3a-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="d8b3a-117">Çalışma zamanı, bir uygulama etki alanı oluşturulduğunda yapılandırma dosyalarını bir kez ayrıştırır ve kodu bu uygulama etki alanına yükler.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="d8b3a-118">Ortak dil çalışma süresi, girişi yoksayarak yapılandırma dosyasındaki hataları işler.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="d8b3a-119">Çalışma süresi, hatalı biçimlendirilmiş XML içeriyorsa tüm yapılandırma dosyasını yoksa.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="d8b3a-120">Geçersiz XML için yalnızca geçersiz bölümler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="d8b3a-121">Derleme bağlama yönlendirmelerinin oluşup oluşmadığını belirleyerek yapılandırma dosyasının kullanılıp kullanılmayacağını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="d8b3a-122">Hangi derlemelerin yüklendiğini görmek için [Derleme Bağlama Günlük Görüntüleyici'ni (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="d8b3a-123">Tüm montaj bağlarını görmek için, kayıt defterine **ForceLog** için bir giriş ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b3a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8b3a-124">See also</span></span>

- [<span data-ttu-id="d8b3a-125">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="d8b3a-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
