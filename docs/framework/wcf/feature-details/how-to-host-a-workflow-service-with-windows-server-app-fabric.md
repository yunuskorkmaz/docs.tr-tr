---
title: 'Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: d71052edaccd34bab7354c93431a260f41647f2b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500036"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma
App Fabric içinde iş akışı hizmetlerini barındırma IIS altında barındırmak için benzer / WAS'da. Tek fark, App Fabric dağıtma, izleme ve yönetme iş akışı hizmetleri için sağladığı araçlara olmasıdır. Bu konuda oluşturulan iş akışı hizmeti kullanan [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Bu konu bir iş akışı hizmeti oluşturma işleminde size yol gösterir. Bu konuda, App Fabric kullanarak iş akışı hizmeti barındırma nasıl açıklayacak. Windows Server App Fabric hakkında daha fazla bilgi için bkz: [Windows Server App Fabric belgeleri](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Aşağıdaki adımları tamamlamadan önce Windows Server App Fabric olduğundan emin olun.  Bu açık Internet bilgi hizmetlerini (inetmgr.exe) yapmak için sunucu adınıza tıklayın **bağlantıları** görüntülemek, siteler ve tıklayın **varsayılan Web sitesi**. Ekranın sağ tarafı adlandırılan bir bölüm görmeniz gerekir **App Fabric**. Bu bölümde (sağ bölmenin üst kısmındaki olacaktır) görmüyorsanız, App Fabric yüklü yoktur. Windows Server AppFabric yükleme hakkında daha fazla bilgi için bkz. [yükleme Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Basit bir iş akışı hizmeti oluşturma  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve oluşturduğunuz OrderProcessing çözümü yüklemek [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) konu.  
  
2.  Sağ tıklayın **OrderService** seçin ve proje **özellikleri** seçip **Web** sekmesi.  
  
3.  İçinde **başlatma eylemi** özellik sayfasının bir bölümü seçin **belirli sayfa** Service1.xamlx düzenleme kutusuna yazın.  
  
4.  İçinde **sunucuları** özellik sayfasının bir bölümü seçin **kullanım yerel IIS Web sunucusunda** kullanın ve şu URL'yi yazın: `http://localhost/OrderService`.  
  
5.  Tıklayın **sanal dizin oluştur** düğmesi. Bu, yeni bir sanal dizin oluşturma ve projesi, proje oluşturulduğunda sanal dizin için gerekli dosyaları kopyalamak için ayarlayın.  Alternatif olarak, el ile .xamlx, web.config ve gerekli DLL'lerin sanal dizine kopyalanamadı.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Windows Server AppFabric barındırılan iş akışı hizmeti yapılandırma  
  
1.  Internet Information Services Manager (inetmgr.exe) açın.  
  
2.  OrderService sanal dizinine gidin **bağlantıları** bölmesi.  
  
3.  OrderService sağ tıklatın ve seçin **WCF yönetmek ve WF Hizmetleri**, **Yapılandır...** . **WCF yapılandırma ve uygulama için WF** iletişim kutusu görüntülenir.  
  
