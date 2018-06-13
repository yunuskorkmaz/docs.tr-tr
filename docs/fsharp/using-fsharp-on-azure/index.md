---
title: 'F # Azure üzerinde kullanma'
description: 'F # ile Azure hizmetlerini kullanmaya Kılavuzu'
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 9a6e384874426584a19e1dc83a35c3f80e59537a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569713"
---
# <a name="using-f-on-azure"></a>F # Azure üzerinde kullanma

F # bulut programlama için mükemmel bir dildir ve web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro yazmak için sık kullanılan ve ölçeklenebilir veri işleme için.

Aşağıdaki bölümlerde, aralığı, Azure Hizmetleri F # ile kullanma hakkında kaynaklar bulacaksınız.

> [!NOTE]
> Lütfen belirli bir Azure hizmet bu belgelerde değilse, bu hizmet için Azure işlevleri veya .NET belgelerine başvurun. Bazı Azure Hizmetleri dilden bağımsız ve hiçbir dile özgü belge gerektirir ve burada listelenmeyen.

## <a name="using-azure-virtual-machines-with-f"></a>Azure sanal makineleri F # ile kullanma #

Azure sanal makine (VM) yapılandırmaları çeşitli destekler, bkz: [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).

F # yürütme, derleme ve/veya bkz için bir sanal makinede yüklemek için [kullanarak F # Linux'ta](http://fsharp.org/use/linux) ve [kullanarak F # Windows](http://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Azure işlevleri F # ile kullanma #

