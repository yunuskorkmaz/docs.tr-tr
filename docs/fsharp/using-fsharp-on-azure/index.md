---
title: 'Azure’da F# Kullanma'
description: 'Azure Hizmetleri ile kullanarakF#'
author: sylvanc
ms.date: 09/22/2016
---
# <a name="using-f-on-azure"></a>Azure’da F# Kullanma

F#Bulut programlama için mükemmel bir dildir ve web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro hizmetler, yazmak için sık kullanılan ve ölçeklenebilir veri işleme için.

Aşağıdaki bölümlerde, çeşitli Azure Hizmetleri ile kullanma hakkında kaynaklar bulacaksınız F#.

> [!NOTE]
> Belirli bir Azure hizmeti bu belgelerde değilse, lütfen Azure işlevleri veya .NET bu hizmet için belgelere bakın. Bazı Azure Hizmetleri, dilden bağımsız ve hiçbir dile özgü belge gerektirir ve burada listelenmeyen.

## <a name="using-azure-virtual-machines-with-f"></a>Azure sanal makineler F ile kullanma\#

Azure, çok çeşitli sanal makine (VM) yapılandırmaları destekler, bkz: [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).

Yüklenecek F# yürütme, derleme ve/veya bkz için bir sanal makinede [kullanma F# Linux'ta](https://fsharp.org/use/linux) ve [kullanma F# Windows üzerinde](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>F ile Azure işlevleri'ni kullanarak\#

