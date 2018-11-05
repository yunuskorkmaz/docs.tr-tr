---
title: Azure’da F# Kullanma
description: F# ile Azure hizmetlerini kullanmaya Kılavuzu
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 1fbb85a07fc057c1b89a4c4a1ad356066cebf2b8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50201510"
---
# <a name="using-f-on-azure"></a>Azure’da F# Kullanma

F# bulut programlama için mükemmel bir dildir ve web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro hizmetler, yazmak için sık kullanılan ve ölçeklenebilir veri işleme için.

Aşağıdaki bölümlerde, çeşitli Azure Hizmetleri F# ile kullanma hakkında kaynaklar bulacaksınız.

> [!NOTE]
> Belirli bir Azure hizmeti bu belgelerde değilse, lütfen Azure işlevleri veya .NET bu hizmet için belgelere bakın. Bazı Azure Hizmetleri, dilden bağımsız ve hiçbir dile özgü belge gerektirir ve burada listelenmeyen.

## <a name="using-azure-virtual-machines-with-f"></a>Azure sanal makineler F# ile kullanma #

Azure, çok çeşitli sanal makine (VM) yapılandırmaları destekler, bkz: [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).

F# yürütme, derleme ve/veya bkz için bir sanal makinede yüklemek için [kullanarak F# Linux'ta](https://fsharp.org/use/linux) ve [kullanarak F# üzerinde Windows](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Azure işlevleri ile F# kullanma #

