---
title: "WCF Hizmet Yayımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 823edadf7d387d1a509edbdf839ac6eeece5d41f
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2018
---
# <a name="wcf-service-publishing"></a>WCF Hizmet Yayımlama
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet yayımlama yardımcı olur, İleri aşamalara tarafından sağlanan erken geliştirme ortamı'ndan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı ve [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] gerçekten uygulamayı test amacıyla bir üretim ortamında dağıtmak için Test istemcisi. Son dağıtım plana yürütme önce kullanabileceğiniz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] doğrulamak için Yayımlama hizmeti, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet doğru şekilde gerçekleştirir ve yayımlanmaya hazır. Ayrıca dağıtmayı seçebilirsiniz, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet test etmek için çeşitli hedef konumlara kitaplıkları.  
  
## <a name="supported-services-and-target-locations"></a>Desteklenen hizmetler ve hedef konumları  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet yayımlama destekleyen yayımlama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kümesinden oluşturulan Hizmetleri [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplık şablonları ve aşağıdakiler dahil, karşılık gelen öğe şablonları:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Öğe şablonu şablonla hizmet kitaplığı.  
  
-   Dağıtım Hizmeti kitaplığı.  
  
 Bu hizmet şablonları seçerek bulabileceğiniz **dosya** -> **yeni proje** -> **Visual Basic** veya **Visual C#**  ->  **WCF**. (WCF iş akışı hizmeti uygulama ve WCF Hizmeti uygulama dahil) bu konumda diğer WCF şablonları kullanarak yayımlayabileceğiniz [tek tıklatmayla web uygulamaları için yayımlamayı](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx).  
  
 Hizmet aşağıdaki hedef konumlara yayımlanabilir.  
  
-   Yerel IIS.  
  
-   Dosya sistemi.  
  
-   FTP sitesi.  
  
## <a name="using-wcf-service-publishing"></a>WCF kullanarak hizmet yayımlama  
 Bir hizmet uygulaması dağıtmak için aşağıdaki adımları gerçekleştirin:  
  
1.  Yükseltilmiş ayrıcalık ile Visual Studio'yu açın (yürütülebilir dosyayı sağ tıklayın ve başlatmak için "Yönetici olarak çalıştır" kullanın).  Daha sonra "IIS metatabanı ve IIS6 yapılandırma Uyumluluğu" bileşenini kullanarak yüklediğinizden emin olun veya IIS 7.0 kullanıyorsanız "' dönüş Windows özelliklerini aç veya kapat" Denetim Masası'nda.  
  
2.  Bir hizmet projesi'ni açın, **yapı**->**Yayımla \<proje adı >** ana menüden veya'nde projeye sağ **Çözüm Gezgini**tıklatıp **Yayımla**.  
  
3.  **Yayımla** penceresi görüntülenir. Tıklatın **...** . hizmetin dağıtılması hedef konumu belirtmek için düğmesi. Yerel IIS, dosya sistemi veya FTP sitesi için uygulama dağıtmak için seçebilirsiniz. Yerel IIS uygulama dağıtımı, Web sitenizi seçin ve tıklayarak, altında web uygulamanızı oluşturun **yeni Web uygulaması oluştur** sağ üst köşedeki simgesine tıklayın.  
  
