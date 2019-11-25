---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: def876b13fdc938970e02d63febedf39a240ebac
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141841"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek, barındırma katmanının <xref:System.Web.Routing> ad alanındaki sınıflarla tümleşmesini gösterir. <xref:System.Web.Routing> ad alanındaki sınıflar, bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'Leri kullanmasına izin verir. Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir. Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır. Bu örnek, Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'Ler oluşturmak için <xref:System.Web.Routing.RouteTable> sınıfını nasıl kullanacağınızı gösterir. 

> [!NOTE]
> <xref:System.Web.Routing> ad alanındaki sınıflar yalnızca HTTP üzerinden barındırılan hizmetler için çalışır.  
  
Bu örnek, iki RSS akışı oluşturmak için WCF kullanır: bir `movies` akışı ve `channels` akışı. Hizmetleri etkinleştirmeye yönelik URL 'Ler bir uzantı içermez ve <xref:System.Web.HttpApplication> sınıfından türetilen `Global` sınıfının `Application_Start` metoduna kaydedilir.  
  
> [!NOTE]
> Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.  

#### <a name="to-download-this-sample"></a>Bu örneği indirmek için
  
Bu örnek bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.  
  
     Örnek için bir dizin listesi görüntülenir. . Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.  
  
3. Adres çubuğunda URL 'ye `movies` ekleyin, böylece `http://localhost:[port]/movies` okuyup ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
4. Adres çubuğunda URL 'ye `channels` ekleyin, böylece `http://localhost:[port]/channels` okur ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
5. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
     Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS 'de barındırıldığında bu örneği kullanmak için  
  
1. Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.  
  
2. CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.  
  
3. Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.  
  
    1. IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.  
  
    2. **Diğer ad**için `WebRoutingIntegration`yazın.  
  
    3. **Fiziksel yol**için, projenin içindeki hizmet klasörünü seçin.  
  
    4. **Tamam**'a basın.  
  
4. Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.  
  
5. Adres çubuğunda URL 'ye `movies` ekleyin, böylece `http://localhost:[port]/movies` okur ve ENTER tuşuna basın.  
  
     Filmler akışı tarayıcıda görüntülenir.  
  
6. Adres çubuğunda URL 'ye `channels` ekleyin, böylece `http://localhost:[port]/channels` okur ve ENTER tuşuna basın.  
  
     Kanallar akışı tarayıcıda görüntülenir.  
  
7. ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.  
  
 Bu örnek, barındırma katmanının, HTTP üzerinden barındırılan hizmetlerin isteklerini yönlendirmek için <xref:System.Web.Routing> ad alanındaki sınıflarla oluşturma yeteneğine sahip olduğunu gösterir.  
  
> [!NOTE]
> Sürüm 2 olarak ayarlandıysa, varsayılan uygulama havuzu sürümünü .NET Framework 4 ' e güncelleştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
