---
title: "WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="366b7-102">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="366b7-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="366b7-103">Otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet Konağı (WcfSvcHost.exe) için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aynı başka bir projenin hata ayıklamasını yaparken hizmet kitaplığı proje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] içeren birden çok proje çözümü.</span><span class="sxs-lookup"><span data-stu-id="366b7-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="366b7-104">Bunu yapmak için sağ tıklatın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesinde **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="366b7-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="366b7-105">Kutusunu temizleyebilirsiniz böylece [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı belirli bu proje için başka bir projeye aynı çözüm içinde hata ayıklaması sırasında değil başlattı.</span><span class="sxs-lookup"><span data-stu-id="366b7-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="366b7-106">Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.</span><span class="sxs-lookup"><span data-stu-id="366b7-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="366b7-107">Bu seçenek şu projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="366b7-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="366b7-108">Hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="366b7-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="366b7-109">Sıralı iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="366b7-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="366b7-110">Durum makinesi iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="366b7-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="366b7-111">Dağıtım Hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="366b7-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366b7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="366b7-112">See Also</span></span>  
 [<span data-ttu-id="366b7-113">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="366b7-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
