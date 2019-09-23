---
title: Azure Kubernetes hizmetlerinde izleme
description: Azure Kubernetes hizmetlerinde izleme
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184990"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Azure Kubernetes hizmetlerinde izleme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kubernetes 'te yerleşik günlük oluşturma basit bir. Ancak, günlükleri Kubernetes dışında ve düzgün çözümlenebilecekleri bir yere almak için bazı harika seçenekler vardır. AKS kümelerinizi izlemeniz gerekiyorsa, Kubernetes için elastik yığının yapılandırılması harika bir çözümdür.

## <a name="elastic-stack"></a>Elastik yığın

Elastik yığın, bir Kubernetes kümesinden bilgi toplamak için güçlü bir seçenektir. Kubernetes, bir Elakes arama uç noktasına günlük göndermeyi destekler ve [çoğu bölüm](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)Için, Şekil 7-5 ' de gösterildiği gibi, ortam değişkenlerini ayarlamak gerekir:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Şekil 7-5** -Kubernetes için yapılandırma değişkenleri

Bu, küme üzerinde elaa araması yükleyecek ve tüm küme günlüklerini buna gönderen hedeflenecek.

![Kubernetes](./media/kibana-dashboard.png)
**Şekil 7-6**' den alınan günlüklere yönelik bir sorgunun sonuçlarını gösteren bir kibana panosu örneği. Kubernetes 'ten alınan günlüklere yönelik bir sorgunun sonuçlarını gösteren bir kibana panosu örneği

## <a name="azure-container-monitoring"></a>Azure Kapsayıcı Izleme

Azure Container Monitoring yalnızca Kubernetes değil, DC/OS, Docker Sısınma ve Red Hat OpenShift gibi diğer düzenleme altyapılarından günlük kullanmayı destekler.

![Çeşitli kapsayıcılardan](./media/containers-diagram.png)
günlükleri kullanma**Şekil 7-7**.  Çeşitli kapsayıcılardan günlükleri kullanma

Günlük ve ölçüm bilgileri yalnızca kümede çalışan kapsayıcılardan değil, küme konaklarından da toplanır. Bu, bir hatayı daha kolay bir şekilde izlemek için, günlük bilgilerinin iki ' dan daha kolay olmasını sağlar.

Günlük toplayıcıların yüklenmesi [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) ve [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) kümelerine göre farklılık gösterir. Ancak her iki durumda da günlük koleksiyonu bir Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)olarak uygulanır. Bu, günlük toplayıcının düğümlerin her birinde bir kapsayıcı olarak çalıştırıldığı anlamına gelir.

Hangi Orchestrator veya işletim sisteminin Azure Izleyici arka plan programını çalıştırıyor olduğuna bakılmaksızın, günlük bilgileri kullanıcıların tanıdık olduğu Azure Izleyici araçlarına iletilir. Bu, karma bir Kubernetes/Azure Işlevleri ortamı gibi farklı günlük kaynaklarını karıştırarak oluşan ortamlarda paralel bir deneyim sağlar.

![Bir dizi çalışan kapsayıcıyı günlüğe kaydetme ve ölçüm bilgilerini gösteren örnek bir Pano. **Şekil 7-8**. ](./media/containers-dashboard.png)
 Bir dizi çalışan kapsayıcıyı günlüğe kaydetme ve ölçüm bilgilerini gösteren örnek bir Pano.

## <a name="logfinalize"></a>Log. Finalize ()

Günlüğe kaydetme, her türlü uygulamayı ölçeklendirmenin en fazla ve en önemli bölümlerinden biridir. Uygulamaların boyutu ve karmaşıklığı artdıkça, bunları hata ayıklamanın zorluğunu ortadan kaldırın. Kullanılabilir en yüksek kaliteli günlüklere sahip olmak, hata ayıklamayı çok daha kolay hale getirir ve "neredeyse olanaksız" olarak "bir Pleasant deneyimi" bölgesine taşımaktır.

>[!div class="step-by-step"]
>[Önceki](logging-with-elastic-stack.md)
>[İleri](azure-monitor.md)
