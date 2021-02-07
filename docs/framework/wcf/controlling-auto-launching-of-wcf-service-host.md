---
description: 'Hakkında daha fazla bilgi edinin: WCF hizmet konağının otomatik olarak başlatılmasını denetleme'
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f0e9a4e79a403920c0bc6a512b30fb038b2aa1f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677398"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="3d323-103">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="3d323-103">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="3d323-104">Birden çok proje içeren aynı Visual Studio çözümünde başka bir projede hata ayıklarken, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe) otomatik başlatma özelliğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d323-104">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="3d323-105">Bunu yapmak için, **Çözüm Gezgini**' de WCF hizmeti projesine sağ tıklayın, **Özellikler**' i seçin ve **WCF seçenekleri** sekmesi ' ne tıklayın. **Aynı çözümdeki başka bir projenin hatalarını AYıKLARKEN WCF hizmet ana bilgisayarı Başlat** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="3d323-105">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="3d323-106">Aynı çözümde başka bir proje hata ayıklaması yapıldığında, bu belirli proje için WCF hizmeti ana bilgisayarının başlatılmaması için kutuyu temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d323-106">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="3d323-107">Bu davranış, bu proje için F5 hata ayıklamayı veya Hizmet Başvurusu Ekle işlevlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="3d323-107">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="3d323-108">Bu seçenek şu projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3d323-108">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="3d323-109">WCF hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="3d323-109">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="3d323-110">Sıralı Iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="3d323-110">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="3d323-111">Durum makinesi Iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="3d323-111">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="3d323-112">Dağıtım hizmeti kitaplık projesi.</span><span class="sxs-lookup"><span data-stu-id="3d323-112">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d323-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d323-113">See also</span></span>

- [<span data-ttu-id="3d323-114">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="3d323-114">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
