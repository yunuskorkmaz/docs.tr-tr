---
title: Elastik Yığın ile günlüğe kaydetme
description: Elastik yığın, Logstash ve kibana kullanarak günlüğe kaydetme
ms.date: 05/13/2020
ms.openlocfilehash: 3f10b0d06c87b7bed6d3e302742b1dc52e2c9d3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155347"
---
# <a name="logging-with-elastic-stack"></a>Elastik Yığın ile günlüğe kaydetme

Birçok iyi Merkezi günlük aracı vardır ve daha pahalı seçeneklere karşı ücretsiz, açık kaynaklı araçlar ve maliyet bakımından farklılık gösterir. Birçok durumda, ücretsiz araçlar ücretli tekliflerle veya daha iyi bir seçenektir. Bu tür bir araç, üç açık kaynaklı bileşen birleşimidir: elastik arama, Logstash ve kibana.

Toplu olarak bu araçlar elastik yığın veya ELK yığını olarak bilinir.

## <a name="elastic-stack"></a>Elastik yığın

Elastik yığın, bir Kubernetes kümesinden bilgi toplamak için güçlü bir seçenektir. Kubernetes, bir Elakes arama uç noktasına günlük göndermeyi destekler ve [çoğu bölüm](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)Için, Şekil 7-5 ' de gösterildiği gibi, ortam değişkenlerini ayarlamak gerekir:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Şekil 7-5**. Kubernetes için yapılandırma değişkenleri

Bu, küme üzerinde elaa araması yükleyecek ve tüm küme günlüklerini buna gönderen hedeflenecek.

![Kubernetes ](./media/kibana-dashboard.png)
 **Şekil 7-6**' den alınan günlüklere yönelik bir sorgunun sonuçlarını gösteren bir kibana panosu örneği. Kubernetes 'ten alınan günlüklere yönelik bir sorgunun sonuçlarını gösteren bir kibana panosu örneği

## <a name="what-are-the-advantages-of-elastic-stack"></a>Esnek yığının avantajları nelerdir?

Elastik yığın, düşük maliyetli, ölçeklenebilir, bulut kullanımı kolay bir şekilde Merkezi günlük kaydı sağlar. Kullanıcı arabirimi, veri analizini kolaylaştırarak, bir clunky arabirimi ile uğraşmaya değil, verilerinizden verilerinize yönelik Öngörüler elde edebilirsiniz. Dağıtılmış uygulamanız daha fazla ve farklı hizmet türlerine yayıldığında, günlük ve ölçüm verilerini sisteme akışa almaya devam etmeyi beklemeniz için çok çeşitli girdileri destekler. Elastik yığın, büyük veri kümelerinde bile hızlı aramaları destekler, böylece büyük uygulamalar ayrıntılı verileri günlüğe kaydeder ve yine de bir performans üzerinde görünebilmesini sağlar.

## <a name="logstash"></a>Logstash

