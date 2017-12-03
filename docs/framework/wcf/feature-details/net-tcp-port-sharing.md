---
title: "Net.TCP Bağlantı Noktası Paylaşımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c54ce56cccffa350479d0dd4dcec130ddd004764
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="nettcp-port-sharing"></a>Net.TCP Bağlantı Noktası Paylaşımı
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Yeni bir TCP tabanlı ağ protokolü (net.tcp://) için yüksek performanslı iletişim sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aynı zamanda yeni bir sistem bileşeni olan birden çok kullanıcı işlemleri arasında paylaşılacak net.tcp bağlantı noktalarını etkinleştirir Net.TCP bağlantı noktası Paylaşımı hizmeti sunar.  
  
## <a name="background-and-motivation"></a>Arka plan ve amacı  
 TCP/IP Protokolü ilk olarak kullanılmıştır, yalnızca az sayıda uygulama protokolleri yapılan bunu kullanın. TCP/IP bağlantı noktası numaralarını her uygulama protokolü için bir benzersiz 16 bit bağlantı noktası numarası atayarak uygulamaları birbirinden ayırmak için kullanılır. Örneğin, HTTP trafiği 80 numaralı TCP bağlantı noktasını kullanmak için bugün standartlaştırılmıştır, TCP bağlantı noktası 25 SMTP kullanır ve FTP 20 ve 21 TCP bağlantı noktalarını kullanır. Bir taşıma olarak TCP kullanan diğer uygulamalar, kural tarafından ya da resmi Standartlaştırma üzerinden başka bir kullanılabilir bağlantı noktası numarası seçebilirsiniz.  
  
 Uygulamalar arasında ayrım yapmak için bağlantı noktası numaralarını kullanarak güvenlik sorunlarla karşılaştı. Güvenlik duvarları, genellikle standart olmayan bağlantı noktası kullanan bir uygulama dağıtımı genellikle karmaşık ya da Kurumsal ve kişisel güvenlik duvarları nedeniyle bile olanaksız böylece birkaç iyi bilinen giriş noktaları dışındaki tüm bağlantı noktalarındaki TCP trafiği engellemek için yapılandırılır. Zaten izin verilen standart, iyi bilinen bağlantı noktaları üzerinden iletişim kurabilen uygulamaları dış saldırı yüzeyini azaltın. Birçok ağ uygulamaları HTTP kullanan yapmak çoğu Güvenlik Duvarı varsayılan olarak TCP bağlantı noktası 80 üzerinde trafiğe izin verecek şekilde yapılandırıldığından protokol.  
  
 HTTP. Trafiği birçok farklı HTTP uygulama için tek bir TCP bağlantı noktası üzerinde çoğaltıldı SYS modeli Windows platformunda standart haline gelmiştir. Bu güvenlik duvarı için ortak bir denetim noktası sağlar yapabilirsiniz yeni uygulamaları derleme dağıtım maliyetini en aza indirmek uygulama geliştiricileri verirken Yöneticiler ağı kullanın.  
  
 Birden çok HTTP uygulamalar arasında bağlantı noktalarını paylaşma olanağı uzun bir özellik Internet Information Services (IIS) olmuştur. Ancak, yalnızca HTTP sunulmasıyla idi. SYS (çekirdek modu HTTP protokolü dinleyici) ile [!INCLUDE[iis601](../../../../includes/iis601-md.md)] bu altyapı tam olarak genelleştirilmiş. Aslında, HTTP. SYS TCP bağlantı noktaları HTTP trafiği için ayrılmış paylaşmak isteğe bağlı bir kullanıcı işlemler sağlar. Bu özellik birçok HTTP uygulamalarının ayrı, yalıtılmış işlemlerde aynı fiziksel bilgisayarda TCP bağlantı noktası 80 trafiği alıp göndermek için gereken ağ altyapısı paylaşırken arada olanak sağlar. Net.TCP bağlantı noktası Paylaşımı hizmeti bağlantı noktası paylaşma net.tcp uygulamalar için aynı türde sağlar.  
  
## <a name="port-sharing-architecture"></a>Bağlantı noktası paylaşımı mimarisi  
 Bağlantı noktası paylaşımı mimarisinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] üç ana bileşeni vardır:  
  
