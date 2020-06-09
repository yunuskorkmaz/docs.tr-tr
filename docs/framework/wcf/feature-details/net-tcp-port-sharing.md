---
title: Net.TCP Bağlantı Noktası Paylaşımı
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: d9c6caa546d9f31f4e68b850dc1b1e750da2e93c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598768"
---
# <a name="nettcp-port-sharing"></a>Net.TCP Bağlantı Noktası Paylaşımı
Windows Communication Foundation (WCF), yüksek performanslı iletişim için yeni bir TCP tabanlı Ağ Protokolü (net. TCP://) sağlar. WCF Ayrıca, net. TCP bağlantı noktalarının birden çok kullanıcı işlemi arasında paylaşılmasını sağlayan net. TCP bağlantı noktası paylaşma hizmeti olan yeni bir sistem bileşeni de sunar.  
  
## <a name="background-and-motivation"></a>Arka plan ve Mosyon  
 TCP/IP Protokolü ilk kez sunulmasıyla, yalnızca az sayıda uygulama protokolü tarafından kullanılır. Her uygulama protokolüne benzersiz bir 16-bit bağlantı noktası numarası atayarak uygulamalar arasında ayrım yapmak için TCP/IP kullanılan bağlantı noktası numaraları. Örneğin, günümüzde HTTP trafiği TCP bağlantı noktası 80 ' ü kullanmak için standartlaştırılmış, SMTP TCP bağlantı noktası 25 ' i ve FTP ise 20 ve 21 numaralı TCP bağlantı noktalarını kullanır. Aktarım olarak TCP kullanan diğer uygulamalar, kural veya biçimsel standartlaşma aracılığıyla başka bir kullanılabilir bağlantı noktası numarası seçebilir.  
  
 Uygulamalar arasında ayrım yapmak için bağlantı noktası numaralarını kullanmak güvenlik sorunlarıyla karşılaştı. Güvenlik duvarları genellikle, birkaç iyi bilinen giriş noktası dışındaki tüm bağlantı noktalarında TCP trafiğini engelleyecek şekilde yapılandırılmıştır. bu nedenle, kurumsal ve kişisel güvenlik duvarlarının varlığı nedeniyle standart olmayan bir bağlantı noktası kullanan bir uygulamanın dağıtımı genellikle karmaşık veya hatta imkansız olur. Zaten izin verilen standart, iyi bilinen bağlantı noktaları üzerinden iletişim kurabilen uygulamalar, dış saldırı yüzeyini azaltır. Birçok ağ uygulaması HTTP protokolünü kullanır, çünkü çoğu güvenlik duvarı varsayılan olarak TCP bağlantı noktası 80 ' de trafiğe izin verecek şekilde yapılandırılır.  
  
 HTTP. Birçok farklı HTTP uygulamasının trafiğinin tek bir TCP bağlantı noktasında çoğullanmış olduğu SYS modeli, Windows platformunda standart hale gelmiştir. Bu, güvenlik duvarı yöneticileri için ortak bir denetim noktası sağlar, böylece uygulama geliştiricilerinin, ağı kullanan yeni uygulamalar oluşturma maliyetini en aza indirmesine izin verir.  
  
 Birden çok HTTP uygulamasında bağlantı noktası paylaşma özelliği, büyük bir Internet Information Services (IIS) özelliğidir. Ancak, yalnızca HTTP 'nin tanıtılmasıyla karşılaşıldı. Bu altyapının tamamen Genelleştirilmiş olduğunu ISS 6,0 ile SYS (çekirdek modu HTTP protokol dinleyicisi). Aslında HTTP. SYS, rastgele kullanıcı işlemlerinin HTTP trafiğine adanmış TCP bağlantı noktalarını paylaşmasına izin verir. Bu özellik, çok sayıda HTTP uygulamasının aynı fiziksel makinede, TCP bağlantı noktası 80 üzerinden trafik göndermek ve almak için gereken ağ altyapısını paylaşırken ayrı, yalıtılmış süreçler üzerinde birlikte bulunmasını sağlar. Net. TCP bağlantı noktası paylaşma hizmeti, net. TCP uygulamaları için aynı bağlantı noktası paylaşımı türünü sunar.  
  
## <a name="port-sharing-architecture"></a>Bağlantı noktası paylaşma mimarisi  
 WCF 'deki bağlantı noktası paylaşma mimarisi üç ana bileşene sahiptir:  
  
- Çalışan Işlemi: net. TCP://üzerinde iletişim kuran tüm işlemler paylaşılan bağlantı noktalarını kullanıyor.  
  
- WCF TCP taşıması: net. TCP://protokolünü uygular.  
  
- Net. TCP bağlantı noktası paylaşma hizmeti: birçok çalışan işleminin aynı TCP bağlantı noktasını paylaşmasına Izin verir.  
  
 Net. TCP bağlantı noktası paylaşım hizmeti, üzerinden bağlanan çalışan süreçler adına net. TCP://bağlantılarını kabul eden bir Kullanıcı modu Windows hizmetidir. Bir yuva bağlantısı geldiğinde, bağlantı noktası Paylaşımı hizmeti gelen ileti akışını inceleyerek hedef adresini elde eder. Bağlantı noktası paylaşım hizmeti, bu adrese göre veri akışını son işleyen uygulamaya yönlendirebilir.  
  
 Net. TCP://bağlantı noktası Paylaşımı kullanan bir WCF hizmeti açıldığında, WCF TCP Aktarım altyapısı uygulama sürecinde doğrudan bir TCP yuvası açmaz. Bunun yerine, taşıma altyapısı, hizmetin temel adres Tekdüzen Kaynak tanımlayıcısı 'nı (URI) net. TCP bağlantı noktası paylaşım hizmeti ile kaydeder ve bağlantı noktası paylaşım hizmeti 'nin adına iletileri dinlemesi için bekler.  Bağlantı noktası paylaşım hizmeti, uygulama hizmetine ulaşan iletileri geldikçe gönderir.  
  
## <a name="installing-port-sharing"></a>Bağlantı noktası Paylaşımı yükleniyor  
 Net. TCP bağlantı noktası paylaşma hizmeti, WinFX 'i destekleyen tüm işletim sistemlerinde kullanılabilir, ancak hizmet varsayılan olarak etkinleştirilmemiştir. Bir güvenlik önlemi olarak, yöneticinin ilk kullanımdan önce net. TCP bağlantı noktası paylaşım hizmetini el ile etkinleştirmesi gerekir. Net. TCP bağlantı noktası paylaşım hizmeti, bağlantı noktası paylaşım hizmeti 'nin sahip olduğu ağ yuvalarının çeşitli özelliklerini değiştirmenize olanak sağlayan yapılandırma seçeneklerini sunar. Daha fazla bilgi için bkz. [nasıl yapılır: net. TCP bağlantı noktası paylaşım hizmetini etkinleştirme](how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Bir uygulamada net. TCP bağlantı noktası paylaşımını kullanma  
 WCF uygulamanızda net. TCP://bağlantı noktası paylaşımını kullanmanın en kolay yolu, kullanarak bir hizmeti kullanıma sunmak <xref:System.ServiceModel.NetTcpBinding> ve sonra özelliği kullanarak net. TCP bağlantı noktası paylaşma hizmetini etkinleştirmek için kullanılır <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> .  
  
 Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF hizmetini bağlantı noktası Paylaşımı kullanmak Için yapılandırma](how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Bağlantı noktası paylaşımının güvenlik etkileri  
 Net. TCP bağlantı noktası paylaşım hizmeti, uygulamalar ve ağ arasında bir işleme katmanı sağlasa da, bağlantı noktası Paylaşımı kullanan uygulamaların yine de ağı dinlemiş gibi güvenli hale getirilmesi gerekir. Özellikle, bağlantı noktası Paylaşımı kullanan uygulamalar çalıştıkları işlem ayrıcalıklarını değerlendirmelidir. Ağ iletişimi için gereken en düşük işlem ayrıcalıkları kümesiyle çalışan yerleşik ağ hizmeti hesabını kullanarak uygulamanızı çalıştırmayı göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](configuring-the-net-tcp-port-sharing-service.md)
- [Hosting](hosting.md)
- [Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir WCF Hizmetini Yapılandırma](how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme](how-to-enable-the-net-tcp-port-sharing-service.md)
