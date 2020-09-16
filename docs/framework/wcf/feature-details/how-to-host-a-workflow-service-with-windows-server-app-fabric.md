---
title: 'Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 2cf77753a0540e75ae6778065f7fa006729f8d6a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555991"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma

Uygulama dokusunda barındırma iş akışı hizmetleri, IIS/WAS altında barındırılmasına benzer. Tek fark, iş akışı hizmetlerini dağıtmak, izlemek ve yönetmek için uygulama dokusunun sağladığı araçlardır. Bu konu, [uzun süre çalışan bir Iş akışı hizmeti oluşturma](creating-a-long-running-workflow-service.md)bölümünde oluşturulan iş akışı hizmetini kullanır. Bu konu, bir iş akışı hizmeti oluşturma işleminde size yol gösterecektir. Bu konu, App Fabric kullanılarak iş akışı hizmetinin nasıl barındıralınacağını açıklar. Windows Server App Fabric hakkında daha fazla bilgi için bkz. [Windows Server App Fabric belgeleri](/previous-versions/appfabric/ff384253(v=azure.10)). Aşağıdaki adımları tamamlamadan önce, Windows Server App Fabric 'in yüklü olduğundan emin olun.  Bunu yapmak için Internet Information Services (inetmgr.exe) açın, **Bağlantılar** görünümündeki sunucu adına tıklayın, siteler ' e tıklayın ve **varsayılan Web sitesi**' ne tıklayın. Ekranın sağ tarafında, **App Fabric**adlı bir bölüm görmeniz gerekir. Bu bölümü görmüyorsanız (Sağ bölmenin üst kısmında olacaktır) App Fabric yüklü değildir. Windows Server App Fabric 'i yükleme hakkında daha fazla bilgi için bkz. [Windows Server App Fabric 'ı yükleme](/previous-versions/appfabric/ee790960(v=azure.10)).  
  
### <a name="creating-a-simple-workflow-service"></a>Basit bir Iş akışı hizmeti oluşturma  
  
1. Visual Studio 2012 ' i açın ve [uzun süre çalışan bir Iş akışı hizmeti oluşturma](creating-a-long-running-workflow-service.md) konusunda oluşturduğunuz OrderProcessing çözümünü yükleyin.  
  
2. **OrderService** projesine sağ tıklayın ve **Özellikler** ' i seçin ve **Web** sekmesini seçin.  
  
3. Özellik sayfasının **başlatma eylemi** bölümünde **belirli sayfa** ' yı seçin ve düzenleme kutusuna Service1. xamlx yazın.  
  
4. Özellik sayfasının **sunucular** bölümünde **yerel IIS Web sunucusu kullan** ' ı SEÇIN ve şu URL 'yi yazın: `http://localhost/OrderService` .  
  
5. **Sanal dizin oluştur** düğmesine tıklayın. Bu, yeni bir sanal dizin oluşturur ve Proje yapılandırıldığında, gerekli dosyaları sanal dizine kopyalamak üzere projeyi ayarlar.  Alternatif olarak,. xamlx, web.config ve gerekli dll 'Leri sanal dizine el ile kopyalayabilirsiniz.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Windows Server App Fabric 'te barındırılan bir Iş akışı hizmetini yapılandırma  
  
1. Internet Information Services Yöneticisi 'Ni açın (inetmgr.exe).  
  
2. **Bağlantılar** bölmesindeki OrderService sanal dizinine gidin.  
  
3. OrderService öğesine sağ tıklayın ve **WCF ve WF Hizmetlerini Yönet**, **Yapılandır..**. seçeneğini belirleyin. **Uygulama IÇIN WCF ve WF yapılandırma** iletişim kutusu görüntülenir.  
  
4. Aşağıdaki ekran görüntüsünde gösterildiği gibi uygulamayla ilgili genel bilgileri göstermek için **genel** sekmesini seçin.  
  
     ![App Fabric yapılandırma iletişim kutusunun Genel sekmesi](media/appfabricconfiguration-general.gif "AppFabricConfiguration-genel")  
  
5. **İzleme** sekmesini seçin. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi çeşitli izleme ayarlarını gösterir.  
  
     ![App Fabric yapılandırma Izleme sekmesi](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-Izleme")  
  
     Uygulama dokusunda iş akışı hizmeti izlemeyi yapılandırma hakkında daha fazla bilgi için bkz. [App Fabric ile Izleme yapılandırma](/previous-versions/appfabric/ee677384(v=azure.10)).  
  
6. **Iş akışı kalıcılığı** sekmesini seçin. Bu, uygulamanızı aşağıdaki ekran görüntüsünde gösterildiği gibi App Fabric 'in varsayılan kalıcılık sağlayıcısını kullanacak şekilde yapılandırmanıza olanak tanır.  
  
     ![App Fabric yapılandırma &#45; kalıcılığı](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-Kalıcılık")  
  
     Windows Server App Fabric 'te iş akışı kalıcılığını yapılandırma hakkında daha fazla bilgi için bkz. [App Fabric 'Te Iş akışı kalıcılığı yapılandırma](/previous-versions/appfabric/ee677353(v=azure.10))  
  
7. **Iş akışı konak yönetimi** sekmesini seçin. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi boştaki iş akışı hizmeti örneklerinin ne zaman kaldırılabileceğini ve kalıcı hale gelmelidir belirtmenizi sağlar.  
  
     ![App Fabric yapılandırma Iş akışı konak yönetimi](media/appfabricconfiguration-management.gif "AppFabricConfiguration-yönetim")  
  
     İş akışı konak Yönetimi yapılandırması hakkında daha fazla bilgi için bkz. [App Fabric 'Te Iş akışı konak yönetimini yapılandırma](/previous-versions/appfabric/ff383424(v=azure.10)).  
  
8. **Otomatik Başlat** sekmesini seçin. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi, uygulamadaki iş akışı hizmetleri için otomatik başlatma ayarları belirtmenize olanak tanır.  
  
     ![App Fabric otomatik&#45;başlangıç yapılandırmasını gösteren ekran görüntüsü.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Otomatik başlatmayı yapılandırma hakkında daha fazla bilgi için bkz. [App Fabric Ile otomatik başlatmayı yapılandırma](/previous-versions/appfabric/ee677261(v=azure.10)).  
  
9. **Daraltma** sekmesini seçin. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi iş akışı hizmeti için azaltma ayarlarını yapılandırmanızı sağlar.  
  
     ![App Fabric azaltma yapılandırmasını gösteren ekran görüntüsü.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Azaltmayı yapılandırma hakkında daha fazla bilgi için bkz. [uygulama dokusuna kısıtlama yapılandırma](/previous-versions/appfabric/ee677261(v=azure.10)).  
  
10. **Güvenlik** sekmesini seçin. Bu, aşağıdaki ekran görüntüsünde gösterildiği gibi uygulamanın güvenlik ayarlarını yapılandırmanızı sağlar.  
  
     ![App Fabric güvenlik yapılandırması](media/appfabricconfiguration-security.gif "AppFabricConfiguration-güvenlik")  
  
     Windows Server App Fabric ile güvenliği yapılandırma hakkında daha fazla bilgi için bkz. [App Fabric Ile güvenliği yapılandırma](/previous-versions/appfabric/ee677278(v=azure.10)).  
  
### <a name="using-windows-server-app-fabric"></a>Windows Server App Fabric kullanma  
  
1. Gerekli dosyaları sanal dizine kopyalamak için çözümü oluşturun.  
  
2. İstemci uygulamasını başlatmak için OrderClient projesine sağ tıklayın ve **Hata Ayıkla**, **Yeni örnek Başlat** ' ı seçin.  
  
3. İstemci çalışacaktır ve Visual Studio, bir **güvenlik uyarısı Ekle** iletişim kutusunu görüntüleyecektir, **Ekle** düğmesine tıklayın. Bu, Visual Studio 'Nun hata ayıklama için IIS işlemine iliştirmeyeceğini söyler.  
  
4. İstemci uygulaması, Iş akışı hizmetini anında çağırır ve sonra bekler. İş akışı hizmeti boşta kalacak ve kalıcı olacak. Bunu Internet Information Services (inetmgr.exe) başlatarak, Bağlantılar bölmesinde OrderService 'e giderek ve onu seçerek doğrulayabilirsiniz. Sonra sağ bölmedeki App Fabric panosu simgesine tıklayın. Kalıcı WF Örnekleri altında, aşağıdaki ekran görüntüsünde gösterildiği gibi kalıcı bir iş akışı hizmeti örneği olduğunu görürsünüz.  
  
     ![App Fabric panosunu gösteren ekran görüntüsü.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **WF Örnek Geçmişi** , iş akışı hizmeti etkinleştirmeleri, iş akışı hizmeti örneği sayısı ve hatalara sahip iş akışı örneği sayısı gibi bilgileri listeler. Etkin veya boşta olan örneklerde bir bağlantı görüntülenir, bağlantıya tıkladığınızda aşağıdaki ekran görüntüsünde gösterildiği gibi boş iş akışı örnekleri hakkında daha fazla bilgi görüntülenir.  
  
     ![Kalıcı Iş akışı örneği ayrıntılarını gösteren ekran görüntüsü.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Windows Server App Fabric özellikleri ve bunların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](creating-a-long-running-workflow-service.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
- [Windows Server uygulama dokusunu yükleme](/previous-versions/appfabric/ee790960(v=azure.10))
- [Windows Server App Fabric belgeleri](/previous-versions/appfabric/ff384253(v=azure.10))
