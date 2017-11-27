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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 511ff8fa982e9a9ca29faf714725626f7925f659
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="3ae7a-102">Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="3ae7a-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="3ae7a-103">Bir iş akışı uygulamasında bir hizmet başvurusu ekleme biraz normal bir WCF uygulaması farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="3ae7a-104">Hizmet Başvurusu Ekle seçtiğinizde ve hizmet URL'sini belirtin meta verileri indirilir ve özel etkinlikler WCF hizmeti çağırmasına olanak tanıyan oluşturulur veya WCF iş akışı hizmeti için bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="3ae7a-105">Oluşturulan etkinlikleri yerleşik şekilde hizmet başvurusu eklendikten sonra çözümü yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="3ae7a-106">Bunlar daha sonra iş akışı Tasarımcısı araç kutusunda görünür.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="3ae7a-107">Ancak, bir iş akışı çözümünde hizmet başvurusu ekliyorsanız bu yalnızca çalışacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="3ae7a-108">Aşağıdaki web cast diğer tür projelerde hizmet Başvurusu Ekle gösterilmektedir: [bir WCF hizmeti bir Web projesi bir iş akışında arama](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="3ae7a-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="3ae7a-109">Aynı işlemi adını içeren Hizmetleri iki veya daha fazla hizmeti başvuruları ekleme bir sorunu neden olur.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="3ae7a-110">Oluşturulan etkinlikleri yalnızca ilk hizmet işlemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="3ae7a-111">Bu sorunu yeniden adlandırma hizmet işlemleri çalışmak için bu nedenle bunlar farklı veya oluşturulan her etkinlik uç nokta Yapılandırması adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae7a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ae7a-112">See Also</span></span>  
 [<span data-ttu-id="3ae7a-113">İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3ae7a-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="3ae7a-114">Nasıl yapılır: başka bir iş akışı hizmeti çağıran bir iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ae7a-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="3ae7a-115">Bir WCF hizmeti bir Web projesi bir iş akışında arama</span><span class="sxs-lookup"><span data-stu-id="3ae7a-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
