---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2fa060e567fba9bb5e6344b2c8fc67fb639ad0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228503"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="d412d-102">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="d412d-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="d412d-103">Aynı Visual Studio çözümde birden çok proje içeren başka bir projede hata ayıklaması yaparken, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe) otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d412d-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="d412d-104">Bunu yapmak için WCF Hizmeti projeye sağ tıklayın **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmet aynı çözümdeki başka bir proje hata ayıklama konağı** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="d412d-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="d412d-105">Böylece bu belirli proje için WCF hizmet konağı aynı çözümdeki başka bir projenin hataları ayıklandığında başlatılmaz kutusunun işaretini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d412d-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="d412d-106">F5 hata ayıklaması veya hizmet Başvurusu Ekle işlevleri bu proje için bu davranışı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d412d-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="d412d-107">Bu seçenek, aşağıdaki projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d412d-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="d412d-108">WCF hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="d412d-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="d412d-109">Sıralı iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="d412d-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="d412d-110">Durum makinesi iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="d412d-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="d412d-111">Dağıtım hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="d412d-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d412d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d412d-112">See also</span></span>

- [<span data-ttu-id="d412d-113">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="d412d-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
