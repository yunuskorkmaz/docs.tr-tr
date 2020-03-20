---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143960"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek, barındırma katmanının ad alanındaki sınıflarla tümleştirmesini <xref:System.Web.Routing> gösterir. Ad alanındaki <xref:System.Web.Routing> sınıflar, bir uygulamanın fiziksel kaynağa doğrudan karşılık olmayan URL'leri kullanmasına izin verir. Web yönlendirmesi kullanmak, geliştiricinin HTTP için gerçek WCF hizmetlerine eşlenen sanal adresler oluşturmasına olanak tanır. Bu, bir WCF hizmetinin fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya hizmetlere .html veya .aspx gibi dosyalar içermeyen URL'lerle erişilmesi gerektiğinde yararlıdır. Bu örnek, global.asax'ta tanımlanan hizmetleri çalıştırmak için eşharitasını alan sanal URL'ler oluşturmak için sınıfın nasıl kullanılacağını <xref:System.Web.Routing.RouteTable> gösterir.

> [!NOTE]
> <xref:System.Web.Routing> Ad alanındaki sınıflar yalnızca HTTP üzerinden barındırılan hizmetler için çalışır.  
  
Bu örnekte wcf iki RSS akışı `movies` oluşturmak `channels` için kullanır: bir besleme ve bir besleme. Hizmetleri etkinleştirmek için URL'ler bir uzantı içermez `Application_Start` ve `Global` <xref:System.Web.HttpApplication> sınıftan türetilen sınıfın yöntemine kaydedilir.  
  
> [!NOTE]
> Bu örnek yalnızca Internet Information Services (IIS) 7.0 ve sonraki yerlerde çalışır, çünkü IIS 6.0 uzantısız URL'leri desteklemek için farklı bir yöntem kullanır.  

#### <a name="to-download-this-sample"></a>Bu örneği indirmek için
  
Bu örnek bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  

`<InstallDrive>:\WF_WCF_Samples`  

 Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio'yu kullanarak WebRoutingIntegration.sln dosyasını açın.  
  
2. Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 tuşuna basın.  
  
     Örnek için bir dizin listesi görüntülenir. .svc dosya uzantısı olan dosya olmadığını unutmayın.  
  
3. Adres çubuğunda URL'ye ekleyin, `movies` böylece `http://localhost:[port]/movies` okuyup ENTER tuşuna basın.  
  
     Film akışı tarayıcıda görünür.  
  
4. Adres çubuğunda URL'ye ekleyin, `channels` böylece `http://localhost:[port]/channels` okunacak ve ENTER tuşuna basın.  
  
     Kanal akışı tarayıcıda görünür.  
  
5. ALT+F4 tuşuna basarak Web tarayıcısını kapatın.  
  
     Geliştirme sunucusu çıkmamışsa, bildirim alanı simgesine sağ tıklayın ve **Durdur'u**seçin.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS'de barındırıldığında bu örneği kullanmak için  
  
1. Visual Studio'yu kullanarak WebRoutingIntegration.sln dosyasını açın.  
  
2. CTRL+SHIFT+B tuşuna basarak projeyi oluşturun.  
  
3. Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.  
  
    1. IIS Manager'da **Varsayılan Web Sitesi'ni** sağ tıklatın ve **Uygulama Ekle'yi**seçin.  
  
    2. Takma **ad**için , `WebRoutingIntegration`yazın .  
  
    3. Fiziksel **Yol**için, proje içindeki Hizmet klasörünü seçin.  
  
    4. **Tamam**'a basın.  
  
4. Web uygulamasını sağ tıklayarak ve **Uygulamayı Yönet'i** seçerek uygulamayı başlatın ve ardından **Gözat.**  
  
5. Adres çubuğunda URL'ye ekleyin, `movies` böylece `http://localhost:[port]/movies` okunacak ve ENTER tuşuna basın.  
  
     Film akışı tarayıcıda görünür.  
  
6. Adres çubuğunda URL'ye ekleyin, `channels` böylece `http://localhost:[port]/channels` okunacak ve ENTER tuşuna basın.  
  
     Kanal akışı tarayıcıda görünür.  
  
7. ALT+F4 tuşuna basarak Web tarayıcısını kapatın.  
  
 Bu örnek, barındırma katmanının http üzerinden barındırılan <xref:System.Web.Routing> hizmetlerin isteklerini yönlendirmek için ad alanındaki sınıflarla birlikte beste yapabileceğini göstermektedir.  
  
> [!NOTE]
> Sürüm 2 olarak ayarlanmışsa varsayılan uygulama havuzu sürümünü .NET Framework 4 olarak güncelleştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
