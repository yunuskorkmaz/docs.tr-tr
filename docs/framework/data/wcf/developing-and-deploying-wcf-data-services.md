---
title: "Geliştirme ve WCF Veri Hizmetleri dağıtma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8abe23aebefadc68268aa1dada8474336b1f87e7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="developing-and-deploying-wcf-data-services"></a>Geliştirme ve WCF Veri Hizmetleri dağıtma
Bu konuda geliştirme ve dağıtma hakkında bilgi verilmektedir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Hakkında daha fazla temel bilgiler için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bkz: [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) ve [genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## <a name="developing-wcf-data-services"></a>WCF Veri Hizmetleri Geliştirme  
 Kullandığınızda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] destekleyen bir veri hizmeti oluşturmak için [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], geliştirme sırasında aşağıdaki temel görevleri gerçekleştirmeniz gerekir:  
  
1.  **Veri modelini tanımlar**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]geç bağlama veri türleri için ilişkisel veritabanlarından veri kaynakları çeşitli dayalı bir veri modeli tanımlamanıza olanak sağlayan veri hizmeti sağlayıcıları, çeşitli destekler. Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Veri hizmeti oluşturma**  
  
     Öğesinden devralınan bir sınıf en temel veri hizmeti sunan <xref:System.Data.Services.DataService%601> sınıfının bir türü `T` olan ad alanı tam varlık kapsayıcısının adı. Daha fazla bilgi için bkz: [tanımlayan WCF Veri Hizmetleri](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Veri Hizmeti yapılandırma**  
  
     Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık kapsayıcısı tarafından sunulan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirimi kaynaklarına erişimi yapılandırmak ve işlemleri hizmet, desteklenen bir sürümü olanak tanır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]ve davranışları veya yapabilirsiniz varlıkların sayısı toplu işleme gibi diğer hizmet geneli davranışları tanımlamak için Akış tek bir yanıtta döndürülen. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Bu konu öncelikle geliştirme ve Veri Hizmetleri dağıtımını kullanarak kapsar [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Tarafından sağlanan esneklik hakkında bilgi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verilerinizi olarak gösterme için [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışlarını bkz [tanımlayan WCF Veri Hizmetleri](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### <a name="choosing-a-development-web-server"></a>Geliştirme Web Sunucusu Seçme  
 WCF veri hizmeti olarak geliştirirken bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kullanarak Web sitesi [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], geliştirme sırasında veri hizmeti çalıştırmak için Web sunucularında seçmesini. Aşağıdaki Web sunucularından tümleştirileceğini [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] test ve hata ayıklama veri hizmetlerinizi yerel bilgisayarda daha kolay hale getirmek için.  
  
1.  **Yerel IIS sunucusu**  
  
     Veri Hizmeti oluşturduğunuzda olan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Internet Information Services (IIS) çalıştıran Web sitesini öneririz geliştirmek ve veri hizmeti yerel bilgisayarda IIS kullanarak test. IIS üzerinde veri hizmetinin çalıştırılması, hata ayıklama sırasında HTTP isteklerinin izlenmesini kolaylaştırır. Bu, IIS tarafından dosyalara, veritabanlarına ve veri hizmeti tarafından gerekli kılınan diğer kaynaklara erişmek için gereken hakları önceden belirlemenizi de sağlar. Veri Hizmeti IIS üzerinde çalıştırmak için size gereken emin olur hem IIS ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yüklü ve doğru şekilde yapılandırıldığını ve dosya sistemi ve veritabanlarında IIS hesaplarına erişim vermek. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Çalıştırmalısınız [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] yerel IIS sunucusunu yapılandırmak geliştirme ortamı sağlamak için yönetici haklarına sahip.  
  
2.  **Visual Studio geliştirme sunucusu**  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Yerleşik bir Web sunucusu içeren [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] varsayılan Web sunucusu geliştirme sunucusu için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeleri. Bu Web sunucusu çalışmak üzere tasarlanmıştır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeleri geliştirme sırasında yerel bilgisayarda. [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) çalışan veri hizmeti oluşturmayı gösteren [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] geliştirme sunucusu.  
  
     Kullanırken aşağıdaki sınırlamaları bilmeniz gereken [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] veri hizmeti geliştirmek için geliştirme sunucusu:  
  
    -   Bu sunucuya yalnızca yerel bilgisayar üzerinde erişilebilir.  
  
    -   Bu sunucunun dinlediği `localhost` ve belirli bir bağlantı noktası, HTTP iletileri için varsayılan bağlantı noktası olan olmayan bağlantı noktası 80. Daha fazla bilgi için bkz: [ASP.NET Web projeleri için Visual Studio'da Web sunucuları](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Bu sunucu, geçerli kullanıcı hesabınızın bağlamında veri hizmetini çalıştırır. Örneğin, bir yönetici düzeyi kullanıcı olarak çalışan bir veri Hizmeti çalışıyorsa [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Development Server yönetici ayrıcalıklarına sahip olacaktır. Bu, veri hizmetinin IIS sunucusuna dağıtıldığında erişim hakkı olmayan kaynaklara erişebilmesini sağlar.  
  
    -   Bu sunucu, IIS'nin kimlik doğrulama gibi ek özelliklerini içermez.  
  
    -   Bu sunucu öbekli HTTP işleyemiyor gönderilen akışları olması varsayılan olarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] büyük ikili veri veri hizmetinden erişirken istemci. Daha fazla bilgi için bkz: [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Bu sunucu işleme süresi ile sorunları vardır (`.`) rağmen bu karakteri tarafından desteklenen bir URL'de karakter [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] anahtar değerleri.  
  
    > [!TIP]
    >  Kullanabileceğiniz olsa bile [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] verilerinizi test etmek için geliştirme sunucusu Hizmetleri geliştirme sırasında IIS çalıştıran bir Web sunucusu dağıttıktan sonra sınamalısınız.  
  
3.  **Windows Azure geliştirme ortamı**  
  
     Windows Azure Araçları için [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] tümleşik birtakım Microsoft Azure hizmetlerini geliştirmek için Araçlar içerir [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Bu araçlarla, Microsoft Azure'a dağıtılabilen bir veri hizmeti geliştirebilir ve veri hizmetini dağıtımdan önce yerel bilgisayarda test edebilirsiniz. Kullanırken bu araçları [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Windows Azure platformunda çalışan veri hizmeti geliştirmek için. Windows Azure Araçları için indirebilirsiniz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] gelen [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Azure üzerinde çalışan veri hizmeti geliştirme Bkz post [Windows Azure bir OData hizmetini dağıtma](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="development-tips"></a>Geliştirme İpuçları  
 Bir veri hizmeti geliştirirken, aşağıdakileri dikkate almanız gerekir:  
  
-   Kullanıcıların kimliğini doğrulamayı veya belirli kullanıcılar için erişimi kısıtlamayı planlıyorsanız, veri hizmetinizin güvenlik gereksinimlerini belirleyin. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   HTTP inceleme programı, istek ve yanıt iletilerinin içeriğini denetlemenizi sağlayarak veri hizmetinde hata ayıklarken size epey yardımcı olabilir. Veri hizmetine yapılan HTTP isteklerini ve veri hizmetinden alınan yanıtları denetlemek için ham paketleri görüntüleyebilen herhangi bir ağ paketi çözümleyicisi kullanılabilir.  
  
-   Veri hizmetinde hata ayıklarken, veri hizmetinden bir hatayla ilgili olarak normal çalışmaya göre daha fazla bilgi almak isteyebilirsiniz. Ek hata bilgileri ayarlayarak veri hizmetinden veri alma <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> özelliğinde <xref:System.Data.Services.DataServiceConfiguration> için `true` ayarlayarak <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliği <xref:System.ServiceModel.Description.ServiceDebugBehavior> verihizmetisınıfınaöznitelikte`true`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]post [hata ayıklama WCF Veri Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=201868). İzleme de etkinleştirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP Mesajlaşma katmanda yükseltilmiş özel durumlarını görüntülemek için. Daha fazla bilgi için bkz: [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Veri Hizmeti genellikle olarak geliştirilen bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama projesi, ancak da oluşturabilir, veri hizmeti olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi projesinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. İki proje türleri arasındaki farklar hakkında daha fazla bilgi için bkz: [NIB: Visual Studio'da Web sitesi projeleri ile Web uygulaması projelerine](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Kullanarak bir veri hizmeti oluşturduğunuzda **Yeni Öğe Ekle** iletişim kutusunda [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], veri hizmeti tarafından barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS'de. Sırada [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve IIS varsayılan ana bilgisayar veri hizmeti için farklı barındırma seçenekleri desteklenir. Daha fazla bilgi için bkz: [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## <a name="deploying-wcf-data-services"></a>WCF Veri Hizmetlerini Dağıtma  
 WCF Veri Hizmeti, veri hizmetini barındıran işlemi seçmede esneklik sağlar. Kullanabileceğiniz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] aşağıdaki platformlara veri hizmeti dağıtmak için:  
  
-   **IIS tarafından barındırılan Web sunucusu**  
  
     Bir veri hizmeti zaman geliştirilmiş olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projesi için IIS Web sunucusunu, dağıtılabilir standart kullanarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıtım işlemleri.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]için aşağıdaki dağıtım teknolojileri sağlar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]türü bağlı olarak, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıtmakta olduğunuz veri hizmeti barındıran proje.  
  
    -   **ASP.NET Web uygulamaları için dağıtım teknolojileri**  
  
        -   [Web dağıtım paketi](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [Tek tıklamayla yayımlama](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **ASP.NET Web siteleri için dağıtım teknolojileri**  
  
        -   [Web sitesi aracı kopyalayın](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Web sitesi aracı yayımlama](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dağıtım seçenekleri bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama, bkz: [Visual Studio ve ASP.NET Web dağıtımına genel bakış](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Veri hizmetini IIS'ye dağıtmayı denemeden önce, IIS çalıştıran Web sunucusuna dağıtımı test ettiğinizden emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Windows Azure**  
  
     Veri Hizmeti için Windows Azure için Windows Azure araçları kullanarak dağıtabileceğiniz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Windows Azure Araçları için indirebilirsiniz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] gelen [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: post için Windows Azure, bir veri hizmeti dağıtma [Windows Azure bir OData hizmetini dağıtma](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="deployment-considerations"></a>Dağıtım Hakkında Önemli Noktalar  
 Bir veri hizmetini dağıtırken, aşağıdakileri dikkate almanız gerekir:  
  
-   Kullanan bir veri hizmeti dağıttığınızda [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] bir SQL Server veritabanına erişmek için sağlayıcı veri yapılarını, verileri yaymak gerekebilir veya ikisi verilerinizi ile dağıtım hizmet. [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Hedef veritabanında bunun için komut dosyalarını (.sql dosyaları) otomatik olarak oluşturabilir ve bu komut dosyaları Web dağıtımı paketi dahil edilebilir bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: bir veritabanı ile bir Web uygulaması projesi dağıtma](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). İçin bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi, bunu yapabilirsiniz kullanarak **veritabanı Yayımlama Sihirbazı'nı** içinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Daha fazla bilgi için bkz: [veritabanı Yayımlama Sihirbazı'nı kullanarak bir veritabanı dağıtma](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).  
  
-   Çünkü [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] temel içeren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulaması, Windows Server'da çalışan IIS dağıtılmış bir veri hizmeti izlemek için Windows Server AppFabric kullanabilirsiniz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server AppFabric bir veri hizmeti izlemek için bkz post [izleme WCF Veri Hizmetleri ile Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti Barındırma](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