4.  Seçin **genel** aşağıdaki ekran görüntüsünde gösterildiği gibi uygulama hakkında genel bilgileri görüntülemek için sekmesinde.  
  
     ![App Fabric yapılandırma iletişim kutusunun Genel sekmesinde](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-genel")  
  
5.  Seçin **izleme** sekmesi. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi çeşitli izleme ayarlarını gösterir.  
  
     ![Uygulama yapılandırma yapı İzleme sekmesini](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration izleme")  
  
     İş akışı hizmeti yapılandırma hakkında daha fazla bilgi için bkz App Fabric izleme [App Fabric ile izlemeyi yapılandırma](https://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Seçin **iş akışı kalıcılığı** sekmesi. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi App Fabric'ın varsayılan Kalıcılık sağlayıcısı kullanmak için uygulamanızı yapılandırma sağlar.  
  
     ![App Fabric yapılandırma &#45; Kalıcılık](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration kalıcılığı")  
  
     Windows Server AppFabric iş akışı kalıcılığını yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma iş akışı kalıcılığı, App Fabric](https://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Seçin **iş akışı konak Yönetimi** sekmesi. Bu boş iş akışı hizmet örneklerine kaldırıldığında ve aşağıdaki ekran görüntüsünde gösterildiği gibi kalıcı olduğunda belirtmenize olanak sağlar.  
  
     ![App Fabric yapılandırma iş akışı konak Yönetimi](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration-Yönetim")  
  
     İş akışı konak yönetimi yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma iş akışı uygulama dokusunda konak Yönetimi](https://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Seçin **otomatik başlatma** sekmesi. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi uygulama iş akışı hizmetleri için otomatik başlangıç ayarlarını belirtmenize olanak sağlar.  
  
     ![App Fabric otomatik&#45;yapılandırma başlatma](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     Otomatik başlatma yapılandırma hakkında daha fazla bilgi için bkz. [otomatik başlatma yapılandırma App Fabric ile](https://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Seçin **azaltma** sekmesi. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi iş akışı hizmeti için daraltma ayarları yapılandırmanıza olanak sağlar.  
  
     ![App Fabric yapılandırma azaltma](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     Azaltmasını yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma azaltma App Fabric ile](https://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Seçin **güvenlik** sekmesi. Bu uygulamanın aşağıdaki ekran görüntüsünde gösterildiği gibi güvenlik ayarlarını yapılandırmanıza olanak sağlar.  
  
     ![App Fabric Güvenlik Yapılandırması](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration-güvenlik")  
  
     Windows Server App Fabric ile güvenlik yapılandırma hakkında daha fazla bilgi için bkz. [App Fabric ile güvenlik yapılandırma](https://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Windows Server AppFabric kullanma  
  
1.  Sanal dizin için gerekli dosyaları kopyalamak için çözümü oluşturun.  
  
2.  OrderClient projeyi sağ tıklatın ve seçin **hata ayıklama**, **yeni örnek Başlat** istemci uygulamayı başlatmak için.  
  
3.  İstemci çalışır ve Visual Studio görüntüler bir **güvenlik uyarısı ekleme** iletişim kutusu, tıklayın **yoksa ekleme** düğmesi. Bu, Visual Studio hata ayıklama için IIS işlemine iliştirme değil bildirir.  
  
4.  İstemci uygulama, hemen iş akışı hizmeti çağırmak ve bekleyin. İş akışı hizmeti, boşta geçilir ve kalıcı. Bu, Internet Information Services (inetmgr.exe) başlangıç OrderService bağlantılar bölmesinde gezinme ve seçerek doğrulayabilirsiniz. Ardından, sağ bölmede App Fabric Pano simgesine tıklayın. Kalıcı WF örnekleri altında aşağıdaki ekran görüntüsünde gösterildiği gibi bir kalıcı iş akışı hizmeti örnek görürsünüz.  
  
     ![Uygulama doku Panosu](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     **WF örneği geçmişi** hataları olan iş akışı örneği sayısını iş akışı hizmeti etkinleştirmelerin sayısı ve iş akışı hizmeti örneği tamamlamaları sayısı gibi iş akışı hizmeti hakkında bilgi listeler. Bir bağlantı görüntülenir etkin veya boş örnekleri altında bağlantıya tıkladığınızda aşağıdaki ekran görüntüsünde gösterildiği gibi boş iş akışı örnekleri hakkında daha fazla bilgi görüntüler.  
  
     ![İş akışı örneği ayrıntıları kalıcı](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Windows Server App Fabric hakkında daha fazla bilgi için özellikleri ve bunları nasıl kullanacağınızı görmek [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=193143)  
 [Windows Server AppFabric yükleme](https://go.microsoft.com/fwlink/?LinkId=193136)  
 [Windows Server App Fabric belgeleri](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
