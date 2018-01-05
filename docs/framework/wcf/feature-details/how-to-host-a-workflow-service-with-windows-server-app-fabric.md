---
title: "Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7af813f7fff422a2513c58c9e3cba6376de060
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma
Uygulama yapıda iş akışı hizmetlerini barındırma benzer IIS altında barındırma / OLUŞTU. Tek fark, dağıtma, izleme ve yönetme iş akışı hizmetleri için App Fabric sağlayan araçlar olmasıdır. Bu konu içinde oluşturulan iş akışı hizmeti kullanan [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Bu konu bir iş akışı hizmeti oluşturmada size yol gösterir. Bu konuda App Fabric kullanarak iş akışı hizmeti barındırma açıklanacaktır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server App Fabric bkz [Windows Server App Fabric belgelerine](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Aşağıdaki adımları gerçekleştirmeden önce Windows Server App Fabric olduğundan emin olun.  Bu açık Internet Information Services (inetmgr.exe) ayarlama yapmak için sunucunuzun adına tıklayın **bağlantıları** görüntülemek, Siteler'i tıklatın ve'ı tıklatın **varsayılan Web sitesi**. Ekranın sağ tarafındaki adlı bir bölüm görmelisiniz **App Fabric**. (Sağ bölmedeki üst kısmında olur) bu bölümü görmüyorsanız, yüklü App Fabric yok. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server App Fabric yükleme bkz [yükleme Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Basit iş akışı hizmeti oluşturma  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve oluşturduğunuz OrderProcessing çözüm yük [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) konu.  
  
2.  Sağ tıklayın **OrderService** proje ve seçin **özellikleri** seçip **Web** sekmesi.  
  
3.  İçinde **eylemi Başlat** özellik sayfasının bölümü seçmek **belirli sayfa** ve Service1.xamlx düzenleme kutusuna yazın.  
  
4.  İçinde **sunucuları** özellik sayfasının bölümü seçmek **kullanım yerel IIS Web sunucusu** ve şu URL'yi yazın: `http://localhost/OrderService`.  
  
5.  Tıklatın **sanal dizin oluştur** düğmesi. Bu, yeni bir sanal dizin oluşturma ve proje yapılandırıldığında sanal dizin için gerekli dosyaları kopyalamak için projesi ayarlayın.  Alternatif olarak, el ile .xamlx, web.config ve gerekli DLL'lerin sanal dizinine kopyalayın.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Windows Server App Fabric içinde barındırılan bir iş akışı hizmeti yapılandırma  
  
1.  Internet Information Services Yöneticisi (inetmgr.exe) açın.  
  
2.  OrderService sanal dizinine gidin **bağlantıları** bölmesi.  
  
3.  OrderService sağ tıklatın ve seçin **yönetmek WCF ve WF Hizmetleri**, **Yapılandır...** . **WCF yapılandırma ve uygulama için WF** iletişim kutusu görüntülenir.  
  
4.  Seçin **genel** sekmesinde aşağıdaki ekran görüntüsünde gösterildiği gibi uygulama hakkında genel bilgileri görüntülemek için.  
  
     ![Uygulama doku yapılandırması iletişim kutusu, Genel sekmesinde](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-genel")  
  
5.  Seçin **izleme** sekmesi. Bu aşağıdaki ekran görüntüsünde gösterildiği gibi çeşitli izleme ayarlarını gösterir.  
  
     ![Uygulama yapılandırma doku İzleme sekmesini](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration izleme")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İş akışı izleme hizmeti uygulama yapıda bkz [App Fabric ile izlemeyi yapılandırma](http://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Seçin **iş akışı kalıcılığı** sekmesi. Bu aşağıdaki ekran görüntüsünde gösterildiği gibi App Fabric'ın varsayılan Kalıcılık sağlayıcısını kullanmak için uygulamanızı yapılandırmanıza olanak sağlar.  
  
     ![Uygulama yapı yapılandırma &#45; Kalıcılığı](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration kalıcılığı")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: Windows Server App Fabric iş akışı kalıcılığı yapılandırma [yapılandırma iş akışı Kalıcılık uygulama yapıda](http://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Seçin **iş akışı ana bilgisayar yönetimi** sekmesi. Boşta iş akışı hizmeti örnekleri kaldırıldı ve gerekir aşağıdaki ekran görüntüsünde gösterildiği gibi kalıcı olduğunda belirtmenizi sağlar.  
  
     ![Uygulama doku yapılandırma iş akışı ana bilgisayar yönetimi](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration Yönetimi")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İş akışı ana bilgisayar yönetimi yapılandırma Bkz: [yapılandırma iş akışı ana yönetiminde App Fabric](http://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Seçin **otomatik başlatma** sekmesi. Bu uygulama aşağıdaki ekran görüntüsünde gösterildiği gibi iş akışı hizmetleri için otomatik başlangıç ayarlarını belirtmenize olanak sağlar.  
  
     ![Uygulama doku otomatik &#45; başlangıç yapılandırması](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Otomatik başlatma bkz [otomatik başlatma yapılandırma App Fabric ile](http://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Seçin **azaltma** sekmesi. Bu aşağıdaki ekran görüntüsünde gösterildiği gibi iş akışı hizmeti daraltma ayarlarını yapılandırmanıza olanak sağlar.  
  
     ![App Fabric kısıtlama Yapılandırması](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Azaltma bkz [yapılandırma azaltma App Fabric ile](http://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Seçin **güvenlik** sekmesi. Bu aşağıdaki ekran görüntüsünde gösterildiği gibi uygulama için güvenlik ayarlarını yapılandırmanıza olanak sağlar.  
  
     ![Uygulama doku Güvenlik Yapılandırması](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration güvenlik")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: Windows Server App Fabric ile güvenlik yapılandırma [App Fabric ile güvenlik yapılandırma](http://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Windows Server App Fabric kullanma  
  
1.  Sanal dizin için gerekli dosyaları kopyalamak için çözümü oluşturun.  
  
2.  OrderClient projeyi sağ tıklatın ve seçin **hata ayıklama**, **Başlat yeni örnek** istemci uygulamasını başlatmak için.  
  
3.  İstemci çalışır ve Visual Studio görüntüler bir **Attach Güvenlik Uyarısı** iletişim kutusu, tıklatın **yok ekleme** düğmesi. Bu hata ayıklama için IIS işlemi iliştirmek değil için Visual Studio bildirir.  
  
4.  İstemci uygulaması iş akışı hizmeti hemen arayın ve ardından bekleyin. İş akışı hizmeti boşta geçilir ve kalıcı. Bu, Internet Information Services (inetmgr.exe) başlangıç OrderService bağlantılar bölmesinde gezinme ve seçerek doğrulayabilirsiniz. Ardından, sağ taraftaki bölmeden uygulama doku Panosu simgesine tıklayın. Kalıcı WF örnekleri altında aşağıdaki ekran görüntüsünde gösterildiği gibi bir kalıcı iş akışı hizmeti örneği olduğunu görürsünüz.  
  
     ![Uygulama doku Panosu](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     **WF örneği geçmişi** iş akışı hizmeti etkinleştirme sayısını, iş akışı hizmeti örneği tamamlamalar sayısı ve iş akışı örneği hatalarıyla sayısı gibi iş akışı hizmeti hakkındaki bilgiler listelenir. Bir bağlantı görüntülenir etkin veya boş örnekleri altında aşağıdaki bağlantıyı tıklatarak aşağıdaki ekran görüntüsünde gösterildiği gibi boş iş akışı örnekleri hakkında daha fazla bilgi görüntüler.  
  
     ![İş akışı örneği ayrıntıları kalıcı](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Özellikleri ve bunların nasıl kullanılacağını Windows Server App Fabric hakkında daha fazla bilgi için bkz [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=193143)  
 [Windows Server App Fabric yükleme](http://go.microsoft.com/fwlink/?LinkId=193136)  
 [Windows Server App Fabric belgeleri](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
