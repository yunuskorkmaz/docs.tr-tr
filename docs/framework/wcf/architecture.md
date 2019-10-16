---
title: Windows Communication Foundation Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: f34a05a436dd021f0d1fcc05f3a12a058123acdc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320832"
---
# <a name="windows-communication-foundation-architecture"></a>Windows Communication Foundation Mimarisi
Aşağıdaki grafikte Windows Communication Foundation (WCF) mimarisinin ana katmanları gösterilmektedir.  
  
## <a name="wcf-architecture"></a>WCF mimarisi  
 ![WCF mimarisi](./media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Sözleşmeler ve açıklamalar  
 Sözleşmeler, ileti sisteminin çeşitli yönlerini tanımlar. Veri sözleşmesi, bir hizmetin oluşturabileceğiniz veya tüketebileceği her iletiyi oluşturan her parametreyi açıklar. İleti parametreleri, XML şeması tanım dili (XSD) belgeleri tarafından tanımlanır ve belgeyi işlemek için XML 'yi anlayan tüm sistemleri etkinleştirir. İleti anlaşması, SOAP protokollerini kullanarak belirli ileti parçalarını tanımlar ve birlikte çalışabilirlik bu tür duyarlık taleplerini daha ayrıntılı olarak kontrol etmenizi sağlar. Hizmet sözleşmesi, hizmetin gerçek Yöntem imzalarını belirtir ve Visual Basic veya görsel C#gibi desteklenen programlama dillerinden birinde bir arabirim olarak dağıtılır.  
  
 İlkeler ve bağlamalar, bir hizmetle iletişim kurmak için gereken koşulları ifade edin.  Örneğin, bağlama (en azından), kullanılan taşıma (örneğin, HTTP veya TCP) ve bir kodlama belirtir. İlkeler, güvenlik gereksinimlerini ve hizmet ile iletişim kurmak için karşılanması gereken diğer koşulları içerir.  
  
### <a name="service-runtime"></a>Hizmet çalışma zamanı  
 Hizmet çalışma zamanı katmanı, yalnızca hizmetin gerçek işlemi sırasında, diğer bir deyişle hizmetin çalışma zamanı davranışlarından oluşan davranışları içerir. Daraltma, hizmet talebi önceden ayarlanmış bir sınıra arttıkça değiştirilebilir olan kaç ileti işleneceğini denetler. Bir hata davranışı, hizmette bir iç hata oluştuğunda ne olduğunu belirtir, örneğin, istemciye hangi bilgilerin iletildiğini kontrol edin. (Çok fazla bilgi kötü amaçlı bir kullanıcıya saldırı bağlama konusunda avantaj verebilir.) Meta veri davranışı, meta verilerin dış dünyanın kullanımına açık yapılıp yapılmadığını yönetir. Örnek davranışı, hizmetin kaç örneğinin çalıştırılacağını belirtir (örneğin, tek tek bir örneği tüm iletileri işlemek için tek bir örnek belirtir). İşlem davranışı, bir hata oluşursa işlenen işlemlerin geri alınmasını mümkün olur. Dağıtım davranışı, bir iletinin WCF altyapısı tarafından nasıl işlendiği denetimidir.  
  
 Genişletilebilirlik, çalışma zamanı işlemlerinin özelleştirilmesine izin vermez. Örneğin, ileti incelemesi bir iletinin parçalarını inceleme özelliğindedir ve parametre filtrelemesi, ileti üstbilgilerinde çalışan filtrelere göre önceden ayarlanmış eylemlerin oluşmasına olanak sağlar.  
  
### <a name="messaging"></a>İleti  
 Mesajlaşma katmanı, *kanallardan*oluşur. Kanal, bir iletiyi bir ileti kimlik doğrulaması ile, örneğin, bir şekilde işleyen bir bileşendir. Kanal kümesi, *kanal yığını*olarak da bilinir. Kanallar iletiler ve ileti üstbilgilerinde çalışır. Bu, özellikle ileti gövdelerinin içeriklerinin işlenmesiyle ilgili olan hizmet çalışma zamanı katmanından farklıdır.  
  
 İki tür kanal vardır: taşıma kanalları ve protokol kanalları.  
  
 Taşıma kanalları ağdan iletileri okur ve yazar (veya dış dünya ile diğer iletişim noktaları). Bazı aktarımlar, iletileri (XML bilgi kümeleri olarak temsil edilen) ağ tarafından kullanılan bayt akışı gösteriminden ve arasında dönüştürmek için bir kodlayıcı kullanır. Aktarım örnekleri HTTP, adlandırılmış kanallar, TCP ve MSMQ olarak adlandırılır. Kodlama örnekleri, XML ve iyileştirilmiş ikili bir örnektir.  
  
 Protokol kanalları ileti işleme protokollerini, genellikle iletiye ek üstbilgiler okuyarak veya yazarak uygular. Bu protokollerin örnekleri arasında WS-Security ve WS-güvenirlik bulunur.  
  
 Mesajlaşma katmanı, verilerin olası biçimlerini ve değişim düzenlerini gösterir. WS-Security, ileti katmanında güvenliği etkinleştiren WS-güvenlik belirtiminin bir uygulamasıdır. WS-güvenilir mesajlaşma kanalı ileti teslimi garantisi verir. Kodlayıcılarda, iletinin ihtiyaçlarını karşılamak için kullanılabilecek çeşitli kodlamalar vardır. HTTP kanalı, ileti teslimi için Köprü Metni Aktarım protokolünün kullanıldığını belirtir. TCP kanalı benzer şekilde TCP protokolünü belirtir. Işlem akışı kanalı, işlem temelli ileti düzenlerini yönetir. Adlandırılmış kanal kanalı, işlemler arası iletişimi mümkün. MSMQ kanalı, MSMQ uygulamalarıyla birlikte çalışabilirlik özelliğini sunar.  
  
### <a name="hosting-and-activation"></a>Barındırma ve etkinleştirme  
 Son formunda bir hizmet bir programdır. Diğer programlar gibi, bir hizmetin yürütülebilir dosya içinde çalıştırılması gerekir. Bu, *kendi kendine barındırılan* hizmet olarak bilinir.  
  
 Hizmetler *Ayrıca, IIS*veya Windows etkinleştirme HIZMETI (was) gibi bir dış aracı tarafından yönetilen yürütülebilir dosya içinde de çalıştırılabilir. , WAS, çalıştıran bir bilgisayara dağıtıldığında WCF uygulamalarının otomatik olarak etkinleştirilmesini sağlar. Hizmetler Ayrıca çalıştırılabilir (. exe dosyaları) olarak el ile çalıştırılabilir. Bir hizmet, otomatik olarak bir Windows hizmeti olarak da çalıştırılabilir. COM+ bileşenleri, WCF Hizmetleri olarak da barındırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation nedir?](whats-wcf.md)
- [Temel Windows Communication Foundation Kavramları](fundamental-concepts.md)
