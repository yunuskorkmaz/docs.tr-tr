---
title: Derlemenin Konumunu Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: b76537a347cdf30c65bfd6e56f274108e796a315
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259000"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="dd2b8-102">Derlemenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="dd2b8-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="dd2b8-103">Derlemenin konumunu belirtmek için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="dd2b8-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="dd2b8-104">Kullanarak [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="dd2b8-105">Kullanarak [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="dd2b8-106">Ayrıca [.NET Framework yapılandırma aracı (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) değerleme konumlarını belirtmeniz veya derlemeler için araştırma ortak dil çalışma zamanı konumlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="dd2b8-107">Kullanarak \<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="dd2b8-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="dd2b8-108">Kullanabileceğiniz  **\<codeBase >** öğesi de derleme sürümünü yeniden yönlendirme yalnızca makine yapılandırması veya yayımcı ilkesi dosyaları.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="dd2b8-109">Çalışma zamanının hangi derleme sürümünün kullanılacağını belirler sürüm belirleyen dosyasından kodu temel ayarı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="dd2b8-110">Hiçbir kod tabanının belirtilirse, çalışma zamanı derlemesi için normal bir şekilde araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="dd2b8-111">Ayrıntılar için bkz [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dd2b8-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="dd2b8-112">Aşağıdaki örnek, bir derlemenin konumunu belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="dd2b8-113">**Sürüm** özniteliği için tüm Tanımlayıcı adlı derlemeler gereklidir ancak olmayan tanımlayıcı adlı derlemeler için atlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="dd2b8-114"> *\*\<CodeBase >** öğesi gerektiriyor *\*href** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="dd2b8-115">Sürüm aralığı belirtemezsiniz  **\<codeBase >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd2b8-116">Tanımlayıcı adlı değil bir derleme için bir kod temel ipucu sağlayarak, ipucu uygulama temel ya da uygulama temel dizininin bir alt işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="dd2b8-117">Kullanarak \<yoklama > öğesi</span><span class="sxs-lookup"><span data-stu-id="dd2b8-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="dd2b8-118">Çalışma zamanı bir kod temeli yoklama işlemi tarafından olmayan derlemeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="dd2b8-119">Algılama hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dd2b8-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="dd2b8-120">Kullanabileceğiniz [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) alt çalışma zamanı derleme bulurken arama belirtmek için uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="dd2b8-121">Aşağıdaki örnek, çalışma zamanı araması gereken dizinleri belirt gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="dd2b8-122">**PrivatePath** özniteliği çalışma zamanı derlemeleri araması gereken dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="dd2b8-123">Uygulama C:\Program Files\MyApp bulunuyorsa, çalışma zamanı bir kod tabanına C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3 belirtmeyin derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="dd2b8-124">İçinde belirtilen dizinler **privatePath** uygulama temel dizininin alt dizinleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2b8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd2b8-125">See also</span></span>
- [<span data-ttu-id="dd2b8-126">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="dd2b8-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="dd2b8-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="dd2b8-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="dd2b8-128">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="dd2b8-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="dd2b8-129">.NET Framework uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd2b8-129">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
