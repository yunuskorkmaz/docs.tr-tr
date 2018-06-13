---
title: Windows İşlem Etkinleştirme Hizmetinde Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 5cd2244c4b44592e436dfd983985dca3c1a50144
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492453"
---
# <a name="hosting-in-windows-process-activation-service"></a>Windows İşlem Etkinleştirme Hizmetinde Barındırma
Windows İşlem Etkinleştirme Hizmeti (WAS) etkinleştirme ve uygulamaları Windows Communication Foundation (WCF) hizmetlerini barındırmak içeren çalışan işlemleri ömrü yönetir. WAS işlem modelini genelleştirir [!INCLUDE[iis601](../../../../includes/iis601-md.md)] işlem modeli HTTP bağımlılığını kaldırarak HTTP sunucusu. Bu, hem HTTP hem de uygulamaları belirli bir makineye çok sayıda konak olanağı sunar ve ileti tabanlı etkinleştirme desteklediğini bir barındırma ortamında Net.TCP gibi HTTP olmayan protokolleri kullanmak WCF hizmetleri sağlar.  
  
 Bir WCF hizmeti oluşturma hakkında daha fazla bilgi WAS barındırma ortamında çalışan için bkz: [nasıl yapılır: bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 WAS işlem modeli uygulamaların, daha sağlam ve daha kolay yönetilebilir ve kaynaklarını verimli bir şekilde kullanan bir biçimde barındırılmasına olanak sağlayan birçok özellik sağlar:  
  
-   İleti tabanlı etkinleştirme, uygulamaların ve çalışan işlem uygulamaları başlatabilir ve yanıt olarak HTTP ve HTTP olmayan protokolleri kullanarak gelmesini gelen iş öğelerini dinamik olarak durdurabilirsiniz.  
  
-   Güçlü uygulama ve çalışan işlem geri dönüştürme çalışan uygulamalar sistem korumak için.  
  
-   Merkezi uygulama yapılandırması ve yönetimi.  
  
-   Uygulamaların dağıtım yüklemesi ayak izinin bir tam IIS gerekmeksizin IIS işlem modelini yararlanmak izin verir.  
  
 WAS özellikler hakkında daha fazla bilgi için bkz: [IIS 7.0 Beta: IIS 7.0 Web yönetimi](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ve barındırma ortamı NET4 WCF ve WF Hizmetleri için zengin bir uygulama sağlamak için Windows İşlem Etkinleştirme Hizmeti (WAS). Bu, işlem yaşam döngüsü yönetimi, işlem geri dönüştürme, paylaşılan barındırma, hızlı hata koruması, işlem alt öğe Yitimi, isteğe bağlı etkinleştirme ve sistem durumu izleme yararları. Ayrıntılı bilgi için bkz: [AppFabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=196494) ve [AppFabric barındırma kavramları](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Model adresleme WAS öğeleri  
 Uygulamaların, yaşam süresi ve yürütme ortamı sunucu tarafından yönetilen kod birimleri Tekdüzen Kaynak Tanımlayıcısı (URI) adresleri vardır. Tek bir WAS sunucu örneği olabilir birçok farklı uygulama giriş. Sunucularını düzenlemek şeklinde adlandırılan gruplara uygulamalara *siteleri*. Bir site içinde uygulamaları hizmet dış adresleri URI'ler yapısını yansıtan hiyerarşik olarak düzenlenir.  
  
 Uygulama adreslerine sahip iki bölümden oluşur: birlikte katıldığında bir uygulama için dış adresini sağlamanız taban URI öneki ve uygulamaya özgü, göreli adresi (yol). Taban URI öneki site bağlamayı oluşturulur ve site altındaki tüm uygulamalar için kullanılır. Uygulama adresleri ardından oluşturulur uygulamaya özgü yol parçaları gerçekleştirerek (gibi "/ applicationOne") ve bunları tam uygulamayı URI ulaşması için temel (örneğin, "net.tcp://localhost") URI öneki sonuna ekleme.  
  
 Aşağıdaki tabloda WAS siteleriyle hem HTTP hem de HTTP olmayan site bağlamaları için birkaç olası adresleme senaryo gösterilmektedir.  
  
|Senaryo|Site bağlamaları|Uygulama yolu|Temel uygulama URI'ler|  
|--------------|-------------------|----------------------|---------------------------|  
|Yalnızca HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|Hem HTTP hem de HTTP olmayan|http: *: 80:\*<br /><br /> NET.TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />NET.TCP://localhost/appTwo/|  
|HTTP olmayan yalnızca|NET.pipe: *|/appThree|NET.pipe://appThree/|  
  
 Hizmet ve kaynakları bir uygulama içinde de çözülebilir. Bir uygulama içinde uygulama kaynakları göre taban uygulama yol ele alınmıştır. Örneğin, bir makine adı contoso.com sitesinde hem HTTP hem de Net.TCP protokoller için site bağlamalarını sahip olduğunu varsayın. Ayrıca site GetOrders.svc bir hizmeti sunan /Billing konumunda bulunan bir uygulama içerdiğini varsayar. GetOrders.svc hizmet SecureEndpoint göreli adresi olan bir uç nokta kullanıma sunulan, daha sonra hizmet uç noktası aşağıdaki iki URI'ler eline:  
  
 http://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
NET.TCP://contoso.com/billing/GetOrders.svc/SecureEndpoint  
  
## <a name="the-was-runtime"></a>WAS çalışma zamanı  
 Uygulamaları siteye adresleme ve yönetim amacıyla düzenlenir. Çalışma zamanında uygulamalar da birlikte uygulama havuzları halinde gruplandırılır. Bir uygulama havuzu birçok farklı sitelerin birçok farklı uygulama barındırabilir. Tüm uygulamalar içindeki bir uygulama havuzu çalışma zamanı özelliklerine genel bir kümesini paylaşır. Örneğin, tümü ortak dil çalışma zamanı (CLR) aynı sürümü altında çalışması ve ortak bir işlem kimliği paylaşır. Her bir uygulama havuzu bir çalışan işleminin (w3wp.exe) bir örneğine karşılık gelir. Paylaşılan uygulama havuzu içinde çalışan her bir yönetilen uygulama CLR AppDomain yoluyla diğer uygulamalardan ayrı tutulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WAS Etkinleştirme Mimarisi](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
