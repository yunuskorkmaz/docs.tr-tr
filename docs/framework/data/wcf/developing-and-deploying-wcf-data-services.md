---
title: Geliştirme ve WCF veri hizmetlerini dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: cf1782eaf54701f0cf93576325b3d46e8bc4d3f1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353700"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Geliştirme ve WCF veri hizmetlerini dağıtma

Bu konu, geliştirme ve WCF veri hizmetlerini dağıtma hakkında bilgi sağlar. WCF veri hizmetleri hakkında daha temel bilgiler için bkz: [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) ve [genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>WCF Veri Hizmetleri Geliştirme

WCF veri hizmetleri destekleyen bir veri hizmeti oluşturmak için kullandığınızda [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], geliştirme sırasında aşağıdaki temel görevleri gerçekleştirmeniz gerekir:

1.  **Veri modelini tanımlama**

     WCF Veri Hizmetleri, çeşitli çeşitli ilişkisel veritabanlarından geç bağlanan veri türlerine veri kaynaklarından alınan verileri temel alan bir veri modeli tanımlamanızı sağlayan çeşitli veri hizmeti sağlayıcılarını destekler. Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

2.  **Veri hizmeti oluşturma**

     En temel veri hizmeti devralınan bir sınıfı gösterir <xref:System.Data.Services.DataService%601> türüne sahip bir sınıf `T` varlık kapsayıcısının yani ad alanıyla nitelenen adı. Daha fazla bilgi için [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3.  **Veri hizmetini yapılandırma**

     Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından kullanılan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirimi, kaynaklara erişimi yapılandırma ve hizmet işlemlerine, desteklenen OData sürümü belirtin ve döndürülebilecek varlık davranışları veya en büyük toplu işleme gibi diğer hizmet kapsamındaki davranışları tanımlamanızı sağlar tek bir yanıt akışında. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Bu konu, Visual Studio kullanarak, öncelikli olarak geliştirme ve Veri Hizmetleri dağıtımını kapsar. Verilerinizi OData akışı olarak kullanıma sunmak için WCF Veri Hizmetleri tarafından sağlanan esneklik hakkında daha fazla bilgi için bkz. [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Bir geliştirme Web sunucusu seçin

Olarak WCF veri hizmeti geliştirirken bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio 2015 kullanarak Web sitesi geliştirme sırasında veri hizmetinin çalıştırılacağı Web sunucularını bir seçenek vardır. Aşağıdaki Web sunucuları, test ve hata ayıklama yerel bilgisayarda veri hizmetlerinizin daha kolay hale getirmek için Visual Studio ile tümleştirin.

1.  **Yerel IIS sunucusu**

     Bir veri hizmeti oluşturduğunuzda olduğu bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Internet Information Services (IIS) çalıştıran Web sitesini öneririz geliştirin ve veri hizmetinizi yerel bilgisayarda IIS'yi kullanarak test edin. IIS üzerinde veri hizmetinin çalıştırılması, hata ayıklama sırasında HTTP isteklerinin izlenmesini kolaylaştırır. Bu, IIS tarafından dosyalara, veritabanlarına ve veri hizmeti tarafından gerekli kılınan diğer kaynaklara erişmek için gereken hakları önceden belirlemenizi de sağlar. Veri hizmetinizi IIS üzerinde çalıştırmak için size gereken sağlar hem IIS hem de Windows Communication Foundation (WCF) yüklü ve düzgün yapılandırıldığından emin ve dosya sistemi ve veritabanlarında IIS hesaplarına erişim izin verin. Daha fazla bilgi için [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Visual Studio geliştirme ortamının yerel IIS sunucusunu yapılandırmasını etkinleştirmek için yönetici haklarıyla çalıştırmanız gerekir.

2.  **Visual Studio geliştirme sunucusu**

     Visual Studio içeren yerleşik bir Web sunucusu, Visual Studio geliştirme sunucusu için varsayılan Web sunucu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeleri. Bu Web sunucusu, çalışacak şekilde tasarlanmıştır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştirme sırasında yerel bilgisayarda projeleri. [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) Visual Studio geliştirme sunucusu içinde çalışan bir veri hizmeti oluşturulacağını gösterir.

     Veri hizmeti geliştirmek için Visual Studio geliştirme sunucusu kullanırken aşağıdaki sınırlamaları bilmeniz gerekir:

    -   Bu sunucuya yalnızca yerel bilgisayar üzerinde erişilebilir.

    -   Bu sunucunun dinlediği `localhost` ve belirli bir bağlantı noktası, HTTP iletileri için varsayılan bağlantı noktası olan olmayan bağlantı noktası 80. Daha fazla bilgi için [ASP.NET Web projeleri için Visual Studio'daki Web sunucuları](https://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).

    -   Bu sunucu, geçerli kullanıcı hesabınızın bağlamında veri hizmetini çalıştırır. Örneğin, bir yönetici düzeyinde kullanıcı olarak çalıştırıyorsanız, Visual Studio geliştirme sunucusu içinde çalışan bir veri hizmeti yönetici düzeyinde ayrıcalıkları olacaktır. Bu, veri hizmetinin IIS sunucusuna dağıtıldığında erişim hakkı olmayan kaynaklara erişebilmesini sağlar.

    -   Bu sunucu, IIS'nin kimlik doğrulama gibi ek özelliklerini içermez.

    -   Bu sunucu öbekli HTTP akışlarını işleyemez gönderildiği olması WCF Veri Hizmetleri istemci tarafından varsayılan veri hizmetinden büyük ikili verilere erişilirken. Daha fazla bilgi için [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

    -   Bu sunucu işleme süresi olan sorunlar varsa (`.`) bu karakteri anahtar değerlerinde WCF Veri Hizmetleri tarafından desteklenmesine rağmen URL'de karakter.

    > [!TIP]
    > Geliştirme sırasında veri hizmetlerinizi test etmek için Visual Studio geliştirme sunucusunu kullanıyor olsanız da, IIS çalıştıran Web sunucusuna dağıttıktan sonra test etmeniz gerekir.

3.  **Windows Azure geliştirme ortamı**

     Visual Studio için Windows Azure Araçları, tümleşik bir Visual Studio içinde Windows Azure hizmetleri geliştirmek için araçlar kümesi içerir. Bu araçlarla, Microsoft Azure'a dağıtılabilen bir veri hizmeti geliştirebilir ve veri hizmetini dağıtımdan önce yerel bilgisayarda test edebilirsiniz. Visual Studio Windows Azure platformunda çalışan bir veri hizmeti geliştirmek için kullanırken bu araçları kullanın. Visual Studio için Windows Azure Araçları'nı indirebilirsiniz [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Windows Azure üzerinde çalışan bir veri hizmeti geliştirme hakkında daha fazla bilgi için gönderiye bakın [Windows azure'da OData hizmeti dağıtma](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="development-tips"></a>Geliştirme İpuçları

Bir veri hizmeti geliştirirken, aşağıdakileri dikkate almanız gerekir:

-   Kullanıcıların kimliğini doğrulamayı veya belirli kullanıcılar için erişimi kısıtlamayı planlıyorsanız, veri hizmetinizin güvenlik gereksinimlerini belirleyin. Daha fazla bilgi için [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

-   HTTP inceleme programı, istek ve yanıt iletilerinin içeriğini denetlemenizi sağlayarak veri hizmetinde hata ayıklarken size epey yardımcı olabilir. Veri hizmetine yapılan HTTP isteklerini ve veri hizmetinden alınan yanıtları denetlemek için ham paketleri görüntüleyebilen herhangi bir ağ paketi çözümleyicisi kullanılabilir.

-   Veri hizmetinde hata ayıklarken, veri hizmetinden bir hatayla ilgili olarak normal çalışmaya göre daha fazla bilgi almak isteyebilirsiniz. Ayarlayarak veri hizmetinden ek hata bilgileri alabilirsiniz <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> özelliğinde <xref:System.Data.Services.DataServiceConfiguration> için `true` ayarlayarak <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliği <xref:System.ServiceModel.Description.ServiceDebugBehavior> verihizmetisınıfındakiözniteliği`true`. Daha fazla bilgi için gönderiye bakın [hata ayıklama WCF Veri Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=201868). WCF HTTP ileti katmanında oluşturulan özel durumları görüntülemek için izlemeyi de etkinleştirebilirsiniz. Daha fazla bilgi için [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).

-   Bir veri hizmeti genellikle olarak geliştirilen bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama projesi, ancak da oluşturabilir, veri hizmeti olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio'da Web sitesi projesi. İki proje türü arasındaki farklar hakkında daha fazla bilgi için bkz: [NIB: Web Application Projects versus Web sitesi projeleri Visual Studio'da](https://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).

-   Kullanarak bir veri hizmeti oluşturduğunuzda **Yeni Öğe Ekle** iletişim kutusu Visual Studio'da veri hizmeti tarafından barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS'de. Sırada [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve IIS veri hizmeti için varsayılan ana bilgisayarda, diğer barındırma seçenekleri desteklenir. Daha fazla bilgi için [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>WCF veri hizmetlerini dağıtma

WCF Veri Hizmeti, veri hizmetini barındıran işlemi seçmede esneklik sağlar. Veri hizmetini aşağıdaki platformlara dağıtmak için Visual Studio'yu kullanabilirsiniz:

-   **IIS barındırılan Web sunucusu**

     Ne zaman bir veri hizmeti geliştirilen olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje, bir IIS Web sunucusuna standardını kullanarak dağıtılabileceğini [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıtım işlemleri.  Visual Studio için aşağıdaki dağıtım teknolojileri sağlar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]türüne bağlı olarak, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıttığınız veri hizmetini barındıran bir proje.

    -   **ASP.NET Web uygulamaları için dağıtım teknolojileri**

        -   [Web dağıtım paketi](https://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)

        -   [Tek tıklamayla yayımlama](https://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)

    -   **ASP.NET Web siteleri için dağıtım teknolojileri**

        -   [Web sitesini kopyalama aracı](https://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)

        -   [Web sitesini yayımlama aracı](https://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)

        -   [XCopy](https://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)

     Dağıtım seçenekleri hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulaması, bakın [Visual Studio ve ASP.NET Web dağıtımı genel bakış](https://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).

    > [!TIP]
    > Veri hizmetini IIS'ye dağıtmayı denemeden önce, IIS çalıştıran Web sunucusuna dağıtımı test ettiğinizden emin olun. Daha fazla bilgi için [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

-   **Windows Azure**

     Visual Studio için Windows Azure araçlarını kullanarak bir veri hizmeti Windows Azure'a dağıtabilirsiniz. Visual Studio için Windows Azure Araçları'nı indirebilirsiniz [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Post Windows Azure'a veri hizmetini dağıtma hakkında daha fazla bilgi için bkz. [Windows azure'da OData hizmeti dağıtma](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="deployment-considerations"></a>Dağıtım Hakkında Önemli Noktalar

Bir veri hizmetini dağıtırken, aşağıdakileri dikkate almanız gerekir:

-   Kullanan bir veri hizmeti dağıtırken [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] bir SQL Server veritabanına erişmek için sağlayıcı veri yapılarını, verileri yaymak gerekebilir veya her ikisi de verilerinizi dağıtım hizmet. Visual Studio otomatik olarak hedef veritabanında Bunu yapmak için betikler (.sql dosyaları) oluşturma ve bu betikleri Web Dağıtım paketine dahil edilebilir bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Daha fazla bilgi için [nasıl yapılır: bir veritabanı ile bir Web uygulaması projesi dağıtma](https://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). İçin bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi, bunu yapabilirsiniz kullanarak **Database Publishing Wizard** Visual Studio'da. Daha fazla bilgi için [veritabanı Yayımlama Sihirbazı'nı kullanarak bir veritabanı dağıtma](https://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).

-   WCF Veri Hizmetleri temel bir WCF uygulaması içerdiğinden, Windows Server üzerinde çalışan IIS'ye Dağıtılmış veri hizmetini izlemek için Windows Server Appfabric'i kullanabilirsiniz. Veri hizmetini izlemek için Windows Server AppFabric kullanma hakkında daha fazla bilgi için gönderiye bakın [Windows Server AppFabric ile WCF veri hizmetlerini izleme](https://go.microsoft.com/fwlink/?LinkID=202005).

## <a name="see-also"></a>Ayrıca Bkz.

- [Veri Hizmeti Barındırma](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
