---
title: Azure’da F# Kullanma
description: 'F ile Azure hizmetlerini kullanma kılavuzu #'
author: sylvanc
ms.date: 07/29/2020
ms.openlocfilehash: 24ef3fd14a4d0173935fac3e67aadf86110fa6d8
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517379"
---
# <a name="using-f-on-azure"></a>Azure’da F# Kullanma

F #, bulut programlamaya yönelik mükemmel bir dildir ve Web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro hizmetler ve ölçeklenebilir veri işleme için sık sık kullanılır.

Aşağıdaki bölümlerde, F # ile bir dizi Azure hizmetini nasıl kullanacağınızı öğrenmek için kaynaklar bulacaksınız.

> [!NOTE]
> Belirli bir Azure hizmeti bu belge kümesinde değilse, lütfen bu hizmetin Azure Işlevlerine veya .NET belgelerine danışın. Bazı Azure hizmetleri dilden bağımsızdır ve dile özgü bir belge gerektirmez ve burada listelenmez.

## <a name="using-azure-virtual-machines-with-f"></a>Azure sanal makinelerini F ile kullanma\#

Azure, çok çeşitli sanal makine (VM) yapılandırmasını destekler, bkz. [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).

Yürütme, derleme ve/veya komut dosyası oluşturma için bir sanal makineye F # yüklemek için bkz. [Linux üzerinde f # kullanma](https://fsharp.org/use/linux) ve [Windows üzerinde f #](https://fsharp.org/use/windows)kullanma.

## <a name="using-azure-functions-with-f"></a>F ile Azure Işlevleri kullanma\#

