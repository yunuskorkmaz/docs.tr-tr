---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091132"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="f4226-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="f4226-102">Migrating .NET Remoting Applications to WCF</span></span>
**<span data-ttu-id="f4226-103">Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknolojidir özgüdür.</span><span class="sxs-lookup"><span data-stu-id="f4226-103">This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development.</span></span> <span data-ttu-id="f4226-104">Dağıtılmış uygulamalar WCF kullanarak artık geliştirilmiş olmalı.</span><span class="sxs-lookup"><span data-stu-id="f4226-104">Distributed applications should now be developed using WCF.</span></span>**  
  
 <span data-ttu-id="f4226-105">WCF ile mevcut .NET uzaktan iletişim uygulamalarını yararlanmak için iki yolu vardır: tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="f4226-105">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="f4226-106">Tümleştirme .NET uzaktan iletişim 2.0 ve yan yana çalıştırma, mevcut .NET uzaktan iletişim 2.0 kodunuzu değiştirmek zorunda kalmadan aynı anda aynı iş nesnelerini hem teknolojiler kullanıma izin vererek WCF sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4226-106">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="f4226-107">Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya üzerinin.</span><span class="sxs-lookup"><span data-stu-id="f4226-107">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="f4226-108">WCF özelliklerinden yararlanmak istiyorsanız ve uzak 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetinizi WCF'ye geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4226-108">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="f4226-109">WCF geçişi .NET uzaktan iletişim 2.0 Uzak nesnenin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4226-109">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="f4226-110">Hem bu konuların ele alınmaktadır [öğesinden uzaktan iletişim için Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="f4226-110">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4226-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4226-111">See also</span></span>

- [<span data-ttu-id="f4226-112">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4226-112">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
