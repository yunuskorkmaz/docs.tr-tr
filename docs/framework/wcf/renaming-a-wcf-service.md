---
title: "Bir WCF Hizmetini Yeniden Adlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee707a898bf915491cc1ca44e0606c261dc87dc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="a3513-102">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a3513-102">Renaming a WCF Service</span></span>
<span data-ttu-id="a3513-103">Bu konu, nasıl adlandırabilirsiniz açıklar bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="a3513-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="a3513-104">Bir WCF Hizmetini Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a3513-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="a3513-105">Bir hizmet olarak yeniden adlandırmak için aşağıdaki adımları izleyerek bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] şablonu</span><span class="sxs-lookup"><span data-stu-id="a3513-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="a3513-106">Hizmet uygulayan sınıf adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3513-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="a3513-107">Hizmet yapılandırma dosyasında hizmetin adı aşağıdaki örnekte gösterildiği gibi seçtiğiniz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3513-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="a3513-108">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3513-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="a3513-109">Hizmetinizi webhosted ise, bir *.svc dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="a3513-109">If your service is webhosted, it uses an *.svc file.</span></span> <span data-ttu-id="a3513-110">Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmet adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3513-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="a3513-111">Svc dosya olduğundan bu adımı kendini barındıran uygulamalar için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a3513-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="a3513-112">WCF hizmet sözleşmesini yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="a3513-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="a3513-113">Hizmet sözleşmesi yeniden adlandırmak için aşağıdaki adımları gerçekleştirin,</span><span class="sxs-lookup"><span data-stu-id="a3513-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="a3513-114">Hizmet sözleşmesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3513-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="a3513-115">Hizmet yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi hizmet sözleşmesi adı seçtiğiniz yeni bir adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a3513-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="a3513-116">Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3513-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
