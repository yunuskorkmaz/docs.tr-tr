---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 43785f84cb3852a35f1ed3bd555287842455a89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting Tümleştirme Örneği
Bu örnek sınıflar ile barındırma katmanın tümleştirme gösterir <xref:System.Web.Routing> ad alanı. Sınıflarda <xref:System.Web.Routing> ad alanı izin doğrudan fiziksel bir kaynağa karşılık gelmeyen URL'leri kullanmak bir uygulama. Web yönlendirme kullanarak sağlar sonra geri gerçek eşlenen HTTP için sanal adres oluşturmak üzere Geliştirici [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri. Bu, bir WCF Hizmeti gerektirmeden fiziksel dosya veya kaynak barındırılan gerekir ya da hizmetleri .html veya .aspx gibi dosya içermediğini URL'ler ile erişilmesi gerektiğinde kullanışlıdır. Bu örnek nasıl kullanılacağını gösteren <xref:System.Web.Routing.RouteTable> sanal URI'ler global.asax dosyasında tanımlanmış hizmetlerini çalıştırmak için bu harita oluşturmak için sınıfı. 

> [!NOTE]
>  Sınıflarda <xref:System.Web.Routing> ad alanı yalnızca çalışmak için HTTP üzerinden barındırılan hizmetleri.  
  
Bu örnek iki RSS akışları oluşturmak için WCF kullanır: bir `movies` akış ve `channels` akış. Hizmetleri etkinleştirmek için URL'leri bir uzantıyı içermeyen ve kayıtlı `Application_Start` yöntemi `Global` türetilmiş sınıf <xref:System.Web.HttpApplication> sınıfı.  
  
> [!NOTE]
>  Bu örnek yalnızca Internet Information Services (IIS) 7.0 çalışır ve daha sonra IIS 6. 0 ' farklı bir yöntem uzantısız URL'lerin desteklemek için kullanır.  

#### <a name="to-download-this-sample"></a>Bu örnek karşıdan yüklemek için
  
Bu örnek, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Visual Studio kullanarak WebRoutingIntegration.sln dosyasını açın.  
  
2.  Çözümü çalıştırın ve Web geliştirme sunucusu başlatmak için F5 tuşuna basın.  
  
     Bir dizin için örnek listesi görüntülenir. Hiçbir dosya .svc dosya uzantısına sahip olduğuna dikkat edin.  
  
3.  Adres çubuğunda eklemek `movies` URL'si, bu nedenle, BT'nin okur http://localhost:[bağlantı noktası] / filmler ve ENTER tuşuna BASIN.  
  
     Film akış tarayıcısında görüntülenir.  
  
4.  Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost:[bağlantı noktası] / Kanallar ve ENTER tuşuna basın.  
  
     Kanallar akış tarayıcısında görüntülenir.  
  
5.  Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.  
  
     Geliştirme Sunucusu yaptı değil, bildirim alanı simgesini sağ tıklatın ve seçin **durdurmak**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>IIS içinde barındırıldığında Bu örneği kullanmak için  
  
1.  Visual Studio kullanarak WebRoutingIntegration.sln dosyasını açın.  
  
2.  CTRL + SHIFT + B tuşuna basarak projeyi oluşturun.  
  
3.  Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.  
  
    1.  IIS Yöneticisi'nde sağ tıklayın **varsayılan Web sitesi** seçip **bir uygulama eklemek**.  
  
    2.  İçin **diğer**, yazın `WebRoutingIntegration`.  
  
    3.  İçin **fiziksel yolu**, proje içindeki hizmeti klasörünü seçin.  
  
    4.  Press **OK**.  
  
4.  Web uygulaması sağ tıklayıp seçerek uygulamayı başlatmak **yönetmek uygulama** ve ardından **Gözat**.  
  
5.  Adres çubuğunda eklemek `movies` URL'si, bu nedenle olan okuma http://localhost:[bağlantı noktası] / filmler ve ENTER tuşuna BASIN.  
  
     Film akış tarayıcısında görüntülenir.  
  
6.  Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost:[bağlantı noktası] / Kanallar ve ENTER tuşuna basın.  
  
     Kanallar akış tarayıcısında görüntülenir.  
  
7.  Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.  
  
 Bu örnek barındırma katman içindeki sınıflarla oluşturma kapasitesine sahip olduğunu gösteren <xref:System.Web.Routing> HTTP üzerinden barındırılan hizmetleri istekleri yönlendirme için ad alanı.  
  
> [!NOTE]
>  Varsayılan uygulama havuzunu sürüme güncelleştirmelisiniz [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] sürüm 2 ayarlarsanız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
