---
title: WCF Hizmet Yayımlama
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 90d2a841fa5ce14b1ad5295b3bb6493df0350339
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321233"
---
# <a name="wcf-service-publishing"></a>WCF Hizmet Yayımlama

Windows Communication Foundation (WCF) hizmeti yayımlama, WCF hizmet ana bilgisayarı ve WCF test Istemcisi tarafından sunulan erken geliştirme ortamından, uygulamayı test amaçlı olarak bir üretim ortamına dağıtmak için ilerleyerek size yardımcı olur. Son bir dağıtım planına işlemeden önce, WCF hizmetinizin doğru şekilde gerçekleştiğini ve yayımlanmaya hazırlanmadığını doğrulamak için Windows Communication Foundation (WCF) hizmet yayımlamayı kullanabilirsiniz. Ayrıca, WCF hizmeti kitaplıklarınızı test için çeşitli hedef konumlara dağıtmayı seçebilirsiniz.

## <a name="supported-services-and-target-locations"></a>Desteklenen hizmetler ve hedef konumlar

WCF hizmeti yayımlama, WCF hizmet kitaplığı şablonları kümesinden oluşturulan WCF hizmetlerinin yayımlanmasını ve aşağıdakiler dahil olmak üzere ilgili öğe şablonlarını destekler:

- Öğe şablonu olan WCF hizmet kitaplığı şablonu.

- Dağıtım Hizmeti kitaplığı.

Bu hizmet şablonlarını **Dosya** > **Yeni proje** > [**Visual Basic** veya **Visual C#** ] > **WCF**' i seçerek bulabilirsiniz. Bu konumdaki diğer WCF şablonları için (WCF Iş akışı hizmeti uygulaması ve WCF hizmeti uygulaması dahil), [Web uygulamaları Için tek tıklamayla yayımlama](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))kullanarak yayımlayabilirsiniz.

Hizmet aşağıdaki hedef konumlara yayımlanabilir.

- Yerel IIS.

- Dosya sistemi.

- FTP sitesi.

## <a name="using-wcf-service-publishing"></a>WCF hizmeti yayımlamayı kullanma

Bir hizmet uygulamasını dağıtmak için aşağıdaki adımları gerçekleştirin:

1. Yükseltilmiş ayrıcalıklarla Visual Studio 'Yu açın (yürütülebilir dosya üzerinde sağ tıklayın ve açmak için **yönetici olarak çalıştır** ' ı seçin).  IIS 7,0 veya sonraki bir sürümü kullanıyorsanız, Denetim Masası 'ndaki "Windows özelliklerini aç veya kapat" seçeneğini kullanarak "IIS metatabanı ve ııS6 yapılandırma uyumluluğu" bileşenini yüklediğinizden emin olun.

2. Bir hizmet projesi açın, ana menüden @no__t **Oluştur**-1 **\<proje adı >** ' nı seçin ya da **Çözüm Gezgini** ' de projeye sağ tıklayıp **Yayımla**' ya tıklayın.

3. **Yayımla** penceresi görüntülenir. **..** . Öğesine tıklayın. düğmesini seçin ve hizmetin dağıtılması gereken hedef konumu belirtin. Uygulamayı yerel IIS, dosya sistemi veya FTP sitesine dağıtmayı seçebilirsiniz. Uygulamayı yerel IIS 'e dağıtıyorsanız, sağ üst köşedeki **Yeni Web uygulaması oluştur** simgesine tıklayarak web sitenizi seçip Web uygulamanızı oluşturabilirsiniz.

4. Ana pencerede **Yayımla** ' yı tıklattıktan sonra, Visual Studio uygulamayı belirtilen hedef konuma dağıtır ve Web. config,. svc ve derleme dosyalarını hedef dizine kopyalar. biçimindeki telefon numarasıdır. . Svc adı "ProjectName. ServiceName. svc" olacaktır. Hizmet başarıyla yayımlandıktan sonra, Visual Studio çıktı penceresinde "`http://localhost/WebApplicationFolderName...` ' a bağlanma" ile benzer bir anında bağlantı bulabilirsiniz. CTRL tuşuna basabilir ve bağlantıya tıklayarak Visual Studio içindeki bir tarayıcı sayfasını açabilirsiniz.

     Siteye gözatamıyorsanız, dizin tarayıcısı IIS 'de etkinleştirilmemiş olabilir. ' İ etkinleştirmek için lütfen "deneyebileceğiniz şeyler" bölümündeki ipuçlarını izleyin. Alternatif olarak, hizmet sayfanızı görüntülemek için `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` ' ı doğrudan yazabilirsiniz.

