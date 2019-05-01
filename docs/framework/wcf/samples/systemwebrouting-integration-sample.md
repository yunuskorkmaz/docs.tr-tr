---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: f4f9772583bbd66d19cc59f453489965aabf74b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007766"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek, sınıflarda barındırma katmanın tümleştirmesiyle gösterir <xref:System.Web.Routing> ad alanı. Sınıflarda <xref:System.Web.Routing> ad alanı, doğrudan fiziksel kaynağa karşılık gelmeyen URL'lerini kullanacak şekilde bir uygulama izin verin. Web yönlendirme kullanarak geri gerçek WCF hizmetleri ardından eşlenen HTTP sanal adresleri oluşturmak Geliştirici sağlar. Bu, bir WCF hizmeti bir fiziksel dosya ya da kaynağa gerek kalmadan barındırılması gerekir veya hizmetleri gibi .html veya .aspx dosyaları içermeyen URL'lerle erişilmesi gerektiğinde kullanışlıdır. Bu örnek nasıl kullanılacağını gösterir <xref:System.Web.Routing.RouteTable> global.asax dosyasında tanımlanmış hizmetleri çalıştırmak için eşlenen sanal bir URI'leri oluşturmak için sınıf. 

> [!NOTE]
>  Sınıflarda <xref:System.Web.Routing> ad alanı yalnızca iş için HTTP üzerinden barındırılan hizmetler.  
  
Bu örnek, iki RSS akışlarını oluşturmak için WCF kullanır: bir `movies` akışı ve `channels` akış. URL'leri, hizmetleri etkinleştirmek için bir uzantı içermiyor ve kayıtlı `Application_Start` yöntemi `Global` türetilmiş sınıf <xref:System.Web.HttpApplication> sınıfı.  
  
> [!NOTE]
>  Bu örnek yalnızca Internet Information Services (IIS) 7.0 çalışır ve daha sonra IIS 6. 0 ' farklı bir yöntem uzantısız URL'lerin desteklemek için kullanır.  

#### <a name="to-download-this-sample"></a>Bu örneği indirmek için
  
Bu örnek, bilgisayarınızda zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio kullanarak, WebRoutingIntegration.sln dosyasını açın.  
  
2. Çözümü çalıştırın ve Web geliştirme sunucusunu başlatmak için F5 tuşuna basın.  
  
     Bir dizin için örnek listesi görüntülenir. Hiçbir dosya .svc dosya uzantısına sahip olduğuna dikkat edin.  
  
3. Adres çubuğuna ekleyin `movies` URL'ye yapılır; bu nedenle BT'nin okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Film akışı tarayıcıda görüntülenir.  
  
4. Adres çubuğuna ekleyin `channels` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanalları akış tarayıcıda görüntülenir.  
  
5. ALT + F4 tuşuna basarak Web tarayıcısını kapatın.  
  
     Geliştirme Sunucusu çıkıldı değil, bildirim alanı simgesine sağ tıklayıp **Durdur**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS içinde barındırıldığında Bu örneği kullanmak için  
  
1. Visual Studio kullanarak, WebRoutingIntegration.sln dosyasını açın.  
  
2. CTRL + SHIFT + B tuşlarına basarak projeyi oluşturun.  
  
3. Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.  
  
    1. IIS Yöneticisi'nde sağ tıklayın **varsayılan Web sitesi** seçip **uygulama ekleme**.  
  
    2. İçin **diğer**, yazın `WebRoutingIntegration`.  
  
    3. İçin **fiziksel yolu**, projenin içinde hizmet klasörü seçin.  
  
    4. Tuşuna **Tamam**.  
  
4. Web uygulaması'nı sağ tıklatıp seçerek, uygulamayı başlatmak **uygulamasını Yönet** ardından **Gözat**.  
  
5. Adres çubuğuna ekleyin `movies` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Film akışı tarayıcıda görüntülenir.  
  
6. Adres çubuğuna ekleyin `channels` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanalları akış tarayıcıda görüntülenir.  
  
7. ALT + F4 tuşuna basarak Web tarayıcısını kapatın.  
  
 Bu örnek, barındırma katman sınıfları ile oluşturma kapasitesine sahip olduğunu gösterir. <xref:System.Web.Routing> istekler HTTP üzerinden barındırılan hizmetlerin yönlendirme için ad alanı.  
  
> [!NOTE]
>  Varsayılan uygulama havuzu sürüme güncelleştirmelisiniz [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] sürüm 2 ayarlarsanız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
