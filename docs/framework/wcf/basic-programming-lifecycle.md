---
title: Temel Programlama Yaşam Döngüsü
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: b20167ad776f3524e4516b71e43ab8cdb5c2aea4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803698"
---
# <a name="basic-programming-lifecycle"></a>Temel Programlama Yaşam Döngüsü
Windows Communication Foundation (WCF) uygulamaların aynı bilgisayarda Internet üzerinden veya farklı bir uygulama platformlarda olup olmadıklarını iletişim kurmasına olanak sağlar. Bu konuda bir WCF uygulaması oluşturmak için gerekli görevleri açıklanmaktadır. Çalışan bir örnek uygulama için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Basit görevler  
 Temel görevleri gerçekleştirmek için sırasıyla şunlardır:  
  
1.  Hizmet sözleşmesi tanımlayın. Bir hizmet sözleşmesini bir hizmet, bu alış verişleri veri ve diğer kapsamındaki gerekli verileri imzası belirtir. Daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Sözleşme uygulayın. Bir hizmet sözleşmesini uygulama için sözleşme uygulayan bir sınıf oluşturun ve çalışma zamanı olmalıdır özel davranışlar belirtin. Daha fazla bilgi için bkz: [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Hizmet uç noktaları ve diğer davranış bilgileri belirterek yapılandırın. Daha fazla bilgi için bkz: [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hizmetini barındırır. Daha fazla bilgi için bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Bir istemci uygulaması oluşturun. Daha fazla bilgi için bkz: [istemci derleme](../../../docs/framework/wcf/building-clients.md).  
  
 Bu bölümdeki konular, bu sırada izleyin rağmen bazı senaryolar başında başlatmayın. Örneğin, önceden var olan bir hizmet için bir istemci oluşturmak istiyorsanız, adım 5 başlatın. Veya diğer kullanıcıların kullanacağı bir hizmet oluşturuluyorsa, adım 5 atlayabilirsiniz.  
  
 Hizmet sözleşmelerini geliştirmeyi hakkında bilgi sahibi olduktan sonra ayrıca okuyabilirsiniz [genişletilebilirlik genel bakış](../../../docs/framework/wcf/introduction-to-extensibility.md). Hizmetiniz ile ilgili sorununuz varsa, denetleyin [WCF sorun giderme Hızlı Başlangıç](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) başkalarının aynı veya benzer sorunlar yüklü olup olmadığını görmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