[Azure işlevleri](https://azure.microsoft.com/services/functions/) , küçük kod parçalarını veya bulutta "işlevleri" kolayca çalıştırmaya yönelik bir çözümdür. Tüm uygulama veya bunu çalıştıracak altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz. İşlevleriniz, Azure depolama 'daki olaylara ve bulut tarafından barındırılan diğer kaynaklara bağlanır. Veri, işlev bağımsız değişkenleri aracılığıyla F # işlevleriniz içine akar. Tercih ettiğiniz geliştirme dilini kullanarak istediğiniz kadar ölçeklendirerek Azure 'a erişebilirsiniz.

Azure Işlevleri, f # kodu verimli, reaktif, ölçeklenebilir yürütmesi olan birinci sınıf bir dil olarak F # destekler. Azure Işlevleri ile F # kullanma hakkında başvuru belgeleri için bkz. [Azure Işlevleri f # geliştirici başvurusu](/azure/azure-functions/functions-reference-fsharp) .

Azure Işlevleri ve F # kullanmaya yönelik diğer kaynaklar:

* [Suave kullanarak F # içindeki Azure Işlevlerini ölçeklendirin](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [F 'de Azure işlevi oluşturma #](https://www.mnie.me/azurefunctions)
* [Azure Işlevleri ile Azure tür sağlayıcısını kullanma](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>F ile Azure Storage kullanma\#

Azure depolama, müşterilerin ihtiyaçlarını karşılamak üzere dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik kullanan modern uygulamalar için bir temel depolama hizmetleri katmanıdır. F # programları, aşağıdaki makalelerde açıklanan teknikleri kullanarak doğrudan Azure Storage Services ile etkileşime geçebilir.

* [F# kullanarak Azure Blob depolama kullanmaya başlama](blob-storage.md)
* [F# kullanarak Azure Dosya depolama kullanmaya başlama](file-storage.md)
* [F# kullanarak Azure Kuyruk depolama kullanmaya başlama](queue-storage.md)
* [F# kullanarak Azure Tablo depolama kullanmaya başlama](table-storage.md)

Azure depolama Ayrıca, açık API çağrıları yerine bildirim temelli yapılandırma aracılığıyla Azure Işlevleri ile birlikte kullanılabilir. F # örnekleri içeren Azure [depolama Için Azure işlevleri Tetikleyicileri ve bağlamaları](/azure/azure-functions/functions-bindings-storage) bölümüne bakın.

## <a name="using-azure-app-service-with-f"></a>F ile Azure App Service kullanma\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) , bulutta veya şirket içinde verilere her yerden bağlanan güçlü web uygulamaları ve mobil uygulamalar oluşturmak için kullanılan bir bulut platformudur.

* [F # Azure Web API örneği](https://github.com/fsprojects/azure-webapi-example)
* [Azure 'da bir Web uygulamasında F # barındırma](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a>Azure HDInsight veya Azure Databricks 'de F # ile Apache Spark kullanma

[Azure HDInsight için Apache Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) , büyük ölçekli veri analizi uygulamalarını çalıştıran bir açık kaynak işleme çerçevesidir. [Azure Databricks](https://docs.microsoft.com/azure/databricks/scenarios/what-is-azure-databricks), Microsoft Azure bulut hizmetleri platformu için iyileştirilen Apache Spark tabanlı bir analiz platformudur. Azure, dağıtıma Apache Spark kolaylaştırır ve ekonomik hale gelir. Apache Spark için bir dizi .NET bağlaması olan [Apache Spark için .net](../../spark/what-is-apache-spark-dotnet.md)kullanarak Spark uygulamanızı geliştirin.

* [Apache Spark F # örnekleri için .NET](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.FSharp.Examples)
* [Azure HDInsight 'a .NET etkileşimli Jupyıter not defterlerini yükler](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [Azure HDInsight 'a Apache Spark işleri gönderme](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [Azure Databricks Apache Spark işleri gönder](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a>F ile Azure Cosmos DB kullanma\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) , yüksek oranda kullanılabilir, genel olarak dağıtılmış uygulamalar Için bir NoSQL hizmetidir.

Azure Cosmos DB, F # ile iki şekilde kullanılabilir:

1. Azure Cosmos DB koleksiyonlarındaki değişikliklere tepki veren veya bunlara neden olan F # Azure Işlevlerinin oluşturulması aracılığıyla. Bkz. [Azure işlevleri için Azure Cosmos DB bağlamaları](/azure/azure-functions/functions-bindings-cosmosdb)veya
2. [SQL API için Azure Cosmos DB .NET SDK 'yı](/azure/cosmos-db/sql-api-sdk-dotnet)kullanarak. İlgili örnekler C# ' de bulunur.

## <a name="using-azure-event-hubs-with-f"></a>F ile Azure Event Hubs kullanma\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) , Web sitelerinden, uygulamalardan ve cihazlardan bulut ölçekli telemetri alımı sağlar.

Azure Event Hubs, F # ile iki şekilde kullanılabilir:

1. Olaylar tarafından tetiklenen F # Azure Işlevlerinin oluşturulması aracılığıyla. [Event Hubs Için Azure işlev tetikleyicilerine](/azure/azure-functions/functions-bindings-event-hubs)bakın veya
2. [Azure için .NET SDK 'yı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted)kullanarak. Bu örneklerin C# dilinde olduğunu aklınızda edin.

## <a name="using-azure-notification-hubs-with-f"></a>F ile Azure Notification Hubs kullanma\#

[Azure Notification Hubs](/azure/notification-hubs/) , herhangi bir arka uçtan (bulutta veya şirket içinde) herhangi bir mobil platforma mobil anında iletme bildirimleri göndermenize olanak tanıyan çok platformlu, genişleme bir gönderim altyapısıdır.

Azure Notification Hubs, F # ile iki şekilde kullanılabilir:

1. Bir Bildirim Hub 'ına sonuçları gönderen F # Azure Işlevlerinin oluşturulması aracılığıyla. [Notification Hubs Için Azure işlev çıkış tetikleyicilerine](/azure/azure-functions/functions-bindings-notification-hubs)bakın veya
2. [Azure için .NET SDK 'yı](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend)kullanarak. Bu örneklerin C# dilinde olduğunu aklınızda edin.

## <a name="implementing-webhooks-on-azure-with-f"></a>F ile Azure 'da Web kancaları uygulama\#

Web [kancası](https://en.wikipedia.org/wiki/Webhook) , bir Web isteği aracılığıyla tetiklenen bir geri çağırmasıdır. Web kancaları GitHub gibi siteler tarafından olayları işaret etmek için kullanılır.

Web kancaları F # ' da uygulanabilir ve [bir Web kancası bağlaması Ile f # içindeki bir Azure işlevi](/azure/azure-functions/functions-bindings-http-webhook)aracılığıyla Azure 'da barındırılabilir.

## <a name="using-webjobs-with-f"></a>F ile WebJobs kullanma\#

[WebJobs](/azure/app-service-web/web-sites-create-web-jobs) , App Service Web uygulamanızda çalıştırdığınız programlardır. isteğe bağlı, sürekli veya bir zamanlamaya göre.

[Örnek F # WebJob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>F ile Azure 'da zamanlayıcılar uygulama\#

Zamanlayıcı, bir zamanlamaya göre, bir kez veya yinelenen işlevleri çağırır.

Süreölçerler, F # ' da uygulanabilir ve [bir Zamanlayıcı tetikleyicisi Ile f # içindeki bir Azure işlevi](/azure/azure-functions/functions-bindings-timer)aracılığıyla Azure 'da barındırılabilir.

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>F # betiklerle Azure kaynaklarını dağıtma ve yönetme

Azure VM 'leri, Microsoft. Azure. Yönetim paketleri ve API 'Leri kullanılarak, F # betiklerinden programlı bir şekilde dağıtılabilir ve yönetilebilir. Örneğin, bkz. [.net Için yönetim kitaplıklarını kullanmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [Azure Resource Manager kullanma](/azure/azure-resource-manager/resource-manager-deployment-model).

Benzer şekilde, diğer Azure kaynakları da aynı bileşenleri kullanarak F # betiklerinden dağıtılabilir ve yönetilebilir. Örneğin, bir depolama hesabı oluşturabilir, Azure Cloud Services dağıtabilir, Azure Cosmos DB örnekleri oluşturabilir ve Azure Notification Hubs F # betiklerinden programlı bir şekilde yönetebilirsiniz.

Kaynakları dağıtmak ve yönetmek için F # betikleri kullanılması normalde gerekli değildir. Örneğin, Azure kaynakları, parametreleştirilen parametreli bir şekilde doğrudan JSON şablonu açıklamalarından da dağıtılabilir. Bkz. [Azure hızlı başlangıç şablonları](https://azure.microsoft.com/resources/templates/)gibi örnekler de [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) .

## <a name="other-resources"></a>Diğer kaynaklar

* [Tüm Azure hizmetlerinde tam belgeler](/azure/)
