---
title: Esnek Stack ile günlüğe kaydetme
description: Elastik yığın, Logstash ve kibana kullanarak günlüğe kaydetme
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182834"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="51e85-103">Esnek Stack ile günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="51e85-103">Logging with Elastic Stack</span></span> 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="51e85-104">Birçok iyi Merkezi günlük aracı vardır ve daha pahalı seçeneklere karşı ücretsiz, açık kaynaklı araçlar ve maliyet bakımından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="51e85-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="51e85-105">Birçok durumda, ücretsiz araçlar ücretli tekliflerle veya daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="51e85-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="51e85-106">Bu tür bir araç, üç açık kaynaklı bileşen birleşimidir: Elastik arama, Logstash ve kibana.</span><span class="sxs-lookup"><span data-stu-id="51e85-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span> <span data-ttu-id="51e85-107">Toplu olarak bu araçlar elastik yığın veya ELK yığını olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="51e85-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="51e85-108">Esnek yığının avantajları nelerdir?</span><span class="sxs-lookup"><span data-stu-id="51e85-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="51e85-109">Elastik yığın, düşük maliyetli, ölçeklenebilir, bulut kullanımı kolay bir şekilde Merkezi günlük kaydı sağlar.</span><span class="sxs-lookup"><span data-stu-id="51e85-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="51e85-110">Kullanıcı arabirimi, veri analizini kolaylaştırarak, bir clunky arabirimi ile uğraşmaya değil, verilerinizden verilerinize yönelik Öngörüler elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e85-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="51e85-111">Dağıtılmış uygulamanız daha fazla ve farklı hizmet türlerine yayıldığında, günlük ve ölçüm verilerini sisteme akışa almaya devam etmeyi beklemeniz için çok çeşitli girdileri destekler.</span><span class="sxs-lookup"><span data-stu-id="51e85-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="51e85-112">Esnek yığın, büyük veri kümelerinde bile hızlı aramaları destekler, hatta büyük uygulamaların ayrıntılı verileri günlüğe kaydedebilmesini ve yine de bir performans açısından görünebilmesini olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="51e85-112">The Elastic Stack also supports fast searches even across large data sets, making it possible to for even large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="51e85-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="51e85-113">Logstash</span></span>

