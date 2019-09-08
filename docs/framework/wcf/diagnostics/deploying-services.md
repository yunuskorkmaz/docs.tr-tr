---
title: Dağıtma Hizmetleri
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 684b781c568518cfb321d8021e4f7062e855e6aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798133"
---
# <a name="deploying-services"></a><span data-ttu-id="ed8f2-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ed8f2-102">Deploying Services</span></span>
<span data-ttu-id="ed8f2-103">Bu konuda, bir Windows Communication Foundation (WCF) uygulamasını çalışma zamanı ortamına nasıl dağıtabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed8f2-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="ed8f2-104">Uygulamanız için barındırma ortamı seçme</span><span class="sxs-lookup"><span data-stu-id="ed8f2-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="ed8f2-105">WCF Hizmetleri, yönetilen kodu destekleyen herhangi bir Windows işleminde çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ed8f2-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="ed8f2-106">Etkin hale gelmesi için bir hizmetin kendisini oluşturan bir çalışma zamanı ortamı içinde barındırılması ve bağlamını ve ömrünü denetmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed8f2-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="ed8f2-107">Barındırma seçenekleri, en basit konsol uygulaması içinde, Windows hizmeti, Internet Information Services (IIS) gibi sunucu ortamlarına veya Windows etkinleştirme hizmeti (WAS) tarafından yönetilen bir çalışan işlemi içinde çalışmaya göre değişir.</span><span class="sxs-lookup"><span data-stu-id="ed8f2-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="ed8f2-108">WCF uygulamanızın farklı barındırma seçeneklerini gözden geçirmek için bkz. [barındırma hizmetleri](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="ed8f2-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8f2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed8f2-109">See also</span></span>

- [<span data-ttu-id="ed8f2-110">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ed8f2-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="ed8f2-111">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ed8f2-111">Hosting Services</span></span>](../hosting-services.md)
