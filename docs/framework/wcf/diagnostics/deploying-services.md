---
title: Dağıtma Hizmetleri
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 4d9efcb4da064021d93345285982c0cbd29dde2e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="deploying-services"></a><span data-ttu-id="1256d-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1256d-102">Deploying Services</span></span>
<span data-ttu-id="1256d-103">Bu konuda, bir çalışma zamanı ortamı Windows Communication Foundation (WCF) uygulamaya nasıl dağıtılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1256d-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="1256d-104">Barındırma ortamı, uygulamanız için seçme</span><span class="sxs-lookup"><span data-stu-id="1256d-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="1256d-105">WCF hizmetleri destekleyen yönetilen kodu herhangi bir Windows işlemin çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1256d-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="1256d-106">Etkin hale gelmesi bir hizmet oluşturduğu ve yaşam süresi ve bağlam denetleyen bir çalışma zamanı ortamında barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1256d-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="1256d-107">Sunucu ortamlara bir çalışan işlemi içinde veya bir Windows hizmeti, Internet Information Services (IIS) gibi basit konsol uygulaması içinde çalışan seçenekleri aralığından barındırma Windows Etkinleştirme Hizmeti (WAS) tarafından yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="1256d-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="1256d-108">WCF uygulamanız için farklı barındırma seçenekleri gözden geçirmek için bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="1256d-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1256d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1256d-109">See Also</span></span>  
 [<span data-ttu-id="1256d-110">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1256d-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="1256d-111">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1256d-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