[Azure işlevleri](https://azure.microsoft.com/services/functions/) kolayca kodu veya "işlevleri" küçük parçalarını çalıştırmak için bir bulutta çözümüdür. Tüm uygulama veya çalıştırmak için altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz. İşlevlerinizi Azure depolama ve diğer bulutta barındırılan kaynakları olayları bağlıdır. Veri, F # işlevleri işlev bağımsız değişkenleri aracılığıyla akar. İhtiyaca göre ölçekleme için güvenen Azure tercih ettiğiniz geliştirme dilini kullanabilirsiniz.

Azure işlevleri F # olarak F # kodu verimli, geriye dönük, ölçeklenebilir yürütülmesi ile birinci sınıf bir dil için destek. Bkz: [Azure işlevleri F # Geliştirici Başvurusu](/azure/azure-functions/functions-reference-fsharp) F # ile Azure işlevlerinin nasıl kullanılacağı hakkında başvuru belgeleri için.

Azure işlevleri ve F # kullanma için diğer kaynaklar:

* [F # Suave kullanarak Azure işlevleri ölçeklendirin](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [F #'de Azure işlevi oluşturma](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure türü sağlayıcısı ile Azure işlevlerini kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Azure Storage F # ile kullanma #

Azure depolama, depolama hizmetleri dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik müşterilerin ihtiyaçlarını karşılamak üzere kullanan modern uygulamalar için temel bir katmanıdır. F # programları, doğrudan aşağıdaki makalelerde açıklanan techinques kullanarak Azure storage Hizmetleri ile etkileşim kurabilir.

* [F# kullanarak Azure Blob depolama kullanmaya başlama](blob-storage.md)
* [F# kullanarak Azure Dosya depolama kullanmaya başlama](file-storage.md)
* [F# kullanarak Azure Kuyruk depolama kullanmaya başlama](queue-storage.md)
* [F# kullanarak Azure Tablo depolama kullanmaya başlama](table-storage.md)

Azure depolama, Azure işlevleri ile birlikte açık API çağrıları yerine bildirim temelli yapılandırma aracılığıyla da kullanılabilir. Bkz: [Azure işlevleri Tetikleyicileri ve bağlamaları için Azure Storage](/azure/azure-functions/functions-bindings-storage) F # örnekleri içerir.

## <a name="using-azure-app-service-with-f"></a>Azure uygulama hizmeti F # ile kullanma #

[Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/) güçlü web ve Bulut veya şirket içi herhangi bir yerden, veri bağlanmak mobil uygulamaları oluşturmak için bir bulut Platform.

* [F # Azure Web API örneği](https://github.com/fsprojects/azure-webapi-example)
* [F # Azure üzerinde bir web uygulamasında barındırma](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Apache Spark F # Azure Hdınsight ile kullanma

[Azure Hdınsight'ta Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) büyük ölçekli veri analizi uygulamaları çalıştıran bir açık kaynak işleme altyapısıdır. Azure Apache Spark, kolay ve dağıtmak için uygun maliyetli hale getirir. F # kullanarak Spark uygulamanızı geliştirin [Mobius](https://github.com/Microsoft/Mobius), Spark için bir .NET API.

* [F # Mobius kullanarak uygulama Spark uygulamaları](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Örnek F # Spark Mobius kullanan uygulamalar](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Azure Cosmos DB F # ile kullanma #

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) yüksek oranda kullanılabilir, genel olarak dağıtılmış uygulamalar için bir NoSQL hizmetidir.

Azure Cosmos DB F # ile iki şekilde kullanılabilir:

1. F # Azure işlevleri oluşturulmasını aracılığıyla hangi tepki veya Azure Cosmos DB koleksiyonlarda yapılan değişiklikler neden olabilir. Bkz: [Azure işlevleri için Azure Cosmos DB bağlamaları](/azure/azure-functions/functions-bindings-cosmosdb), veya
2. Kullanarak [SQL API için Azure Cosmos DB .NET SDK](/azure/cosmos-db/sql-api-sdk-dotnet). İlgili C# ' ta örneklerdir.

## <a name="using-azure-event-hubs-with-f"></a>Azure Event Hubs'a F # ile kullanma #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) bulut ölçekli telemetri alım Web siteleri, uygulamaları ve cihazları sağlayın.

Azure Event Hubs F # ile iki şekilde kullanılabilir:

1. F # Azure işlevleri oluşturulmasını, olaylar tarafından tetiklenen. Bkz: [Azure Event Hubs için Tetikleyiciler](/azure/azure-functions/functions-bindings-event-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Bu örnekler C# dilinde olduğunu unutmayın.

## <a name="using-azure-notification-hubs-with-f"></a>Azure bildirim hub'ları F # ile kullanma #

[Azure bildirim hub'ları](/azure/notification-hubs/) herhangi bir arka uçtan (içinde bulutta veya şirket içi) herhangi bir mobil platforma mobil anında iletme bildirimleri göndermek etkinleştirmeniz çok platformlu, ölçeği gönderim altyapısı şunlardır.

Azure bildirim hub'ları F # ile iki şekilde kullanılabilir:

1. F # Azure işlevleri oluşturulmasını, bir bildirim hub'ına sonuçları gönderir. Bkz: [Azure işlevi bildirim hub'ları için Tetikleyiciler çıkış](/azure/azure-functions/functions-bindings-notification-hubs), veya
2. Kullanarak [için Azure .NET SDK'sı](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Bu örnekler C# dilinde olduğunu unutmayın.


## <a name="implementing-webhooks-on-azure-with-f"></a>F # ile Azure üzerinde Web Kancalarını uygulama #

A [Web kancası](https://en.wikipedia.org/wiki/Webhook) olan bir web isteği tetiklenen geri çağırma. Web kancası sinyal olayları GitHub gibi siteleri tarafından kullanılır. 

Web kancası F # içinde uygulanan ve Azure üzerinde barındırılan bir [Azure işlevi F # Web kancası bağlama ile](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Webjobs F # ile kullanma #

[Web işleri](/azure/app-service-web/web-sites-create-web-jobs) programları App Service web uygulamanızda üç yolla çalıştırabilirsiniz: isteğe bağlı olarak, sürekli olarak veya bir zamanlamaya göre.

[Örnek F # Webjob](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a>F # ile Azure üzerinde zamanlayıcılar uygulama #

Zamanlayıcı bir zamanlama, bir kez veya yinelenen göre işlevlerine çağrı tetikler.

Zamanlayıcılar F # içinde uygulanan ve Azure üzerinde barındırılan bir [Azure işlevi F # Zamanlayıcı tetikleyicisi ile](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Dağıtma ve F # kodlarıyla Azure kaynaklarını yönetme #

Azure VM'ler programlı olarak dağıtılan ve F # komut dosyalarından Microsoft.Azure.Management paketleri ve API'leri kullanılarak yönetilen. Örneğin, [.NET için yönetim kitaplıkları ile çalışmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [kullanarak Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Benzer şekilde, diğer Azure kaynaklarına de dağıtılan ve aynı Bileşenleri'ni kullanarak F # betiklerinden yönetilen. Örneğin, depolama hesapları, Azure bulut Hizmetleri dağıtma, Azure Cosmos DB örnekleri oluşturmak oluşturup Azure gönderemedi hub'ları programlı olarak F # komut dosyalarından yönetebilirsiniz.

Dağıtmak ve kaynakları yönetmek için F # komut dosyalarını kullanarak normal şekilde gerekli değildir. Örneğin, Azure kaynaklarını parametreli olabilir JSON şablonu açıklamaları gelen dağıtılan directy olabilir. Bkz: [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) örnekler gibi dahil [Azure hızlı başlangıç şablonlarını](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure hizmetleri hakkında tüm belgeleri](/azure/)
