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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="585aa-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="585aa-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="585aa-103">**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknoloji özgüdür. Dağıtılmış uygulamalar şimdi geliştirilen kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="585aa-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="585aa-104">Yararlanmak için iki yolla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut .NET uzaktan iletişim uygulamalarla: tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="585aa-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="585aa-105">Tümleştirme .net sahip olmanızı sağlar Remoting 2.0 ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışan yan yana, olanak tanıyarak, aynı iş nesneleri iki teknolojiyi aynı anda var olan .net değiştirmek zorunda kalmadan ortaya Remoting 2.0 kodu.</span><span class="sxs-lookup"><span data-stu-id="585aa-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="585aa-106">Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="585aa-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="585aa-107">Yararlanmak isterseniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özellikleri ve değil wire Remoting 2.0 sistemleriyle uyumluluk, tüm hizmetinize geçirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="585aa-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="585aa-108">.NET uzaktan iletişim 2.0 geçişini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzak nesnesinin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="585aa-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="585aa-109">Bu konular her ikisi de ele alınmaktadır [gelen Windows Communication Foundation Remoting](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="585aa-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585aa-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="585aa-110">See Also</span></span>  
 [<span data-ttu-id="585aa-111">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="585aa-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
