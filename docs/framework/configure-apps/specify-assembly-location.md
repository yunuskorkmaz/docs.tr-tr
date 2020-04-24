---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646025"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="6acc8-102">Derlemenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="6acc8-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="6acc8-103">Bir derlemenin konumunu belirtmenin iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="6acc8-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="6acc8-104">[ \<CodeBase>](./file-schema/runtime/codebase-element.md) öğesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6acc8-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="6acc8-105">[ \<Sondalama>](./file-schema/runtime/probing-element.md) öğesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6acc8-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="6acc8-106">Montaj konumlarını belirtmek veya derlemeler için sondalamak için ortak dil çalışma zamanı için konumları belirtmek için [.NET Framework Configuration Tool'u (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6acc8-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="6acc8-107">CodeBase \<> Öğesi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="6acc8-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="6acc8-108">\*\* \<CodeBase>\*\* öğesini yalnızca makine yapılandırmasında veya derleme sürümünü yeniden yönlendiren yayımcı ilke dosyalarında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6acc8-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="6acc8-109">Çalışma zamanı hangi derleme sürümünün kullanılacağını belirlediğinde, sürümü belirleyen dosyadan kod temel ayarı uygular.</span><span class="sxs-lookup"><span data-stu-id="6acc8-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="6acc8-110">Kod tabanı belirtilmezse, montaj için çalışma süresi normal şekilde sondalanır.</span><span class="sxs-lookup"><span data-stu-id="6acc8-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="6acc8-111">Ayrıntılar [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'](../deployment/how-the-runtime-locates-assemblies.md)a bakın.</span><span class="sxs-lookup"><span data-stu-id="6acc8-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6acc8-112">Aşağıdaki örnek, bir derlemenin konumunu nasıl belirtini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6acc8-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="6acc8-113">**Sürüm** özniteliği tüm güçlü adlandırılmış derlemeler için gereklidir, ancak güçlü adlandırılmış olmayan derlemeler için atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6acc8-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="6acc8-114">CodeBase>öğesi **href** özniteliğini gerektirir. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="6acc8-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="6acc8-115">\*\* \<CodeBase>\*\* öğesinde sürüm aralıklarını belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6acc8-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6acc8-116">Güçlü adlandırılmış olmayan bir derleme için kod temel ipucu sağlıyorsanız, ipucunun uygulama tabanını veya uygulama temel dizininin bir alt dizinini işaret etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6acc8-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="6acc8-117">Sondalama> Öğesini \<Kullanma</span><span class="sxs-lookup"><span data-stu-id="6acc8-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="6acc8-118">Çalışma zamanı, sondalama yaparak kod tabanı olmayan derlemeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="6acc8-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="6acc8-119">Sondalama hakkında daha fazla bilgi [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../deployment/how-the-runtime-locates-assemblies.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6acc8-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6acc8-120">Sondalama>öğesini, bir derlemeyi konumalırken çalışma zamanının araması gereken alt dizinleri belirtmek için kullanabilirsiniz. [ \<](./file-schema/runtime/probing-element.md)</span><span class="sxs-lookup"><span data-stu-id="6acc8-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="6acc8-121">Aşağıdaki örnek, çalışma zamanının araması gereken dizinlerin nasıl belirtilen şekilde gösteriş yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6acc8-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="6acc8-122">**privatePath** özniteliği, çalışma zamanının derlemeleri araması gereken dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6acc8-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="6acc8-123">Uygulama C:\Program Files\MyApp'ta bulunuyorsa, çalışma zamanı C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin ve C:\Program Files\MyApp\Bin3'te kod tabanı belirtmeyan derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="6acc8-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="6acc8-124">**privatePath'te** belirtilen dizinler, uygulama temel dizininin alt dizinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6acc8-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acc8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6acc8-125">See also</span></span>

- [<span data-ttu-id="6acc8-126">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="6acc8-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="6acc8-127">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="6acc8-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="6acc8-128">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="6acc8-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6acc8-129">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6acc8-129">Configuring Apps by using Configuration Files</span></span>](index.md)
