---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 6233c603c30dbd021050caa2c5fd9c1849c80700
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546516"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="dbc26-102">.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="dbc26-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="dbc26-103">**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için saklanan eski bir teknolojiye özgüdür ve yeni geliştirme için önerilmez. Dağıtılmış uygulamalar artık WCF kullanılarak geliştirilebilmelidir.**</span><span class="sxs-lookup"><span data-stu-id="dbc26-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="dbc26-104">Mevcut .NET uzaktan Iletişim uygulamalarıyla WCF 'den faydalanması gereken iki yol vardır: Tümleştirme ve geçiş.</span><span class="sxs-lookup"><span data-stu-id="dbc26-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="dbc26-105">Tümleştirme, .NET Remoting 2,0 ve WCF 'nin yan yana çalışmasını sağlar ve aynı iş nesnelerini, mevcut .NET Remoting 2,0 kodunuzu değiştirmek zorunda kalmadan her iki teknolojiden aynı anda kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbc26-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="dbc26-106">Tümleştirme için .NET Framework 2,0 veya üzeri bir sürümü çalıştırıyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbc26-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="dbc26-107">WCF özelliklerinden yararlanmak istiyorsanız ve Remoting 2,0 sistemleri ile hat uyumluluğuna gerek duymayın, tüm hizmetinizi WCF 'ye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbc26-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="dbc26-108">.NET Remoting 2,0 ' den WCF 'ye geçiş, uzak nesnenin arabiriminde ve yapılandırma ayarlarında değişiklik yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dbc26-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="dbc26-109">Bu konuların her ikisi de [Windows Communication Foundation uzaktan Iletişim üzerinden](/previous-versions/aa730857(v=vs.80))ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="dbc26-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc26-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbc26-110">See also</span></span>

- [<span data-ttu-id="dbc26-111">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dbc26-111">Conceptual Overview</span></span>](../conceptual-overview.md)
