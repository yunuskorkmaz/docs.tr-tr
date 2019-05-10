---
title: WCF Hizmet Yayımlama
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: f10aabd2a2258f98915f1bbcc8b30fc1b7f677ac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654577"
---
# <a name="wcf-service-publishing"></a>WCF Hizmet Yayımlama

Windows Communication Foundation (WCF) hizmet yayımlama, aslında bir üretim ortamında test amacıyla uygulamayı dağıtmak için WCF hizmet konağı ve WCF Test istemcisi tarafından sağlanan erken geliştirme ortamından ilerlediğini yardımcı olur. Son dağıtım planına göndermeden önce Windows Communication Foundation (WCF) hizmet yayımlama, WCF hizmeti doğru bir şekilde gerçekleştirir ve yayımlanmaya hazır olduğunu doğrulamak için kullanabilirsiniz. Ayrıca test etmek için çeşitli hedef konumlara WCF Hizmeti Kitaplıklarınızı dağıtmayı tercih edebilirsiniz.

## <a name="supported-services-and-target-locations"></a>Desteklenen hizmetler ve hedef konumları

WCF hizmet yayımlama dizi WCF hizmet kitaplığı şablonları ve aşağıdakileri içerir, karşılık gelen öğe şablonları, oluşturulan yayımlama WCF hizmetleri destekler:

- Öğe şablonu ile WCF hizmet kitaplığı şablonu.

- Dağıtım hizmet kitaplığı.

