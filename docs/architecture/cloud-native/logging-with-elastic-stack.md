---
title: Elastik Yığın ile günlüğe kaydetme
description: Elastik yığın, Logstash ve kibana kullanarak günlüğe kaydetme
ms.date: 02/05/2020
ms.openlocfilehash: 6863c66b63854fe3ecaabe2919beded2926ea64c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448935"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="acdd9-103">Elastik Yığın ile günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="acdd9-103">Logging with Elastic Stack</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="acdd9-104">Birçok iyi Merkezi günlük aracı vardır ve daha pahalı seçeneklere karşı ücretsiz, açık kaynaklı araçlar ve maliyet bakımından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="acdd9-105">Birçok durumda, ücretsiz araçlar ücretli tekliflerle veya daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="acdd9-106">Bu tür bir araç, üç açık kaynaklı bileşen birleşimidir: elastik arama, Logstash ve kibana.</span><span class="sxs-lookup"><span data-stu-id="acdd9-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="acdd9-107">Toplu olarak bu araçlar elastik yığın veya ELK yığını olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="acdd9-108">Elastik yığın</span><span class="sxs-lookup"><span data-stu-id="acdd9-108">Elastic Stack</span></span>

<span data-ttu-id="acdd9-109">Elastik yığın, bir Kubernetes kümesinden bilgi toplamak için güçlü bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="acdd9-110">Kubernetes, bir Elakes arama uç noktasına günlük göndermeyi destekler ve [çoğu bölüm](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)Için, Şekil 7-5 ' de gösterildiği gibi, ortam değişkenlerini ayarlamak gerekir:</span><span class="sxs-lookup"><span data-stu-id="acdd9-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="acdd9-111">**Şekil 7-5**.</span><span class="sxs-lookup"><span data-stu-id="acdd9-111">**Figure 7-5**.</span></span> <span data-ttu-id="acdd9-112">Kubernetes için yapılandırma değişkenleri</span><span class="sxs-lookup"><span data-stu-id="acdd9-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="acdd9-113">Bu, küme üzerinde elaa araması yükleyecek ve tüm küme günlüklerini buna gönderen hedeflenecek.</span><span class="sxs-lookup"><span data-stu-id="acdd9-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="acdd9-114">Kubernetes](./media/kibana-dashboard.png)
**şekil 7-6**' den alınan günlüklere yönelik sorgu sonuçlarının gösterildiği bir kibana panosu örneği ![.</span><span class="sxs-lookup"><span data-stu-id="acdd9-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="acdd9-115">Kubernetes 'ten alınan günlüklere yönelik bir sorgunun sonuçlarını gösteren bir kibana panosu örneği</span><span class="sxs-lookup"><span data-stu-id="acdd9-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="acdd9-116">Esnek yığının avantajları nelerdir?</span><span class="sxs-lookup"><span data-stu-id="acdd9-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="acdd9-117">Elastik yığın, düşük maliyetli, ölçeklenebilir, bulut kullanımı kolay bir şekilde Merkezi günlük kaydı sağlar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="acdd9-118">Kullanıcı arabirimi, veri analizini kolaylaştırarak, bir clunky arabirimi ile uğraşmaya değil, verilerinizden verilerinize yönelik Öngörüler elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acdd9-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="acdd9-119">Dağıtılmış uygulamanız daha fazla ve farklı hizmet türlerine yayıldığında, günlük ve ölçüm verilerini sisteme akışa almaya devam etmeyi beklemeniz için çok çeşitli girdileri destekler.</span><span class="sxs-lookup"><span data-stu-id="acdd9-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="acdd9-120">Elastik yığın, büyük veri kümelerinde bile hızlı aramaları destekler, böylece büyük uygulamalar ayrıntılı verileri günlüğe kaydeder ve yine de bir performans üzerinde görünebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="acdd9-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="acdd9-121">Logstash</span></span>

