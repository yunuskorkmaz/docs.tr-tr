---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492502"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="82cda-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="82cda-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="82cda-103">**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknoloji özgüdür. Dağıtılmış uygulamalar artık WCF kullanılarak geliştirilen.**</span><span class="sxs-lookup"><span data-stu-id="82cda-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="82cda-104">WCF mevcut .NET uzaktan iletişim uygulamalarla yararlanmak için iki yolu vardır: tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="82cda-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="82cda-105">Tümleştirme .net sahip olmanızı sağlar Remoting 2.0 ve çalışan WCF tarafı yan yana aynı iş nesneleri iki teknolojiyi aynı anda var olan .net değiştirmek zorunda kalmadan kullanıma izin vererek Remoting 2.0 kodu.</span><span class="sxs-lookup"><span data-stu-id="82cda-105">Integration allows you to have .Net Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="82cda-106">Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="82cda-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="82cda-107">WCF özelliklerden yararlanmak istiyor ve Uzaktan iletişim 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetiniz için WCF geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82cda-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="82cda-108">WCF .NET uzaktan iletişim 2.0 geçiş uzak nesnesinin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82cda-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="82cda-109">Bu konular her ikisi de ele alınmaktadır [gelen Windows Communication Foundation Remoting](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="82cda-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82cda-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82cda-110">See Also</span></span>  
 [<span data-ttu-id="82cda-111">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82cda-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
