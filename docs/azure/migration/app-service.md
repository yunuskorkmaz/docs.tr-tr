---
title: .NET web uygulamanızı veya hizmetinizi Azure Uygulama Hizmetine geçirin
description: Bir .NET web uygulamasını veya hizmetini şirket içinden Azure Uygulama Hizmeti'ne geçirme hakkında bilgi edinin.
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 57f3b981a1d94c2193160f55f9c8242da694c169
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072139"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>.NET web uygulamanızı veya hizmetinizi Azure Uygulama Hizmetine geçirin

[App Service,](https://docs.microsoft.com/azure/app-service/overview) ölçeklenebilir web sitelerini ve web uygulamalarını barındırmak için optimize edilmiş tam olarak yönetilen bir bilgi işlem platformu hizmetidir. Bu makalede, varolan bir uygulamanın Azure Uygulama Hizmetine nasıl kaldırılıp kaydırılacak veya kaydırılabilmek, göz önünde bulundurulması gereken değişiklikler ve [buluta geçmek](https://azure.microsoft.com/migration/web-applications/)için ek kaynaklar hakkında bilgiler verilmektedir. Çoğu ASP.NET web sitesi (Web forms, MVC) ve hizmetler (Web API, WCF) hiçbir değişiklik olmadan doğrudan Azure Uygulama Hizmeti'ne taşınabilir. Bazıları küçük değişikliklere ihtiyaç duyabilirken, bazılarının yeniden düzenlemeye ihtiyacı olabilir.

Başlamaya hazır mısınız? [ASP.NET + SQL uygulamanızı Azure Uygulama Hizmeti'nde yayımlayın.](https://tutorials.visualstudio.com/azure-webapp-migrate/intro)

## <a name="considerations"></a>Dikkat edilmesi gerekenler

### <a name="on-premises-resources-including-sql-server"></a>Şirket içi kaynaklar (SQL Server dahil)

Bunların geçirilmesi veya değiştirilmesi gerekebileceğiiçin şirket içi kaynaklara erişimi doğrulayın. Şirket içi kaynaklara erişimi azaltma seçenekleri şunlardır:

* [Azure Sanal Ağları](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet)kullanarak Uygulama Hizmetini şirket içi kaynaklara bağlayan bir VPN oluşturun.
* [Azure Röle'yi](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)kullanarak güvenlik duvarı değişiklikleri olmadan şirket içi hizmetleri güvenli bir şekilde buluta maruz bırakabilirsiniz.
* [SQL veritabanı](https://go.microsoft.com/fwlink/?linkid=863217) gibi bağımlılıkları Azure'a geçirin.
* Bağımlılıkları azaltmak için buluttaki hizmet olarak platform tekliflerini kullanın. Örneğin, şirket içi posta sunucusuna bağlanmak yerine [SendGrid'i](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email)kullanmayı düşünün.

### <a name="port-bindings"></a>Bağlantı Noktası Bağlamaları

Azure Uygulama Hizmeti, HTTP için 80 portu ve HTTPS trafiği için 443 bağlantı noktasını destekler.

WCF için aşağıdaki bağlamalar desteklenir:

Bağlama | Notlar
--------|--------
Temel http://www. |
WSHttp |
WSDualhttpbinding | [Web soketi desteği](https://docs.microsoft.com/azure/app-service/web-sites-configure) etkinleştirilmelidir.
Nethttpbinding | Çift yönlü sözleşmeler için [web soketi desteği](https://docs.microsoft.com/azure/app-service/web-sites-configure) etkinleştirilmelidir.
NethttpsBinding | Çift yönlü sözleşmeler için [web soketi desteği](https://docs.microsoft.com/azure/app-service/web-sites-configure) etkinleştirilmelidir.
Temel https://rıçbağlama |
Web'e Bağlanma |
WShttps://ritme |

### <a name="authentication"></a>Kimlik Doğrulaması

Azure Uygulama Hizmeti varsayılan olarak anonim kimlik doğrulamasını destekler ve amaçlandığı zaman kimlik doğrulamasını oluşturur. Windows kimlik doğrulaması yalnızca Azure Etkin Dizini ve ADFS ile tümleştirilerek kullanılabilir. [Şirket içi dizinlerinizi Azure Etkin Dizini ile nasıl entegre edebilirsiniz hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>GAC'deki derlemeler (Küresel Montaj Önbelleği)

Bu özellik desteklenmez. Gerekli derlemeleri uygulamanın *\bin* klasörüne kopyalamayı düşünün. Sunucuya yüklenen özel *.msi* dosyaları (örneğin, PDF jeneratörleri) kullanılamaz.

### <a name="iis-settings"></a>IIS ayarları
Uygulamanızdaki applicationHost.config aracılığıyla geleneksel olarak yapılandırılan her şey artık Azure portalı üzerinden yapılandırılabilir. Bu, AppPool bitness, etkinleştirme/devre dışı, websockets, yönetilen boru hattı sürümü, .NET Framework sürümü (2.0/4.0) vb. için geçerlidir. [Uygulama ayarlarınızı](https://docs.microsoft.com/azure/app-service/web-sites-configure)değiştirmek için [Azure portalına](https://portal.azure.com)gidin, web uygulamanız için bıçağı açın ve ardından **Uygulama Ayarları** sekmesini seçin.

#### <a name="iis5-compatibility-mode"></a>IIS5 Uyumluluk Modu
IIS5 Uyumluluk Modu desteklenmez. Azure Uygulama Hizmeti'nde, her web uygulaması ve altındaki tüm uygulamalar belirli bir [uygulama havuzu](https://technet.microsoft.com/library/cc735247(v=WS.10).aspx)kümesiyle aynı alt işlemde çalışır.

#### <a name="iis7-schema-compliance"></a>IIS7+ şema uyumluluğu  
Azure App Service IIS şemasında bazı öğeler ve öznitelikler tanımlanmamıştır. Sorunlarla karşılaşırsanız, [XDT dönüşümlerini](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/)kullanmayı düşünün.

#### <a name="single-application-pool-per-site"></a>Site başına tek uygulama havuzu  
Azure Uygulama Hizmeti'nde, her web uygulaması ve altındaki tüm uygulamalar aynı uygulama havuzunda çalışır. Ortak ayarlara sahip tek bir uygulama havuzu oluşturmayı veya her uygulama için ayrı bir web uygulaması oluşturmayı düşünün.

### <a name="com-and-com-components"></a>COM ve COM+ bileşenleri  
Azure Uygulama Hizmeti, platformda COM bileşenlerinin kaydedilmesine izin vermez. Uygulamanız herhangi bir COM bileşenini kullanıyorsa, bunların yönetilen kodda yeniden yazılması ve site veya uygulamayla birlikte dağıtılması gerekir.

### <a name="physical-directories"></a>Fiziksel dizinler
Azure Uygulama Hizmeti fiziksel sürücü erişimine izin vermez. Dosyalara SMB üzerinden erişmek için [Azure Dosyaları'nı](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) kullanmanız gerekebilir. [Azure Blob Depolama,](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) https üzerinden erişim için dosyaları depolayabilir.

### <a name="isapi-filters"></a>ISAPI filtreleri  
Azure Uygulama Hizmeti ISAPI Filtreleri kullanımını destekleyebilir, ancak ISAPI DLL sitenizle dağıtılmalı ve web.config üzerinden kaydedilmelidir.

### <a name="https-bindings-and-ssl"></a>HTTPS ciltlemeler ve SSL
HTTPS bağlamaları geçirilmez ve Web sitelerinizle ilişkili SSL sertifikaları da kullanılmaz. Ancak, site geçişi tamamlandıktan sonra [SSL sertifikaları el ile yüklenebilir.](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl)

### <a name="sharepoint-and-frontpage"></a>SharePoint ve FrontPage
SharePoint ve FrontPage Server Uzantıları (FPSE) desteklenmez.

### <a name="web-site-size"></a>Web sitesi boyutu  
Ücretsiz sitelerde 1 GB içerik boyutu sınırı vardır. Siteniz 1 GB'dan büyükse, ücretli bir SKU'ya yükseltmeniz gerekir. [Bkz. App Service fiyatlandırması.](https://azure.microsoft.com/pricing/details/app-service/windows/)

### <a name="database-size"></a>Veritabanı boyutu  
SQL Server veritabanları için lütfen geçerli [SQL Veritabanı fiyatlandırmasını](https://azure.microsoft.com/pricing/details/sql-database)kontrol edin.

### <a name="azure-active-directory-aad-integration"></a>Azure Etkin Dizin (AAD) tümleştirmesi  
AAD ücretsiz uygulamalarla çalışmaz. AAD'yi kullanmak için SKU uygulamasını yükseltmeniz gerekir. [Bkz. App Service fiyatlandırması.](https://azure.microsoft.com/pricing/details/app-service/windows/)

### <a name="monitoring-and-diagnostics"></a>İzleme ve tanılama
İzleme ve tanılama için mevcut şirket içi çözümlerinizin bulutta çalışması olası değildir. Ancak Azure, web uygulamalarıyla ilgili sorunları belirleyebilmeniz ve hata ayıklama yapabilmeniz için günlüğe kaydetme, izleme ve tanılama için araçlar sağlar. Web uygulamanızın yapılandırmasında tanılamayı kolayca etkinleştirebilir ve Azure Uygulama Öngörüleri'nde kaydedilen günlükleri görüntüleyebilirsiniz. [Web uygulamaları için tanılama günlüğe kaydetmeyi etkinleştirme hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log)

### <a name="connection-strings-and-application-settings"></a>Bağlantı dizeleri ve uygulama ayarları
Uygulamanızda kullanılan hassas bilgileri güvenli bir şekilde depolayan bir hizmet olan [Azure KeyVault'u](https://docs.microsoft.com/azure/key-vault/)kullanmayı düşünün. Alternatif olarak, bu verileri Bir Uygulama Hizmeti ayarı olarak depolayabilirsiniz.

### <a name="dns"></a>DNS
DNS yapılandırmalarını uygulamanızın gereksinimlerine göre güncelleştirmeniz gerekebilir. Bu DNS ayarları, App Service [özel etki alanı ayarlarında](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)yapılandırılabilir.

## <a name="azure-app-service-with-windows-containers"></a>Windows Kapsayıcılı Azure Uygulama Hizmeti
Uygulamanız doğrudan App Service'e geçirilemezse, GAC, COM bileşenleri, MSI'lar, .NET FX API'lerine, DirectX'e ve daha fazlasına tam erişim sağlayan Windows Kapsayıcıları'nı kullanarak Uygulama Hizmeti'ni düşünün.

## <a name="see-also"></a>Ayrıca bkz.

* [Uygulamanızın Uygulama Hizmeti için uygun olup olmadığını belirleme](https://appmigration.microsoft.com/)
* [Veritabanınızı buluta taşıma](https://go.microsoft.com/fwlink/?linkid=863217)
* [Azure web uygulaması sandbox ayrıntıları ve kısıtlamaları](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
