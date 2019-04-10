---
title: Temel Programlama Yaşam Döngüsü
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: 6d9ea3b877e7c735cf789039b2a6956037372888
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330564"
---
# <a name="basic-programming-lifecycle"></a>Temel Programlama Yaşam Döngüsü
Windows Communication Foundation (WCF) uygulamaların aynı bilgisayarda Internet üzerinden ya da farklı uygulama platformları üzerinde olup olmadıklarını iletişim kurmasına olanak sağlar. Bu konu, bir WCF uygulaması oluşturmak için gereken görevleri özetler. Çalışan bir örnek uygulama için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Temel görevleri  
 Temel görevleri gerçekleştirmek için sırayla şöyledir:  
  
1. Hizmet sözleşmesini tanımlamaktır. Hizmet sözleşmesi, hizmet, veri, birbiriyle değiştirir ve diğer sözleşmeye dayalı olarak gerekli veri imzası belirtir. Daha fazla bilgi için [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2. Sözleşme uygulayın. Bir hizmet sözleşmesini uygulama için sözleşme uygulayan bir sınıf oluşturun ve çalışma zamanı olması gereken özel davranışlar belirtin. Daha fazla bilgi için [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3. Hizmet uç noktaları ve diğer davranışı bilgileri belirterek yapılandırın. Daha fazla bilgi için [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
4. Hizmet ana bilgisayar. Daha fazla bilgi için [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
5. Bir istemci uygulaması oluşturun. Daha fazla bilgi için [istemci derleme](../../../docs/framework/wcf/building-clients.md).  
  
 Bu bölümdeki konular bu sırayı takip olsa da, bazı senaryolar başında başlatmayın. Örneğin, önceden mevcut olan bir hizmet için bir istemci oluşturmak istiyorsanız, 5. adımda başlatın. Veya diğer kullanıcıların kullanacağı bir hizmet geliştiriyorsanız, 5. adımı atlayabilirsiniz.  
  
 Hizmet sözleşmeleri geliştirmeyle ilgili bilgi sahibi olduktan sonra ayrıca okuyabilirsiniz [Genişletilebilirliğe genel bakış](../../../docs/framework/wcf/introduction-to-extensibility.md). Hizmetinizle ilgili sorunlar, denetleyin [WCF sorun giderme hızlı başlangıcı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) başkalarının aynı veya benzer sorunlara sahip olup olmadığını görmek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmelerini Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