4.  Tıklattıktan sonra **Yayımla** ana penceresinde, Visual Studio, belirtilen hedef konuma uygulama dağıtır ve Web.config, .svc ve derleme dosyalarını hedef dizine kopyalar. biçimindeki telefon numarasıdır. .Svc adı "ProjectName.ServiceName.svc" olacaktır. Hizmet başarıyla yayımlandıktan sonra "..."http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName köprü bağlanma" benzer Visual Studio çıktı penceresinde bir etkin bağlantı bulabilirsiniz. CTRL tuşunu BASILI tutun ve hizmet dizin yapısını görüntülemek için Visual Studio içinde tarayıcı sayfasını açmak için bağlantıya tıklayın.  
  
     Siteye göz atın, dizin tarayıcısı IIS'de etkinleştirilmediğinden olabilir. Lütfen etkinleştirmek için "Şeyler deneyebilirsiniz" bölümünde ipuçlarını izleyin. Alternatif olarak, doğrudan yazabileceğiniz"Köprü"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc" hizmet sayfasını görüntülemek için.  
  
 Kullanabileceğiniz **Yayımla** derleme, yapılandırma ve hedef konumuna proje tanımlanan tüm hizmetler için .svc dosyasını kopyalamak isteyip istemediğinizi belirtin ve hedef konumda mevcut dosyaların üzerine yazabilirsiniz.  
  
 Uygulamanızı yerel IIS dağıtmak isterseniz IIS kurulumu için ilgili hatalarla karşılaşabilirsiniz. IIS düzgün yüklendiğinden emin olun. Tarayıcınızda "Köprü"http://localhost"http://localhost" yazın ve IIS varsayılan sayfasını gösteren olup olmadığını denetleyin.  Bazı durumlarda, sorunları da ASP.NET tarafından kaynaklanıyor olabilir veya [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS'de hatalı kayıt. Visual Studio komut istemi açın ve ASP.NET kayıt sorunlarını gidermek için "aspnet_regiis.exe - ir" komutunu çalıştırın veya düzeltme WCF kayıt sorunları için "ServiceModelReg.exe – ia" komutunu çalıştırın.  
  
## <a name="files-generated-for-publishing"></a>Yayımlama için oluşturulan dosyalar  
 Önce bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet Kitaplığı Web barındırılan olabilir, aracı tarafından oluşturulan aşağıdaki dosyaları: derleme dosyalarını, Web.config dosyasında ve .svc dosya. Tüm dosyalar, hedef konuma kopyalanır. Hizmet sonra yayımlanır.  
  
### <a name="assembly-files"></a>Derleme dosyaları  
 Yayımladığınızda bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bu aracı kullanarak hizmet, hizmet otomatik olarak ilk oluşturulur ve derleme dosyalarını oluşturma işleminden sonra hizmet projede oluşturulur.  
  
### <a name="svc-file"></a>. SVC dosyası  
 Yayımlama işlemi *.svc dosyası her biri için oluşturur [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] veya değil, bir sürüm doğruluğundan emin olmak için dosyanın var olup olmadığını hizmet. Svc dosyaları iki farklı tür vardır: biri [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı ve dağıtım hizmeti kitaplığı ve başka bir sıralı ve Durum makinesi iş akışı hizmeti kitaplığı. Oluşturulan \*.svc dosya hedef konumu kök klasörüne kopyalanır.  
  
### <a name="webconfig-file"></a>Web.config dosyası  
 Bir hizmet projesi belirli hedef konuma yayımlanan her seferinde bir Web.config dosyası oluşturulur.  
  
 Oluşturulan Web.config dosyası Web barındırma ve App.config için içeriği için yararlı olan Web bölümleri içerir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aşağıdaki değişiklikleri hizmet kitaplığı:  
  
-   Temel adres dışlandı.  
  
-   Ayarlarında `<diagnostics>` öğesi, hedef platformu izleme ayarlarını korumak için dışlanır.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS WCF hizmetleri HTTP olmayan bağlamaları ile yayımlama  
 Daha sonra yayımlayabilirsiniz veya IIS7.0 kullanıyorsanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS HTTP olmayan bağlamalar hizmetleriyle. Bazı öncesi yapılandırmalar yapmanız gerekir. Daha fazla bilgi için lütfen konuları Bkz [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Güvenlik  
 IIS Yönetici hesabında çalıştıran gerektirdiğinden yayımlama yerel IIS Yönetici ayrıcalığı gerektirir. Yönetici ayrıcalığı olmayan bir kullanıcı açarsa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet yayımlama, IIS bir hedef konum olarak kullanılabilir değil. Dosya sistemi veya FTP sitesi için yayımlama yönetici ayrıcalığı çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
