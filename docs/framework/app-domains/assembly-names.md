---
title: "Derleme Adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 624cc6ad264f32b9a43917d9bae751f57b4421a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-names"></a><span data-ttu-id="b8818-102">Derleme Adları</span><span class="sxs-lookup"><span data-stu-id="b8818-102">Assembly Names</span></span>
<span data-ttu-id="b8818-103">Bir derlemenin adı meta verilerinde depolanır ve önemli bir derlemenin kapsamına etkileyebilir ve bir uygulama tarafından kullanılıyor sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b8818-103">An assembly's name is stored in metadata and has a significant impact on the assembly's scope and use by an application.</span></span> <span data-ttu-id="b8818-104">Tanımlayıcı adlı bir derleme derlemenin adı, kültür, ortak anahtar ve sürüm numarasını içeren tam bir adı vardır.</span><span class="sxs-lookup"><span data-stu-id="b8818-104">A strong-named assembly has a fully qualified name that includes the assembly's name, culture, public key, and version number.</span></span> <span data-ttu-id="b8818-105">Görünen adını ve yüklenen derlemeler için kullanarak elde edilebilir bu sık verilir <xref:System.Reflection.Assembly.FullName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8818-105">This is frequently referred to as the display name, and for loaded assemblies can be obtained by using the <xref:System.Reflection.Assembly.FullName%2A> property.</span></span>  
  
 <span data-ttu-id="b8818-106">Çalışma zamanı derlemesi bulun ve aynı ada sahip diğer derlemelerden ayırt etmek için bu bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8818-106">The runtime uses this information to locate the assembly and differentiate it from other assemblies with the same name.</span></span> <span data-ttu-id="b8818-107">Örneğin, kesin adlandırılmış bir derleme adlı `myTypes` aşağıdaki tam ada sahip:</span><span class="sxs-lookup"><span data-stu-id="b8818-107">For example, a strong-named assembly called `myTypes` could have the following fully qualified name:</span></span>  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  <span data-ttu-id="b8818-108">İşlemci mimarisi, .NET Framework sürüm 2.0 derlemeleri işlemci özgü sürümleri izin vermek için derleme kimlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="b8818-108">Processor architecture is added to the assembly identity in the .NET Framework version 2.0, to allow processor-specific versions of assemblies.</span></span> <span data-ttu-id="b8818-109">Yalnızca İşlemci mimarisi tarafından örneğin 32-bit ve 64-bit işlemci özgü sürümleri kimliği farklı bir derleme sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8818-109">You can create versions of an assembly whose identity differs only by processor architecture, for example 32-bit and 64-bit processor-specific versions.</span></span> <span data-ttu-id="b8818-110">İşlemci mimarisi için güçlü adları gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b8818-110">Processor architecture is not required for strong names.</span></span> <span data-ttu-id="b8818-111">Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8818-111">For more information, see <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b8818-112">Bu örnekte, tam adı bildiren `myTypes` derleme bir ortak anahtar belirteci ile güçlü bir ada sahip, kültür değeri ABD İngilizcesi için sahip ve 1.0.1234.0 sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="b8818-112">In this example, the fully qualified name indicates that the `myTypes` assembly has a strong name with a public key token, has the culture value for US English, and has a version number of 1.0.1234.0.</span></span> <span data-ttu-id="b8818-113">Tam zamanında (JIT) anlamına gelir "MSIL" işlemci mimarisini olduğu-32 bit kod veya 64-bit işlemci ve işletim sistemine bağlı olarak kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="b8818-113">Its processor architecture is "msil", which means that it will be just-in-time (JIT)-compiled to 32-bit code or 64-bit code depending on the operating system and processor.</span></span>  
  
 <span data-ttu-id="b8818-114">Derlemedeki türleri istekleri kodu tam nitelikli derleme adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8818-114">Code that requests types in an assembly must use a fully qualified assembly name.</span></span> <span data-ttu-id="b8818-115">Bu tam bağlama çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b8818-115">This is called fully qualified binding.</span></span> <span data-ttu-id="b8818-116">Yalnızca derleme adını belirtir, kısmi bağlama .NET Framework derlemelerde başvururken izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="b8818-116">Partial binding, which specifies only an assembly name, is not permitted when referencing assemblies in the .NET Framework.</span></span>  
  
 <span data-ttu-id="b8818-117">.NET Framework olun derlemeleri tüm derleme başvurularını da derlemenin tam adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b8818-117">All assembly references to assemblies that make up the .NET Framework also must contain a fully qualified name of the assembly.</span></span> <span data-ttu-id="b8818-118">Örneğin, sürüm 1.0 için System.Data .NET Framework derleme başvurusu için aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b8818-118">For example, to reference the System.Data .NET Framework assembly for version 1.0 would include:</span></span>  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 <span data-ttu-id="b8818-119">Sürüm .NET Framework sürüm 1.0 ile birlikte gelen tüm .NET Framework derleme sürüm numarası karşılık geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b8818-119">Note that the version corresponds to the version number of all .NET Framework assemblies that shipped with .NET Framework version 1.0.</span></span> <span data-ttu-id="b8818-120">.NET Framework derlemeler için kültür değer her zaman dilden bağımsız olur ve ortak anahtar yukarıdaki örnekte gösterildiği gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b8818-120">For .NET Framework assemblies, the culture value is always neutral, and the public key is the same as shown in the above example.</span></span>  
  
 <span data-ttu-id="b8818-121">Örneğin, bir derleme başvurusu İzleme dinleyicisi Kur için bir yapılandırma dosyası eklemek için .NET Framework derleme sistem tam adını şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b8818-121">For example, to add an assembly reference in a configuration file to set up a trace listener, you would include the fully qualified name of the system .NET Framework assembly:</span></span>  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  <span data-ttu-id="b8818-122">Çalışma zamanı, bir derlemeye bağlanırken derleme adları büyük küçük harf duyarsız davranır ancak her durumda bir derleme adı kullanılır korur.</span><span class="sxs-lookup"><span data-stu-id="b8818-122">The runtime treats assembly names as case-insensitive when binding to an assembly, but preserves whatever case is used in an assembly name.</span></span> <span data-ttu-id="b8818-123">Birkaç araçlarında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] derleme adları büyük küçük harfe duyarlı olarak işler.</span><span class="sxs-lookup"><span data-stu-id="b8818-123">Several tools in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] handle assembly names as case-sensitive.</span></span> <span data-ttu-id="b8818-124">Büyük küçük harfe duyarlı gibi en iyi sonuçlar için derleme adları yönetin.</span><span class="sxs-lookup"><span data-stu-id="b8818-124">For best results, manage assembly names as though they were case-sensitive.</span></span>  
  
