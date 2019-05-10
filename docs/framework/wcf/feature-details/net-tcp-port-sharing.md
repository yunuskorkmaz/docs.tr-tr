---
title: Net.TCP Bağlantı Noktası Paylaşımı
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: f40afe25bbc3238ec773ee1ee19673d4d5a3ef1d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603950"
---
# <a name="nettcp-port-sharing"></a>Net.TCP Bağlantı Noktası Paylaşımı
Windows Communication Foundation (WCF), yüksek performanslı iletişim için yeni TCP tabanlı ağ protokolü (net.tcp://) sağlar. WCF da yeni bir sistem bileşeni olan birden çok kullanıcı süreçler arasında paylaşılacak net.tcp bağlantı noktası sağlayan Net.TCP bağlantı noktası paylaşma hizmeti tanıtılmaktadır.  
  
## <a name="background-and-motivation"></a>Arka plan ve motivasyon  
 TCP/IP Protokolü ilk olarak sunulmuştur, yalnızca az sayıda uygulama protokolleri yapılan bunu kullanın. TCP/IP bağlantı noktası numaralarını her uygulama protokolü için bir benzersiz 16 bit bağlantı noktası numarası atayarak uygulamaları birbirinden ayırmak için kullanılır. Örneğin, HTTP trafiğini 80 numaralı TCP bağlantı noktasını kullanmak için bugün standartlaştırılmıştır, SMTP 25 numaralı TCP bağlantı noktasını kullanır ve FTP 20 ve 21 TCP bağlantı noktalarını kullanır. Aktarım olarak TCP kullanarak diğer uygulamaları başka bir kullanılabilir bağlantı noktası numarası, kural tarafından ya da resmi Standardizasyon üzerinden seçebilirsiniz.  
  
 Uygulamalar arasında ayrım yapmak için bağlantı noktası numaralarını kullanarak güvenlik sorunlarını vardı. Güvenlik duvarları, genellikle bir standart olmayan bağlantı noktasını kullanan bir uygulamayı dağıtma genellikle karmaşık ya da Kurumsal ve kişisel güvenlik duvarları varlığı nedeniyle olanaksız bile, bu nedenle, bazı iyi bilinen bir giriş noktaları dışında tüm bağlantı noktalarındaki TCP trafiği engellemek için yapılandırılır. Zaten izin verilen standart, iyi bilinen bağlantı noktaları üzerinden iletişim kurabilen uygulamaları dış saldırı yüzeyini azaltın. Birçok ağ uygulamaları HTTP yararlanması çoğu Güvenlik Duvarı varsayılan olarak 80 numaralı TCP bağlantı noktasında trafiğe izin verecek şekilde yapılandırıldığından protokol.  
  
 HTTP. Trafiği birçok farklı HTTP uygulamaları için tek bir TCP bağlantı noktası üzerinde çoğaltıldı SYS modeli Windows platformunda standart haline gelmiştir. Bu güvenlik duvarı için ortak bir denetim noktası sağlar yapabileceğiniz yeni uygulamalar oluşturmak dağıtım maliyeti en aza indirmek, uygulama geliştiricilerinin sağlarken Yöneticiler ağ kullanın.  
  
 Birden çok uygulamada HTTP bağlantı noktası paylaşma olanağı, uzun bir özellik Internet Information Services (IIS) kaldırıldı. Ancak, yalnızca HTTP sunulmasıyla birlikte idi. SYS (çekirdek modu HTTP protokolü dinleyici) ile [!INCLUDE[iis601](../../../../includes/iis601-md.md)] bu altyapı tam olarak genelleştirilmiş. Aslında, HTTP. SYS TCP bağlantı noktası HTTP trafiğine ayrılmış paylaşmak rastgele kullanıcı işlemleri sağlar. Bu özellik, ayrı, yalıtılmış işlemlerde aynı fiziksel makinede gönderin ve TCP bağlantı noktası 80 üzerinden trafiği almak için gereken ağ altyapısını paylaşırken bulunabilmesi birçok HTTP uygulamaları tanır. Net.TCP bağlantı noktası paylaşma hizmeti aynı türde uygulamalar için net.tcp bağlantı noktası sağlar.  
  
## <a name="port-sharing-architecture"></a>Bağlantı noktası paylaşımı mimarisi  
 Wcf'de bağlantı noktası paylaşımı mimari üç ana bileşene sahiptir:  
  
- Bir çalışan işlemi: Paylaşılan bağlantı noktalarını kullanarak net.tcp:// iletişim kuran herhangi bir işlem.  
  
- WCF TCP taşıma: Net.tcp:// Protokolü uygular.  
  
- Net.TCP bağlantı noktası Paylaşımı hizmeti: Çok sayıda çalışan işlemine aynı TCP bağlantı noktasını paylaşmasına izin verir.  
  
 Net.TCP bağlantı noktası paylaşma hizmeti üzerinden bağlanan çalışan işlemleri adına net.tcp:// bağlantılarını kabul eden bir kullanıcı modu Windows hizmetidir. Bir yuva bağlantısı geldiğinde, hizmet bağlantı noktası hedef adresini almak için gelen ileti akışı inceler. Bu adresini temel alan, hizmet bağlantı noktası, sonuçta işlediği uygulamaya veri akışını yönlendirebilirsiniz.  
  
 Açılır net.tcp:// bağlantı noktası kullanan bir WCF hizmeti, WCF TCP taşıma altyapısını doğrudan bir TCP yuva uygulama işleminde açılmaz. Bunun yerine, aktarım altyapısı Net.TCP bağlantı noktası paylaşma hizmeti hizmetin taban adresi Tekdüzen Kaynak Tanımlayıcısı (URI) kaydeder ve onun adına iletileri dinlemek için hizmet bağlantı noktası bekler.  Hizmet bağlantı noktası geldikçe uygulama hizmetine gönderilen iletiler gönderir.  
  
## <a name="installing-port-sharing"></a>Bağlantı noktası paylaşımı yükleme  
 Net.TCP bağlantı noktası paylaşma hizmeti destekleyen tüm işletim sistemlerinde kullanılabilir [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ancak hizmet varsayılan olarak etkin değildir. Bir güvenlik önlemi olarak yönetici Net.TCP bağlantı noktası paylaşma hizmeti ilk kullanım önce el ile etkinleştirmeniz gerekir. Net.TCP bağlantı noktası paylaşma hizmeti bağlantı noktası paylaşma hizmeti tarafından sahip olunan ağ yuvaları çeşitli özelliklerini değiştirmenize izin veren bir yapılandırma seçenekleri sunar. Daha fazla bilgi için [nasıl yapılır: Net.TCP bağlantı noktası hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>NET.TCP bir uygulamaya bağlantı noktası kullanma  
 Kullanarak bir hizmeti kullanıma sunmak için WCF uygulamanızı net.tcp:// bağlantı noktası kullanmak için en kolay yolu olan <xref:System.ServiceModel.NetTcpBinding> Net.TCP bağlantı noktası paylaşım hizmetini kullanarak etkinleştirmek için sonra da <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği.  
  
 Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bağlantı noktası paylaşımı kullanarak bir WCF hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Bağlantı noktası paylaşımı, güvenlikle ilgili etkileri  
 Net.TCP bağlantı noktası paylaşma hizmeti bir katman uygulamalar ve ağ arasındaki işleme sağlasa da, ağ üzerinde doğrudan dinleme gibi bağlantı noktası Paylaşımı kullanan uygulamalar yine de sağlanmalıdır. Özellikle, bağlantı noktası Paylaşımı kullanan uygulamalar, altında çalıştığı işlem ayrıcalıklarını değerlendirmelidir. Ağ iletişimi için gerekli işlem ayrıcalıklarını en az sayıda çalıştırır yerleşik ağ hizmeti hesabı kullanarak uygulamanızı çalıştırmayı göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [Barındırma](../../../../docs/framework/wcf/feature-details/hosting.md)
- [Nasıl yapılır: Bağlantı noktası paylaşımı kullanarak bir WCF hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Nasıl yapılır: Net.TCP bağlantı noktası hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
