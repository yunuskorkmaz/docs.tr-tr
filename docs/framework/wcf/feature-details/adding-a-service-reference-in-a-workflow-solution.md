---
title: "Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="1c388-102">Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="1c388-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="1c388-103">Bir iş akışı uygulamasında bir hizmet başvurusu ekleme biraz normal bir WCF uygulaması farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1c388-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="1c388-104">Hizmet Başvurusu Ekle seçtiğinizde ve hizmet URL'sini belirtin meta verileri indirilir ve özel etkinlikler WCF hizmeti çağırmasına olanak tanıyan oluşturulur veya WCF iş akışı hizmeti için bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="1c388-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="1c388-105">Oluşturulan etkinlikleri yerleşik şekilde hizmet başvurusu eklendikten sonra çözümü yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="1c388-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="1c388-106">Bunlar daha sonra iş akışı Tasarımcısı araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="1c388-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="1c388-107">Ancak, bir iş akışı çözümünde hizmet başvurusu ekliyorsanız bu yalnızca çalışacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1c388-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="1c388-108">Aşağıdaki web cast diğer tür projelerde hizmet Başvurusu Ekle gösterilmektedir: [bir WCF hizmeti bir Web projesi bir iş akışında arama](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="1c388-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="1c388-109">Aynı işlemi adını içeren Hizmetleri iki veya daha fazla hizmeti başvuruları ekleme bir sorunu neden olur.</span><span class="sxs-lookup"><span data-stu-id="1c388-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="1c388-110">Oluşturulan etkinlikleri yalnızca ilk hizmet işlemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1c388-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="1c388-111">Bu sorunu yeniden adlandırma hizmet işlemleri çalışmak için bu nedenle bunlar farklı veya oluşturulan her etkinlik uç nokta Yapılandırması adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1c388-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c388-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c388-112">See Also</span></span>  
 [<span data-ttu-id="1c388-113">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1c388-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="1c388-114">Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c388-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="1c388-115">Bir WCF hizmeti bir Web projesi bir iş akışında arama</span><span class="sxs-lookup"><span data-stu-id="1c388-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