[Azure işlevleri](https://azure.microsoft.com/services/functions/) kod veya "işlevleri" küçük parçaları kolayca çalıştırmaya yönelik bir bulutta çözümüdür. Yalnızca çalıştırmak için tüm uygulama veya altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz. İşlevlerinizi olayları Azure depolama ve diğer bulutta barındırılan kaynaklara bağlıdır. Veri, F# işlevleri işlev bağımsız değişkenleri aracılığıyla akar. Seçtiğiniz, gerektiği gibi ölçek güvenen Azure geliştirme dilini kullanabilirsiniz.

Azure işlevleri F# birinci sınıf bir dil ile F# kodu yürütme verimli, ölçeklenebilir, reaktif olarak destekler. Bkz: [Azure işlevleri F# Geliştirici Başvurusu](/azure/azure-functions/functions-reference-fsharp) için F# Azure işlevleri ile kullanma hakkında başvuru belgeleri.

Azure işlevleri ve F# kullanarak diğer kaynaklar:

* [F# Suave kullanarak Azure işlevleri ölçeği](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [F# Azure işlevi oluşturma](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure işlevleri ile Azure tür sağlayıcısını kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Azure depolama ile F# kullanma #

Azure depolama, depolama hizmetleri dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik, müşterilerin ihtiyaçlarını karşılamak üzere dayanan modern uygulamalar için temel bir katmanıdır. F#Program, doğrudan aşağıdaki makalelerde açıklanan teknikleri kullanarak Azure depolama hizmetleri ile etkileşim kurabilir.

* [F# kullanarak Azure Blob depolama kullanmaya başlama](blob-storage.md)
* [F# kullanarak Azure Dosya depolama kullanmaya başlama](file-storage.md)
* [F# kullanarak Azure Kuyruk depolama kullanmaya başlama](queue-storage.md)
* [F# kullanarak Azure Tablo depolama kullanmaya başlama](table-storage.md)

Azure depolama, Azure işlevleri ile birlikte açık API çağrıları yerine bildirim temelli yapılandırması aracılığıyla da kullanılabilir. Bkz: [Azure depolama için Azure işlevleri Tetikleyicileri ve bağlamaları](/azure/azure-functions/functions-bindings-storage) F# örnekleri içerir.

## <a name="using-azure-app-service-with-f"></a>Azure App Service ile F# kullanma #

[Azure App Service](https://azure.microsoft.com/services/app-service/) güçlü web uygulamaları ve bulutta veya şirket içinde her yerden, veri bağlanan mobil uygulamaları oluşturmak için bir bulut platformu.

* [F# Azure Web API'si örneği](https://github.com/fsprojects/azure-webapi-example)
* [F# azure'da bir web uygulaması barındırma](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>F# ile Azure HDInsight ile Apache Spark'ı kullanma

[Azure HDInsight için Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) büyük ölçekli veri analizi uygulamalarını çalıştıran bir açık kaynak işleme çerçevesidir. Azure Apache Spark, kolay ve dağıtmak için uygun maliyetli hale getirir. F# kullanarak Spark geliştirmeye [Mobius](https://github.com/Microsoft/Mobius), Spark için .NET API'si.

* [F# Mobius kullanarak uygulama Spark uygulamaları](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Örnek F# Spark uygulamaları Mobius kullanma](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Azure Cosmos DB ile F# kullanma #

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) yüksek kullanılabilirliğe sahip, Global olarak dağıtılmış uygulamalar için bir NoSQL hizmetidir.

Azure Cosmos DB F# ile iki şekilde kullanılabilir:

1. F# Azure işlevleri oluşturmayı aracılığıyla hangi tepki verin veya Azure Cosmos DB koleksiyonları değişiklikleri neden olabilir. Bkz: [Azure işlevleri için Azure Cosmos DB bağlamaları](/azure/azure-functions/functions-bindings-cosmosdb), veya
2. Kullanarak [SQL API'si için Azure Cosmos DB .NET SDK](/azure/cosmos-db/sql-api-sdk-dotnet). İlgili örnekler C# ' de var.

## <a name="using-azure-event-hubs-with-f"></a>Azure Event Hubs'a F# ile kullanma #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) Web siteleri, uygulamalardan ve cihazlardan bulut ölçekli telemetri içe alma sağlayın.

Azure Event Hubs F# ile iki şekilde kullanılabilir:

1. F# Azure işlevleri ile oluşturma, olayları tarafından tetiklenir. Bkz: [Azure Event Hubs için Tetikleyiciler](/azure/azure-functions/functions-bindings-event-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Bu örnekler C# ' ta olduğunu unutmayın.

## <a name="using-azure-notification-hubs-with-f"></a>Azure Notification hubs'ı F# ile kullanma #

[Azure Notification hubs'ı](/azure/notification-hubs/) dilediğiniz mobil platforma herhangi bir arka uçtan (bulutta veya şirket içi) mobil anında iletme bildirimleri göndermenize olanak tanıyan çok platformlu, ölçeği genişletilmiş bir gönderim altyapısı olan.

Azure Notification hubs'ı F# ile iki şekilde kullanılabilir:

1. F# Azure işlevleri ile oluşturma, bir bildirim hub'ına sonuçları gönderir. Bkz: [Azure işlevi için Notification hubs'ı Tetikleyicileri çıkış](/azure/azure-functions/functions-bindings-notification-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Bu örnekler C# ' ta olduğunu unutmayın.


## <a name="implementing-webhooks-on-azure-with-f"></a>Azure'da F# ile Web Kancalarını uygulama #

A [Web kancası](https://en.wikipedia.org/wiki/Webhook) olan bir web isteği aracılığıyla tetiklenen bir geri çağırma. Web kancaları, sinyal olayları için GitHub gibi siteleri tarafından kullanılır. 

Web kancaları F#'ta uygulanan ve azure'da barındırılan bir [bağlama Web kancası ile F# Azure işlevi](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Webjobs ile F# kullanma #

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) programlar üç yolla App Service web uygulamasında çalıştırabilirsiniz: talep üzerine, kesintisiz veya bir planlamaya göre.

[Örneğin F# Webjob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>F# ile azure'da uygulama zamanlayıcılar #

Zamanlayıcı, bir zamanlama, bir kez veya yinelenen göre arama işlevleri tetikler.

Zamanlayıcılar F#'ta uygulanan ve azure'da barındırılan bir [bir zamanlayıcı tetikleyicisi ile F# Azure işlevi](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Dağıtma ve F# betikleri ile Azure kaynaklarını yönetme #

Azure sanal makineleri program aracılığıyla dağıtılan ve F# komut dosyalarından Microsoft.Azure.Management paketler ve API'leri kullanarak yönetilen. Örneğin, [.NET için yönetim kitaplıkları ile çalışmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [Azure Resource Manager'ı kullanarak](/azure/azure-resource-manager/resource-manager-deployment-model).

Benzer şekilde, diğer Azure kaynakları da dağıtılabilir ve aynı bileşenleri kullanarak F# betiklerin yönetilen. Örneğin, depolama hesapları oluşturun, Azure bulut Hizmetleri dağıtabilir, Azure Cosmos DB örnekleri oluşturmak ve Azure bildirim hub'ları F# komut dosyalarından programlama yoluyla yönetme.

Kaynakları yönetmek ve dağıtmak için F# betikleri kullanarak genellikle gerekli değildir. Örneğin, Azure kaynaklarını parametreleştirilebilir JSON şablonu açıklamaları alanından dağıtılan directy olabilir. Bkz: [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) örnekleri gibi [Azure hızlı başlangıç şablonları](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure Hizmetleri tüm belgeler](/azure/)
