---
title: 'Nasıl yapılır: Derlenmiş hizmet kodunu doğrulamak için svcutil.exe kullanma'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: a06cf57fce883753af4686b294396d6d6da73a13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531934"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="cf53a-102">Nasıl yapılır: Derlenmiş hizmet kodunu doğrulamak için svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="cf53a-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="cf53a-103">Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) barındırma hizmeti olmadan hizmet uygulamaları ve yapılandırmalarında hataları algılamak için.</span><span class="sxs-lookup"><span data-stu-id="cf53a-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="cf53a-104">Bir hizmeti doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="cf53a-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="cf53a-105">Hizmetiniz bir yürütülebilir dosyasına ve bir veya daha fazla bağımlı derlemeleri derleyin.</span><span class="sxs-lookup"><span data-stu-id="cf53a-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="cf53a-106">Bir SDK komut istemi açın</span><span class="sxs-lookup"><span data-stu-id="cf53a-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="cf53a-107">Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="cf53a-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="cf53a-108">Çeşitli parametreler hakkında daha fazla bilgi için bkz, hizmet Validationsection [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) konu.</span><span class="sxs-lookup"><span data-stu-id="cf53a-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="cf53a-109">Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmeti yapılandırma adını belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf53a-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="cf53a-110">`assemblyPath` Bağımsız değişkeni hizmeti ve doğrulanması için hizmet türlerini içeren bir veya daha fazla derlemeler için yürütülebilir dosyanın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf53a-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="cf53a-111">Yürütülebilir derleme hizmeti yapılandırması sağlamak için ilişkili bir yapılandırma dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf53a-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="cf53a-112">Birden çok derleme sağlamak için standart bir komut satırı joker karakterler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf53a-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf53a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf53a-113">Example</span></span>  
 <span data-ttu-id="cf53a-114">Aşağıdaki komutu, hizmet myServiceName myServiceHost.exe yürütülebilir dosya olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cf53a-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="cf53a-115">Yapılandırma dosyası (myServiceHost.exe.config) hizmeti için otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cf53a-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf53a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf53a-116">See also</span></span>
- [<span data-ttu-id="cf53a-117">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="cf53a-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
