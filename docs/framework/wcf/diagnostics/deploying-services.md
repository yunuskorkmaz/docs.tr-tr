---
title: Dağıtma Hizmetleri
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 07bd2a3938f238336dc00fa2e0826a28a9363a4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294813"
---
# <a name="deploying-services"></a><span data-ttu-id="72e06-102">Dağıtma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="72e06-102">Deploying Services</span></span>

<span data-ttu-id="72e06-103">Bu konuda, bir Windows Communication Foundation (WCF) uygulamasını çalışma zamanı ortamına nasıl dağıtabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72e06-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="72e06-104">Uygulamanız için barındırma ortamı seçme</span><span class="sxs-lookup"><span data-stu-id="72e06-104">Choosing the Hosting Environment for Your Application</span></span>  

 <span data-ttu-id="72e06-105">WCF Hizmetleri, yönetilen kodu destekleyen herhangi bir Windows işleminde çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="72e06-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="72e06-106">Etkin hale gelmesi için bir hizmetin kendisini oluşturan bir çalışma zamanı ortamı içinde barındırılması ve bağlamını ve ömrünü denetmasıdır.</span><span class="sxs-lookup"><span data-stu-id="72e06-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="72e06-107">Barındırma seçenekleri, en basit konsol uygulaması içinde, Windows hizmeti, Internet Information Services (IIS) gibi sunucu ortamlarına veya Windows etkinleştirme hizmeti (WAS) tarafından yönetilen bir çalışan işlemi içinde çalışmaya göre değişir.</span><span class="sxs-lookup"><span data-stu-id="72e06-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="72e06-108">WCF uygulamanızın farklı barındırma seçeneklerini gözden geçirmek için bkz. [barındırma hizmetleri](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="72e06-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e06-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e06-109">See also</span></span>

- [<span data-ttu-id="72e06-110">Hosting</span><span class="sxs-lookup"><span data-stu-id="72e06-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="72e06-111">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="72e06-111">Hosting Services</span></span>](../hosting-services.md)
