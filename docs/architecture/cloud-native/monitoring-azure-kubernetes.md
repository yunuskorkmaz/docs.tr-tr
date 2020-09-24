---
title: Azure Kubernetes Service'te İzleme
description: Azure Kubernetes Service'te İzleme
ms.date: 05/13/2020
ms.openlocfilehash: 3900f169b9be4f807e72392da38a1224d6ce28e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163706"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Azure Kubernetes Service'te İzleme

Kubernetes 'te yerleşik günlük oluşturma basit bir. Ancak, günlükleri Kubernetes dışında ve düzgün çözümlenebilecekleri bir yere almak için bazı harika seçenekler vardır. AKS kümelerinizi izlemeniz gerekiyorsa, Kubernetes için elastik yığının yapılandırılması harika bir çözümdür.

## <a name="azure-monitor-for-containers"></a>Kapsayıcılar için Azure İzleyici

[Kapsayıcılar Için Azure izleyici](/azure/azure-monitor/insights/container-insights-overview) , yalnızca Kubernetes değil de, DC/OS, Docker Sısınma ve Red Hat OpenShift gibi diğer düzenleme altyapılarından günlük kullanmayı destekler.

![Çeşitli kapsayıcılardan günlükleri kullanma ](./media/containers-diagram.png)
 **Şekil 7-10**. Çeşitli kapsayıcılardan günlükleri kullanma

[Prometheus](https://prometheus.io/) , popüler bir açık kaynak ölçüm izleme çözümüdür. Bulut Yerel Işlem altyapısı 'nın bir parçasıdır. Genellikle, Prometheus 'ın kullanılması için kendi deposu ile bir Prometheus sunucusunun yönetilmesi gerekir. Ancak, [kapsayıcılar Için Azure izleyici, Prometheus ölçüm uç noktaları ile doğrudan tümleştirme sağlar](/azure/azure-monitor/insights/container-insights-prometheus-integration), bu yüzden ayrı bir sunucu gerekli değildir.

Günlük ve ölçüm bilgileri yalnızca kümede çalışan kapsayıcılardan değil, küme konaklarından da toplanır. Bu, bir hatayı daha kolay bir şekilde izlemek için, günlük bilgilerinin iki ' dan daha kolay olmasını sağlar.

Günlük toplayıcıların yüklenmesi [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) ve [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) kümelerine göre farklılık gösterir. Ancak her iki durumda da günlük koleksiyonu bir Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)olarak uygulanır. Bu, günlük toplayıcının düğümlerin her birinde bir kapsayıcı olarak çalıştırıldığı anlamına gelir.

Hangi Orchestrator veya işletim sisteminin Azure Izleyici arka plan programını çalıştırıyor olduğuna bakılmaksızın, günlük bilgileri kullanıcıların tanıdık olduğu Azure Izleyici araçlarına iletilir. Bu, karma bir Kubernetes/Azure Işlevleri ortamı gibi farklı günlük kaynaklarını karıştırarak oluşan ortamlarda paralel bir deneyim sağlar.

![Bir dizi çalışan kapsayıcıyı günlüğe kaydetme ve ölçüm bilgilerini gösteren örnek bir Pano. ](./media/containers-dashboard.png)
 **Şekil 7-11**. Bir dizi çalışan kapsayıcıyı günlüğe kaydetme ve ölçüm bilgilerini gösteren örnek bir Pano.

## <a name="logfinalize"></a>Log. Finalize ()

Günlüğe kaydetme, her türlü uygulamayı ölçeklendirmenin en fazla ve en önemli bölümlerinden biridir. Uygulamaların boyutu ve karmaşıklığı artdıkça, bunları hata ayıklamanın zorluğunu ortadan kaldırın. Kullanılabilir en yüksek kaliteli günlüklere sahip olmak, hata ayıklamayı çok daha kolay hale getirir ve "neredeyse olanaksız" olarak "bir Pleasant deneyimi" bölgesine taşımaktır.

>[!div class="step-by-step"]
>[Önceki](logging-with-elastic-stack.md) 
> [Sonraki](azure-monitor.md)
