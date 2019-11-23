---
title: Elastik Yığın ile günlüğe kaydetme
description: Elastik yığın, Logstash ve kibana kullanarak günlüğe kaydetme
ms.date: 09/23/2019
ms.openlocfilehash: 989834925bc08541bf484e1a4567a56ac324872f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087063"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="437e3-103">Elastik Yığın ile günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="437e3-103">Logging with Elastic Stack</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="437e3-104">Birçok iyi Merkezi günlük aracı vardır ve daha pahalı seçeneklere karşı ücretsiz, açık kaynaklı araçlar ve maliyet bakımından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="437e3-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="437e3-105">Birçok durumda, ücretsiz araçlar ücretli tekliflerle veya daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="437e3-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="437e3-106">Bu tür bir araç, üç açık kaynaklı bileşen birleşimidir: elastik arama, Logstash ve kibana.</span><span class="sxs-lookup"><span data-stu-id="437e3-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>
<span data-ttu-id="437e3-107">Toplu olarak bu araçlar elastik yığın veya ELK yığını olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="437e3-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="437e3-108">Esnek yığının avantajları nelerdir?</span><span class="sxs-lookup"><span data-stu-id="437e3-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="437e3-109">Elastik yığın, düşük maliyetli, ölçeklenebilir, bulut kullanımı kolay bir şekilde Merkezi günlük kaydı sağlar.</span><span class="sxs-lookup"><span data-stu-id="437e3-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="437e3-110">Kullanıcı arabirimi, veri analizini kolaylaştırarak, bir clunky arabirimi ile uğraşmaya değil, verilerinizden verilerinize yönelik Öngörüler elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="437e3-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="437e3-111">Dağıtılmış uygulamanız daha fazla ve farklı hizmet türlerine yayıldığında, günlük ve ölçüm verilerini sisteme akışa almaya devam etmeyi beklemeniz için çok çeşitli girdileri destekler.</span><span class="sxs-lookup"><span data-stu-id="437e3-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="437e3-112">Elastik yığın, büyük veri kümelerinde bile hızlı aramaları destekler, böylece büyük uygulamalar ayrıntılı verileri günlüğe kaydeder ve yine de bir performans üzerinde görünebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="437e3-112">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="437e3-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="437e3-113">Logstash</span></span>

