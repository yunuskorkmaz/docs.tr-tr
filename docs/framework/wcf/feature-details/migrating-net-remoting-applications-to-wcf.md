---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592872"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="58045-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="58045-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="58045-103">**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknolojidir özgüdür. Dağıtılmış uygulamalar WCF kullanarak artık geliştirilmiş olmalı.**</span><span class="sxs-lookup"><span data-stu-id="58045-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="58045-104">WCF ile mevcut .NET uzaktan iletişim uygulamalarını yararlanmak için iki yolu vardır: tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="58045-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="58045-105">Tümleştirme .NET uzaktan iletişim 2.0 ve yan yana çalıştırma, mevcut .NET uzaktan iletişim 2.0 kodunuzu değiştirmek zorunda kalmadan aynı anda aynı iş nesnelerini hem teknolojiler kullanıma izin vererek WCF sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="58045-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="58045-106">.NET Framework 2.0 veya üzeri çalıştığını tümleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="58045-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="58045-107">WCF özelliklerinden yararlanmak istiyorsanız ve uzak 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetinizi WCF'ye geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58045-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="58045-108">WCF geçişi .NET uzaktan iletişim 2.0 Uzak nesnenin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="58045-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="58045-109">Hem bu konuların ele alınmaktadır [öğesinden uzaktan iletişim için Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="58045-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58045-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58045-110">See also</span></span>

- [<span data-ttu-id="58045-111">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58045-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
