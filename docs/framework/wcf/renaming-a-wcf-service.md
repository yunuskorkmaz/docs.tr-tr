---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8cb86621972423f55bfa18c60c1d4eb60cacb205
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651053"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="e7ede-102">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="e7ede-102">Renaming a WCF Service</span></span>
<span data-ttu-id="e7ede-103">Bu konuda, bir Windows Communication Foundation (WCF) hizmeti nasıl yeniden adlandırabilirsiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7ede-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="e7ede-104">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="e7ede-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="e7ede-105">Bir Windows Communication Foundation (WCF) şablonu hizmetinde yeniden adlandırmak için aşağıdaki adımları uygulayın,</span><span class="sxs-lookup"><span data-stu-id="e7ede-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="e7ede-106">Hizmet uygulayan sınıfın adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7ede-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="e7ede-107">Hizmet yapılandırma dosyasında hizmetin adı aşağıdaki örnekte gösterildiği gibi seçtiğiniz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7ede-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="e7ede-108">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7ede-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="e7ede-109">Hizmetinizi webhosted ise, \*.svc dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7ede-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="e7ede-110">Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmetin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7ede-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="e7ede-111">Svc dosya olduğundan bu adım şirket içinde barındırılan uygulamalar için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e7ede-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="e7ede-112">Bir WCF hizmet sözleşmesini yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="e7ede-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="e7ede-113">Hizmet sözleşmesi yeniden adlandırmak için aşağıdaki adımları uygulayın,</span><span class="sxs-lookup"><span data-stu-id="e7ede-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="e7ede-114">Hizmet sözleşmesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7ede-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="e7ede-115">Hizmet yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi hizmet sözleşmesi adı seçmiş olduğunuz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7ede-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="e7ede-116">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7ede-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