<span data-ttu-id="437e3-114">İlk bileşen [Logstash](https://www.elastic.co/products/logstash)' dir.</span><span class="sxs-lookup"><span data-stu-id="437e3-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="437e3-115">Bu araç, çok çeşitli farklı kaynaklardan günlük bilgilerini toplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="437e3-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="437e3-116">Örneğin Logstash, günlükleri diskten okuyabilir ve ayrıca [Serilog](https://serilog.net/)gibi günlük kitaplıklarından iletiler alabilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="437e3-117">Logstash, geldikçe günlüklerde bazı temel filtreleme ve genişleme işlemlerini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="437e3-118">Örneğin, günlükleriniz IP adresleri içeriyorsa, Logstash coğrafi arama yapmak ve bu ileti için bir ülke veya hatta kaynak şehir almak üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="437e3-119">Serilog, parametreli günlüğe kaydetmeye olanak sağlayan .NET dilleri için bir günlüğe kaydetme kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="437e3-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="437e3-120">Alanları katıştıran bir metin günlüğü iletisi oluşturmak yerine Parametreler ayrı tutulur.</span><span class="sxs-lookup"><span data-stu-id="437e3-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="437e3-121">Bu, daha akıllı filtreleme ve arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="437e3-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="437e3-122">Şekil 7-2 ' de Logstash yazmak için örnek bir Serilog yapılandırması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="437e3-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="437e3-123">**Şekil 7-2** HTTP üzerinden logstash 'e doğrudan günlük bilgilerini yazmak için Serilog config</span><span class="sxs-lookup"><span data-stu-id="437e3-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="437e3-124">Logstash, Şekil 7-3 ' de gösterilen şekilde bir yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="437e3-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span>

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

<span data-ttu-id="437e3-125">**Şekil 7-3** -Serilog 'dan günlük tüketme Için bir Logstash yapılandırması</span><span class="sxs-lookup"><span data-stu-id="437e3-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="437e3-126">Kapsamlı günlük işleme gerekli olmadığı senaryolar için, [tempts](https://www.elastic.co/products/beats)olarak bilinen Logstash için bir alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="437e3-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="437e3-127">Pts, günlüklerdeki ağ verilerine ve çalışma süresi bilgilerine çok çeşitli veriler toplayabilen bir araç ailesidir.</span><span class="sxs-lookup"><span data-stu-id="437e3-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="437e3-128">Birçok uygulama, hem Logstash hem de Pts 'yi kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="437e3-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="437e3-129">Günlükler Logstash tarafından toplandıktan sonra, bunları yerleştirmek için bir yere ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="437e3-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="437e3-130">Logstash birçok farklı çıkışı desteklese de, daha heyecan verici bir arama, elastik aramalardır.</span><span class="sxs-lookup"><span data-stu-id="437e3-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="437e3-131">Elastik arama</span><span class="sxs-lookup"><span data-stu-id="437e3-131">Elastic search</span></span>

<span data-ttu-id="437e3-132">Elastik arama, geldikçe günlükleri dizinlebilecekleri güçlü bir arama altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="437e3-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="437e3-133">Günlüklere hızlı şekilde çalışan sorgular yapar.</span><span class="sxs-lookup"><span data-stu-id="437e3-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="437e3-134">Elastik arama çok büyük miktarlarda günlüğü işleyebilir ve olağanüstü durumlarda birçok düğüm arasında ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="437e3-135">Parametreleri içermesi için üretilmiş olan veya parametreleri Logstash işleme aracılığıyla bölüşdüğü olan günlük iletileri, bu bilgileri koruyan şekilde doğrudan sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="437e3-136">`jill@example.com`tarafından ziyaret edilen ilk 10 sayfayı arayan sorgu Şekil 7-4 ' de görünür.</span><span class="sxs-lookup"><span data-stu-id="437e3-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

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

<span data-ttu-id="437e3-137">**Şekil 7-4** -bir kullanıcı tarafından ziyaret edilen ilk 10 sayfayı bulmak Için bir elaa arama sorgusu</span><span class="sxs-lookup"><span data-stu-id="437e3-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="437e3-138">Kibana Web panolarıyla bilgi görselleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="437e3-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="437e3-139">Yığının son bileşeni kibana.</span><span class="sxs-lookup"><span data-stu-id="437e3-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="437e3-140">Bu araç, bir Web panosunda etkileşimli görselleştirmeler sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="437e3-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="437e3-141">Panolar, teknik olmayan kullanıcılar tarafından da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="437e3-142">Elaun Search dizininde yerleşik olan çoğu veri, kibana panolarına dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="437e3-143">Bireysel kullanıcılar farklı Pano isteklerine sahip olabilir ve kibana Bu özelleştirmeyi kullanıcıya özgü panolara izin vererek sağlar.</span><span class="sxs-lookup"><span data-stu-id="437e3-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="437e3-144">Azure 'da elastik yığın yükleme</span><span class="sxs-lookup"><span data-stu-id="437e3-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="437e3-145">Esnek yığın, çeşitli yollarla Azure 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="437e3-146">Her zaman olduğu gibi, [sanal makineler sağlamak ve doğrudan elastik yığın yüklemek](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)mümkündür.</span><span class="sxs-lookup"><span data-stu-id="437e3-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="437e3-147">Bu seçenek, deneyimli bazı kullanıcılar tarafından, en yüksek özelleştirme derecesini sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="437e3-148">Bir hizmet olarak altyapıya dağıtım, bu yolu alan bir hizmet olarak altyapı ile ilişkili tüm görevlerin sahipliğini alma ve düzeltme ekleriyle güncel tutmaya yönelik önemli yönetim yükü sunar.</span><span class="sxs-lookup"><span data-stu-id="437e3-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="437e3-149">Daha az ek yük olan bir seçenek, elastik yığının zaten yapılandırıldığı birçok Docker kapsayıcılarından birini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="437e3-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="437e3-150">Bu kapsayıcılar, var olan bir Kubernetes kümesine bırakılabilir ve uygulama kodu ile birlikte çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="437e3-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="437e3-151">[Sebp/elk](https://elk-docker.readthedocs.io/) kapsayıcısı iyi belgelenmiş ve test edilmiş bir elastik yığın kapsayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="437e3-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="437e3-152">Diğer bir seçenek [de, son bildirilen bir hizmet olarak yeni tekliftir](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="437e3-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="437e3-153">Referanslar</span><span class="sxs-lookup"><span data-stu-id="437e3-153">References</span></span>

- [<span data-ttu-id="437e3-154">Azure 'da elastik yığın yüklemesi</span><span class="sxs-lookup"><span data-stu-id="437e3-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="437e3-155">[Önceki](observability-patterns.md)
>[İleri](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="437e3-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
