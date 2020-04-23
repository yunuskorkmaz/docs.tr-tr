---
title: Azure ve .NET ile başlayın
description: Azure ve .NET hakkında bilmeniz gereken temel bilgileri öğrenin.
ms.date: 03/15/2020
ms.openlocfilehash: 64defed4433647c2a0dcce91493d9ec77d21b541
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072146"
---
# <a name="introduction-to-azure-and-net"></a>Azure ve .NET’e giriş

Bu belge, Azure hizmetlerini kullanarak uygulama geliştirmeye başlamak için .NET geliştiricilerin in bilmelidir olması gereken temel kavramlara ve hizmetlere genel bir bakış sağlar.

## <a name="key-concepts"></a>Önemli Kavramlar

**Azure hesabınız**: Azure hesabınız, [Azure Portalı](https://portal.azure.com) veya [Bulut Kabuğu](https://shell.azure.com)gibi Azure hizmetlerinde oturum açtırmak için kullandığınız kimlik bilgisidir. Azure hesabınız yoksa, [ücretsiz bir hesap oluşturabilirsiniz.](https://azure.microsoft.com/free/dotnet/)

**Azure aboneliği**: Abonelik, Azure kaynaklarının oluşturulduğu faturalandırma planıdır. Abonelikler, şirketiniz tarafından yönetilen bireysel abonelikler veya kurumsal abonelikler olabilir. Azure hesabınız birden çok abonelikle ilişkilendirilebilir. Bu durumda, kaynak oluştururken doğru aboneliği seçtiğinizden emin olun. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing)

> [!TIP]
> Visual Studio aboneliğiniz varsa, [etkinleştirilmeyi bekleyen aylık Azure kredileriniz vardır.](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)

**Kaynak grubu**: Kaynak grupları, Azure kaynaklarınızı yönetim için gruplar halinde düzenlemenin bir yoludur. Azure'da oluşturulan kaynaklar, bir dosyayı bilgisayardaki bir klasörde kaydetmeye benzer şekilde bir kaynak grubunda depolanır.

**Barındırma**: Kodu Azure'da çalıştırmak için, kullanıcı tarafından sağlanan kodun yürütülmesini destekleyen bir hizmette barındırılması gerekir.

**Yönetilen hizmetler**: Azure, Azure'a veri veya bilgi sağladığınız bazı hizmetler sağlar ve Azure'un uygulaması uygun eylemi sağlar. Bir örnek, dosyaları sağladığınız ve Azure'un okuma, yazma ve kalıcı hale getirerek bunları işlediği Azure Blob Depolama'dır.

## <a name="choosing-a-hosting-option"></a>Barındırma seçeneği seçme

Azure'da barındırma üç kategoriye ayrılabilir.

* **Hizmet Olarak Altyapı (IaaS) : IaaS**ile, ihtiyacınız olan sanal makineleri ilişkili ağ ve depolama bileşenleriyle birlikte sağlarsınız. Daha sonra istediğiniz yazılımı ve uygulamaları bu VM'lere dağırsınız. Bu model, Microsoft'un altyapıyı yönetmesi dışında geleneksel şirket içi ortama en yakın modeldir. İşletim sistemi, özel yazılım ve güvenlik güncelleştirmeleri de dahil olmak üzere tek tek VM'leri yönetmeye devam edin.

* **Hizmet Olarak Platform (PaaS) : PaaS,** VM'leri veya ağ kaynaklarını yönetmenize gerek kalmadan uygulamanızı dağıttığınız yönetilen bir barındırma ortamı sağlar. Örneğin, tek tek sanal makineler oluşturmak yerine bir örnek sayısı belirtirsiniz ve hizmet tarafından gerekli kaynaklar sağlanır, yapılandırılır ve yönetilir. PaaS hizmetine örnek olarak Azure App Service verilebilir.
  
* **Fonksiyonlar-as-a-Service (FaaS)**: Genellikle sunucusuz bilgi işlem olarak anılacaktır, FaaS barındırma ortamının endişelerini soyutlamapaaS daha da ileri gider. İşlem örnekleri oluşturmak ve ardından bu örneklere kod dağıtmak yerine, kodunuzu dağıtırsınız ve hizmet otomatik olarak çalıştırır. İşlem kaynaklarını yönetmeniz gerekmez. Platform, kodunuzu trafiği işlemek için gereken düzeye sorunsuz bir şekilde ölçeklendirilir ve yalnızca kodunuz çalışırken ödeme yaparsınız. Azure İşlevler bir FaaS hizmetidir.

Genellikle, uygulamanız FaaS ve PaaS modellerini ne kadar çok tercih ettikçe, bulutta çalışırken o kadar çok avantaj elde elabilirsiniz. Aşağıda, Azure'da ve bunları ne zaman seçeceğinizde üç ortak barındırma seçeneğinin bir özeti verilmiştir.

* [Azure Uygulama Hizmeti](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): Bir web uygulaması veya hizmeti barındırmak istiyorsanız, önce App Service'e bakın. App Service ve ASP.NET, WCF ve ASP.NET Core uygulamalarını işe başlamak için [Azure'da ASP.NET Bir Çekirdek web uygulaması oluştur'a](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)bakın.

