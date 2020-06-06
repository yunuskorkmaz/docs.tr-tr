---
title: 'Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912994"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="e86c3-102">Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="e86c3-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="e86c3-103">Geliştiriciler, oluşturmakta oldukları paylaşılan bir derlemenin birden çok uygulamayla doğru şekilde çalıştığından emin olmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="e86c3-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="e86c3-104">Geliştirici, geliştirme çevrimi sırasında derlemeyi genel bütünleştirilmiş kod önbelleğine sürekli koymak yerine, derleme için derleme çıkış dizinini işaret eden bir DEVPATH ortam değişkeni oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e86c3-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="e86c3-105">Örneğin, MySharedAssembly adlı bir paylaşılan derleme oluşturduğunuzu ve çıkış dizininin C:\mysharedassembly\debugolduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e86c3-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="e86c3-106">C:\MySharedAssembly\Debug öğesini DEVPATH değişkenine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e86c3-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="e86c3-107">Ardından, [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) öğesini makine yapılandırma dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e86c3-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="e86c3-108">Bu öğe, ortak dil çalışma zamanına derlemeleri bulmak için DEVPATH kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="e86c3-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="e86c3-109">Paylaşılan derleme çalışma zamanı tarafından bulunabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e86c3-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="e86c3-110">Derleme başvurularını çözümlemek için özel bir dizin belirtmek üzere [derleme konumunu belirtme](specify-assembly-location.md)bölümünde [ \<probing> açıklandığı](./file-schema/runtime/probing-element.md) gibi bir yapılandırma dosyasındaki [ \<codeBase> öğesini](./file-schema/runtime/codebase-element.md) veya öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e86c3-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="e86c3-111">Derlemeyi uygulama dizininin bir alt dizininde de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e86c3-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="e86c3-112">Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e86c3-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e86c3-113">Bu, yalnızca geliştirme için tasarlanan gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e86c3-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="e86c3-114">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e86c3-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e86c3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e86c3-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e86c3-116">Bu ayar varsayılan olarak false değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e86c3-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e86c3-117">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="e86c3-117">Use this setting only at development time.</span></span> <span data-ttu-id="e86c3-118">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="e86c3-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="e86c3-119">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e86c3-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e86c3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e86c3-120">See also</span></span>

- [<span data-ttu-id="e86c3-121">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e86c3-121">Configuring Apps by using Configuration Files</span></span>](index.md)
