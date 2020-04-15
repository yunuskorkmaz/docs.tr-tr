---
title: WCF Veri Hizmetleri Geliştirme ve Dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 4591175da5078a194bfe69884701e5432a0c38a3
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389735"
---
# <a name="develop-and-deploy-wcf-data-services"></a>WCF Veri Hizmetleri Geliştirme ve Dağıtma

Bu makalede, WCF Veri Hizmetleri geliştirme ve dağıtma hakkında bilgi verilmektedir. WCF Veri Hizmetleri hakkında daha fazla temel [Overview](wcf-data-services-overview.md)bilgi için [bkz.](getting-started-with-wcf-data-services.md)

## <a name="develop-wcf-data-services"></a>WCF Veri Hizmetleri Geliştirin

Açık Veri Protokolü'nü (OData) destekleyen bir veri hizmeti oluşturmak için WCF Veri Hizmetleri'ni kullandığınızda, geliştirme sırasında aşağıdaki temel görevleri gerçekleştirmeniz gerekir:

1. **Veri modelini tanımlama**

     WCF Veri Hizmetleri, ilişkisel veritabanlarından geç bağlanan veri türlerine kadar çeşitli veri kaynaklarından gelen verilere dayalı bir veri modeli tanımlamanızı sağlayan çeşitli veri hizmeti sağlayıcılarını destekler. Daha fazla bilgi için [Bkz. Veri Hizmetleri Sağlayıcıları.](data-services-providers-wcf-data-services.md)

