---
title: "Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ea14631208f755b45a27ff323b7d875c1ae5cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="07a69-102">Nasıl yapılır: Derlenmiş Hizmet Kodunu Doğrulamak için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="07a69-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="07a69-103">Kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) barındırma hizmeti olmadan hatalarını hizmet uygulamaları ve yapılandırmaları algılamak için.</span><span class="sxs-lookup"><span data-stu-id="07a69-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="07a69-104">Bir hizmeti doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="07a69-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="07a69-105">Hizmetinizi yürütülebilir bir dosya halinde ve bir veya daha fazla bağımlı derlemeleri derleyin.</span><span class="sxs-lookup"><span data-stu-id="07a69-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="07a69-106">Bir SDK komut istemi açın</span><span class="sxs-lookup"><span data-stu-id="07a69-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="07a69-107">Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe Aracı'nı başlatın.</span><span class="sxs-lookup"><span data-stu-id="07a69-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="07a69-108">Hizmet Validationsection, çeşitli parametreleri hakkında daha fazla bilgi için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) konu.</span><span class="sxs-lookup"><span data-stu-id="07a69-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="07a69-109">Kullanmalısınız `/serviceName` doğrulamak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="07a69-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="07a69-110">`assemblyPath` Bağımsız değişkeni hizmeti ve doğrulanacak hizmet türlerini içeren bir veya daha fazla derlemeler için yürütülebilir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="07a69-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="07a69-111">Yürütülebilir derleme hizmet yapılandırmasını sağlamak için ilişkili bir yapılandırma dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07a69-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="07a69-112">Birden çok derleme sağlamak için standart komut satırı joker karakterleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07a69-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a69-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="07a69-113">Example</span></span>  
 <span data-ttu-id="07a69-114">Aşağıdaki komutu hizmet myServiceName myServiceHost.exe yürütülebilir dosya olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07a69-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="07a69-115">Yapılandırma dosyası (myServiceHost.exe.config) hizmeti için otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="07a69-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="07a69-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07a69-116">See Also</span></span>  
 [<span data-ttu-id="07a69-117">ServiceModel meta veri yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="07a69-117">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
