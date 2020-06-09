---
title: Windows İşlem Etkinleştirme Hizmetinde Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: d0253202b0fad9a452507ed4296bc4a09b78e569
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597312"
---
# <a name="hosting-in-windows-process-activation-service"></a>Windows İşlem Etkinleştirme Hizmetinde Barındırma
Windows Işlem etkinleştirme hizmeti (WAS), Windows Communication Foundation (WCF) hizmetlerini barındıran uygulamalar içeren çalışan işlemlerinin etkinleştirilmesini ve ömrünü yönetir. WAS işlem modeli http sunucusu için IIS 6,0 işlem modelini genelleştirir ve HTTP 'nin bağımlılığını ortadan kaldırır. Bu, WCF hizmetlerinin, ileti tabanlı etkinleştirmeyi destekleyen bir barındırma ortamında ve belirli bir makinede çok sayıda uygulamayı barındırma olanağı sunan, hem HTTP hem de HTTP olmayan protokolleri (net. TCP gibi) kullanmasına izin verir.  
  
 WAS barındırma ortamında çalışan bir WCF hizmeti oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: BIR WCF hizmetini BARıNDıRMA was](how-to-host-a-wcf-service-in-was.md).  
  
 WAS işlem modeli, uygulamaların daha sağlam, daha yönetilebilir ve kaynakları verimli bir şekilde kullandığı bir şekilde barındırılmasını sağlayan çeşitli özellikler sağlar:  
  
- Uygulamaların ve çalışan işlem uygulamalarının ileti tabanlı etkinleştirilmesi, HTTP ve HTTP olmayan ağ protokollerini kullanan gelen iş öğelerine yanıt olarak başlatılır ve dinamik olarak durdurulur.  
  
- Çalışan uygulamaların sistem durumunu korumak için sağlam uygulama ve çalışan işlemi geri dönüştürülüyor.  
  
- Merkezi uygulama yapılandırması ve yönetimi.  
  
- Uygulamaların, tam bir IIS yüklemesinin dağıtım ayak izine gerek kalmadan IIS işlem modelinden yararlanmasını sağlar.  
[Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) , NET4 WCF ve WF hizmetleri için zengin bir uygulama barındırma ortamı sağlamak üzere IIS 7,0 ve Windows Işlem etkinleştirme HIZMETI (was) ile birlikte çalışarak. Bu avantajlar arasında işlem yaşam döngüsü yönetimi, işlem geri dönüşümü, paylaşılan barındırma, hızlı hata koruması, işlem orphaning, isteğe bağlı etkinleştirme ve sistem durumu izleme sayılabilir. Ayrıntılı bilgi için bkz. [AppFabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) ve [AppFabric barındırma kavramları](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).  
  
## <a name="elements-of-the-was-addressing-model"></a>WAS adresleme modelinin öğeleri  
 Uygulamalar, yaşam süresi ve yürütme ortamı sunucu tarafından yönetilen kod birimleri olan Tekdüzen Kaynak tanımlayıcısı (URI) adresleridir. Tek bir WAS sunucu örneği, birçok farklı uygulamaya giriş yapabilir. Sunucular uygulamaları *siteler*adlı gruplar halinde düzenler. Bir site içinde uygulamalar, dış adresleri olarak görev yapan URI 'lerin yapısını yansıtan hiyerarşik bir şekilde düzenlenir.  
  
 Uygulama adresleri iki bölümden oluşur: bir temel URI öneki ve bir uygulamayla birlikte katıldığında bir uygulama için dış adres sağlayan uygulamaya özgü, göreli bir adres (yol). Temel URI öneki site bağlamalarından oluşturulur ve site altındaki tüm uygulamalar için kullanılır. Uygulama adresleri bundan sonra uygulamaya özel yol parçaları (örneğin, "/applicationOne") alınarak oluşturulur ve bunları, tam uygulama URI 'sine ulaşmak için temel URI ön ekine (örneğin, "net. TCP: TC localhost") ekleyerek oluşturulur.  
  
 Aşağıdaki tabloda, hem HTTP hem de HTTP olmayan site bağlamaları olan WAS siteleri için birkaç olası adresleme senaryosu gösterilmektedir.  
  
|Senaryo|Site bağlamaları|Uygulama yolu|Temel uygulama URI 'Leri|  
|--------------|-------------------|----------------------|---------------------------|  
|Yalnızca HTTP|http: *: 80:\*|/appTwo|`http://localhost/appTwo/`|  
|Hem HTTP hem de HTTP olmayan|http: *: 80:\*<br /><br /> net. TCP: 808:\*|/appTwo|`http://localhost/appTwo/`<br />`net.tcp://localhost/appTwo/`|  
|Yalnızca HTTP olmayan|net. pipe: *|/appThree|`net.pipe://appThree/`|  
  
 Bir uygulama içindeki hizmetler ve kaynaklar da çözülebilir. Bir uygulama içinde uygulama kaynakları, temel uygulama yoluna göre karşılanır. Örneğin, contoso.com makine adındaki bir sitenin, hem HTTP hem de net. TCP protokolleri için site bağlamaları olduğunu varsayalım. Ayrıca, sitenin, GetOrders. svc ' de bir hizmet sunan,/faturalandırma konumunda bulunan bir uygulama içerdiğini varsayın. Daha sonra, GetOrders. svc hizmeti SecureEndpoint 'in göreli adresiyle bir uç nokta açıkalıyorsa, hizmet uç noktası aşağıdaki iki URI 'de gösterilebilir:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS çalışma zamanı  
 Uygulamalar, adresleme ve yönetim amacıyla siteler halinde düzenlenir. Çalışma zamanında uygulamalar da uygulama havuzlarında birlikte gruplandırılır. Bir uygulama havuzu birçok farklı siteden birçok farklı uygulamayı barındırabilir. Bir uygulama havuzu içindeki tüm uygulamalar ortak bir çalışma zamanı özellikleri kümesini paylaşır. Örneğin, hepsi aynı ortak dil çalışma zamanı (CLR) sürümü altında çalışır ve hepsi ortak bir işlem kimliğini paylaşır. Her uygulama havuzu bir çalışan işleminin (W3wp. exe) örneğine karşılık gelir. Paylaşılan bir uygulama havuzu içinde çalışan her yönetilen uygulama, CLR AppDomain 'i aracılığıyla diğer uygulamalardan yalıtılmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WAS Etkinleştirme Mimarisi](was-activation-architecture.md)
- [WAS'ı WCF ile Kullanmak için Yapılandırma](configuring-the-wpa--service-for-use-with-wcf.md)
- [Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma](how-to-install-and-configure-wcf-activation-components.md)
- [Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma](how-to-host-a-wcf-service-in-was.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