* [Azure İşlevleri](https://docs.microsoft.com/azure/azure-functions/functions-overview): Azure Fonksiyonları, etkinliğe dayalı iş akışları için idealdir. Örnekler arasında web hooks yanıt, kuyruklar veya blob depolama öğeleri işleme ve zamanlayıcılar içerir. Azure İşlevlerini kullanmaya başlamak için [Visual Studio'u kullanarak ilk işlevinizi oluştur'a](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)bakın.

* [Azure Sanal Makineler](https://docs.microsoft.com/azure/virtual-machines/): Uygulama Hizmeti, belirli bağımlılıklar nedeniyle varolan bir uygulamayı barındırma gereksinimlerinizi karşılamazsa, Sanal Makineler başlamak için en kolay yer olacaktır. Sanal Makineler ve ASP.NET veya WCF ile başlamak [için ASP.NET](https://tutorials.visualstudio.com/aspnet-vm/intro)bkz.

> [!TIP]
> Hizmet seçme hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree)

## <a name="choose-a-data-storage-service"></a>Bir veri depolama hizmeti seçin

Azure, verilerinizin gereksinimlerinize bağlı olarak depolanması için çeşitli hizmetler sunar. .NET geliştiricileri için en yaygın veri hizmetleri şunlardır:

* [Azure SQL Veritabanı](https://docs.microsoft.com/azure/sql-database/): SQL Server'ı zaten kullanmakta olan bir uygulamayı buluta geçirmek istiyorsanız, Azure SQL Veritabanı başlamak için doğal bir yerdir. Başlamak için [Bkz. Tutorial: SQL Veritabanı ile Azure'da bir ASP.NET uygulaması oluşturun.](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase)

* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB, bulut için tasarlanmış modern bir veritabanıdır. Henüz belirli bir veritabanı bağımlılığı olmayan yeni bir uygulamaya başlarken Azure Cosmos DB'ye bakmanız gerekir. Cosmos DB, otomatik ölçek, öngörülebilir performans, hızlı yanıt süreleri ve şema içermeyen verileri sorgulama becerisinin önemli olduğu yeni web, mobil, oyun ve IoT uygulamaları için iyi bir seçimdir. Başlamak için [Quickstart: SQL API ve Azure portalını kullanarak Azure Cosmos DB ile bir .NET web uygulaması oluşturun.](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)

* Azure Blob Depolama : Azure [Blob Depolama,](https://docs.microsoft.com/azure/storage/)görüntüler, dosyalar ve akışlar gibi büyük ikili nesneleri depolamak ve almak için optimize edilmiştir. Nesne depoları, son derece büyük miktarda yapılandırılmamış verilerin yönetimini sağlar. Başlamak için [Quickstart: Object depolamada bir leke oluşturmak için .NET'i kullanın.](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet)

> [!TIP]
> Daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview)

## <a name="connect-to-azure-services"></a>Azure hizmetlerine bağlanma

Visual Studio kullanıyorsanız, projelerinize belirli Azure hizmetleri için destek ekleyebilirsiniz. Visual Studio'daki **Bağlı Hizmetler** iletişim kutusu, projelerinize gerekli tüm başvuruları, bağlantı kodunu ve yapılandırma ayarlarını eklemenin kolay bir yolunu sağlar. Depolama, [Azure Etkin Dizin](/azure/active-directory/develop/vs-active-directory-add-connected-service) kimlik doğrulaması, [Storage](/azure/vs-azure-tools-connected-services-storage)Azure [Anahtar Kasası](/azure/key-vault/vs-key-vault-add-connected-service)ve [Computer Vision](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service)gibi [Bilişsel Hizmetler](/azure/cognitive-services/) gibi sık kullanılan bazı Azure hizmetleri kutunun dışında desteklenir. Üçüncü taraf hizmetleri de dahil olmak üzere daha fazla hizmet, [Visual Studio Marketplace'te](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance)uzantı olarak mevcuttur.

## <a name="diagnosing-problems-in-the-cloud"></a>Bulutta sorunları tanılama
Uygulamanızı Azure'a dağıttıktan sonra, uygulamanın geliştirme aşamasında çalıştığı ancak Azure'da çalışmadığı durumlara rastlayabilirsiniz. Aşağıda sorunları tanılarken başlamak için iki iyi yer verilmiştir:

* **Visual Studio'dan uzaktan hata ayıklama**: Çoğu Azure bilgi işlem hizmeti (bu belgede tartışılan hizmetler dahil) Visual Studio ile uzaktan hata ayıklama yı ve günlükleri satın alma yı destekler. Uygulamanızla Visual Studio'nun yeteneklerini keşfetmek için Visual Studio'nun hızlı başlatma araç çubuğuna (sağ üst köşede) 'Cloud Explorer' yazarak Bulut Gezgini araç penceresini açın ve ardından uygulamanızı ağaçta bulun. Ayrıntılar için [Visual Studio'yu kullanarak Azure Uygulama Hizmeti'ndeki bir web uygulamasını sorun giderme](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug)bilgisine bakın.

* **Uygulama Öngörüleri**: [Application Insights,](https://docs.microsoft.com/azure/application-insights/) uygulamalardaki tanısal verileri, telemetriyi ve performans verilerini otomatik olarak yakalayan eksiksiz bir uygulama performans izleme (APM) çözümüdür. Uygulamanız için tanılama verilerini toplamaya başlamak için [ASP.NET](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal)bkz.

## <a name="next-steps"></a>Sonraki adımlar

* [İlk ASP.NET Core web uygulamanızı Azure'a dağıtın](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [.NET için Azure SDK'da kimlik doğrulama hakkında bilgi edinin](./sdk/authentication.md)
* [Bulut uygulamalarınızdaki hataları tanılama](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* .NET Geliştiricileri için ücretsiz e-kitap [Azure Hızlı Başlangıç Kılavuzu'nu indirin](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