-   Bir çalışan işlem: paylaşılan bağlantı noktalarını kullanarak net.tcp:// iletişim herhangi bir işlem.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] TCP taşıma: net.tcp:// protokolünü uygular.  
  
-   Net.TCP bağlantı noktası Paylaşımı hizmeti: aynı TCP bağlantı noktasını paylaşmak çok çalışan işlemi sağlar.  
  
 Net.TCP bağlantı noktası Paylaşımı hizmeti net.tcp:// bağlantıları üzerinden bağlanma çalışan işlemleri adına kabul eden bir kullanıcı modu Windows hizmetidir. Bir yuva bağlantısı geldiğinde hedef adresini almak için gelen ileti akışı Paylaşım Hizmeti bağlantı noktası olup olmadığını denetler. Bu adresi temelinde, hizmet bağlantı noktası veri akışını sonuçta işler uygulamaya yönlendirebilirsiniz.  
  
 Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] açar, net.tcp:// bağlantı noktası kullanan hizmet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] TCP Aktarım altyapısı uygulama işleminde bir TCP yuvasını doğrudan açılmaz. Bunun yerine, aktarım altyapısı Net.TCP bağlantı noktası Paylaşımı hizmeti hizmetin taban adresi Tekdüzen Kaynak Tanımlayıcısı (URI) kaydeder ve iletileri kendi adına dinlemek için hizmet bağlantı noktası bekler.  Hizmet bağlantı noktası geldikçe uygulama hizmetine gönderilen iletiler gönderir.  
  
## <a name="installing-port-sharing"></a>Bağlantı noktası paylaşımı yükleme  
 Net.TCP bağlantı noktası Paylaşımı hizmeti destekleyen tüm işletim sistemlerinde kullanılabilir [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ancak hizmet varsayılan olarak etkin değildir. Bir güvenlik önlemi olarak yönetici Net.TCP bağlantı noktası Paylaşımı hizmeti ilk kullanım önce el ile etkinleştirmeniz gerekir. Net.TCP bağlantı noktası Paylaşımı hizmeti bağlantı noktası Paylaşımı hizmeti tarafından sahip olunan ağ yuva birkaç özelliklerini değiştirmenize izin veren yapılandırma seçenekleri sunar. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: Net.TCP bağlantı noktası hizmetini etkinleştirmek](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>NET.TCP bir uygulamada bağlantı noktası kullanma  
 İçinde net.tcp:// bağlantı noktası kullanmak için en kolay yolu, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamasıdır kullanarak hizmet kullanıma sunmak için <xref:System.ServiceModel.NetTcpBinding> ve ardından Net.TCP bağlantı noktası Paylaşımı hizmeti kullanarak etkinleştirmek için <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bunu yapmak için bkz: nasıl [nasıl yapılır: bir WCF hizmetini kullan bağlantı noktası paylaşımı için yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Bağlantı noktası paylaşımı güvenlik etkileri  
 Net.TCP bağlantı noktası Paylaşımı hizmeti işlemleri uygulamalar ve ağ arasında bir katmanı sağlasa da, ağ üzerinde doğrudan dinleme gibi bağlantı noktası Paylaşımı kullanan uygulamalar yine güvenli hale getirilmelidir. Özellikle, bağlantı noktası Paylaşımı kullanan uygulamalar, altında çalıştığı işlem ayrıcalıkları değerlendirmelisiniz. Ağ iletişimi için gereken işlem ayrıcalıklar en az sayıda ile çalıştırır yerleşik ağ hizmeti hesabını kullanarak uygulamanızı çalıştıran göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Net.TCP bağlantı noktası hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)  
 [Barındırma](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Nasıl yapılır: bağlantı noktası paylaşımı için bir WCF hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)  
 [Nasıl yapılır: Net.TCP bağlantı noktası hizmetini etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