<span data-ttu-id="51e85-114">İlk bileşen [Logstash](https://www.elastic.co/products/logstash)' dir.</span><span class="sxs-lookup"><span data-stu-id="51e85-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="51e85-115">Bu araç, çok çeşitli farklı kaynaklardan günlük bilgilerini toplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51e85-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="51e85-116">Örneğin Logstash, günlükleri diskten okuyabilir ve ayrıca [Serilog](https://serilog.net/)gibi günlük kitaplıklarından iletiler alabilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="51e85-117">Logstash, geldikçe günlüklerde bazı temel filtreleme ve genişleme işlemlerini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="51e85-118">Örneğin, günlükleriniz IP adresleri içeriyorsa, Logstash coğrafi arama yapmak ve bu ileti için bir ülke veya hatta kaynak şehir almak üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span> 

<span data-ttu-id="51e85-119">Serilog, parametreli günlüğe kaydetmeye olanak sağlayan .NET dilleri için bir günlüğe kaydetme kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="51e85-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="51e85-120">Alanları katıştıran bir metin günlüğü iletisi oluşturmak yerine Parametreler ayrı tutulur.</span><span class="sxs-lookup"><span data-stu-id="51e85-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="51e85-121">Bu, daha akıllı filtreleme ve arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="51e85-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="51e85-122">Şekil 7-2 ' de Logstash yazmak için örnek bir Serilog yapılandırması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="51e85-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="51e85-123">**Şekil 7-2** HTTP üzerinden logstash 'e doğrudan günlük bilgilerini yazmak için Serilog config</span><span class="sxs-lookup"><span data-stu-id="51e85-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="51e85-124">Logstash, Şekil 7-3 ' de gösterilen şekilde bir yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="51e85-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span> 

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

<span data-ttu-id="51e85-125">**Şekil 7-3** -Serilog 'dan günlük tüketme Için bir Logstash yapılandırması</span><span class="sxs-lookup"><span data-stu-id="51e85-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="51e85-126">Kapsamlı günlük işleme gerekli olmadığı senaryolar için, [tempts](https://www.elastic.co/products/beats)olarak bilinen Logstash için bir alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="51e85-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="51e85-127">Pts, günlüklerdeki ağ verilerine ve çalışma süresi bilgilerine çok çeşitli veriler toplayabilen bir araç ailesidir.</span><span class="sxs-lookup"><span data-stu-id="51e85-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="51e85-128">Birçok uygulama, hem Logstash hem de Pts 'yi kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="51e85-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="51e85-129">Günlükler Logstash tarafından toplandıktan sonra, bunları yerleştirmek için bir yere ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="51e85-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="51e85-130">Logstash birçok farklı çıkışı desteklese de, daha heyecan verici bir arama, elastik aramalardır.</span><span class="sxs-lookup"><span data-stu-id="51e85-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="51e85-131">Elastik arama</span><span class="sxs-lookup"><span data-stu-id="51e85-131">Elastic search</span></span>

<span data-ttu-id="51e85-132">Elastik arama, geldikçe günlükleri dizinlebilecekleri güçlü bir arama altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="51e85-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="51e85-133">Günlüklere hızlı şekilde çalışan sorgular yapar.</span><span class="sxs-lookup"><span data-stu-id="51e85-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="51e85-134">Elastik arama çok büyük miktarlarda günlüğü işleyebilir ve olağanüstü durumlarda birçok düğüm arasında ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span> 

<span data-ttu-id="51e85-135">Parametreleri içermesi için üretilmiş olan veya parametreleri Logstash işleme aracılığıyla bölüşdüğü olan günlük iletileri, bu bilgileri koruyan şekilde doğrudan sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="51e85-136">Tarafından `jill@example.com`ziyaret edilen ilk 10 sayfayı arayan bir sorgu, Şekil 7-4 ' de görünür.</span><span class="sxs-lookup"><span data-stu-id="51e85-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

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

<span data-ttu-id="51e85-137">**Şekil 7-4** -bir kullanıcı tarafından ziyaret edilen ilk 10 sayfayı bulmak Için bir elaa arama sorgusu</span><span class="sxs-lookup"><span data-stu-id="51e85-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="51e85-138">Kibana Web panolarıyla bilgi görselleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="51e85-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="51e85-139">Yığının son bileşeni kibana.</span><span class="sxs-lookup"><span data-stu-id="51e85-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="51e85-140">Bu araç, bir Web panosunda etkileşimli görselleştirmeler sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51e85-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="51e85-141">Panolar, teknik olmayan kullanıcılar tarafından da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="51e85-142">Elaun Search dizininde yerleşik olan çoğu veri, kibana panolarına dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="51e85-143">Bireysel kullanıcılar farklı Pano isteklerine sahip olabilir ve kibana Bu özelleştirmeyi kullanıcıya özgü panolara izin vererek sağlar.</span><span class="sxs-lookup"><span data-stu-id="51e85-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span> 

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="51e85-144">Azure 'da elastik yığın yükleme</span><span class="sxs-lookup"><span data-stu-id="51e85-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="51e85-145">Esnek yığın, çeşitli yollarla Azure 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="51e85-146">Her zaman olduğu gibi, [sanal makineler sağlamak ve doğrudan elastik yığın yüklemek](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)mümkündür.</span><span class="sxs-lookup"><span data-stu-id="51e85-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="51e85-147">Bu seçenek, deneyimli bazı kullanıcılar tarafından, en yüksek özelleştirme derecesini sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="51e85-148">Bir hizmet olarak altyapıya dağıtım, bu yolu alan bir hizmet olarak altyapı ile ilişkili tüm görevlerin sahipliğini alma ve düzeltme ekleriyle güncel tutmaya yönelik önemli yönetim yükü sunar.</span><span class="sxs-lookup"><span data-stu-id="51e85-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span> 

<span data-ttu-id="51e85-149">Daha az ek yük olan bir seçenek, elastik yığının zaten yapılandırıldığı birçok Docker kapsayıcılarından birini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="51e85-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="51e85-150">Bu kapsayıcılar, var olan bir Kubernetes kümesine bırakılabilir ve uygulama kodu ile birlikte çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="51e85-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="51e85-151">[Sebp/elk](https://elk-docker.readthedocs.io/) kapsayıcısı iyi belgelenmiş ve test edilmiş bir elastik yığın kapsayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="51e85-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="51e85-152">Diğer bir seçenek [de, son bildirilen bir hizmet olarak yeni tekliftir](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="51e85-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="51e85-153">Referanslar</span><span class="sxs-lookup"><span data-stu-id="51e85-153">References</span></span>

- [<span data-ttu-id="51e85-154">Azure 'da elastik yığın yüklemesi</span><span class="sxs-lookup"><span data-stu-id="51e85-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="51e85-155">[Önceki](observability-patterns.md)
>[İleri](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="51e85-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
