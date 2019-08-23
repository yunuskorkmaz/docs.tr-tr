---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 032be700beaa38ed6c08ed1940aab558b2106591
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964490"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek, barındırma katmanının <xref:System.Web.Routing> ad alanındaki sınıflarla tümleşmesini gösterir. <xref:System.Web.Routing> Ad alanındaki sınıflar, bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'leri kullanmasına izin verir. Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir. Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır. Bu örnek, <xref:System.Web.Routing.RouteTable> Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'ler oluşturmak için sınıfını nasıl kullanacağınızı gösterir. 

> [!NOTE]
> <xref:System.Web.Routing> Ad alanındaki sınıflar yalnızca http üzerinden barındırılan hizmetler için çalışır.  
  
Bu örnek `movies` `channels` , iki RSS akışı oluşturmak için WCF kullanır: bir akış ve akış. Hizmetleri etkinleştirmeye yönelik URL 'ler bir uzantı içermez ve `Application_Start` <xref:System.Web.HttpApplication> sınıfından türetilen `Global` sınıfın yöntemine kaydedilir.  
  
> [!NOTE]
> Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.  

#### <a name="to-download-this-sample"></a>Bu örneği indirmek için
  
Bu örnek bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.  
  
     Örnek için bir dizin listesi görüntülenir. . Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.  
  
3. Adres çubuğunda URL 'ye ekleyin `movies` , böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
4. Adres çubuğunda URL 'ye ekleyin `channels` , böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
5. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
     Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS 'de barındırıldığında bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.  
  
3. Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.  
  
    1. IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.  
  
    2. **Diğer ad**için, yazın `WebRoutingIntegration`.  
  
    3. **Fiziksel yol**için, projenin içindeki hizmet klasörünü seçin.  
  
    4. Tuşuna **Tamam**.  
  
4. Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.  
  
5. Adres çubuğunda URL 'ye ekleyin `movies` , böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
6. Adres çubuğunda URL 'ye ekleyin `channels` , böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
7. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
 Bu örnek, barındırma katmanının http üzerinden barındırılan hizmet isteklerini yönlendirmek için <xref:System.Web.Routing> ad alanındaki sınıflarla birlikte oluşturma yeteneğine sahip olduğunu gösterir.  
  
> [!NOTE]
> Sürüm 2 olarak ayarlandıysa varsayılan uygulama havuzu sürümünü [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] güncelleştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