İlk bileşen [Logstash](https://www.elastic.co/products/logstash)' dir. Bu araç, çok çeşitli farklı kaynaklardan günlük bilgilerini toplamak için kullanılır. Örneğin Logstash, günlükleri diskten okuyabilir ve ayrıca [Serilog](https://serilog.net/)gibi günlük kitaplıklarından iletiler alabilir. Logstash, geldikçe günlüklerde bazı temel filtreleme ve genişleme işlemlerini gerçekleştirebilir. Örneğin, günlükleriniz IP adresleri içeriyorsa, Logstash coğrafi arama yapmak ve bu ileti için bir ülke veya hatta kaynak şehir almak üzere yapılandırılabilir.

Serilog, parametreli günlüğe kaydetmeye olanak sağlayan .NET dilleri için bir günlüğe kaydetme kitaplığıdır. Alanları katıştıran bir metin günlüğü iletisi oluşturmak yerine Parametreler ayrı tutulur. Bu, daha akıllı filtreleme ve arama sağlar. Şekil 7-7 ' de Logstash yazmak için örnek bir Serilog yapılandırması görüntülenir.

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**Şekil 7-7**. HTTP üzerinden logstash 'e doğrudan günlük bilgilerini yazmak için Serilog config

Logstash, Şekil 7-8 ' de gösterilen şekilde bir yapılandırma kullanır.

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

**Şekil 7-8**. Serilog 'dan günlük tüketme için bir Logstash yapılandırması

Kapsamlı günlük işleme gerekli olmadığı senaryolar için, [tempts](https://www.elastic.co/products/beats)olarak bilinen Logstash için bir alternatif vardır. Pts, günlüklerdeki ağ verilerine ve çalışma süresi bilgilerine çok çeşitli veriler toplayabilen bir araç ailesidir. Birçok uygulama, hem Logstash hem de Pts 'yi kullanacaktır.

Günlükler Logstash tarafından toplandıktan sonra, bunları yerleştirmek için bir yere ihtiyacı vardır. Logstash birçok farklı çıkışı desteklese de, daha heyecan verici bir arama, elastik aramalardır.

## <a name="elastic-search"></a>Elastik arama

Elastik arama, geldikçe günlükleri dizinlebilecekleri güçlü bir arama altyapısıdır. Günlüklere hızlı şekilde çalışan sorgular yapar. Elastik arama çok büyük miktarlarda günlüğü işleyebilir ve olağanüstü durumlarda birçok düğüm arasında ölçeklendirilebilir.

Parametreleri içermesi için üretilmiş olan veya parametreleri Logstash işleme aracılığıyla bölüşdüğü olan günlük iletileri, bu bilgileri koruyan şekilde doğrudan sorgulanabilir.

Tarafından ziyaret edilen ilk 10 sayfayı arayan bir sorgu `jill@example.com` , şekil 7-9 ' de görünür.

```json
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

**Şekil 7-9**. Bir kullanıcı tarafından ziyaret edilen ilk 10 sayfayı bulmak için bir elaa arama sorgusu

## <a name="visualizing-information-with-kibana-web-dashboards"></a>Kibana Web panolarıyla bilgi görselleştiriliyor

Yığının son bileşeni kibana. Bu araç, bir Web panosunda etkileşimli görselleştirmeler sağlamak için kullanılır. Panolar, teknik olmayan kullanıcılar tarafından da oluşturulabilir. Elaun Search dizininde yerleşik olan çoğu veri, kibana panolarına dahil edilebilir. Bireysel kullanıcılar farklı Pano isteklerine sahip olabilir ve kibana Bu özelleştirmeyi kullanıcıya özgü panolara izin vererek sağlar.

## <a name="installing-elastic-stack-on-azure"></a>Azure 'da elastik yığın yükleme

Esnek yığın, çeşitli yollarla Azure 'a yüklenebilir. Her zaman olduğu gibi, [sanal makineler sağlamak ve doğrudan elastik yığın yüklemek](/azure/virtual-machines/linux/tutorial-elasticsearch)mümkündür. Bu seçenek, deneyimli bazı kullanıcılar tarafından, en yüksek özelleştirme derecesini sağladığından tercih edilir. Bir hizmet olarak altyapıya dağıtım, bu yolu alan bir hizmet olarak altyapı ile ilişkili tüm görevlerin sahipliğini alma ve düzeltme ekleriyle güncel tutmaya yönelik önemli yönetim yükü sunar.

Daha az ek yük olan bir seçenek, elastik yığının zaten yapılandırıldığı birçok Docker kapsayıcılarından birini kullanmaktır. Bu kapsayıcılar, var olan bir Kubernetes kümesine bırakılabilir ve uygulama kodu ile birlikte çalıştırılabilir. [Sebp/elk](https://elk-docker.readthedocs.io/) kapsayıcısı iyi belgelenmiş ve test edilmiş bir elastik yığın kapsayıcısıdır.

Diğer bir seçenek [de, son bildirilen bir hizmet olarak yeni tekliftir](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).

## <a name="references"></a>Başvurular

- [Azure 'da elastik yığın yüklemesi](/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[Önceki](observability-patterns.md) 
> [Sonraki](monitoring-azure-kubernetes.md)
