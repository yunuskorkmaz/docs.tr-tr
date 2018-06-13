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
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknoloji özgüdür. Dağıtılmış uygulamalar artık WCF kullanılarak geliştirilen.**  
  
 WCF mevcut .NET uzaktan iletişim uygulamalarla yararlanmak için iki yolu vardır: tümleştirme ve geçiş. Tümleştirme .net sahip olmanızı sağlar Remoting 2.0 ve çalışan WCF tarafı yan yana aynı iş nesneleri iki teknolojiyi aynı anda var olan .net değiştirmek zorunda kalmadan kullanıma izin vererek Remoting 2.0 kodu. Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya daha büyük. WCF özelliklerden yararlanmak istiyor ve Uzaktan iletişim 2.0 sistemleriyle kablo uyumluluk gerekmez, tüm hizmetiniz için WCF geçirebilirsiniz. WCF .NET uzaktan iletişim 2.0 geçiş uzak nesnesinin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir. Bu konular her ikisi de ele alınmaktadır [gelen Windows Communication Foundation Remoting](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kavramsal Genel Bakış](../../../../docs/framework/wcf/conceptual-overview.md)
