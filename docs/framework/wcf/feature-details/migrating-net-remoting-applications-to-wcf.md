---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 863679b5c6333d8049d335f263aa3b1729859d8b
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843315"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknolojidir özgüdür. Dağıtılmış uygulamalar WCF kullanarak artık geliştirilmiş olmalı.**  
  
 WCF ile mevcut .NET uzaktan iletişim uygulamalarını yararlanmak için iki yolu vardır: tümleştirme ve geçiş. Tümleştirme .NET uzaktan iletişim 2.0 ve yan yana çalıştırma, mevcut .NET uzaktan iletişim 2.0 kodunuzu değiştirmek zorunda kalmadan aynı anda aynı iş nesnelerini hem teknolojiler kullanıma izin vererek WCF sahip olmanızı sağlar. Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya üzerinin. WCF özelliklerinden yararlanmak istiyorsanız ve uzak 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetinizi WCF'ye geçiş yapabilirsiniz. WCF geçişi .NET uzaktan iletişim 2.0 Uzak nesnenin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir. Hem bu konuların ele alınmaktadır [öğesinden uzaktan iletişim için Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kavramsal Genel Bakış](../../../../docs/framework/wcf/conceptual-overview.md)
