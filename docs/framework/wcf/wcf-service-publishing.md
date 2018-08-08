---
title: WCF Hizmet Yayımlama
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 258c7e65b69648477e58880f35b100a9378dc9c0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806467"
---
# <a name="wcf-service-publishing"></a>WCF Hizmet Yayımlama
Windows Communication Foundation (WCF) hizmetini yayımlama, İleri aşamalara gerçekte test amacıyla bir üretim ortamında uygulamayı dağıtmak için WCF hizmet ana bilgisayarı ve WCF Test istemcisi tarafından sağlanan erken geliştirme ortamından yardımcı olur. Son dağıtım plana kullanmadan önce Windows Communication Foundation (WCF) hizmetini yayımlama, WCF hizmeti doğru bir şekilde gerçekleştirir ve yayımlanmaya hazır olduğunu doğrulamak için kullanabilirsiniz. Test etmek için çeşitli hedef konumlara WCF Hizmeti Kitaplıklarınızı dağıtmayı seçebilirsiniz.  
  
## <a name="supported-services-and-target-locations"></a>Desteklenen hizmetler ve hedef konumları  
 WCF hizmet yayımlama WCF Hizmeti kitaplık şablonları ve şunlardır bunların karşılık gelen öğe şablonları kümesinden oluşturulan yayımlama WCF hizmetleri destekler:  
  
-   WCF hizmet kitaplığı şablonu öğesi şablonla.  
  
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
  
4.  Tıklattıktan sonra **Yayımla** ana penceresinde, Visual Studio, belirtilen hedef konuma uygulama dağıtır ve Web.config, .svc ve derleme dosyalarını hedef dizine kopyalar. biçimindeki telefon numarasıdır. .Svc adı "ProjectName.ServiceName.svc" olacaktır. Hizmet başarıyla yayımlandıktan sonra "Köprü bağlanma" benzer Visual Studio çıktı penceresinde bir etkin bağlantı bulabilirsinizhttp://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ...". CTRL tuşunu BASILI tutun ve hizmet dizin yapısını görüntülemek için Visual Studio içinde tarayıcı sayfasını açmak için bağlantıya tıklayın.  
  
     Siteye göz atın, dizin tarayıcısı IIS'de etkinleştirilmediğinden olabilir. Lütfen etkinleştirmek için "Şeyler deneyebilirsiniz" bölümünde ipuçlarını izleyin. Alternatif olarak, doğrudan yazabileceğiniz"Köprü"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc"hizmet sayfanızı görüntülemek için.  
  
 Kullanabileceğiniz **Yayımla** derleme, yapılandırma ve hedef konumuna proje tanımlanan tüm hizmetler için .svc dosyasını kopyalamak isteyip istemediğinizi belirtin ve hedef konumda mevcut dosyaların üzerine yazabilirsiniz.  
  
 Uygulamanızı yerel IIS dağıtmak isterseniz IIS kurulumu için ilgili hatalarla karşılaşabilirsiniz. IIS düzgün yüklendiğinden emin olun. "Köprü" yazabilirsinizhttp://localhost" http://localhost", tarayıcı ve onay mi IIS varsayılan sayfa başlanan bir uyarıdır.  Bazı durumlarda sorunlar Ayrıca, IIS'de ASP.NET veya WCF hatalı kayıt kaynaklanıyor olabilir. Visual Studio komut istemi açın ve ASP.NET kayıt sorunlarını gidermek için "aspnet_regiis.exe - ir" komutunu çalıştırın veya düzeltme WCF kayıt sorunları için "ServiceModelReg.exe – ia" komutunu çalıştırın.  
  
## <a name="files-generated-for-publishing"></a>Yayımlama için oluşturulan dosyalar  
 Web barındırılan bir WCF Hizmeti kitaplığı kullanılabilmesi için öncelikle aşağıdaki dosyaları aracı tarafından oluşturulan: derleme dosyalarını, Web.config dosyasında ve .svc dosya. Tüm dosyalar, hedef konuma kopyalanır. Hizmet sonra yayımlanır.  
  
### <a name="assembly-files"></a>Derleme dosyaları  
 Bir WCF Hizmeti yayımladığınızda, bu aracı kullanarak hizmet otomatik olarak ilk oluşturulur ve derleme dosyalarını oluşturma işleminden sonra hizmet projede oluşturulur.  
  
### <a name="svc-file"></a>. SVC dosyası  
 Sürüm doğruluğundan emin olmak için veya değil, dosyanın var olup olmadığını yayımlama işlemi her bir WCF hizmeti için bir *.svc dosyası oluşturur. Svc dosyaları iki farklı tür vardır: bir WCF Hizmeti kitaplık ve dağıtım hizmeti kitaplığı ve başka bir sıralı ve Durum makinesi iş akışı hizmeti kitaplığı. Oluşturulan \*.svc dosya hedef konumu kök klasörüne kopyalanır.  
  
### <a name="webconfig-file"></a>Web.config dosyası  
 Bir hizmet projesi belirli hedef konuma yayımlanan her seferinde bir Web.config dosyası oluşturulur.  
  
 Oluşturulan Web.config dosyası Web barındırma ve App.config içerik WCF Hizmeti kitaplığı aşağıdaki değişiklikleri için yararlı olan Web bölümleri içerir:  
  
-   Temel adres dışlandı.  
  
-   Ayarlarında `<diagnostics>` öğesi, hedef platformu izleme ayarlarını korumak için dışlanır.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS WCF hizmetleri HTTP olmayan bağlamaları ile yayımlama  
 IIS7.0 kullanıyorsanız veya daha sonra IIS HTTP olmayan bağlamalarla WCF hizmetlerine yayımlayabilirsiniz. Bazı öncesi yapılandırmalar yapmanız gerekir. Daha fazla bilgi için lütfen konuları Bkz [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Güvenlik  
 IIS Yönetici hesabında çalıştıran gerektirdiğinden yayımlama yerel IIS Yönetici ayrıcalığı gerektirir. Yönetici ayrıcalığı olmayan bir kullanıcı WCF hizmet yayımlama açılırsa, IIS bir hedef konum olarak kullanılamaz. Dosya sistemi veya FTP sitesi için yayımlama yönetici ayrıcalığı çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
