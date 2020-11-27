---
title: 'Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 21cd0c13cea764efb60b7b94b699e9a483269da8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280669"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="4301d-102">Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="4301d-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>

<span data-ttu-id="4301d-103">Hizmeti barındırmadan hizmet uygulamalarında ve yapılandırmalarda hataları algılamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4301d-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="4301d-104">Bir hizmeti doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="4301d-104">To validate a service</span></span>  
  
1. <span data-ttu-id="4301d-105">Hizmetinizi bir yürütülebilir dosya ve bir veya daha fazla bağımlı derlemeye derleyin.</span><span class="sxs-lookup"><span data-stu-id="4301d-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="4301d-106">SDK komut istemi açın</span><span class="sxs-lookup"><span data-stu-id="4301d-106">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="4301d-107">Komut isteminde aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="4301d-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="4301d-108">Çeşitli parametreler hakkında daha fazla bilgi için, [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) konusunun Service validationsection bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4301d-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="4301d-109">`/serviceName`Doğrulamak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4301d-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="4301d-110">`assemblyPath`Bağımsız değişkeni, hizmet için yürütülebilir dosyanın yolunu ve doğrulanacak hizmet türlerini içeren bir veya daha fazla derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4301d-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="4301d-111">Yürütülebilir derlemenin hizmet yapılandırmasını sağlaması için ilişkili bir yapılandırma dosyası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4301d-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="4301d-112">Birden çok derleme sağlamak için standart komut satırı joker karakterlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4301d-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4301d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4301d-113">Example</span></span>  

 <span data-ttu-id="4301d-114">Aşağıdaki komut, myServiceHost.exe çalıştırılabilir dosyasında uygulanan myServiceName hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="4301d-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="4301d-115">Hizmetin yapılandırma dosyası (myServiceHost.exe.config) otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4301d-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="4301d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4301d-116">See also</span></span>

- [<span data-ttu-id="4301d-117">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4301d-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