## <a name="naming-application-components"></a><span data-ttu-id="b8818-125">Uygulama bileşenleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="b8818-125">Naming Application Components</span></span>  
 <span data-ttu-id="b8818-126">Çalışma zamanı dosya adı bir derlemenin kimlik belirlerken dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="b8818-126">The runtime does not consider the file name when determining an assembly's identity.</span></span> <span data-ttu-id="b8818-127">Derleme adı, sürüm, kültür ve güçlü ad oluşur, derleme kimliğini çalışma zamanı açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8818-127">The assembly identity, which consists of the assembly name, version, culture, and strong name, must be clear to the runtime.</span></span>  
  
 <span data-ttu-id="b8818-128">Örneğin, myAssembly.dll adlı bir derlemeye başvurur myAssembly.exe adlı bir derleme varsa, myAssembly.exe yürütüyorsa bağlama doğru oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8818-128">For example, if you have an assembly called myAssembly.exe that references an assembly called myAssembly.dll, binding occurs correctly if you execute myAssembly.exe.</span></span> <span data-ttu-id="b8818-129">Ancak, başka bir uygulama yöntemini kullanarak myAssembly.exe yürütülürse <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, myAssembly.exe "myAssembly" bağlama istediğinde "myAssembly" zaten yüklenmiş çalışma zamanı belirler</span><span class="sxs-lookup"><span data-stu-id="b8818-129">However, if another application executes myAssembly.exe using the method <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, the runtime determines that "myAssembly" is already loaded when myAssembly.exe requests binding to "myAssembly."</span></span> <span data-ttu-id="b8818-130">Bu durumda, myAssembly.dll hiçbir zaman yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b8818-130">In this case, myAssembly.dll is never loaded.</span></span> <span data-ttu-id="b8818-131">MyAssembly.exe istenen tür içermediğinden bir <xref:System.TypeLoadException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8818-131">Because myAssembly.exe does not contain the requested type , a <xref:System.TypeLoadException> occurs.</span></span>  
  
 <span data-ttu-id="b8818-132">Bu sorunu önlemek için uygulamayı oluşturan derlemeler değil aynı derleme adı veya farklı dizinlerde aynı ada sahip derlemeler yerleştirin emin olun.</span><span class="sxs-lookup"><span data-stu-id="b8818-132">To avoid this problem, make sure the assemblies that make up your application do not have the same assembly name or place assemblies with the same name in different directories.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8818-133">Tanımlayıcı adlı bir derleme genel derleme önbelleğinde yerleştirirseniz derlemenin dosya adı (örneğin .exe veya .dll dosya adı uzantısı hariç) derleme adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b8818-133">If you put a strong-named assembly in the global assembly cache, the assembly's file name must match the assembly name (not including the file name extension, such as .exe or .dll).</span></span> <span data-ttu-id="b8818-134">Örneğin, bir derleme dosya adı myAssembly.dll ise, derleme adı myAssembly olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8818-134">For example, if the file name of an assembly is myAssembly.dll, the assembly name must be myAssembly.</span></span> <span data-ttu-id="b8818-135">Yalnızca kök uygulama dizininde dağıtılan özel derlemeler dosya adından farklı bir derleme adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8818-135">Private assemblies deployed only in the root application directory can have an assembly name that is different from the file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8818-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8818-136">See Also</span></span>  
 [<span data-ttu-id="b8818-137">Nasıl yapılır: bir derlemenin tam olarak nitelenmiş adını belirleme</span><span class="sxs-lookup"><span data-stu-id="b8818-137">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 [<span data-ttu-id="b8818-138">Derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8818-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="b8818-139">Tanımlayıcı adlı derlemeler</span><span class="sxs-lookup"><span data-stu-id="b8818-139">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [<span data-ttu-id="b8818-140">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="b8818-140">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="b8818-141">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="b8818-141">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="b8818-142">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="b8818-142">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
