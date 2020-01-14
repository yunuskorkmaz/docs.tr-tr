---
title: Azure’da F# Kullanma
description: İle Azure hizmetlerini kullanma kılavuzuF#
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 6cf2951092074a7fab6707c8ed26bda125ea00b0
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935531"
---
# <a name="using-f-on-azure"></a>Azure’da F# Kullanma

F#, bulut programlamasına yönelik mükemmel bir dildir ve Web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro hizmetler ve ölçeklenebilir veri işleme için sık sık kullanılır.

Aşağıdaki bölümlerde, ile F#bir dizi Azure hizmetinin kullanımıyla ilgili kaynakları bulacaksınız.

> [!NOTE]
> Belirli bir Azure hizmeti bu belge kümesinde değilse, lütfen bu hizmetin Azure Işlevlerine veya .NET belgelerine danışın. Bazı Azure hizmetleri dilden bağımsızdır ve dile özgü bir belge gerektirmez ve burada listelenmez.

## <a name="using-azure-virtual-machines-with-f"></a>Azure sanal makinelerini F\# kullanma

Azure, çok çeşitli sanal makine (VM) yapılandırmasını destekler, bkz. [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).

Yürütme, F# derleme ve/veya komut dosyası oluşturma için bir sanal makineye yüklemek için bkz. [Linux üzerinde kullanma F# ](https://fsharp.org/use/linux) ve [Windows 'da kullanma F# ](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Azure Işlevlerini F\# ile kullanma