Bu hizmet şablonlarını seçerek bulabilirsiniz **dosya** > **yeni proje** > [**Visual Basic** veya **Visual C#** ] > **WCF**. Diğer (WCF iş akışı hizmeti uygulaması ve WCF hizmeti uygulaması gibi) bu konumda WCF şablonları için kullanarak yayımlayabileceğiniz [tek tıklamayla web uygulamaları için yayımlamayı](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110)).

Hizmet aşağıdaki hedef konumlara yayımlanabilir.

- Yerel IIS.

- Dosya sistemi.

- FTP sitesi.

## <a name="using-wcf-service-publishing"></a>Kullanarak WCF hizmet yayımlama

Bir hizmet uygulaması dağıtmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio yükseltilmiş ayrıcalıklarla açın (yürütülebilir dosyaya sağ tıklayıp seçin **yönetici olarak çalıştır** açmak için).  IIS 7.0 kullanıyorsanız veya daha sonra emin olun, Denetim Masası'ndaki "Turn Windows özelliklerini aç veya kapat" kullanarak "IIS metatabanı ve IIS6 yapılandırma Uyumluluğu" bileşeni yüklediniz.

2. Bir hizmet projesi açın, **derleme** > **Yayımla \<proje adı >** ana menüden veya projeye sağ **Çözüm Gezgini**tıklatıp **Yayımla**.

3. **Yayımla** penceresi görüntülenir. Tıklayın **...** . hizmet için dağıtılması hedef konumu belirtmek için düğmesi. Yerel IIS, dosya sistemi veya FTP sitesi için uygulamayı dağıtmayı seçebilirsiniz. Yerel IIS uygulama dağıtımı, Web sitenizi seçin ve tıklayarak altında web uygulamanızı oluşturma **yeni Web uygulaması oluştur** simgesini sağ üst köşedeki.

4. Tıkladıktan sonra **Yayımla** ana penceresinde, Visual Studio, belirtilen hedef konum uygulamayı dağıtır ve Web.config .svc ve derleme dosyaları hedef dizine kopyalar. biçimindeki telefon numarasıdır. .Svc adını "ProjectName.ServiceName.svc" olacaktır. Hizmet başarıyla yayımlandıktan sonra şuna benzer şekilde Visual Studio çıktı penceresinde bir etkin bağlantı bulabilirsiniz "bağlanma `http://localhost/WebApplicationFolderName...`". CTRL tuşunu BASILI tutun ve hizmet dizin yapısını görüntülemek için Visual Studio içindeki bir tarayıcı sayfasını açmak için bağlantıya tıklayın.

     Siteye göz atın, IIS'de directory tarayıcı etkin olmadığından olabilir. Lütfen etkinleştirmek için "Şeyler deneyebilirsiniz" bölümünde ipuçlarını izleyin. Alternatif olarak, doğrudan yazmanız `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` hizmet sayfanızı görüntülemek için.

Kullanabileceğiniz **Yayımla** derleme, yapılandırma ve hedef konum projede tanımlanan tüm hizmetleri .svc dosya kopyalamak isteyip istemediğinizi belirtin ve hedef konumda var olan dosyaların üzerine yaz.

Yerel IIS uygulamanızı dağıtmayı tercih ederseniz, IIS kurulumuyla ilgili hatalarla karşılaşabilirsiniz. IIS düzgün yüklendiğinden emin olun. Girdiğiniz `http://localhost` tarayıcınızın adres çubuğuna ve onay mı IIS varsayılan sayfasını görüntüler. Bazı durumlarda sorunlar yanlış kayıt ASP.NET veya IIS WCF tarafından da kaynaklanabilir. Visual Studio için geliştirici komut istemi açın ve şu komutu çalıştırın `aspnet_regiis.exe -ir` ASP.NET kayıt sorunları düzeltin veya komutu çalıştırmak için `ServiceModelReg.exe –ia` WCF kayıt sorunlarını gidermek için.

## <a name="files-generated-for-publishing"></a>Yayımlama için oluşturulan dosyalar
 Bir WCF hizmet Kitaplığı Web barındırılan kullanılabilmesi için öncelikle aşağıdaki dosyaları araç tarafından oluşturulan: derleme dosyalarını ve Web.config dosyasını .svc dosya. Tüm dosyalar hedef konuma kopyalanır. Hizmet ardından yayımlanır.

### <a name="assembly-files"></a>Derleme dosyaları
 Bir WCF Hizmeti yayımladığınızda, bu aracı kullanarak hizmet önce otomatik olarak oluşturulur ve derleme dosyalarını service projesinde derlemeden sonra oluşturulur.

### <a name="svc-file"></a>. SVC dosyası
 Veya, bir sürüm doğruluğundan emin olmak için dosyanın var olup olmadığını yayımlama işlemi her bir WCF hizmeti için bir *.svc dosyası oluşturur. Svc dosyaları farklı iki çeşit vardır: bir WCF hizmet kitaplığı ve dağıtım hizmeti kitaplığı ve başka bir sıralı ve Durum makinesi iş akışı hizmet kitaplığı. Oluşturulan \*.svc dosyasını, hedef konum kök klasörüne kopyalanır.

### <a name="webconfig-file"></a>Web.config File
 Belirli hedef konuma, her bir hizmet projesi yayımlandığında bir Web.config dosyası oluşturulur.

 Oluşturulan Web.config dosyası Web barındırma ve App.config içeriğini aşağıdaki değişikliklerle birlikte WCF hizmet kitaplığı için faydalı olan Web bölümleri içerir:

- Taban adresi çıkarılır.

- Ayarlarında `<diagnostics>` öğesi, hedef platform izleme ayarlarını korumak için dışlanır.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS WCF hizmetleri HTTP olmayan bağlamaları ile yayımlama
 IIS7.0 kullanıyorsanız veya daha sonra HTTP olmayan IIS bağlamaları ile WCF hizmetlerine yayımlayabilirsiniz. Bazı öncesi yapılandırmalar yapmanız gerekir. Daha fazla bilgi için lütfen konuları bakın [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Güvenlik
 IIS Yönetici hesabında çalıştırılmasına gerektirdiğinden yayımlama yerel IIS Yöneticisi ayrıcalığı gerektirir. IIS Yöneticisi ayrıcalığı olmayan bir kullanıcı WCF hizmet yayımlama açılırsa, bir hedef konum olarak kullanılabilir değil. Dosya sistemi veya FTP sitesi yayımlama yönetici ayrıcalığı çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Visual Studio Şablonları](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)