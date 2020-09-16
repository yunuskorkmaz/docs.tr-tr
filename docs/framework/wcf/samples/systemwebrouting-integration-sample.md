---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 58d720f164c4c35f3de4c282e9aa983d11e4040b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555230"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek, barındırma katmanının ad alanındaki sınıflarla tümleşmesini gösterir <xref:System.Web.Routing> . Ad alanındaki sınıflar, <xref:System.Web.Routing> bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'leri kullanmasına izin verir. Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir. Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır. Bu örnek, <xref:System.Web.Routing.RouteTable> Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'ler oluşturmak için sınıfını nasıl kullanacağınızı gösterir.

> [!NOTE]
> <xref:System.Web.Routing>Ad alanındaki sınıflar yalnızca http üzerinden barındırılan hizmetler için çalışır.  
  
Bu örnek, iki RSS akışı oluşturmak için WCF kullanır: bir `movies` akış ve `channels` akış. Hizmetleri etkinleştirmeye yönelik URL 'Ler bir uzantı içermez ve `Application_Start` `Global` sınıfından türetilen sınıfın yöntemine kaydedilir <xref:System.Web.HttpApplication> .  
  
> [!NOTE]
> Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.  

#### <a name="to-download-this-sample"></a>Bu örneği indirmek için
  
Bu örnek bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  

`<InstallDrive>:\WF_WCF_Samples`  

 Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.  
  
     Örnek için bir dizin listesi görüntülenir. . Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.  
  
3. Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
4. Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
5. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
     Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS 'de barındırıldığında bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.  
  
3. Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.  
  
    1. IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.  
  
    2. **Diğer ad**için, yazın `WebRoutingIntegration` .  
  
    3. **Fiziksel yol**için, projenin içindeki hizmet klasörünü seçin.  
  
    4. **Tamam**'a basın.  
  
4. Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.  
  
5. Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
6. Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
7. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
 Bu örnek, barındırma katmanının <xref:System.Web.Routing> http üzerinden barındırılan hizmet isteklerini yönlendirmek için ad alanındaki sınıflarla birlikte oluşturma yeteneğine sahip olduğunu gösterir.  
  
> [!NOTE]
> Sürüm 2 olarak ayarlandıysa, varsayılan uygulama havuzu sürümünü .NET Framework 4 ' e güncelleştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))
