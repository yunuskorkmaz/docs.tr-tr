---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bb6356ba4698cad00d443fdb80b1a45d35e2175
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="ec9f9-102">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="ec9f9-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="ec9f9-103">Otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet Konağı (WcfSvcHost.exe) için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] birden çok proje içeren aynı Visual Studio çözümü başka bir projesinde hata ayıklarken hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="ec9f9-104">Bunu yapmak için sağ tıklatın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesinde **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="ec9f9-105">Kutusunu temizleyebilirsiniz böylece [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı belirli bu proje için başka bir projeye aynı çözüm içinde hata ayıklaması sırasında değil başlattı.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="ec9f9-106">Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="ec9f9-107">Bu seçenek şu projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ec9f9-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="ec9f9-108"> Hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="ec9f9-109">Sıralı iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="ec9f9-110">Durum makinesi iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="ec9f9-111">Dağıtım Hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9f9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec9f9-112">See Also</span></span>  
 [<span data-ttu-id="ec9f9-113">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ec9f9-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
