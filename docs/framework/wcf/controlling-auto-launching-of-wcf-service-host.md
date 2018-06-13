---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809894"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="c5565-102">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="c5565-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="c5565-103">Birden çok proje içeren aynı Visual Studio çözümüne başka bir projenin hata ayıklamasını yaparken bir WCF Hizmeti kitaplığı projesi için Windows Communication Foundation (WCF) Hizmet Konağı (WcfSvcHost.exe) otomatik olarak başlatılmasını yeteneğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5565-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="c5565-104">Bunu yapmak için WCF Hizmeti projeye sağ **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c5565-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="c5565-105">Böylece aynı çözüm içinde başka bir projeye hata ayıklaması sırasında belirli bu proje için WCF hizmet konağı başlatılmadığı kutusunu temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5565-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="c5565-106">Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c5565-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="c5565-107">Bu seçenek şu projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c5565-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="c5565-108">WCF hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="c5565-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="c5565-109">Sıralı iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="c5565-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="c5565-110">Durum makinesi iş akışı hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="c5565-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="c5565-111">Dağıtım Hizmeti kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="c5565-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5565-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5565-112">See Also</span></span>  
 [<span data-ttu-id="c5565-113">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="c5565-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
