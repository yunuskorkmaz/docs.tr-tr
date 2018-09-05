---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 3f5556eeaf56ac48dd4f1d578ed2e66b90415677
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503440"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknolojidir özgüdür. Dağıtılmış uygulamalar WCF kullanarak artık geliştirilmiş olmalı.**  
  
 WCF ile mevcut .NET uzaktan iletişim uygulamalarını yararlanmak için iki yolu vardır: tümleştirme ve geçiş. Tümleştirme sayesinde sahip .net uzaktan iletişim 2.0 ve çalışan WCF tarafı yan yana, var olan .net değiştirmek zorunda kalmadan aynı anda aynı iş nesnelerini hem teknolojiler kullanıma izin vererek Remoting 2.0 kodu. Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya üzerinin. WCF özelliklerinden yararlanmak istiyorsanız ve uzak 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetinizi WCF'ye geçiş yapabilirsiniz. WCF geçişi .NET uzaktan iletişim 2.0 Uzak nesnenin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir. Hem bu konuların ele alınmaktadır [öğesinden uzaktan iletişim için Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kavramsal Genel Bakış](../../../../docs/framework/wcf/conceptual-overview.md)
