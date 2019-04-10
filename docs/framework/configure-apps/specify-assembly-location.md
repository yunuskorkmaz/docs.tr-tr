---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f7d09e315f2ccc7ecdcf22719ca6dce1ee1411b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186296"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="9c984-102">Derlemenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="9c984-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="9c984-103">Derlemenin konumunu belirtmek için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9c984-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="9c984-104">Kullanarak [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9c984-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="9c984-105">Kullanarak [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9c984-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="9c984-106">Ayrıca [.NET Framework yapılandırma aracı (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) değerleme konumlarını belirtmeniz veya derlemeler için araştırma ortak dil çalışma zamanı konumlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="9c984-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="9c984-107">Kullanarak \<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="9c984-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="9c984-108">Kullanabileceğiniz  **\<codeBase >** öğesi de derleme sürümünü yeniden yönlendirme yalnızca makine yapılandırması veya yayımcı ilkesi dosyaları.</span><span class="sxs-lookup"><span data-stu-id="9c984-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="9c984-109">Çalışma zamanının hangi derleme sürümünün kullanılacağını belirler sürüm belirleyen dosyasından kodu temel ayarı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9c984-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="9c984-110">Hiçbir kod tabanının belirtilirse, çalışma zamanı derlemesi için normal bir şekilde araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="9c984-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="9c984-111">Ayrıntılar için bkz [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9c984-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="9c984-112">Aşağıdaki örnek, bir derlemenin konumunu belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c984-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9c984-113">**Sürüm** özniteliği için tüm Tanımlayıcı adlı derlemeler gereklidir ancak olmayan tanımlayıcı adlı derlemeler için atlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c984-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="9c984-114"> *\*\<CodeBase >** öğesi gerektiriyor *\*href** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9c984-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="9c984-115">Sürüm aralığı belirtemezsiniz  **\<codeBase >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="9c984-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c984-116">Tanımlayıcı adlı değil bir derleme için bir kod temel ipucu sağlayarak, ipucu uygulama temel ya da uygulama temel dizininin bir alt işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c984-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="9c984-117">Kullanarak \<yoklama > öğesi</span><span class="sxs-lookup"><span data-stu-id="9c984-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="9c984-118">Çalışma zamanı bir kod temeli yoklama işlemi tarafından olmayan derlemeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="9c984-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="9c984-119">Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9c984-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="9c984-120">Kullanabileceğiniz [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) alt çalışma zamanı derleme bulurken arama belirtmek için uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="9c984-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="9c984-121">Aşağıdaki örnek, çalışma zamanı araması gereken dizinleri belirt gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c984-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9c984-122">**PrivatePath** özniteliği çalışma zamanı derlemeleri araması gereken dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9c984-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="9c984-123">Uygulama C:\Program Files\MyApp bulunuyorsa, çalışma zamanı bir kod tabanına C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3 belirtmeyin derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="9c984-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="9c984-124">İçinde belirtilen dizinler **privatePath** uygulama temel dizininin alt dizinleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c984-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c984-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c984-125">See also</span></span>

- [<span data-ttu-id="9c984-126">Ortak Dil Çalışma Zamanındaki Derlemeler</span><span class="sxs-lookup"><span data-stu-id="9c984-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="9c984-127">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="9c984-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="9c984-128">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="9c984-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9c984-129">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9c984-129">Configuring Apps by using Configuration Files</span></span>](index.md)
