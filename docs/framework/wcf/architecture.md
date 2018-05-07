---
title: Windows Communication Foundation Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: b54c9cd7f4e6bc33dac07d30a86df81668ae13e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-architecture"></a>Windows Communication Foundation Mimarisi
Aşağıdaki grafikte Windows Communication Foundation (WCF) mimarisi ana katmanları gösterilmektedir.  
  
## <a name="wcf-architecture"></a>WCF mimarisi  
 ![WCF mimarisinin](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Sözleşmeler ve açıklamaları  
 Sözleşmeler ileti sistemi çeşitli yönlerini tanımlar. Veri sözleşmesi bir hizmet oluşturun veya tüketmek her ileti yapar her bir parametre açıklanmıştır. İleti parametrelerinin tanım dili (XSD) belgeleri belgeleri işlemek için XML anlar sistem etkinleştirme XML şeması tarafından tanımlanır. İleti sözleşmesi SOAP protokollerini kullanarak belirli bir ileti bölümleri tanımlar ve birlikte çalışabilirlik gibi duyarlık talep ettiğinde ileti bölümlerini geçirmiş denetime izin verir. Hizmet Sözleşmesi Hizmet gerçek yöntemi imzalarını belirtir ve desteklenen programlama dilleri, Visual Basic veya Visual C# gibi birinde bir arabirim olarak dağıtılır.  
  
 İlkeleri ve bağlamaları hizmeti ile iletişim kurmak için gerekli koşulları iznine.  Örneğin, bağlama (en az) kullanılan aktarım (örneğin, HTTP veya TCP) ve bir kodlama belirtmeniz gerekir. Güvenlik gereksinimleri ve hizmeti ile iletişim kurmak için karşılanması gereken diğer koşulları ilkelerdir.  
  
### <a name="service-runtime"></a>Hizmet çalışma zamanı  
 Hizmet çalışma zamanı katman yalnızca hizmet gerçek işleminde ortaya davranışları hizmet başka bir deyişle, çalışma zamanı davranışlarını içerir. İsteğe bağlı hizmeti için önceden belirlenmiş bir sınır büyürse işlenen kaç iletileri denetimleri kısıtlama, hangi değiştirilebilir. Bir iç hata hizmette, örneğin, hangi bilgilerin istemciye iletilen denetleyerek oluştuğunda neler bir hata davranışını belirtir. (Çok fazla bilgisi kötü niyetli bir kullanıcı bir saldırı takma içinde bir avantajı verebilirsiniz.) Meta veri davranışını yöneten olup olmadığını ve nasıl meta verileri dış dünya için kullanılabilir yapılır. Örnek davranışını belirten hizmetin kaç örneğini çalıştırma (örneğin, bir singleton tüm iletileri işlemek için yalnızca bir örneğini belirtir). Bir hata oluşursa işlem davranışı geri uygulaması yapılan işlemler alınmasını sağlar. Gönderme davranıştır bir ileti tarafından nasıl işleneceğini denetim [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] altyapı.  
  
 Genişletilebilirlik çalışma zamanı işlemleri özelleştirmesini sağlar. Örneğin, ileti denetleme bir iletinin bölümünü incelemek için tesis ve parametre filtreleme ileti üstbilgilerinde hareket filtreleri dayanan gerçekleşmesi önceden belirlenmiş eylemleri etkinleştirir.  
  
### <a name="messaging"></a>İleti  
 İleti katmanı oluşan *kanalları*. Bir kanal bazı şekilde bir ileti, örneğin, bir iletinin kimliğini tarafından işleyen bir bileşenidir. Kanallar olarak da bilinen kümesidir bir *kanal yığını*. Kanallar, iletileri ve ileti üstbilgilerini üzerinde çalışır. Bu, öncelikle İleti gövdeleri içeriğini işleme hakkında kaygı hizmeti çalışma zamanı katmandan farklıdır.  
  
 Kanallar iki tür vardır: taşıma kanalları ve protokol kanalını.  
  
 Taşıma kanalları okuma ve ağ (veya bazı bir iletişim noktası dış dünyayla) iletileri yazma. Bazı taşımaları bir kodlayıcı (XML Infosets temsil edilir) iletilerinin dönüştürmek ve ağı tarafından kullanılan bayt akışı gösterimden kullanın. Adlandırılmış Kanallar, TCP ve MSMQ HTTP taşımaları örnekleridir. XML ve en iyi duruma getirilmiş ikili kodlamaları örnekleridir.  
  
 Protokol kanalını ileti işleme protokolleri, genellikle okuma veya ek üstbilgi işaretlemekdeki uygular. WS güvenliği ve güvenilirliği WS böyle protokolleri örneklerindendir.  
  
 İleti katmanı, verileri exchange desenlerini ve olası biçimleri gösterilmektedir. WS güvenliği güvenlik ileti katmanında etkinleştirme WS-Security belirtimi uygulamasıdır. WS güvenilir Mesajlaşma kanalı ileti teslimi garanti tanır. Kodlayıcılar ileti gereksinimlerine uyacak şekilde kullanılan Kodlamalar çeşitli sunar. HTTP kanalı Köprü Metni Aktarım Protokolü ileti teslimi için kullanıldığını belirtir. TCP kanalı benzer şekilde TCP protokolünü belirtir. İşlem akışını kanal işlenen ileti desenleri yönetir. Adlandırılmış kanal işlemler arası iletişim sağlar. MSMQ kanal MSMQ uygulamalarla birlikte çalışabilirlik sağlar.  
  
### <a name="hosting-and-activation"></a>Barındırma ve etkinleştirme  
 En son şekliyle, bir hizmet bir programdır. Diğer programları gibi bir hizmet bir yürütülebilir dosya içinde çalıştırmanız gerekir. Bu olarak bilinen bir *kendi kendini barındıran* hizmet.  
  
 Hizmetleri de olabilir *barındırılan*, veya IIS ya da Windows Etkinleştirme Hizmeti (WAS) gibi bir dış aracı tarafından yönetilen bir yürütülebilir dosyayı çalıştırın. WAS etkinleştirir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WAS çalıştıran bir bilgisayara dağıtıldığında otomatik olarak etkinleştirilecek uygulamalar. Hizmetleri, yürütülebilir dosyalar (.exe dosyaları) da bir el ile çalıştırılabilir. Bir hizmet ayrıca otomatik olarak bir Windows hizmeti olarak çalıştırılabilir. COM + bileşenleri de barındırılması olarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)  
 [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)
