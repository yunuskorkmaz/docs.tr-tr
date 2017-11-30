---
title: "F # Azure üzerinde kullanma"
description: "F # ile Azure hizmetlerini kullanmaya Kılavuzu"
keywords: "Azure, bulut, visual f #, f #'ta, .NET, .NET Core işlevsel programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: 636604b1a0b645f13ac20d7ed85bde9abae3f9f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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

* [F # Suave kullanarak Azure işlevleri ölçeklendirin](http://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [F #'de Azure işlevi oluşturma](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure türü sağlayıcısı ile Azure işlevlerini kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Azure Storage F # ile kullanma #

Azure depolama, depolama hizmetleri dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik müşterilerin ihtiyaçlarını karşılamak üzere kullanan modern uygulamalar için temel bir katmanıdır. F # programları, doğrudan aşağıdaki makalelerde açıklanan techinques kullanarak Azure storage Hizmetleri ile etkileşim kurabilir.

* [F # kullanarak Azure Blob storage'ı kullanmaya başlama](blob-storage.md)
* [F # kullanarak Azure File storage'ı kullanmaya başlama](file-storage.md)
* [F # kullanarak Azure kuyruk depolamaya başlayın](queue-storage.md)
* [F # kullanarak Azure Table storage'ı kullanmaya başlama](table-storage.md)

Azure depolama, Azure işlevleri ile birlikte açık API çağrıları yerine bildirim temelli yapılandırma aracılığıyla da kullanılabilir. Bkz: [Azure işlevleri Tetikleyicileri ve bağlamaları için Azure Storage](/azure/azure-functions/functions-bindings-storage) F # örnekleri içerir.

## <a name="using-azure-app-service-with-f"></a>Azure uygulama hizmeti F # ile kullanma #

[Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/) güçlü web ve Bulut veya şirket içi herhangi bir yerden, veri bağlanmak mobil uygulamaları oluşturmak için bir bulut Platform.

* [F # Azure Web API örneği](https://github.com/fsprojects/azure-webapi-example)
* [F # Azure üzerinde bir web uygulamasında barındırma](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Apache Spark F # Azure Hdınsight ile kullanma

[Azure Hdınsight'ta Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) büyük ölçekli veri analizi uygulamaları çalıştıran bir açık kaynak işleme altyapısıdır. Azure Apache Spark, kolay ve dağıtmak için uygun maliyetli hale getirir. F # kullanarak Spark uygulamanızı geliştirin [Mobius](https://github.com/Microsoft/Mobius), Spark için bir .NET API.

* [F # Mobius kullanarak uygulama Spark uygulamaları](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Örnek F # Spark Mobius kullanan uygulamalar](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-documentdb-with-f"></a>Azure DocumentDB F # ile kullanma #

[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) yüksek oranda kullanılabilir, genel olarak dağıtılmış uygulamalar için bir NoSQL hizmetidir.

Azure DocumentDB F # ile iki şekilde kullanılabilir:

1. F # Azure işlevleri oluşturulmasını aracılığıyla hangi tepki veya DocumentDB koleksiyonlarda yapılan değişiklikler neden olabilir. Bkz: [Azure DocumentDB için Tetikleyiciler](/azure/azure-functions/functions-bindings-documentdb), veya
2. Kullanarak [için Azure .NET SDK'sı](/azure/documentdb/documentdb-get-started-quickstart). Bu örnekler C# dilinde olduğunu unutmayın.

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

Benzer şekilde, diğer Azure kaynaklarına de dağıtılan ve aynı Bileşenleri'ni kullanarak F # betiklerinden yönetilen. Örneğin, depolama hesabı oluşturma, Azure bulut Hizmetleri dağıtma, Azure DocumentDB örneği oluşturabilir ve Azure gönderemedi hub F # komut dosyalarından programlı olarak yönetmek.

Dağıtmak ve kaynakları yönetmek için F # komut dosyalarını kullanarak normal şekilde gerekli değildir. Örneğin, Azure kaynaklarını parametreli olabilir JSON şablonu açıklamaları gelen dağıtılan directy olabilir. Bkz: [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) örnekler gibi dahil [Azure hızlı başlangıç şablonlarını](https://azure.microsoft.com/documentation/templates/).

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure hizmetleri hakkında tüm belgeleri](/azure/)
