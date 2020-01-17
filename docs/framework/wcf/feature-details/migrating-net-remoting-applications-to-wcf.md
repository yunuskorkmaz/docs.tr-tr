---
title: .NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212157"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için saklanan eski bir teknolojiye özgüdür ve yeni geliştirme için önerilmez. Dağıtılmış uygulamalar artık WCF kullanılarak geliştirilebilmelidir.**  
  
 Mevcut .NET uzaktan Iletişim uygulamalarıyla WCF 'den faydalanması gereken iki yol vardır: Tümleştirme ve geçiş. Tümleştirme, .NET Remoting 2,0 ve WCF 'nin yan yana çalışmasını sağlar ve aynı iş nesnelerini, mevcut .NET Remoting 2,0 kodunuzu değiştirmek zorunda kalmadan her iki teknolojiden aynı anda kullanıma sunabilirsiniz. Tümleştirme için .NET Framework 2,0 veya üzeri bir sürümü çalıştırıyor olmanız gerekir. WCF özelliklerinden yararlanmak istiyorsanız ve Remoting 2,0 sistemleri ile hat uyumluluğuna gerek duymayın, tüm hizmetinizi WCF 'ye geçirebilirsiniz. .NET Remoting 2,0 ' den WCF 'ye geçiş, uzak nesnenin arabiriminde ve yapılandırma ayarlarında değişiklik yapılmasını gerektirir. Bu konuların her ikisi de [Windows Communication Foundation uzaktan Iletişim üzerinden](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80))ele alınmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kavramsal Genel Bakış](../../../../docs/framework/wcf/conceptual-overview.md)
