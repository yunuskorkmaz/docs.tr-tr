---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052058"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="54a40-102">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="54a40-102">Renaming a WCF Service</span></span>
<span data-ttu-id="54a40-103">Bu konu, bir Windows Communication Foundation (WCF) hizmetini nasıl yeniden adlandırabileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="54a40-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="54a40-104">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="54a40-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="54a40-105">Bir Windows Communication Foundation (WCF) şablonunda bir hizmeti yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="54a40-106">Hizmeti uygulayan sınıfın adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="54a40-107">Hizmetin yapılandırma dosyasında, aşağıdaki örnekte gösterildiği gibi hizmetin adını seçtiğiniz yeni adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="54a40-108">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="54a40-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="54a40-109">Hizmetiniz Web 'de barındırılıyorsa, bir \* \* . svc\* dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="54a40-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="54a40-110">Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmetinizin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="54a40-111">Bu adım, bir svc dosyası olmadığından, kendi kendine barındırılan uygulamalar için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="54a40-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="54a40-112">WCF hizmet sözleşmesini yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="54a40-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="54a40-113">Hizmet sözleşmesini yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="54a40-114">Hizmet sözleşmesinin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="54a40-115">Hizmetin yapılandırma dosyasında, hizmet sözleşmesinin adını, aşağıdaki örnekte gösterildiği gibi, seçtiğiniz yeni adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="54a40-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="54a40-116">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="54a40-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
