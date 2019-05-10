---
title: Windows İşlem Etkinleştirme Hizmetinde Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: baa931b64e64c9c2f73ac07424b2cfd1868e725b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613288"
---
# <a name="hosting-in-windows-process-activation-service"></a>Windows İşlem Etkinleştirme Hizmetinde Barındırma
Windows İşlem Etkinleştirme Hizmeti (WAS) etkinleştirme ve uygulamaları Windows Communication Foundation (WCF) hizmetlerini barındırmak içeren çalışan işlemleri yaşam süresini yönetir. WAS işlem modelini genelleştirir [!INCLUDE[iis601](../../../../includes/iis601-md.md)] HTTP sunucusu, HTTP bağımlılığını kaldırarak işlem modeli. Bu, hem HTTP hem de ileti tabanlı etkinleştirme destekleyen ve çok sayıda belirli bir makinede uygulamaları barındırmak için eklenebilir bir barındırma ortamında Net.TCP gibi HTTP olmayan protokolleri kullanmak WCF hizmetleri sağlar.  
  
 Bir WCF hizmeti oluşturma hakkında daha fazla bilgi WAS barındırma ortamında çalışan için bkz: [nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 WAS işlem modeli, uygulamaların daha sağlam, daha kolay yönetilebilir ve kaynakları verimli kullanan bir biçimde barındırılmasına olanak sağlayan birçok özellik sunar:  
  
- İleti tabanlı etkinleştirme uygulamaların ve çalışan işlem uygulamaları başlatabilir ve yanıt olarak HTTP ve HTTP olmayan protokolleri kullanarak gelen gelen iş öğelerini dinamik olarak durdurabilirsiniz.  
  
- Güçlü uygulama ve çalışan işlemi geri dönüştürme çalışan uygulamaların durumunu korumak üzere.  
  
- Merkezi uygulama yapılandırması ve yönetimi.  
  
- Dağıtım ayak izine tam IIS yüklemeye gerek kalmadan IIS işlem modelini yararlanmak uygulamaları sağlar.  
  
 WAS özellikler hakkında daha fazla bilgi için bkz. [IIS 7.0 Beta: IIS 7.0 Web Yönetim](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ve barındırma ortamı ve WF NET4 WCF hizmetleri için zengin bir uygulama sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS). Bu işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem tek bırakma, isteğe bağlı etkinleştirme ve sistem durumu izleme avantajına sahip olur. Ayrıntılı bilgi için bkz. [AppFabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Model adresleme WAS öğeleri  
 Uygulamaları, yaşam süresi ve yürütme ortamı sunucusu tarafından yönetilen kod birimleri Tekdüzen Kaynak Tanımlayıcısı (URI) adreslerine sahiptir. Tek bir WAS sunucu örneği olabilir çok sayıda farklı uygulamaya giriş. Sunucularını düzenlemek uygulamalar olarak adlandırılan gruplara *siteleri*. Bir site içinde uygulamalar, dış adresleri hizmet veren bir URI'leri yapısını gösteren hiyerarşik bir şekilde düzenlenir.  
  
 Uygulama adresine sahip iki bölümden: birlikte katıldığında bir uygulama için dış adresini sağlayan temel bir URI öneki ve uygulamaya özgü, göreli adresi (yol). Taban URI öneki site bağlamayı oluşturulur ve site altındaki tüm uygulamalar için kullanılır. Uygulama adresleri ardından uzamayan uygulamaya özgü yolu parçaları yararlanarak (gibi "/ applicationOne") ve tam URI uygulamayı gelmesi taban URI öneki ("NET.TCP://localhost" gibi) ekleme.  
  
 Aşağıdaki tabloda, hem HTTP hem de HTTP olmayan site bağlamaları WAS siteler için birkaç olası adresleme senaryo gösterilmektedir.  
  
|Senaryo|Site bağlamaları|Uygulama yolu|Temel uygulama URI'ler|  
|--------------|-------------------|----------------------|---------------------------|  
|Yalnızca HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|Hem HTTP hem de HTTP olmayan|http: *: 80:\*<br /><br /> NET.TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />net.tcp://localhost/appTwo/|  
|HTTP olmayan yalnızca|NET.pipe: *|/appThree|NET.pipe://appThree/|  
  
 Hizmet ve uygulama içindeki kaynaklara da çözülebilir. Uygulamanın içinde uygulama kaynaklarını temel uygulama yoluyla göreli ele alınır. Örneğin, bir sitede bir makine adı contoso.com, hem HTTP hem de Net.TCP protokoller için site bağlamaları içerdiğini varsayar. Ayrıca site GetOrders.svc bir hizmeti sunan /Billing konumunda bulunan bir uygulama içerdiğini varsayın. Daha sonra GetOrders.svc hizmeti SecureEndpoint göreli adresi olan bir uç nokta kullanıma sunulan, hizmet uç noktası aşağıdaki iki bir URI'leri sırasında ortaya:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS çalışma zamanı  
 Uygulamaları siteye adresleme ve yönetim amaçları doğrultusunda düzenlenir. Çalışma zamanında uygulamalar da birlikte uygulama havuzları halinde gruplandırılır. Bir uygulama havuzu, birçok farklı uygulama birçok farklı sitelerde barındırmak. Tüm uygulamalar bir uygulama havuzu içindeki ortak çalışma zamanı özelliklerine sahip. Örneğin, hepsi aynı ortak dil çalışma zamanı (CLR) sürümünü altında çalıştırmak ve bunların tümü ortak bir işlem kimliği paylaşın. Her bir uygulama havuzu bir çalışan işlemi (w3wp.exe) örneğine karşılık gelir. İçinde bir paylaşılan uygulama havuzu çalışan her yönetilen uygulamanın bir CLR AppDomain yoluyla diğer uygulamalardan ayrı tutulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WAS Etkinleştirme Mimarisi](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