<span data-ttu-id="acdd9-122">İlk bileşen [Logstash](https://www.elastic.co/products/logstash)' dir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="acdd9-123">Bu araç, çok çeşitli farklı kaynaklardan günlük bilgilerini toplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="acdd9-124">Örneğin Logstash, günlükleri diskten okuyabilir ve ayrıca [Serilog](https://serilog.net/)gibi günlük kitaplıklarından iletiler alabilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="acdd9-125">Logstash, geldikçe günlüklerde bazı temel filtreleme ve genişleme işlemlerini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="acdd9-126">Örneğin, günlükleriniz IP adresleri içeriyorsa, Logstash coğrafi arama yapmak ve bu ileti için bir ülke veya hatta kaynak şehir almak üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="acdd9-127">Serilog, parametreli günlüğe kaydetmeye olanak sağlayan .NET dilleri için bir günlüğe kaydetme kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="acdd9-128">Alanları katıştıran bir metin günlüğü iletisi oluşturmak yerine Parametreler ayrı tutulur.</span><span class="sxs-lookup"><span data-stu-id="acdd9-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="acdd9-129">Bu, daha akıllı filtreleme ve arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="acdd9-130">Şekil 7-7 ' de Logstash yazmak için örnek bir Serilog yapılandırması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="acdd9-131">**Şekil 7-7**.</span><span class="sxs-lookup"><span data-stu-id="acdd9-131">**Figure 7-7**.</span></span> <span data-ttu-id="acdd9-132">HTTP üzerinden logstash 'e doğrudan günlük bilgilerini yazmak için Serilog config</span><span class="sxs-lookup"><span data-stu-id="acdd9-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="acdd9-133">Logstash, Şekil 7-8 ' de gösterilen şekilde bir yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="acdd9-134">**Şekil 7-8**.</span><span class="sxs-lookup"><span data-stu-id="acdd9-134">**Figure 7-8**.</span></span> <span data-ttu-id="acdd9-135">Serilog 'dan günlük tüketme için bir Logstash yapılandırması</span><span class="sxs-lookup"><span data-stu-id="acdd9-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="acdd9-136">Kapsamlı günlük işleme gerekli olmadığı senaryolar için, [tempts](https://www.elastic.co/products/beats)olarak bilinen Logstash için bir alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="acdd9-137">Pts, günlüklerdeki ağ verilerine ve çalışma süresi bilgilerine çok çeşitli veriler toplayabilen bir araç ailesidir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="acdd9-138">Birçok uygulama, hem Logstash hem de Pts 'yi kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="acdd9-139">Günlükler Logstash tarafından toplandıktan sonra, bunları yerleştirmek için bir yere ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="acdd9-140">Logstash birçok farklı çıkışı desteklese de, daha heyecan verici bir arama, elastik aramalardır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="acdd9-141">Elastik arama</span><span class="sxs-lookup"><span data-stu-id="acdd9-141">Elastic search</span></span>

<span data-ttu-id="acdd9-142">Elastik arama, geldikçe günlükleri dizinlebilecekleri güçlü bir arama altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="acdd9-143">Günlüklere hızlı şekilde çalışan sorgular yapar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="acdd9-144">Elastik arama çok büyük miktarlarda günlüğü işleyebilir ve olağanüstü durumlarda birçok düğüm arasında ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="acdd9-145">Parametreleri içermesi için üretilmiş olan veya parametreleri Logstash işleme aracılığıyla bölüşdüğü olan günlük iletileri, bu bilgileri koruyan şekilde doğrudan sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="acdd9-146">`jill@example.com`tarafından ziyaret edilen ilk 10 sayfayı arayan sorgu Şekil 7-9 ' de görünür.</span><span class="sxs-lookup"><span data-stu-id="acdd9-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="acdd9-147">**Şekil 7-9**.</span><span class="sxs-lookup"><span data-stu-id="acdd9-147">**Figure 7-9**.</span></span> <span data-ttu-id="acdd9-148">Bir kullanıcı tarafından ziyaret edilen ilk 10 sayfayı bulmak için bir elaa arama sorgusu</span><span class="sxs-lookup"><span data-stu-id="acdd9-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="acdd9-149">Kibana Web panolarıyla bilgi görselleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="acdd9-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="acdd9-150">Yığının son bileşeni kibana.</span><span class="sxs-lookup"><span data-stu-id="acdd9-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="acdd9-151">Bu araç, bir Web panosunda etkileşimli görselleştirmeler sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="acdd9-152">Panolar, teknik olmayan kullanıcılar tarafından da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="acdd9-153">Elaun Search dizininde yerleşik olan çoğu veri, kibana panolarına dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="acdd9-154">Bireysel kullanıcılar farklı Pano isteklerine sahip olabilir ve kibana Bu özelleştirmeyi kullanıcıya özgü panolara izin vererek sağlar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="acdd9-155">Azure 'da elastik yığın yükleme</span><span class="sxs-lookup"><span data-stu-id="acdd9-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="acdd9-156">Esnek yığın, çeşitli yollarla Azure 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="acdd9-157">Her zaman olduğu gibi, [sanal makineler sağlamak ve doğrudan elastik yığın yüklemek](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)mümkündür.</span><span class="sxs-lookup"><span data-stu-id="acdd9-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="acdd9-158">Bu seçenek, deneyimli bazı kullanıcılar tarafından, en yüksek özelleştirme derecesini sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="acdd9-159">Bir hizmet olarak altyapıya dağıtım, bu yolu alan bir hizmet olarak altyapı ile ilişkili tüm görevlerin sahipliğini alma ve düzeltme ekleriyle güncel tutmaya yönelik önemli yönetim yükü sunar.</span><span class="sxs-lookup"><span data-stu-id="acdd9-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="acdd9-160">Daha az ek yük olan bir seçenek, elastik yığının zaten yapılandırıldığı birçok Docker kapsayıcılarından birini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="acdd9-161">Bu kapsayıcılar, var olan bir Kubernetes kümesine bırakılabilir ve uygulama kodu ile birlikte çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="acdd9-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="acdd9-162">[Sebp/elk](https://elk-docker.readthedocs.io/) kapsayıcısı iyi belgelenmiş ve test edilmiş bir elastik yığın kapsayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="acdd9-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="acdd9-163">Diğer bir seçenek [de, son bildirilen bir hizmet olarak yeni tekliftir](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="acdd9-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="acdd9-164">Başvurular</span><span class="sxs-lookup"><span data-stu-id="acdd9-164">References</span></span>

- [<span data-ttu-id="acdd9-165">Azure 'da elastik yığın yüklemesi</span><span class="sxs-lookup"><span data-stu-id="acdd9-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="acdd9-166">[Önceki](observability-patterns.md)
>[İleri](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="acdd9-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
