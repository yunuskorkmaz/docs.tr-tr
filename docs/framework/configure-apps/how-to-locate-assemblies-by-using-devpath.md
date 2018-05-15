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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 918acf069c63d3aa8187f0f04e1f6c55ec961458
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="df8d0-102">Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="df8d0-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="df8d0-103">Geliştiriciler, oluşturmakta olduğunuz paylaşılan bir derleme birden çok uygulama ile doğru çalıştığından emin olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8d0-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="df8d0-104">Sürekli olarak derlemeyi genel derleme önbelleğinde geliştirme döngüsü sırasında koyma yerine, geliştirici derlemesi için derleme çıktı dizinine işaret eden bir DEVPATH ortam değişkeni oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8d0-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="df8d0-105">Örneğin, MySharedAssembly adlı paylaşılan bir derleme oluşturmakta olduğunuz ve çıktı dizinine C:\MySharedAssembly\Debug olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="df8d0-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="df8d0-106">DEVPATH değişkeninde C:\MySharedAssembly\Debug koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8d0-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="df8d0-107">Ardından belirtmelisiniz [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) makine yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="df8d0-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="df8d0-108">Bu öğe DEVPATH derlemeleri bulmak için kullanılacak ortak dil çalışma zamanı söyler.</span><span class="sxs-lookup"><span data-stu-id="df8d0-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="df8d0-109">Paylaşılan derleme çalışma zamanı tarafından bulunabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="df8d0-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="df8d0-110">Derleme başvuruları kullanım çözmek için özel bir dizin belirtmek için [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) veya [ \<yoklama > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) açıklandığı gibi bir yapılandırma dosyası [Bir derlemenin konumunu belirtme](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="df8d0-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="df8d0-111">Bir uygulama dizini alt dizinde derleme de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8d0-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="df8d0-112">Daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="df8d0-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8d0-113">Yalnızca geliştirme için amaçlanan bir gelişmiş özellik budur.</span><span class="sxs-lookup"><span data-stu-id="df8d0-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="df8d0-114">Aşağıdaki örnek, çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde aramak neden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df8d0-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df8d0-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="df8d0-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="df8d0-116">Bu ayar varsayılan olarak false.</span><span class="sxs-lookup"><span data-stu-id="df8d0-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8d0-117">Bu ayar yalnızca geliştirme sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="df8d0-117">Use this setting only at development time.</span></span> <span data-ttu-id="df8d0-118">Çalışma zamanı tanımlayıcı adlı derlemeler DEVPATH bulunan sürümlerinde denetlemez.</span><span class="sxs-lookup"><span data-stu-id="df8d0-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="df8d0-119">Yalnızca, bulduğu ilk derleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="df8d0-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8d0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df8d0-120">See Also</span></span>  
 [<span data-ttu-id="df8d0-121">.NET Framework uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="df8d0-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
