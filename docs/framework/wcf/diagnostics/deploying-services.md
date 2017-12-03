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
ms.openlocfilehash: 5e8a853ebfa84ab5517e34bd67ae38672fdacddf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-services"></a><span data-ttu-id="69ca9-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="69ca9-102">Deploying Services</span></span>
<span data-ttu-id="69ca9-103">Bu konuda, nasıl dağıtılacağı açıklanmaktadır bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir çalışma zamanı ortamı uygulamaya.</span><span class="sxs-lookup"><span data-stu-id="69ca9-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="69ca9-104">Barındırma ortamı, uygulamanız için seçme</span><span class="sxs-lookup"><span data-stu-id="69ca9-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="69ca9-105">Hizmetleri destekleyen yönetilen kodu herhangi bir Windows işlemin çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="69ca9-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="69ca9-106">Etkin hale gelmesi bir hizmet oluşturduğu ve yaşam süresi ve bağlam denetleyen bir çalışma zamanı ortamında barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="69ca9-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="69ca9-107">Sunucu ortamlara bir çalışan işlemi içinde veya bir Windows hizmeti, Internet Information Services (IIS) gibi basit konsol uygulaması içinde çalışan seçenekleri aralığından barındırma Windows Etkinleştirme Hizmeti (WAS) tarafından yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="69ca9-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="69ca9-108">Farklı barındırma seçenekleri gözden geçirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="69ca9-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ca9-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69ca9-109">See Also</span></span>  
 [<span data-ttu-id="69ca9-110">Barındırma</span><span class="sxs-lookup"><span data-stu-id="69ca9-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="69ca9-111">Barındırma hizmetleri</span><span class="sxs-lookup"><span data-stu-id="69ca9-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