Projede tanımlanan tüm hizmetlere ait derleme, yapılandırma ve. svc dosyalarını hedef konuma kopyalamak ve hedefteki mevcut dosyaların üzerine yazmak istediğinizi belirtmek için **Yayımla** ' yı kullanabilirsiniz.

Uygulamanızı yerel IIS 'e dağıtmayı seçerseniz, IIS kurulumuyla ilgili hatalarla karşılaşabilirsiniz. Lütfen IIS 'nin düzgün yüklendiğinden emin olun. Tarayıcınızın adres çubuğuna `http://localhost` girebilir ve IIS varsayılan sayfasının görüntülenip görüntülenmeyeceğini kontrol edebilirsiniz. Bazı durumlarda, sorunlar da IIS 'de ASP.NET veya WCF 'nin hatalı kaydının oluşmasına neden olabilir. Visual Studio için Geliştirici Komut İstemi açabilir ve @no__t kayıt sorunlarını gidermek için-0 komutunu çalıştırabilir veya WCF kayıt sorunlarını gidermek için `ServiceModelReg.exe –ia` komutunu çalıştırabilirsiniz.

## <a name="files-generated-for-publishing"></a>Yayımlama için oluşturulan dosyalar
 Bir WCF hizmeti kitaplığının Web 'de barındırılması için aşağıdaki dosyalar araç tarafından oluşturulur: derleme dosyaları, Web. config dosyası ve. svc dosyası. Tüm dosyalar hedef konuma kopyalanır. Hizmet daha sonra yayımlanır.

### <a name="assembly-files"></a>Derleme dosyaları
 Bu aracı kullanarak bir WCF hizmeti yayımladığınızda, önce otomatik olarak oluşturulur ve derleme dosyaları derlemeden sonra hizmet projesinde oluşturulur.

### <a name="svc-file"></a>. SVC dosyası
 Yayımlama işlemi, sürüm geçerliliğini sağlamak için her bir WCF hizmeti için dosyanın var olup olmadığına bakılmaksızın bir *. svc dosyası üretir. İki farklı türde svc dosyası vardır: bir adet WCF hizmet kitaplığı ve dağıtım hizmeti kitaplığı ve sıralı ve durum makinesi Iş akışı hizmet kitaplığı için başka bir tane. Oluşturulan @no__t -0. svc dosyası hedef konumdaki kök klasöre kopyalanır.

### <a name="webconfig-file"></a>Web. config dosyası
 Bir hizmet projesi belirli bir hedef konuma yayımlandığında, Web. config dosyası oluşturulur.

 Oluşturulan Web. config dosyası Web barındırma için yararlı olan Web bölümlerini ve WCF Hizmeti kitaplığı için App. config 'in içeriğini aşağıdaki değişikliklerle içerir:

- Taban adres hariç tutulur.

- @No__t-0 öğesindeki ayarlar, hedef platformun izleme ayarlarını korumak için dışlanır.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>HTTP olmayan bağlamalarla WCF hizmetlerini IIS 'ye yayımlama
 IIS 7.0 veya üzerini kullanıyorsanız, HTTP olmayan bağlamalarla WCF hizmetlerini IIS 'e yayımlayabilirsiniz. Bazı ön yapılandırmalarda yapmanız gerekir. Daha fazla bilgi için lütfen [Windows Işlem etkinleştirme hizmeti 'Nde barındırma](./feature-details/hosting-in-windows-process-activation-service.md)konusunun konularına bakın.

## <a name="security"></a>Güvenlik
 IIS 'in yönetici hesabında çalışıyor olması gerektiğinden, yerel IIS 'de yayımlama için yönetici ayrıcalığı gerekir. Yönetici ayrıcalıkları olmayan bir Kullanıcı WCF hizmeti yayımlamayı açarsa, IIS hedef konum olarak kullanılamaz. Dosya sistemine yayımlama veya FTP sitesi, yönetici ayrıcalıkları olmadan çalışmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Visual Studio Şablonları](wcf-vs-templates.md)
- [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF Test İstemcisi (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
