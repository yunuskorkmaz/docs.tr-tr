---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255084"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="8e526-102">WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="8e526-102">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="8e526-103">Birden çok proje içeren aynı Visual Studio çözümünde başka bir projede hata ayıklarken, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe) otomatik başlatma özelliğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e526-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="8e526-104">Bunu yapmak için, **Çözüm Gezgini**' de WCF hizmeti projesine sağ tıklayın, **Özellikler**' i seçin ve **WCF seçenekleri** sekmesi ' ne tıklayın. **Aynı çözümdeki başka bir projenin hatalarını AYıKLARKEN WCF hizmet ana bilgisayarı Başlat** onay kutusu varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="8e526-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="8e526-105">Aynı çözümde başka bir proje hata ayıklaması yapıldığında, bu belirli proje için WCF hizmeti ana bilgisayarının başlatılmaması için kutuyu temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e526-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="8e526-106">Bu davranış, bu proje için F5 hata ayıklamayı veya Hizmet Başvurusu Ekle işlevlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="8e526-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="8e526-107">Bu seçenek şu projeler için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8e526-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="8e526-108">WCF hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="8e526-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="8e526-109">Sıralı Iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="8e526-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="8e526-110">Durum makinesi Iş akışı hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="8e526-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="8e526-111">Dağıtım hizmeti kitaplık projesi.</span><span class="sxs-lookup"><span data-stu-id="8e526-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e526-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e526-112">See also</span></span>

- [<span data-ttu-id="8e526-113">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="8e526-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
