---
description: 'Daha fazla bilgi edinin: bir WCF hizmetini yeniden adlandırma'
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8d75e43f4bda97e8ee6de34b039eb1236d6c4a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779172"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="48183-103">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="48183-103">Renaming a WCF Service</span></span>

<span data-ttu-id="48183-104">Bu konu, bir Windows Communication Foundation (WCF) hizmetini nasıl yeniden adlandırabileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="48183-104">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="48183-105">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="48183-105">Renaming a WCF Service</span></span>  

 <span data-ttu-id="48183-106">Bir Windows Communication Foundation (WCF) şablonunda bir hizmeti yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-106">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="48183-107">Hizmeti uygulayan sınıfın adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-107">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="48183-108">Hizmetin yapılandırma dosyasında, aşağıdaki örnekte gösterildiği gibi hizmetin adını seçtiğiniz yeni adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-108">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="48183-109">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="48183-109">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="48183-110">Hizmetiniz Web 'de barındırılıyorsa, bir *\* . svc* dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="48183-110">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="48183-111">Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmetinizin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-111">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="48183-112">Bu adım, bir svc dosyası olmadığından, kendi kendine barındırılan uygulamalar için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="48183-112">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="48183-113">WCF hizmet sözleşmesini yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="48183-113">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="48183-114">Hizmet sözleşmesini yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-114">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="48183-115">Hizmet sözleşmesinin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-115">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="48183-116">Hizmetin yapılandırma dosyasında, hizmet sözleşmesinin adını, aşağıdaki örnekte gösterildiği gibi, seçtiğiniz yeni adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48183-116">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="48183-117">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="48183-117">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
