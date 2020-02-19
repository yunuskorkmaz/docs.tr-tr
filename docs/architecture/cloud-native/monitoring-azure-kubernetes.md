---
title: Azure Kubernetes Service'te İzleme
description: Azure Kubernetes Service'te İzleme
ms.date: 02/05/2020
ms.openlocfilehash: 5c46b9e8599f70d430ad26cf1364343454d30a16
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450069"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Azure Kubernetes Service'te İzleme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kubernetes 'te yerleşik günlük oluşturma basit bir. Ancak, günlükleri Kubernetes dışında ve düzgün çözümlenebilecekleri bir yere almak için bazı harika seçenekler vardır. AKS kümelerinizi izlemeniz gerekiyorsa, Kubernetes için elastik yığının yapılandırılması harika bir çözümdür.

## <a name="azure-monitor-for-containers"></a>Kapsayıcılar için Azure İzleyici

[Kapsayıcılar Için Azure izleyici](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) , yalnızca Kubernetes değil de, DC/OS, Docker Sısınma ve Red Hat OpenShift gibi diğer düzenleme altyapılarından günlük kullanmayı destekler.

farklı kapsayıcılardan günlük ![](./media/containers-diagram.png)
**şekil 7-10**. Çeşitli kapsayıcılardan günlükleri kullanma

[Prometheus](https://prometheus.io/) , popüler bir açık kaynak ölçüm izleme çözümüdür. Bulut Yerel Işlem altyapısı 'nın bir parçasıdır. Genellikle, Prometheus 'ın kullanılması için kendi deposu ile bir Prometheus sunucusunun yönetilmesi gerekir. Ancak, [kapsayıcılar Için Azure izleyici, Prometheus ölçüm uç noktaları ile doğrudan tümleştirme sağlar](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration), bu yüzden ayrı bir sunucu gerekli değildir.

Günlük ve ölçüm bilgileri yalnızca kümede çalışan kapsayıcılardan değil, küme konaklarından da toplanır. Bu, bir hatayı daha kolay bir şekilde izlemek için, günlük bilgilerinin iki ' dan daha kolay olmasını sağlar.

Günlük toplayıcıların yüklenmesi [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) ve [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) kümelerine göre farklılık gösterir. Ancak her iki durumda da günlük koleksiyonu bir Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)olarak uygulanır. Bu, günlük toplayıcının düğümlerin her birinde bir kapsayıcı olarak çalıştırıldığı anlamına gelir.

Hangi Orchestrator veya işletim sisteminin Azure Izleyici arka plan programını çalıştırıyor olduğuna bakılmaksızın, günlük bilgileri kullanıcıların tanıdık olduğu Azure Izleyici araçlarına iletilir. Bu, karma bir Kubernetes/Azure Işlevleri ortamı gibi farklı günlük kaynaklarını karıştırarak oluşan ortamlarda paralel bir deneyim sağlar.

çeşitli çalışan kapsayıcılardan günlük ve ölçüm bilgilerini gösteren örnek bir pano ![. **şekil 7-11**](./media/containers-dashboard.png)
. Bir dizi çalışan kapsayıcıyı günlüğe kaydetme ve ölçüm bilgilerini gösteren örnek bir Pano.

## <a name="logfinalize"></a>Log. Finalize ()

Günlüğe kaydetme, her türlü uygulamayı ölçeklendirmenin en fazla ve en önemli bölümlerinden biridir. Uygulamaların boyutu ve karmaşıklığı artdıkça, bunları hata ayıklamanın zorluğunu ortadan kaldırın. Kullanılabilir en yüksek kaliteli günlüklere sahip olmak, hata ayıklamayı çok daha kolay hale getirir ve "neredeyse olanaksız" olarak "bir Pleasant deneyimi" bölgesine taşımaktır.

>[!div class="step-by-step"]
>[Önceki](logging-with-elastic-stack.md)
>[İleri](azure-monitor.md)
