---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498993"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="5356c-102">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="5356c-102">Renaming a WCF Service</span></span>
<span data-ttu-id="5356c-103">Bu konu, Windows Communication Foundation (WCF) hizmetini nasıl yeniden adlandırabilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="5356c-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="5356c-104">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="5356c-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="5356c-105">Bir Windows Communication Foundation (WCF) şablonu hizmetinde yeniden adlandırmak için aşağıdaki adımları gerçekleştirin,</span><span class="sxs-lookup"><span data-stu-id="5356c-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
-   <span data-ttu-id="5356c-106">Hizmet uygulayan sınıf adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356c-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="5356c-107">Hizmet yapılandırma dosyasında hizmetin adı aşağıdaki örnekte gösterildiği gibi seçtiğiniz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356c-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="5356c-108">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="5356c-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="5356c-109">Hizmetinizi webhosted ise, bir \*.svc dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="5356c-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="5356c-110">Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmet adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356c-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="5356c-111">Svc dosya olduğundan bu adımı kendini barındıran uygulamalar için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5356c-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="5356c-112">WCF hizmet sözleşmesini yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="5356c-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="5356c-113">Hizmet sözleşmesi yeniden adlandırmak için aşağıdaki adımları gerçekleştirin,</span><span class="sxs-lookup"><span data-stu-id="5356c-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="5356c-114">Hizmet sözleşmesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356c-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="5356c-115">Hizmet yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi hizmet sözleşmesi adı seçtiğiniz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356c-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="5356c-116">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="5356c-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
