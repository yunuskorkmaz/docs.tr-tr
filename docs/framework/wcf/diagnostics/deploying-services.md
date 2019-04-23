---
title: Dağıtma Hizmetleri
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 2c3cd17b597fafcd02b9155089bc583fafbc9dea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085772"
---
# <a name="deploying-services"></a><span data-ttu-id="79678-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="79678-102">Deploying Services</span></span>
<span data-ttu-id="79678-103">Bu konuda, bir çalışma zamanı ortamına bir Windows Communication Foundation (WCF) uygulamanın nasıl dağıtılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79678-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="79678-104">Barındırma ortamı, uygulamanız için seçme</span><span class="sxs-lookup"><span data-stu-id="79678-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="79678-105">WCF hizmetleri destekleyen yönetilen kodu herhangi bir Windows işlem içinde çalıştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79678-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="79678-106">Etkin duruma gelmesi bir hizmet oluşturup kendi bağlam ve yaşam süresini denetleyen bir çalışma zamanı ortamında barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79678-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="79678-107">Barındırma seçenekleri aralığı içinde basit bir konsol uygulaması server ortamları gibi bir Windows hizmeti, Internet Information Services (IIS) olarak ya da bir çalışan işlemi için çalışan Windows Etkinleştirme Hizmeti (WAS) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="79678-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="79678-108">WCF uygulamanız için farklı barındırma seçenekleri gözden geçirmek için bkz: [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="79678-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79678-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79678-109">See also</span></span>

- [<span data-ttu-id="79678-110">Barındırma</span><span class="sxs-lookup"><span data-stu-id="79678-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="79678-111">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="79678-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
