---
title: Bir derlemeyi &#39; belirtme s konumu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5f79ed7af91f2e54edbc2174da2afa1b3cb56557
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="6ffb7-102">Bir derlemeyi &#39; belirtme s konumu</span><span class="sxs-lookup"><span data-stu-id="6ffb7-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="6ffb7-103">Derlemenin konumunu belirtmek için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="6ffb7-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="6ffb7-104">Kullanarak [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="6ffb7-105">Kullanarak [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="6ffb7-106">Aynı zamanda [.NET Framework yapılandırma aracını (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) derleme konumları belirtin veya derlemeler için araştırma ortak dil çalışma zamanı için konumlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="6ffb7-107">Kullanarak \<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="6ffb7-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="6ffb7-108">Kullanabileceğiniz  **\<codeBase >** derleme sürümünü de yönlendiren yalnızca makine yapılandırma veya yayımcı ilke dosyaları öğesinde.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="6ffb7-109">Çalışma zamanı kullanmak için hangi derleme sürümü belirlediğinde, sürüm belirleyen dosyasından kod temel ayar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="6ffb7-110">Hiçbir kod temeli belirtilirse, çalışma zamanı derlemesi için normal bir şekilde araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="6ffb7-111">Ayrıntılar için bkz [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6ffb7-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6ffb7-112">Aşağıdaki örnek derlemenin konumunu belirtme gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="6ffb7-113">**Sürüm** özniteliği tüm Tanımlayıcı adlı derlemeler için gerekli değildir ancak güçlü-adlandırılmamış derlemelerde alınmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="6ffb7-114"> **\<CodeBase >** öğesi gerektiriyor **href** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="6ffb7-115">Sürüm aralıklardaki belirtemezsiniz  **\<codeBase >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ffb7-116">Tanımlayıcı adlı olmayan bir derleme için bir kod temel ipucu sağlayarak, ipucu uygulama temel veya uygulamanın ana dizin alt işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="6ffb7-117">Kullanarak \<yoklama > öğesi</span><span class="sxs-lookup"><span data-stu-id="6ffb7-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="6ffb7-118">Çalışma zamanı temel bir kod yoklama tarafından yok derlemeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="6ffb7-119">Yoklama hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6ffb7-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6ffb7-120">Kullanabileceğiniz [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) alt dizinleri çalışma zamanı bütünleştirilmiş belirlerken arama belirtmek için uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="6ffb7-121">Aşağıdaki örnek, çalışma zamanı arayacağı dizinlerini belirt gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="6ffb7-122">**PrivatePath** özniteliği çalışma zamanı derlemeleri için arayacağı dizinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="6ffb7-123">Uygulama C:\Program Files\MyApp bulunuyorsa, çalışma zamanı kod temeli C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin ve C:\Program Files\MyApp\Bin3 belirtmeyin derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="6ffb7-124">Belirtilen dizin **privatePath** uygulamanın ana dizin alt dizinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffb7-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ffb7-125">See Also</span></span>  
 [<span data-ttu-id="6ffb7-126">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="6ffb7-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="6ffb7-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="6ffb7-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="6ffb7-128">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="6ffb7-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="6ffb7-129">.NET Framework uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ffb7-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
