---
title: Temel Programlama Yaşam Döngüsü
description: Bir WCF uygulaması oluşturmak için görevler hakkında bilgi edinin. WCF, uygulamaların aynı bilgisayarda, ağlar üzerinde veya farklı uygulama platformlarında iletişim kurmasını sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: f958bd06f617a5648b31332ebe9e7662d45cd241
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294852"
---
# <a name="basic-programming-lifecycle"></a>Temel Programlama Yaşam Döngüsü

Windows Communication Foundation (WCF), uygulamaların aynı bilgisayarda, Internet üzerinden veya farklı uygulama platformlarında olup olmadıkları ile iletişim kurmasını sağlar. Bu konu, bir WCF uygulaması oluşturmak için gereken görevleri özetler. Çalışan bir örnek uygulama için bkz. [Başlangıç Öğreticisi](getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Temel görevler  

 Gerçekleştirilecek temel görevler sırasıyla:  
  
1. Hizmet sözleşmesini tanımlayın. Hizmet sözleşmesi bir hizmetin imzasını, yaptığı verileri ve diğer sözleşmeye dayalı gerekli verileri belirler. Daha fazla bilgi için bkz. [hizmet sözleşmelerini tasarlama](designing-service-contracts.md).  
  
2. Sözleşmeyi uygulayın. Bir hizmet sözleşmesi uygulamak için, sözleşmeyi uygulayan bir sınıf oluşturun ve çalışma zamanının sahip olduğu özel davranışları belirtin. Daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).  
  
3. Uç noktaları ve diğer davranış bilgilerini belirterek hizmeti yapılandırın. Daha fazla bilgi için bkz. [Hizmetleri yapılandırma](configuring-services.md).  
  
4. Hizmeti barındırın. Daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).  
  
5. Bir istemci uygulaması oluşturun. Daha fazla bilgi için bkz. [Istemcileri derleme](building-clients.md).  
  
 Bu bölümdeki konular bu sırayı takip etse de, bazı senaryolar başlangıcında başlamaz. Örneğin, önceden var olan bir hizmet için istemci derlemek isterseniz 5. adımda başlar. Veya başkalarının kullanacağı bir hizmet oluşturuyorsanız 5. adımı atlayabilirsiniz.  
  
 Hizmet sözleşmeleri geliştirmeye alışdıktan sonra, [genişletilebilirliğine giriş](introduction-to-extensibility.md)de okuyabilirsiniz. Hizmetinizdeki sorunlarla karşılaşırsanız, diğer kişilerin aynı veya benzer sorunlara sahip olup olmadığını görmek için [WCF sorun giderme hızlı](wcf-troubleshooting-quickstart.md) başlangıcı ' nı kontrol edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmelerini Uygulama](implementing-service-contracts.md)
