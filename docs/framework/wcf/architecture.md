---
title: Windows Communication Foundation Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: b0e4f9af0ff84a8d560b332d227b1ba9ae18bd4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099709"
---
# <a name="windows-communication-foundation-architecture"></a>Windows Communication Foundation Mimarisi
Aşağıdaki grafikte, temel Windows Communication Foundation (WCF) mimari katmanları gösterilmektedir.  
  
## <a name="wcf-architecture"></a>WCF mimarisi  
 ![WCF mimarisinin](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Sözleşmeler ve açıklamaları  
 Sözleşmeler, ileti sistemi çeşitli yönlerini tanımlar. Veri anlaşması bir hizmeti oluşturan veya tüketen her iletiyi yaptığı her bir parametre açıklanmıştır. İleti parametreleri tanım dili (XSD) belge anlayan XML belgeleri işlemek için herhangi bir sistem bu sayede XML şeması tarafından tanımlanır. İleti sözleşmesi, SOAP protokollerini kullanarak belirli bir ileti bölümlerini tanımlar ve birlikte çalışabilirlik gibi duyarlık talep ettiğinde, iletinin bölümleri üzerinde daha ayrıntılı denetim sağlar. Hizmet sözleşmesi hizmetinin gerçek yöntem imzaları belirtir ve bir Visual Basic veya Visual gibi desteklenen programlama dilleri için bir arabirim olarak dağıtılan C#.  
  
 İlkeleri ve bağlamaları bir hizmetle iletişim kurmak için gerekli koşulları gidemez.  Örneğin, bağlama (en az) (örneğin, HTTP veya TCP) kullanılan taşıma ve kodlama belirtmeniz gerekir. İlkeleri, güvenlik gereksinimleri ve bir hizmetle iletişim kurmak için karşılanması gereken diğer koşulları içerir.  
  
### <a name="service-runtime"></a>Hizmet çalışma zamanı  
 Hizmet çalışma zamanı katmanını hizmetinin yalnızca gerçek işlemi sırasında meydana gelen diğer bir deyişle, hizmet çalışma zamanı davranışlarını davranışları içerir. İsteğe bağlı hizmeti için önceden belirlenmiş bir sınır büyürse kaç iletilerin işlenmesini denetimleri kısıtlama, hangi değiştirilebilir. Hata davranışı, bir iç hata hizmette, örneğin, istemciye hangi bilgilerin bildiriliyor denetleyerek meydana geldiğinde ne olacağını belirtir. (Çok fazla bilgi kötü niyetli bir kullanıcı bir saldırı bağlama içinde bir avantajı sağlayabilir.) Meta veri davranışını yöneten olup olmadığını ve nasıl meta veriler için dış dünya kullanılabilir hale getirileceğini. Örnek davranışını belirten kaç hizmeti örneklerini çalıştırılabilir (örneğin, tek tüm iletileri işlemek için yalnızca bir örneği belirtir). Bir hata oluşması durumunda geri alınmasını işlemler işlem davranışını etkinleştirir. Dağıtım davranışı bir ileti WCF altyapısı tarafından nasıl işlendiğini denetimidir.  
  
 Genişletilebilirlik çalışma zamanı işlemleri özelleştirmesini sağlar. Örneğin, ileti İnceleme bir iletinin bölümünü incelemek için özelliğidir ve parametre filtreleme, ileti üstbilgilerini gören filtreleri temel alarak gerçekleşmesi önceden belirlenmiş eylemleri sağlar.  
  
### <a name="messaging"></a>İleti  
 Mesajlaşma katmanı oluşan *kanalları*. Bir kanal iletiyi şekilde, örneğin, bir ileti kimlik doğrulaması yaparak işleyen bir bileşenidir. Kanalları olarak da bilinen kümesidir bir *kanal yığın*. Kanallar, iletileri ve ileti üstbilgileri üzerinde çalışır. Bu, öncelikle İleti gövdeleri içeriğini işleme hakkında endişe hizmeti çalışma zamanı katmandan farklıdır.  
  
 İki tür kanal vardır: taşıma kanalları ve protokol kanalını.  
  
 Taşıma kanalları okuyup iletileri ağ (veya bazı başka bir iletişim noktası dış dünya ile). Bazı taşımalar bir kodlayıcı (XML Infosets temsil edilir) iletiler dönüştürmek ve ağın kullandığı bayt akışı gösterimden kullanın. Adlandırılmış Kanallar, TCP ve MSMQ HTTP taşımaları örnekleridir. XML ve en iyi duruma getirilmiş ikili Kodlamalar örnekleridir.  
  
 Protokol kanalını okuyarak ya da ek üst bilgiler iletiye yazma ileti işleme protokolleri, genellikle uygulayın. WS-güvenlik ve güvenilirlik WS gibi protokolleri örnekleridir.  
  
 Mesajlaşma katmanı, verileri exchange desenlerini ve olası biçimleri gösterilmektedir. WS-Security WS-güvenlik belirtiminin ileti katmanında güvenliği etkinleştirme uygulamasıdır. WS-Reliable Mesajlaşma kanalı ileti teslimi dair bir garanti sağlar. Kodlayıcıları ileti gereksinimlerine uyacak şekilde kullanılabilir Kodlamalar çeşitli sunar. HTTP kanalı, Köprü Metni Aktarım Protokolü ileti teslimi için kullanıldığını belirtir. TCP kanalı benzer şekilde, TCP protokolü belirtir. İşlem akışını kanal işlenen ileti desenleri yönetir. Adlandırılmış kanal işlemler arası iletişimi sağlar. MSMQ kanal MSMQ uygulamalarla birlikte çalışabilirlik sağlar.  
  
### <a name="hosting-and-activation"></a>Barındırma ve etkinleştirme  
 En son şekliyle, bir hizmet bir programdır. Diğer programları gibi bir hizmet, yürütülebilir bir dosyayı çalıştırmanız gerekir. Bu olarak bilinen bir *şirket içinde barındırılan* hizmeti.  
  
 Hizmetleri ayrıca olabilir *barındırılan*, ya da IIS veya Windows Etkinleştirme Hizmeti (WAS) gibi bir dış aracı tarafından yönetilen bir yürütülebilir dosyayı çalıştırın. Çalıştıran bir bilgisayara dağıtıldığında otomatik olarak etkinleştirilmesini sağlar WCF uygulamaları SAHİPTİ. Hizmetleri, yürütülebilir dosyalar (.exe dosyaları) da bir el ile çalıştırılabilir. Hizmet ayrıca otomatik olarak bir Windows hizmeti olarak çalıştırılabilir. COM + bileşenleri, WCF hizmetleri da barındırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)
- [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)
