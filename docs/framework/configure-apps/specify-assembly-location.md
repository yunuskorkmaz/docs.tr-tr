---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646025"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="32862-102">Derlemenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="32862-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="32862-103">Bir derlemenin konumunu belirtmek için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="32862-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="32862-104">Öğesini kullanarak [\<codeBase>](./file-schema/runtime/codebase-element.md) .</span><span class="sxs-lookup"><span data-stu-id="32862-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="32862-105">Öğesini kullanarak [\<probing>](./file-schema/runtime/probing-element.md) .</span><span class="sxs-lookup"><span data-stu-id="32862-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="32862-106">Derleme konumlarını belirtmek için [.NET Framework yapılandırma aracını (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) veya derlemeler için ortak dil çalışma zamanı için konum belirlemek üzere de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32862-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="32862-107">Öğesini kullanma \<codeBase></span><span class="sxs-lookup"><span data-stu-id="32862-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="32862-108">**\<codeBase>** Öğesini, derleme sürümünü de yeniden yönlendiren makine yapılandırması veya yayımcı ilkesi dosyaları içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32862-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="32862-109">Çalışma zamanı hangi derleme sürümünün kullanılacağını belirlediğinde, sürümü belirleyen dosyadan kod tabanı ayarını uygular.</span><span class="sxs-lookup"><span data-stu-id="32862-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="32862-110">Hiçbir kod tabanı belirtilmemişse, çalışma zamanı derlemeyi normal şekilde araştırarak.</span><span class="sxs-lookup"><span data-stu-id="32862-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="32862-111">Ayrıntılar için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="32862-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="32862-112">Aşağıdaki örnek, bir derlemenin konumunun nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32862-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="32862-113">**Sürüm** özniteliği, tanımlayıcı adlı tüm derlemeler için gereklidir, ancak tanımlayıcı olarak adlandırılmış olmayan derlemeler için atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32862-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="32862-114">**\<codeBase>** Öğesi **href** özniteliğini gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="32862-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="32862-115">Öğesinde sürüm aralıkları belirtemezsiniz **\<codeBase>** .</span><span class="sxs-lookup"><span data-stu-id="32862-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32862-116">Güçlü adlandırılmış olmayan bir derleme için bir kod temel ipucu belirtirseniz, ipucu uygulama tabanına veya uygulama temel dizininin bir alt dizinine işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="32862-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="32862-117">Öğesini kullanma \<probing></span><span class="sxs-lookup"><span data-stu-id="32862-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="32862-118">Çalışma zamanı, yoklama ile kod tabanı olmayan derlemeler bulur.</span><span class="sxs-lookup"><span data-stu-id="32862-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="32862-119">Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="32862-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="32862-120">[\<probing>](./file-schema/runtime/probing-element.md)Bir derlemeyi bulurken çalışma zamanının aranması gereken alt dizinleri belirtmek için uygulama yapılandırma dosyasındaki öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32862-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="32862-121">Aşağıdaki örnek, çalışma zamanının arama gereken dizinlerin nasıl gösterileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32862-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="32862-122">**PrivatePath** özniteliği, çalışma zamanının derlemeler için arama gereken dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="32862-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="32862-123">Uygulama C:\Program Files\MyApp konumunda bulunuyorsa, çalışma zamanı C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3. ' de bir kod tabanı belirtmeyen derlemeler arayacaktır</span><span class="sxs-lookup"><span data-stu-id="32862-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="32862-124">**PrivatePath** içinde belirtilen dizinler, uygulama temel dizininin alt dizinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32862-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32862-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32862-125">See also</span></span>

- [<span data-ttu-id="32862-126">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="32862-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="32862-127">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="32862-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="32862-128">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="32862-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="32862-129">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32862-129">Configuring Apps by using Configuration Files</span></span>](index.md)
