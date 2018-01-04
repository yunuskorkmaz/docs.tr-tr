---
title: "Dağıtma Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e32570b381d6cab4326a13246dfe053b5032589
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-services"></a><span data-ttu-id="84544-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="84544-102">Deploying Services</span></span>
<span data-ttu-id="84544-103">Bu konuda, nasıl dağıtılacağı açıklanmaktadır bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir çalışma zamanı ortamı uygulamaya.</span><span class="sxs-lookup"><span data-stu-id="84544-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="84544-104">Barındırma ortamı, uygulamanız için seçme</span><span class="sxs-lookup"><span data-stu-id="84544-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="84544-105">Hizmetleri destekleyen yönetilen kodu herhangi bir Windows işlemin çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="84544-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="84544-106">Etkin hale gelmesi bir hizmet oluşturduğu ve yaşam süresi ve bağlam denetleyen bir çalışma zamanı ortamında barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84544-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="84544-107">Sunucu ortamlara bir çalışan işlemi içinde veya bir Windows hizmeti, Internet Information Services (IIS) gibi basit konsol uygulaması içinde çalışan seçenekleri aralığından barındırma Windows Etkinleştirme Hizmeti (WAS) tarafından yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="84544-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="84544-108">Farklı barındırma seçenekleri gözden geçirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="84544-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84544-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84544-109">See Also</span></span>  
 [<span data-ttu-id="84544-110">Barındırma</span><span class="sxs-lookup"><span data-stu-id="84544-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="84544-111">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="84544-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
