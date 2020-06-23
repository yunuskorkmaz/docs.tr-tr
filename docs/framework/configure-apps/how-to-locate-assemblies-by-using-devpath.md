---
title: 'Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma'
description: Bir XML bilgisayar yapılandırma dosyası ve DEVPATH ortam değişkeni kullanarak, paylaşılan bir derlemenin .NET 'teki birçok uygulamayla doğru şekilde çalışıp çalışmadığını test edin.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105375"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="aa945-103">Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="aa945-103">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="aa945-104">Geliştiriciler, oluşturmakta oldukları paylaşılan bir derlemenin birden çok uygulamayla doğru şekilde çalıştığından emin olmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="aa945-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="aa945-105">Geliştirici, geliştirme çevrimi sırasında derlemeyi genel bütünleştirilmiş kod önbelleğine sürekli koymak yerine, derleme için derleme çıkış dizinini işaret eden bir DEVPATH ortam değişkeni oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="aa945-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="aa945-106">Örneğin, MySharedAssembly adlı bir paylaşılan derleme oluşturduğunuzu ve çıkış dizininin C:\mysharedassembly\debugolduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="aa945-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="aa945-107">C:\MySharedAssembly\Debug öğesini DEVPATH değişkenine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa945-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="aa945-108">Ardından, [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) öğesini makine yapılandırma dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa945-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="aa945-109">Bu öğe, ortak dil çalışma zamanına derlemeleri bulmak için DEVPATH kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="aa945-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="aa945-110">Paylaşılan derleme çalışma zamanı tarafından bulunabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa945-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="aa945-111">Derleme başvurularını çözümlemek için özel bir dizin belirtmek üzere [derleme konumunu belirtme](specify-assembly-location.md)bölümünde [ \<probing> açıklandığı](./file-schema/runtime/probing-element.md) gibi bir yapılandırma dosyasındaki [ \<codeBase> öğesini](./file-schema/runtime/codebase-element.md) veya öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa945-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="aa945-112">Derlemeyi uygulama dizininin bir alt dizininde de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa945-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="aa945-113">Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="aa945-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa945-114">Bu, yalnızca geliştirme için tasarlanan gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="aa945-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="aa945-115">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa945-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa945-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa945-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="aa945-117">Bu ayar varsayılan olarak false değerini alır.</span><span class="sxs-lookup"><span data-stu-id="aa945-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa945-118">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa945-118">Use this setting only at development time.</span></span> <span data-ttu-id="aa945-119">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="aa945-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="aa945-120">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa945-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa945-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa945-121">See also</span></span>

- [<span data-ttu-id="aa945-122">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa945-122">Configuring Apps by using Configuration Files</span></span>](index.md)
