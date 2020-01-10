---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: c7b9dcb99e08a1ef2844c5811897aa87ff86f866
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716562"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="28c58-102">Derleme Bağlama Yönlendirmesini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28c58-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="28c58-103">Uygulamalar, varsayılan olarak, uygulamayı derlemek için kullanılan çalışma zamanı sürümüyle birlikte gelen .NET Framework derlemeleri kümesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28c58-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="28c58-104">Derleme bağlama başvurularını .NET Framework derlemelerinin belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasında [\<assemblyBinding >](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğesinde **AppliesTo** özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28c58-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="28c58-105">Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="28c58-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="28c58-106">Hiçbir **AppliesTo** özniteliği belirtilmemişse, **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="28c58-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="28c58-107">**AppliesTo** özniteliği .NET Framework sürüm 1,1 ' de tanıtılmıştı; .NET Framework 1,0 sürümü tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="28c58-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="28c58-108">Bu, bir **AppliesTo** özniteliği belirtilmiş olsa bile .NET Framework sürüm 1,0 kullanılırken tüm **\<assemblyBinding >** öğelerinin uygulandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28c58-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28c58-109">Derleme bağlama yeniden yönlendirmesini, çalışma zamanının belirli bir sürümüyle sınırlamak için **AppliesTo** özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="28c58-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="28c58-110">Örneğin, .NET Framework sürüm 1,0 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="28c58-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="28c58-111">**\<AssemblyBinding >** sipariş duyarlı öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="28c58-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="28c58-112">Önce .NET Framework herhangi bir sürüm 1,0 derlemesi için derleme bağlama yeniden yönlendirme bilgilerini, ardından herhangi bir .NET Framework sürümü 1,1 derlemesi için derleme bağlama yeniden yönlendirme bilgilerini girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28c58-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="28c58-113">Son olarak, **AppliesTo** özniteliğini kullanmayan ve bu nedenle .NET Framework tüm sürümleri için geçerli olan tüm .NET Framework bütünleştirilmiş kod yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="28c58-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="28c58-114">Yeniden yönlendirmenin bir çakışma olması durumunda, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme ekstresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28c58-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="28c58-115">Örneğin, bir başvuruyu .NET Framework sürüm 1,0 derlemesine ve .NET Framework sürüm 1,1 derlemesine başka bir başvuruya yeniden yönlendirmek için aşağıdaki sözde kodda gösterilen kalıbı kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="28c58-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="28c58-116">Yapılandırma Dosyası Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="28c58-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="28c58-117">Çalışma zamanı, bir uygulama etki alanı oluşturulduğunda yapılandırma dosyalarını bir kez ayrıştırır ve kodu bu uygulama etki alanına yükler.</span><span class="sxs-lookup"><span data-stu-id="28c58-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="28c58-118">Ortak dil çalışma zamanı, girdiyi yoksayarak bir yapılandırma dosyasındaki hataları işler.</span><span class="sxs-lookup"><span data-stu-id="28c58-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="28c58-119">Çalışma zamanı, hatalı biçimlendirilmiş XML içeriyorsa tüm yapılandırma dosyalarını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="28c58-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="28c58-120">Geçersiz XML için yalnızca geçersiz bölümler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="28c58-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="28c58-121">Derleme bağlama yeniden yönlendirmelerinin oluşup oluşmadığını belirleyerek bir yapılandırma dosyasının kullanılıp kullanılmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28c58-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="28c58-122">Hangi derlemelerin yüklenmekte olduğunu görmek için [derleme bağlama günlüğü görüntüleyicisini (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="28c58-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="28c58-123">Tüm derleme bağlamalarını görmek için kayıt defterinde **ForceLog** için bir girdi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28c58-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c58-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28c58-124">See also</span></span>

- [<span data-ttu-id="28c58-125">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="28c58-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
