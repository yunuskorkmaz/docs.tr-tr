---
title: ".NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dff06fbc52c0f4371abf0bcc465fd6a6d8be5859
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="d5a3a-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="d5a3a-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="d5a3a-103">**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknoloji özgüdür. Dağıtılmış uygulamalar şimdi geliştirilen kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="d5a3a-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="d5a3a-104">Yararlanmak için iki yolla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut .NET uzaktan iletişim uygulamalarla: tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="d5a3a-105">Tümleştirme .net sahip olmanızı sağlar Remoting 2.0 ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışan yan yana, olanak tanıyarak, aynı iş nesneleri iki teknolojiyi aynı anda var olan .net değiştirmek zorunda kalmadan ortaya Remoting 2.0 kodu.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="d5a3a-106">Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="d5a3a-107">Yararlanmak isterseniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özellikleri ve değil wire Remoting 2.0 sistemleriyle uyumluluk, tüm hizmetinize geçirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5a3a-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="d5a3a-108">.NET uzaktan iletişim 2.0 geçişini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzak nesnesinin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="d5a3a-109">Bu konular her ikisi de ele alınmaktadır [gelen Windows Communication Foundation Remoting](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="d5a3a-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a3a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-110">See Also</span></span>  
 [<span data-ttu-id="d5a3a-111">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="d5a3a-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
