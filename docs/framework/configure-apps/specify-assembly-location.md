---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f13b19dcd0aceac969d9639e6230ad33c6cd8d84
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971544"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="c725c-102">Derlemenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="c725c-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="c725c-103">Bir derlemenin konumunu belirtmek için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="c725c-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="c725c-104">CodeBase > öğesini kullanma. [ \<](./file-schema/runtime/codebase-element.md)</span><span class="sxs-lookup"><span data-stu-id="c725c-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="c725c-105">Yoklama > öğesi kullanılıyor. [ \<](./file-schema/runtime/probing-element.md)</span><span class="sxs-lookup"><span data-stu-id="c725c-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="c725c-106">Derleme konumlarını belirtmek için [.NET Framework yapılandırma aracını (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) veya derlemeler için ortak dil çalışma zamanı için konum belirlemek üzere de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c725c-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="c725c-107">\<Codebase > öğesini kullanma</span><span class="sxs-lookup"><span data-stu-id="c725c-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="c725c-108">CodeBase > öğesini yalnızca derleme sürümünü yeniden yönlendiren makine yapılandırması veya yayımcı ilkesi dosyaları içinde kullanabilirsiniz.  **\<**</span><span class="sxs-lookup"><span data-stu-id="c725c-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="c725c-109">Çalışma zamanı hangi derleme sürümünün kullanılacağını belirlediğinde, sürümü belirleyen dosyadan kod tabanı ayarını uygular.</span><span class="sxs-lookup"><span data-stu-id="c725c-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="c725c-110">Hiçbir kod tabanı belirtilmemişse, çalışma zamanı derlemeyi normal şekilde araştırarak.</span><span class="sxs-lookup"><span data-stu-id="c725c-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="c725c-111">Ayrıntılar için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c725c-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="c725c-112">Aşağıdaki örnek, bir derlemenin konumunun nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c725c-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="c725c-113">**Sürüm** özniteliği, tanımlayıcı adlı tüm derlemeler için gereklidir, ancak tanımlayıcı olarak adlandırılmış olmayan derlemeler için atlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c725c-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="c725c-114">**\<CodeBase>** öğesi gerektiriyor **href** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c725c-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="c725c-115">Kod temeli > öğesinde sürüm aralıkları  **\<** belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c725c-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c725c-116">Güçlü adlandırılmış olmayan bir derleme için bir kod temel ipucu belirtirseniz, ipucu uygulama tabanına veya uygulama temel dizininin bir alt dizinine işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="c725c-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="c725c-117">\<Yoklama > öğesini kullanma</span><span class="sxs-lookup"><span data-stu-id="c725c-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="c725c-118">Çalışma zamanı, yoklama ile kod tabanı olmayan derlemeler bulur.</span><span class="sxs-lookup"><span data-stu-id="c725c-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="c725c-119">Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c725c-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="c725c-120">Bir derlemeyi bulurken çalışma zamanının aranması gereken alt dizinleri belirtmek için uygulama yapılandırma dosyasındaki [ \<yoklama >](./file-schema/runtime/probing-element.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c725c-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="c725c-121">Aşağıdaki örnek, çalışma zamanının arama gereken dizinlerin nasıl gösterileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c725c-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="c725c-122">**PrivatePath** özniteliği, çalışma zamanının derlemeler için arama gereken dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c725c-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="c725c-123">Uygulama C:\Program Files\MyApp konumunda bulunuyorsa, çalışma zamanı C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3. ' de bir kod tabanı belirtmeyen derlemeler arayacaktır</span><span class="sxs-lookup"><span data-stu-id="c725c-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="c725c-124">**PrivatePath** içinde belirtilen dizinler, uygulama temel dizininin alt dizinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c725c-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c725c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c725c-125">See also</span></span>

- [<span data-ttu-id="c725c-126">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="c725c-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="c725c-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="c725c-127">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="c725c-128">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c725c-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c725c-129">Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c725c-129">Configuring Apps by using Configuration Files</span></span>](index.md)