[Azure işlevleri](https://azure.microsoft.com/services/functions/) kod veya "işlevleri" küçük parçaları kolayca çalıştırmaya yönelik bir bulutta çözümüdür. Yalnızca çalıştırmak için tüm uygulama veya altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz. İşlevlerinizi olayları Azure depolama ve diğer bulutta barındırılan kaynaklara bağlıdır. Veri akışları halinde, F# işlevleri aracılığıyla işlev bağımsız değişkenleri. Seçtiğiniz, gerektiği gibi ölçek güvenen Azure geliştirme dilini kullanabilirsiniz.

Azure işlevleri desteği F# verimli, ölçeklenebilir, reaktif yürütülmesini ile birinci sınıf bir dil olarak F# kod. Bkz: [Azure işlevleri F# Geliştirici Başvurusu](/azure/azure-functions/functions-reference-fsharp) nasıl kullanılacağı hakkındaki referans belgeleri için F# Azure işlevleri ile.

Azure işlevleri'ni kullanarak diğer kaynakları ve F#:

* [Azure işlevleri ölçeğini F# Suave kullanma](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Azure işlevi oluşturmaF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure işlevleri ile Azure tür sağlayıcısını kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Azure depolama ile F kullanma\#

Azure depolama, depolama hizmetleri dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik, müşterilerin ihtiyaçlarını karşılamak üzere dayanan modern uygulamalar için temel bir katmanıdır. F#Program, doğrudan aşağıdaki makalelerde açıklanan teknikleri kullanarak Azure depolama hizmetleri ile etkileşim kurabilir.

* [F# kullanarak Azure Blob depolama kullanmaya başlama](blob-storage.md)
* [F# kullanarak Azure Dosya depolama kullanmaya başlama](file-storage.md)
* [F# kullanarak Azure Kuyruk depolama kullanmaya başlama](queue-storage.md)
* [F# kullanarak Azure Tablo depolama kullanmaya başlama](table-storage.md)

Azure depolama, Azure işlevleri ile birlikte açık API çağrıları yerine bildirim temelli yapılandırması aracılığıyla da kullanılabilir. Bkz: [Azure depolama için Azure işlevleri Tetikleyicileri ve bağlamaları](/azure/azure-functions/functions-bindings-storage) içeren F# örnekler.

## <a name="using-azure-app-service-with-f"></a>Azure App Service ile F kullanarak\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) güçlü web uygulamaları ve bulutta veya şirket içinde her yerden, veri bağlanan mobil uygulamaları oluşturmak için bir bulut platformu.

* [F#Azure Web API'si örneği](https://github.com/fsprojects/azure-webapi-example)
* [Barındırma F# azure'da bir web uygulaması](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Apache Spark'ı kullanarak F# Azure HDInsight ile

[Azure HDInsight için Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) büyük ölçekli veri analizi uygulamalarını çalıştıran bir açık kaynak işleme çerçevesidir. Azure Apache Spark, kolay ve dağıtmak için uygun maliyetli hale getirir. Spark uygulamanızda geliştirme F# kullanarak [Mobius](https://github.com/Microsoft/Mobius), Spark için .NET API'si.

* [Spark uygulamalarında uygulama F# Mobius kullanma](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Örnek F# Spark Mobius kullanan uygulamalar](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Azure Cosmos DB ile F kullanma\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) yüksek kullanılabilirliğe sahip, Global olarak dağıtılmış uygulamalar için bir NoSQL hizmetidir.

Azure Cosmos DB ile kullanılabilir F# iki yolla:

1. Oluşturulmasını aracılığıyla F# tepki veya değişiklikler Azure Cosmos DB koleksiyonları için neden Azure işlevleri. Bkz: [Azure işlevleri için Azure Cosmos DB bağlamaları](/azure/azure-functions/functions-bindings-cosmosdb), veya
2. Kullanarak [SQL API'si için Azure Cosmos DB .NET SDK](/azure/cosmos-db/sql-api-sdk-dotnet). İlgili örnekler C# ' de var.

## <a name="using-azure-event-hubs-with-f"></a>Azure Event Hubs ile F kullanarak\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) Web siteleri, uygulamalardan ve cihazlardan bulut ölçekli telemetri içe alma sağlayın.

Azure Event Hubs ile kullanılabilir F# iki yolla:

1. Oluşturulmasını aracılığıyla F# olaylar tarafından tetiklenen Azure işlevleri. Bkz: [Azure Event Hubs için Tetikleyiciler](/azure/azure-functions/functions-bindings-event-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Bu örnekler C# ' ta olduğunu unutmayın.

## <a name="using-azure-notification-hubs-with-f"></a>Azure Notification hubs'ı F ile kullanma\#

[Azure Notification hubs'ı](/azure/notification-hubs/) dilediğiniz mobil platforma herhangi bir arka uçtan (bulutta veya şirket içi) mobil anında iletme bildirimleri göndermenize olanak tanıyan çok platformlu, ölçeği genişletilmiş bir gönderim altyapısı olan.

Azure Notification Hubs ile kullanılabilir F# iki yolla:

1. Oluşturulmasını aracılığıyla F# Azure işlevleri, sonuçları bir bildirim hub'ına gönderir. Bkz: [Azure işlevi için Notification hubs'ı Tetikleyicileri çıkış](/azure/azure-functions/functions-bindings-notification-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Bu örnekler C# ' ta olduğunu unutmayın.


## <a name="implementing-webhooks-on-azure-with-f"></a>Web kancaları F ile azure'da uygulama\#

A [Web kancası](https://en.wikipedia.org/wiki/Webhook) olan bir web isteği aracılığıyla tetiklenen bir geri çağırma. Web kancaları, sinyal olayları için GitHub gibi siteleri tarafından kullanılır. 

Web kancaları uygulanabilir F# ve azure'da barındırılan bir [Azure işlevinde F# bağlama Web kancası ile](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Webjobs ile F kullanma\#

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) programlar üç yolla App Service web uygulamasında çalıştırabilirsiniz: talep üzerine, kesintisiz veya bir planlamaya göre.

[Örnek F# Webjob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Zamanlayıcılar F ile azure'da uygulama\#

Zamanlayıcı, bir zamanlama, bir kez veya yinelenen göre arama işlevleri tetikler.

Zamanlayıcılar uygulanabilir F# ve azure'da barındırılan bir [Azure işlevinde F# bir zamanlayıcı tetikleyicisi ile](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Azure kaynaklarınızı dağıtıp F# betikleri

Azure sanal makineler programlı olarak dağıtılabilir ve yönetilen engelle F# Microsoft.Azure.Management paketleri ve API'leri kullanarak komut dosyaları. Örneğin, [.NET için yönetim kitaplıkları ile çalışmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [Azure Resource Manager'ı kullanarak](/azure/azure-resource-manager/resource-manager-deployment-model).

Benzer şekilde, diğer Azure kaynakları da dağıtılabilir ve yönetilen engelle F# aynı bileşenleri kullanarak komut dosyaları. Örneğin, depolama hesapları oluşturabilir, Azure bulut Hizmetleri dağıtma, Azure Cosmos DB örnekleri oluşturmak ve Azure bildirim hub'larından programlı olarak yönetmek F# betikler.

Kullanarak F# dağıtmak ve kaynakları yönetmek için betikleri genellikle gerekli değildir. Örneğin, Azure kaynaklarını parametreleştirilebilir JSON şablonu açıklamaları alanından dağıtılan directy olabilir. Bkz: [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) örnekleri gibi [Azure hızlı başlangıç şablonları](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure Hizmetleri tüm belgeler](/azure/)
