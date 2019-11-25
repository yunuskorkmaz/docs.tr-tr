---
title: WCF hizmetlerini yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 332a88530010197187ca3ea787e152b0c95a5514
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141589"
---
# <a name="configuring-wcf-services"></a>WCF hizmetlerini yapılandırma

Hizmet sözleşmenizi tasarladıktan ve uyguladıktan sonra, hizmetinizi yapılandırmaya hazırlanın. Burada, hizmetinizin, bulunabileceği adresi belirtme, ileti göndermek ve almak için kullandığı Aktarım ve ileti kodlama ve gerek duyduğu güvenlik türü dahil olmak üzere, istemcilerin istemcilere sunulma şeklini tanımlamanız ve özelleştirmeniz burada yer alır.  
  
 Burada kullanılan yapılandırma, bir hizmetin uç nokta adreslerini, kullanılan taşımaları ve güvenlik düzenlerini belirtmek gibi bir hizmetin çeşitli yönlerini tanımlayabileceğiniz ve özelleştirebileceğiniz bir yapılandırma dosyası kullanarak tüm yolları, imperatively içinde veya bir yapılandırma dosyasını içerir. Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Basitleştirilmiş Yapılandırma](simplified-configuration.md)  
 WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir. Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı hizmetinizi otomatik olarak varsayılan uç noktalar, bağlamalar ve davranışlar ile yapılandırır.  
  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)  
 Windows Communication Foundation (WCF) hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir. En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web. config dosyasına eklenir. Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.  
  
 [Bağlamalar](bindings.md)  
 Ayrıca, WCF, istemci ve hizmetin nasıl iletişim kurduğu, aktarımlar, güvenlik ve ileti kodlamaları gibi en temel özellikleri hızlı bir şekilde seçmenizi sağlayan bağlamalar biçiminde sistem tarafından sunulan birçok ortak yapılandırmayı içerir.  
  
 [Uç Noktalar](endpoints.md)  
 WCF hizmeti ile kurulan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur. Uç noktalar sözleşmeyi, bağlamalarda belirtilen yapılandırma bilgilerini ve hizmetin nerede bulunacağını veya hizmet hakkındaki bilgilerin nerede alınacağını belirten adresleri içerir.  
  
 [Hizmetleri Güvenli Hale Getirme](securing-services.md)  
 WCF ve mevcut güvenlik mekanizmalarını kullanarak, herhangi bir hizmete gizlilik, bütünlük, kimlik doğrulama ve yetkilendirme uygulayabilirsiniz. Ayrıca güvenlik başarıları ve başarısızlıklarını da denetleyebilirsiniz.  
  
 [WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Diğer platformların veya işletim sistemindeki hizmetler ve istemcilerle birlikte çalışabilen bir hizmeti dağıtmaya yönelik gereksinimler, WS-ı temel profil 1,1 belirtiminde özetlenmiştir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Temel Programlama Yaşam Döngüsü](basic-programming-lifecycle.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](designing-and-implementing-services.md)  
  
 [Barındırma Hizmetleri](hosting-services.md)  
  
 [İstemci Derleme](building-clients.md)  
  
 [Genişletilebilirliğe Genel Bakış](introduction-to-extensibility.md)  
  
 [Yönetim ve Tanılama](./diagnostics/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](basic-wcf-programming.md)
- [Kavramsal Genel Bakış](conceptual-overview.md)
- [WCF Özellik Ayrıntıları](./feature-details/index.md)
