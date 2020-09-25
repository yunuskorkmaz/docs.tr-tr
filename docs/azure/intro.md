---
title: Azure ve .NET ile çalışmaya başlama
description: Azure ve .NET hakkında bilmeniz gereken temel bilgileri öğrenin.
ms.date: 06/20/2020
ms.openlocfilehash: e4a071e302247332cdc98c1aabf595cb4f8e2eff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171578"
---
# <a name="introduction-to-azure-and-net"></a>Azure ve .NET’e giriş

Bu belgede, Azure hizmetleri 'ni kullanarak uygulama geliştirmeye başlamak için önemli kavramlara ve hizmetlere yönelik bir genel bakış sunulmaktadır.

## <a name="key-concepts"></a>Önemli Kavramlar

Azure **hesabı**: Azure hesabınız, Azure [portalı](https://portal.azure.com) veya [Cloud Shell](https://shell.azure.com)gibi Azure hizmetlerinde oturum açmak için kullandığınız kimlik bilgileridir. Bir Azure hesabınız yoksa, [ücretsiz olarak bir tane oluşturabilirsiniz](https://azure.microsoft.com/free/dotnet/).

**Azure aboneliği**: abonelik, Azure kaynaklarının oluşturulduğu faturalandırma plandır. Abonelikler, şirketiniz tarafından yönetilen bireysel abonelikler veya kurumsal abonelikler olabilir. Azure hesabınız, birden çok abonelikle ilişkilendirilebilir. Bu durumda, kaynak oluştururken doğru aboneliği seçtiğinizden emin olun. Daha fazla bilgi için bkz. [hesapları, abonelikleri ve Faturalandırmayı anlama](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Visual Studio aboneliğiniz varsa, [aylık Azure kredilerinin etkinleştirilmesi bekleniyor](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Kaynak grubu**: kaynak grupları, Azure kaynaklarınızı yönetim için gruplar halinde düzenlemenin bir yoludur. Azure 'da oluşturulan kaynaklar, bir dosyayı bir bilgisayardaki klasöre kaydetmeye benzer şekilde bir kaynak grubunda depolanır.

**Barındırma**: Azure 'da kod çalıştırmak için Kullanıcı tarafından sağlanmış kodun yürütülmesini destekleyen bir hizmette barındırılması gerekir.

**Yönetilen hizmetler**: Azure, Azure 'a veri veya bilgi sağladığınız bazı hizmetler sağlar ve Azure 'un uygulanması uygun eylemi gerçekleştirir. Örnek olarak Azure Blob depolama, dosyaları sağladığınız ve Azure 'un bunları okuma, yazma ve kalıcı hale getirme.

**.Net Için Azure SDK** toplu olarak, Azure hizmetleriyle çeşitli etkileşimler ve işlevler sağlayan, projenize yüklediğiniz [NuGet paketlerine](packages.md) başvurur. Bu paketler, kaynakları sağlamak ve yönetmek için kullanılan yönetim kitaplıklarını da içerir.

## <a name="choosing-a-hosting-option"></a>Barındırma seçeneği seçme

Azure 'da barındırma, üç kategoriye ayrılabilir.

* **Hizmet olarak altyapı (IaaS)**: IaaS ile, ihtiyacınız olan sanal makineleri ilişkili ağ ve depolama bileşenleriyle birlikte temin edersiniz. Ardından, bu VM 'lere istediğiniz yazılım ve uygulamaları dağıtabilirsiniz. Bu model, Microsoft 'un altyapıyı yönetmesi dışında geleneksel bir şirket içi ortama en yakın ortamdır. İşletim sistemi, özel yazılım ve güvenlik güncelleştirmeleri dahil olmak üzere tek tek VM 'Leri yine de yönetirsiniz.

* **Hizmet olarak platform (PaaS)**: PaaS, uygulamanızı VM 'leri veya ağ kaynaklarını yönetmeye gerek kalmadan dağıttığınız bir yönetilen barındırma ortamı sağlar. Örneğin, tek tek sanal makineler oluşturmak yerine bir örnek sayısı belirtirsiniz ve hizmet tarafından gerekli kaynaklar sağlanır, yapılandırılır ve yönetilir. PaaS hizmetine örnek olarak Azure App Service verilebilir.
  
* **Hizmet olarak işlevler (FAAS)**: genellikle sunucusuz bilgi işlem olarak adlandırılır, FAAS, barındırma ortamının endişeleri soyutlayan PaaS 'den daha da ileri gider. İşlem örnekleri oluşturmak ve ardından bu örneklere kod dağıtmak yerine, kodunuzu dağıtırsınız ve hizmet otomatik olarak çalıştırır. İşlem kaynaklarını yönetmeniz gerekmez. Platform, kodunuzu, trafiği işlemek için gerekli olan herhangi bir düzeye doğru şekilde ölçeklendirir ve yalnızca kodunuz çalışırken ödeme yaparsınız. Azure Işlevleri bir FaaS hizmetidir.

Genellikle, uygulamanız FaaS ve PaaS modellerini tercih eder, bulutta çalıştırmayı daha fazla avantaj sağlar. Aşağıda, Azure 'daki üç genel barındırma seçiminden ve ne zaman seçseçeneklerinin özeti verilmiştir.

* [Azure App Service](/azure/app-service/app-service-value-prop-what-is): bir Web uygulaması veya hizmeti barındırmak istiyorsanız, önce App Service bakın. App Service ve ASP.NET, WCF ve ASP.NET Core uygulamalarını kullanmaya başlamak için bkz. [Azure 'da ASP.NET Core Web uygulaması oluşturma](/azure/app-service/app-service-web-get-started-dotnet).

* [Azure işlevleri](/azure/azure-functions/functions-overview): Azure işlevleri olay odaklı iş akışları için idealdir. Web kancalarına yanıt verme, kuyruklardaki öğeleri işleme veya blob depolama ve zamanlayıcılar örnekleri dahildir. Azure Işlevleri 'ni kullanmaya başlamak için bkz. [Visual Studio kullanarak ilk işlevinizi oluşturma](/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Azure sanal makineler](/azure/virtual-machines/): belirli bağımlılıklar nedeniyle mevcut bir uygulamayı barındırmak için App Service gereksinimleriniz karşılamıyorsa, sanal makineler başlamak için en kolay yer olacaktır. Sanal makineler ve ASP.NET veya WCF ile çalışmaya başlamak için bkz. bir [Azure sanal makinesine ASP.NET uygulaması dağıtma](https://tutorials.visualstudio.com/aspnet-vm/intro).

> [!TIP]
> Hizmet seçme hakkında daha fazla bilgi için bkz. [uygulamanız için bir Azure işlem hizmeti seçme](/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Veri depolama hizmeti seçin

Azure, verilerinizi gereksinimlerinize bağlı olarak depolamak için çeşitli hizmetler sunar. .NET geliştiricileri için en yaygın veri hizmetleri şunlardır:

* [Azure SQL veritabanı](/azure/sql-database/): zaten SQL Server kullanan bir uygulamayı buluta geçirmek Istiyorsanız, Azure SQL veritabanı, başlamak için doğal bir yerdir. Başlamak için bkz. [öğretici: Azure 'DA SQL veritabanı ile ASP.NET uygulaması oluşturma](/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Azure Cosmos DB](/azure/cosmos-db/): Azure Cosmos DB, bulut için tasarlanmış modern bir veritabanıdır. Henüz belirli bir veritabanı bağımlılığı olmayan yeni bir uygulama başlatırken Azure Cosmos DB bakmanız gerekir. Cosmos DB, otomatik ölçeklendirme, öngörülebilir performans, hızlı yanıt süreleri ve şema içermeyen verileri sorgulama özelliği önemli olan yeni Web, mobil, oyun ve IoT uygulamaları için iyi bir seçimdir. Başlamak için bkz. [hızlı başlangıç: SQL API ve Azure Portal kullanarak Azure Cosmos DB .NET Web uygulaması oluşturma](/azure/cosmos-db/create-sql-api-dotnet).

* [Azure Blob depolama](/azure/storage/): Azure Blob depolama, görüntüler, dosyalar ve akışlar gibi büyük ikili nesneleri depolamak ve almak için iyileştirilmiştir. Nesne depoları, yapılandırılmamış verilerin son derece büyük miktarlarından yönetimini etkinleştirir. Başlamak için bkz. [hızlı başlangıç: nesne depolamada blob oluşturmak için .NET kullanma](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Daha fazla bilgi için bkz. [doğru veri deposunu seçme](/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Azure hizmetlerine bağlanma

Visual Studio kullanıyorsanız, projelerinize belirli Azure hizmetleri için destek ekleyebilirsiniz. Visual Studio 'daki **bağlı hizmetler** iletişim kutusu, tüm gerekli başvuruları, bağlantı kodunu ve yapılandırma ayarlarını projelerinize eklemenin kolay bir yolunu sağlar. Yaygın olarak kullanılan bazı Azure Hizmetleri, [depolama](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) kimlik doğrulaması, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)ve [görüntü işleme](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service)gibi bilişsel [Hizmetler](/azure/cognitive-services/) gibi kullanıma hazır değildir. Üçüncü taraf hizmetler de dahil olmak üzere daha fazla hizmet [Visual Studio Market](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance)uzantılar olarak sunulmaktadır.

## <a name="using-the-azure-sdk-for-net"></a>.NET için Azure SDK 'sını kullanma

.NET için Azure SDK 'sını Azure kaynaklarınıza erişmek veya yönetmek için kullanıyorsanız, lütfen aşağıdakileri unutmayın:

* **Kimlik doğrulaması**: SDK 'daki birçok kitaplık ortak bir kimlik doğrulama altyapısı kullanır, ancak bazı kitaplıklar kullandıkları hizmete özgü kimlik doğrulama mekanizmaları kullanır. Daha fazla bilgi için bkz. [.net Için Azure SDK Ile kimlik doğrulaması](authentication.md).
* **Günlüğe kaydetme**: destekleniyorsa, istemci kitaplıkları, istemci kitaplığı işlemlerini günlüğe kaydetme özelliğini içerir. Daha fazla bilgi için bkz. [.net Için Azure SDK Ile günlüğe kaydetme](logging.md).
* **REST API**: .net IÇIN Azure SDK, [Azure REST API](/rest/api/azure/)oluşturulmuş bir soyutlamadır. İsterseniz Azure REST API, .NET için Azure SDK 'sının yerine veya yanına kullanılabilir.

## <a name="diagnosing-problems-in-the-cloud"></a>Buluttaki sorunları tanılama

Uygulamanızı Azure 'a dağıttıktan sonra, geliştirme aşamasında çalıştığı ancak Azure 'da olmayan durumlarda çalışmaya başlayabilir. Sorunları tanılarken başlamak için iki iyi yer vardır:

* **Visual Studio 'Da uzaktan hata ayıklama**: çoğu Azure işlem hizmeti (Bu belgede ele alınan hizmetler dahil), Visual Studio ile uzaktan hata ayıklamayı ve günlükleri alma işlemini destekler. Visual Studio 'nun uygulamanızla ilgili yeteneklerini araştırmak için, Visual Studio 'nun Hızlı Başlatma araç çubuğuna (sağ üst köşede) ' Cloud Explorer ' yazarak bulut Gezgini araç penceresini açın ve sonra da uygulamanızı ağaçta bulun. Ayrıntılar için bkz. [Visual Studio kullanarak Azure App Service Web uygulamasında bir Web uygulamasında sorun giderme](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: [Application Insights](/azure/application-insights/) , uygulamalardan otomatik olarak tanılama verileri, telemetri ve performans verilerini yakalayan, tüm uygulama performansı izleme (APM) çözümüdür. Uygulamanız için tanılama verileri toplamaya başlamak için bkz. [ASP.NET Web uygulamanızı Izlemeye başlama](/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Sonraki adımlar

* [İlk ASP.NET Core Web uygulamanızı Azure 'a dağıtın](/azure/app-service/app-service-web-get-started-dotnet)
* [.NET için Azure SDK 'da kimlik doğrulaması hakkında bilgi edinin](authentication.md)
* [Bulut uygulamalarınızda hataları tanılama](https://devblogs.microsoft.com/aspnet/diagnosing-errors-on-your-cloud-apps/)
* [.NET geliştiricileri için](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook) ücretsiz e-kitap Azure hızlı başlangıç kılavuzu indirin