[Azure işlevleri](https://azure.microsoft.com/services/functions/) , küçük kod parçalarını veya bulutta "işlevleri" kolayca çalıştırmaya yönelik bir çözümdür. Tüm uygulama veya bunu çalıştıracak altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz. İşlevleriniz, Azure depolama 'daki olaylara ve bulut tarafından barındırılan diğer kaynaklara bağlanır. Veri, işlevleriniz F# içinde işlev bağımsız değişkenleri aracılığıyla akar. Tercih ettiğiniz geliştirme dilini kullanarak istediğiniz kadar ölçeklendirerek Azure 'a erişebilirsiniz.

Azure Işlevleri, F# etkin, reaktif ve ölçeklenebilir F# kod yürütmesiyle birinci sınıf bir dil olarak destekler. Azure Işlevleri ile birlikte kullanma F# hakkında başvuru belgeleri için bkz. [Azure işlevleri F# geliştirici başvurusu](/azure/azure-functions/functions-reference-fsharp) .

Azure Işlevleri 'ni kullanmaya yönelik diğer kaynaklar F#ve:

* [Suave kullanarak Azure Işlevlerini F# ölçeklendirin](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [İçinde Azure işlevi oluşturmaF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure Işlevleri ile Azure tür sağlayıcısını kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Azure Storage 'ı F\# kullanma

Azure depolama, müşterilerin ihtiyaçlarını karşılamak üzere dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik kullanan modern uygulamalar için bir temel depolama hizmetleri katmanıdır. F#Programlar, aşağıdaki makalelerde açıklanan teknikleri kullanarak doğrudan Azure Storage Services ile etkileşime geçebilir.

* [F# kullanarak Azure Blob depolama kullanmaya başlama](blob-storage.md)
* [F# kullanarak Azure Dosya depolama kullanmaya başlama](file-storage.md)
* [F# kullanarak Azure Kuyruk depolama kullanmaya başlama](queue-storage.md)
* [F# kullanarak Azure Tablo depolama kullanmaya başlama](table-storage.md)

Azure depolama Ayrıca, açık API çağrıları yerine bildirim temelli yapılandırma aracılığıyla Azure Işlevleri ile birlikte kullanılabilir. Örnekleri içeren F# Azure [depolama için Azure işlevleri Tetikleyicileri ve bağlamaları](/azure/azure-functions/functions-bindings-storage) bölümüne bakın.

## <a name="using-azure-app-service-with-f"></a>F\# ile Azure App Service kullanma

[Azure App Service](https://azure.microsoft.com/services/app-service/) , bulutta veya şirket içinde verilere her yerden bağlanan güçlü web uygulamaları ve mobil uygulamalar oluşturmak için kullanılan bir bulut platformudur.

* [F#Azure Web API örneği](https://github.com/fsprojects/azure-webapi-example)
* [Azure F# 'da bir Web uygulamasında barındırma](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Azure HDInsight F# ile Apache Spark kullanma

[Azure HDInsight için Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) , büyük ölçekli veri analizi uygulamalarını çalıştıran bir açık kaynak işleme çerçevesidir. Azure, dağıtıma Apache Spark kolaylaştırır ve ekonomik hale gelir. Spark için .NET API 'SI F# olan [Mobius](https://github.com/Microsoft/Mobius)kullanarak Spark uygulamanızı geliştirin.

* [Mobius F# kullanarak Spark uygulamalarını uygulama](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Mobius kullanarak örnek F# Spark uygulamaları](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>F\# ile Azure Cosmos DB kullanma

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) , yüksek oranda kullanılabilir, genel olarak dağıtılmış uygulamalar Için bir NoSQL hizmetidir.

Azure Cosmos DB, iki şekilde ile F# kullanılabilir:

1. Azure Cosmos DB koleksiyonlarındaki değişikliklere tepki F# veren veya bunlara neden olan Azure işlevleri oluşturma. Bkz. [Azure işlevleri için Azure Cosmos DB bağlamaları](/azure/azure-functions/functions-bindings-cosmosdb)veya
2. [SQL API için Azure Cosmos DB .NET SDK 'yı](/azure/cosmos-db/sql-api-sdk-dotnet)kullanarak. İlgili örnekler içinde C#bulunur.

## <a name="using-azure-event-hubs-with-f"></a>F\# ile Azure Event Hubs kullanma

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) , Web sitelerinden, uygulamalardan ve cihazlardan bulut ölçekli telemetri alımı sağlar.

Azure Event Hubs, iki şekilde kullanılabilir F# :

1. Olaylar tarafından tetiklenen F# Azure işlevlerinin oluşturulması. [Event Hubs Için Azure işlev tetikleyicilerine](/azure/azure-functions/functions-bindings-event-hubs)bakın veya
2. [Azure için .NET SDK 'yı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted)kullanarak. Bu örneklerin içinde C#olduğunu aklınızda edin.

## <a name="using-azure-notification-hubs-with-f"></a>F\# ile Azure Notification Hubs kullanma

[Azure Notification Hubs](/azure/notification-hubs/) , herhangi bir arka uçtan (bulutta veya şirket içinde) herhangi bir mobil platforma mobil anında iletme bildirimleri göndermenize olanak tanıyan çok platformlu, genişleme bir gönderim altyapısıdır.

Azure Notification Hubs, iki şekilde kullanılabilir F# :

1. Bir Bildirim Hub 'ına F# sonuçları gönderen Azure işlevleri oluşturma yoluyla. [Notification Hubs Için Azure işlev çıkış tetikleyicilerine](/azure/azure-functions/functions-bindings-notification-hubs)bakın veya
2. [Azure için .NET SDK 'yı](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend)kullanarak. Bu örneklerin içinde C#olduğunu aklınızda edin.

## <a name="implementing-webhooks-on-azure-with-f"></a>F\# ile Azure 'da Web kancaları uygulama

Web [kancası](https://en.wikipedia.org/wiki/Webhook) , bir Web isteği aracılığıyla tetiklenen bir geri çağırmasıdır. Web kancaları GitHub gibi siteler tarafından olayları işaret etmek için kullanılır.

Web kancaları, ' de F# [bir Web kancası bağlamasıyla Içindeki F# bir Azure işlevi](/azure/azure-functions/functions-bindings-http-webhook)aracılığıyla Azure 'da barındırılabilir.

## <a name="using-webjobs-with-f"></a>Web Işlerini F\# kullanma

[WebJobs](/azure/app-service-web/web-sites-create-web-jobs) , App Service Web uygulamanızda çalıştırdığınız programlardır. isteğe bağlı, sürekli veya bir zamanlamaya göre.

[Örnek F# WebJob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>F\# ile Azure 'da zamanlayıcılar uygulama

Zamanlayıcı, bir zamanlamaya göre, bir kez veya yinelenen işlevleri çağırır.

Zamanlayıcılar, ' de [bir Zamanlayıcı tetikleyicisiyle F# ' de bir Azure işlevi](/azure/azure-functions/functions-bindings-timer)aracılığıyla Azure 'da barındırılabilir. F#

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Azure kaynaklarını betiklerle F# dağıtma ve yönetme

Azure VM 'Ler, Microsoft. Azure. Yönetim F# paketleri ve API 'leri kullanılarak program aracılığıyla dağıtılabilir ve betiklerden yönetilebilir. Örneğin, bkz. [.net Için yönetim kitaplıklarını kullanmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [Azure Resource Manager kullanma](/azure/azure-resource-manager/resource-manager-deployment-model).

Benzer şekilde, diğer Azure kaynakları aynı bileşenleri kullanan betiklerden F# de dağıtılabilir ve yönetilebilir. Örneğin, depolama hesapları oluşturabilir, Azure Cloud Services dağıtabilir, Azure Cosmos DB örnekleri oluşturabilir ve Azure notifcation hub 'Larını betiklerden F# programlı bir şekilde yönetebilirsiniz.

Kaynakları F# dağıtmak ve yönetmek için betikler kullanılması normalde gerekli değildir. Örneğin, Azure kaynakları, parametreleştirilen parametreli bir şekilde doğrudan JSON şablonu açıklamalarından da dağıtılabilir. Bkz. [Azure hızlı başlangıç şablonları](https://azure.microsoft.com/resources/templates/)gibi örnekler de [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) .

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure hizmetlerinde tam belgeler](/azure/)