2. **Veri hizmetini oluşturma**

     En temel veri hizmeti, varlık kapsayıcısının <xref:System.Data.Services.DataService%601> ad alanı nitelikli `T` adı olan bir türle, sınıftan devralan bir sınıfı ortaya çıkarır. Daha fazla bilgi için [WCF Veri Hizmetlerini Tanımlama'ya](defining-wcf-data-services.md)bakın.

3. **Veri hizmetini yapılandırma**

     Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından açığa çıkarılan kaynaklara erişimi devre dışı bırakır. Arabirim, <xref:System.Data.Services.DataServiceConfiguration> kaynaklara ve hizmet işlemlerine erişimi yapılandırmanızı, OData'nın desteklenen sürümünü belirtmenizi ve toplu iş davranışları veya tek bir yanıt akışında döndürülebilecek maksimum varlık sayısı gibi hizmet genelindeki diğer davranışları tanımlamanızı sağlar. Daha fazla bilgi için [bkz.](configuring-the-data-service-wcf-data-services.md)

Bu makale, öncelikle Visual Studio kullanarak veri hizmetlerinin geliştirilmesi ve dağıtımı kapsar. Verilerinizi OData akışları olarak teşhir etmek için WCF Veri Hizmetleri tarafından sağlanan esneklik hakkında bilgi için [WCF Veri Hizmetlerini Tanımlama'ya](defining-wcf-data-services.md)bakın.

### <a name="choose-a-development-web-server"></a>Geliştirme Web Sunucusu Seçin

Visual Studio 2015'i kullanarak bir WCF Veri Hizmeti veya ASP.NET bir web sitesi ASP.NET geliştirdiğinizde, geliştirme sırasında veri hizmetini çalıştırabileceğiniz web sunucuları seçeneğiniz vardır. Aşağıdaki Web sunucuları, yerel bilgisayarda veri hizmetlerinizi test etmeyi ve hata ayıklamayı kolaylaştırmak için Visual Studio ile tümleşir.

1. **Yerel IIS Sunucusu**

     Internet Bilgi Hizmetleri (IIS) üzerinde çalışan ASP.NET bir uygulama veya ASP.NET Web sitesi olan bir veri hizmeti oluşturduğunuzda, yerel bilgisayarda IIS kullanarak veri hizmetinizi geliştirmenizi ve test etmemi öneririz. IIS üzerinde veri hizmetinin çalıştırılması, hata ayıklama sırasında HTTP isteklerinin izlenmesini kolaylaştırır. Bu, IIS tarafından dosyalara, veritabanlarına ve veri hizmeti tarafından gerekli kılınan diğer kaynaklara erişmek için gereken hakları önceden belirlemenizi de sağlar. Veri hizmetinizi IIS'de çalıştırmak için, hem IIS hem de Windows Communication Foundation'ın (WCF) doğru şekilde yüklendiğinden ve yapılandırıldığından emin olun ve dosya sisteminde ve veritabanlarındaki IIS hesaplarına erişim izni verin. Daha fazla bilgi için [bkz: IIS'de çalışan bir WCF Veri Hizmeti geliştirin.](how-to-develop-a-wcf-data-service-running-on-iis.md)

    > [!NOTE]
    > Geliştirme ortamının yerel IIS sunucusunu yapılandırmasını sağlamak için Visual Studio'yu yönetici haklarıyla çalıştırmanız gerekir.

2. **Visual Studio Geliştirme Sunucusu**

     Visual Studio, ASP.NET projeleri için varsayılan Web sunucusu olan yerleşik bir Web sunucusu olan Visual Studio Development Server'ı içerir. Bu Web sunucusu geliştirme sırasında yerel bilgisayarda ASP.NET projeleri çalıştırmak için tasarlanmıştır. [WCF Veri Hizmetleri hızlı başlatış,](quickstart-wcf-data-services.md) Visual Studio Development Server'da çalışan bir veri hizmetinin nasıl oluşturulabildiğini gösterir.

     Veri hizmetini geliştirmek için Visual Studio Development Server'ı kullandığınızda aşağıdaki sınırlamalara dikkat edmelisiniz:

    - Bu sunucuya yalnızca yerel bilgisayar üzerinde erişilebilir.

    - Bu sunucu, `localhost` HTTP iletileri için varsayılan bağlantı noktası olan 80 bağlantı noktasında değil, belirli bir bağlantı noktası üzerinde ve üzerinde dinler. Daha fazla bilgi için, [ASP.NET Web Projeleri için Visual Studio'daki Web Sunucuları'na](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120))bakın.

    - Bu sunucu, geçerli kullanıcı hesabınızın bağlamında veri hizmetini çalıştırır. Örneğin, yönetici düzeyinde bir kullanıcı olarak çalışıyorsanız, Visual Studio Development Server'da çalışan bir veri hizmeti yönetici düzeyinde ayrıcalıklara sahip olur. Bu, veri hizmetinin IIS sunucusuna dağıtıldığında erişim hakkı olmayan kaynaklara erişebilmesini sağlar.

    - Bu sunucu, IIS'nin kimlik doğrulama gibi ek özelliklerini içermez.

    - Bu sunucu, veri hizmetinden büyük ikili verilere erişirken Varsayılan olarak WCF Veri Hizmetleri istemcisi tarafından gönderilen ödenmiş HTTP akışlarını işleyemez. Daha fazla bilgi için [Akış Sağlayıcısı'na](streaming-provider-wcf-data-services.md)bakın.

    - Bu sunucu, bu karakter`.`wcf veri hizmetleri tarafından anahtar değerlerde desteklenmiş olsa da, bir URL'deki dönem ( ) karakterini işleme ile ilgili sorunlar vardır.

    > [!TIP]
    > Geliştirme sırasında veri hizmetlerinizi sınamak için Visual Studio Geliştirme Sunucusu'nu kullanabiliyor olsanız da, IIS çalıştıran bir Web sunucusuna dağıttıktan sonra bunları yeniden test etmeniz gerekir.

3. **Windows Azure Geliştirme Ortamı**

     Visual Studio için Windows Azure Araçları, Visual Studio'da Windows Azure hizmetlerini geliştirmek için tümleşik bir araç kümesi içerir. Bu araçlarla, Microsoft Azure'a dağıtılabilen bir veri hizmeti geliştirebilir ve veri hizmetini dağıtımdan önce yerel bilgisayarda test edebilirsiniz. Windows Azure platformunda çalışan bir veri hizmeti geliştirmek için Visual Studio'yu kullanırken bu araçları kullanın. Araçları yükleme hakkında daha fazla bilgi için [Visual Studio 2015 için Azure araçlarına](../../../azure/sdk/vs2015-install.md)bakın. Windows Azure'da çalışan bir veri hizmeti geliştirme hakkında daha fazla bilgi için Windows [Azure'da Bir Veri Hizmeti Dağıtma](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)yazısına bakın.

### <a name="development-tips"></a>Geliştirme İpuçları

Bir veri hizmeti geliştirirken aşağıdakileri göz önünde bulundurun:

- Kullanıcıların kimliğini doğrulamayı veya belirli kullanıcılar için erişimi kısıtlamayı planlıyorsanız, veri hizmetinizin güvenlik gereksinimlerini belirleyin. Daha fazla bilgi için [WCF Veri Hizmetlerinin Güvenliğini Sağlama'ya](securing-wcf-data-services.md)bakın.

- Bir HTTP denetim programı, istek ve yanıt iletilerinin içeriğini incelemenize olanak sağlayarak bir veri hizmetini hata ayıklarken yararlı olabilir. Veri hizmetine yapılan HTTP isteklerini ve veri hizmetinden alınan yanıtları denetlemek için ham paketleri görüntüleyebilen herhangi bir ağ paketi çözümleyicisi kullanılabilir.

- Bir veri hizmetinin hata ayıklama sırasında, normal çalışma sırasında daha veri hizmeti nden bir hata hakkında daha fazla bilgi almak isteyebilirsiniz. <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> Veri hizmeti sınıfındaki <xref:System.Data.Services.DataServiceConfiguration> öznitelik `true` <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğini <xref:System.ServiceModel.Description.ServiceDebugBehavior> `true`'ye ayarlayarak ve 'ye ayarlayarak veri hizmetinden ek hata bilgileri alabilirsiniz. Daha fazla bilgi için, [WCF Veri Hizmetleri Hata Ayıklama](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services)sonrası bakın. HTTP ileti katmanında toplanan özel durumları görüntülemek için WCF'de izleme yi de etkinleştirebilirsiniz. Daha fazla bilgi için [bkz.](../../wcf/diagnostics/tracing/configuring-tracing.md)

- Bir veri hizmeti genellikle ASP.NET bir uygulama projesi olarak geliştirilmiştir, ancak Visual Studio'da ASP.NET bir Web sitesi projesi olarak da veri hizmeti oluşturabilirsiniz. İki proje türü arasındaki farklar hakkında bilgi için [Visual Studio'da Web Uygulama Projeleri ile Web Sitesi Projeleri'ne](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110))bakın.

- Visual Studio'da **Yeni Öğe Ekle** iletişim kutusunu kullanarak bir veri hizmeti oluşturduğunuzda, veri hizmeti IIS'de ASP.NET tarafından barındırılır. ASP.NET ve IIS bir veri hizmeti için varsayılan ana bilgisayar olsa da, diğer barındırma seçenekleri desteklenir. Daha fazla bilgi için Veri [Hizmetini Barındırma'ya](hosting-the-data-service-wcf-data-services.md)bakın.

## <a name="deploy-wcf-data-services"></a>WCF Veri Hizmetlerini Dağıtma

WCF Veri Hizmeti, veri hizmetini barındıran işlemi seçmede esneklik sağlar. Aşağıdaki platformlara bir veri hizmeti dağıtmak için Visual Studio'yu kullanabilirsiniz:

- **IIS Tarafından Barındırılan Web Sunucusu**

    Bir veri hizmeti ASP.NET projesi olarak geliştirildiğinde, dağıtım işlemleri ASP.NET standart kullanılarak bir IIS Web sunucusuna dağıtılabilir.  Visual Studio, dağıttığınız veri hizmetini barındıran ASP.NET projenin türüne bağlı olarak, ASP.NET için aşağıdaki dağıtım teknolojilerini sağlar.

  - **ASP.NET Web Uygulamaları için Dağıtım Teknolojileri**

    - [Nasıl yapIlir: Visual Studio'da Web Dağıtım Paketi Oluşturma](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Nasıl Yapılır: Visual Studio'da Tek Tıklamayla Yayınla'yı Kullanarak Bir Web Projesi Dağıtma](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **ASP.NET Web Siteleri için Dağıtım Teknolojileri**

    - [Nasıl Yapilir: Web Sitesi Dosyalarını Kopyalama Web Sitesi Aracıyla Kopyalama](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Nasıl Yapılsın: Web Sitelerini Yayımla](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Walkthrough: XCOPY kullanarak ASP.NET bir Web Uygulaması dağıtma](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     ASP.NET bir uygulamanın dağıtım seçenekleri hakkında daha fazla bilgi için [Visual Studio ve ASP.NET için Web Dağıtıma Genel Bakış'a](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110))bakın.

    > [!TIP]
    > Veri hizmetini IIS'ye dağıtmayı denemeden önce, IIS çalıştıran Web sunucusuna dağıtımı test ettiğinizden emin olun. Daha fazla bilgi için [bkz: IIS'de çalışan bir WCF Veri Hizmeti geliştirin.](how-to-develop-a-wcf-data-service-running-on-iis.md)

- **Microsoft Azure**

     Visual Studio için Windows Azure Araçlarını kullanarak bir veri hizmetini Windows Azure'a dağıtabilirsiniz. Visual Studio için Windows Azure Araçlarını [Microsoft Download Center'dan](https://go.microsoft.com/fwlink/?LinkID=201848)indirebilirsiniz. Bir veri hizmetini Windows Azure'a dağıtma hakkında daha fazla bilgi için Windows [Azure'da Bir Veri Hizmeti Dağıtma](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)yazısına bakın.

### <a name="deployment-considerations"></a>Dağıtım Hakkında Önemli Noktalar

Bir veri hizmeti dağıtırken aşağıdakileri göz önünde bulundurun:

- Bir SQL Server veritabanına erişmek için Varlık Çerçevesi sağlayıcısını kullanan bir veri hizmeti dağıttığınızda, veri yapılarını, verileri veya her ikisini de veri hizmeti dağıtımınızla yaymanız gerekebilir. Visual Studio, hedef veritabanında bunu yapmak için otomatik olarak komut dosyaları (.sql dosyaları) oluşturabilir ve bu komut dosyaları ASP.NET bir uygulamanın Web dağıtım paketine eklenebilir. Daha fazla bilgi için [bkz: Web Uygulama Projesi ile Veritabanı dağıtma.](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)) Bir ASP.NET Web sitesi için, Visual **Studio'daki Veritabanı Yayımlama Sihirbazı'nı** kullanarak bunu yapabilirsiniz. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100))

- WCF Veri Hizmetleri temel bir WCF uygulaması içerdiğinden, Windows Server'da çalışan IIS'ye dağıtılan bir veri hizmetini izlemek için Windows Server AppFabric'i kullanabilirsiniz. Bir veri hizmetini izlemek için Windows Server AppFabric'i kullanma hakkında daha fazla bilgi için [Windows Server AppFabric ile WCF Veri Hizmetleri](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric)sonrası izleme adresine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Barındırma](hosting-the-data-service-wcf-data-services.md)
- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
