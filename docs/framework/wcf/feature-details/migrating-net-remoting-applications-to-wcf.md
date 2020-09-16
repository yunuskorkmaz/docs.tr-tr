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
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için saklanan eski bir teknolojiye özgüdür ve yeni geliştirme için önerilmez. Dağıtılmış uygulamalar artık WCF kullanılarak geliştirilebilmelidir.**  
  
 Mevcut .NET uzaktan Iletişim uygulamalarıyla WCF 'den faydalanması gereken iki yol vardır: Tümleştirme ve geçiş. Tümleştirme, .NET Remoting 2,0 ve WCF 'nin yan yana çalışmasını sağlar ve aynı iş nesnelerini, mevcut .NET Remoting 2,0 kodunuzu değiştirmek zorunda kalmadan her iki teknolojiden aynı anda kullanıma sunabilirsiniz. Tümleştirme için .NET Framework 2,0 veya üzeri bir sürümü çalıştırıyor olmanız gerekir. WCF özelliklerinden yararlanmak istiyorsanız ve Remoting 2,0 sistemleri ile hat uyumluluğuna gerek duymayın, tüm hizmetinizi WCF 'ye geçirebilirsiniz. .NET Remoting 2,0 ' den WCF 'ye geçiş, uzak nesnenin arabiriminde ve yapılandırma ayarlarında değişiklik yapılmasını gerektirir. Bu konuların her ikisi de [Windows Communication Foundation uzaktan Iletişim üzerinden](/previous-versions/aa730857(v=vs.80))ele alınmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kavramsal Genel Bakış](../conceptual-overview.md)
