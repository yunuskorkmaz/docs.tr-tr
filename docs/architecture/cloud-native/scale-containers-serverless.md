---
title: Kapsayıcıları ve sunucusuz uygulamaları ölçeklendirme
description: Azure Kubernetes hizmeti ile bulutta yerel uygulamaları, Kullanıcı talebini karşılayacak şekilde ölçeklendirin.
ms.date: 05/13/2020
ms.openlocfilehash: a5e1e8df785fd08901d9be41c0a06db35e09296b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613726"
---
# <a name="scaling-containers-and-serverless-applications"></a>Kapsayıcıları ve sunucusuz uygulamaları ölçeklendirme

Bir uygulamayı ölçeklendirmenin iki yolu vardır: yukarı veya çıkış. İlki, kapasiteyi artırmak için daha fazla kaynak eklemeye yönelik olarak, tek bir kaynağa kapasite eklemek anlamına gelir.

## <a name="the-simple-solution-scaling-up"></a>Basit çözüm: ölçeği artırma

Daha fazla CPU, bellek, disk g/ç hızı ve ağ g/ç hızına sahip mevcut bir konak sunucusunu yükseltme, *Ölçek artırma*olarak bilinir. Bulut Yerel uygulamasının ölçeklendirilmesi, bulut satıcısından daha yetenekli kaynakların seçilmesini içerir. Örneğin, Kubernetes kümenizdeki daha büyük VM 'Lere sahip yeni bir düğüm havuzu oluşturabilirsiniz. Ardından Kapsayıcılı hizmetlerinizi yeni havuza geçirin.

Özel bir App Service planından [Premium işlevler planı](https://docs.microsoft.com/azure/azure-functions/functions-scale) veya Premium örnek boyutları seçerek sunucusuz uygulamalar ölçeklendirilir.

## <a name="scaling-out-cloud-native-apps"></a>Bulutta yerel uygulamaların ölçeğini genişletme

Bulutta yerel uygulamalar sıklıkla büyük dalgalanmalar yaşar ve bir süre içinde ölçeklendirilmesi gerekir. Ölçeklendirmeyi tercih ederler. Ölçeği genişletme, var olan bir kümeye ek makineler (düğümler adı verilir) veya uygulama örnekleri eklenerek yatay olarak yapılır. Kubernetes 'te, uygulamanın yapılandırma ayarlarını ayarlayarak (örneğin, [bir düğüm havuzunu ölçeklendirerek](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) veya otomatik ölçeklendirmeyle el ile ölçekleyebilirsiniz.

AKS kümeleri, iki şekilde otomatik ölçeklendirme yapabilir:

İlk olarak, [yatay Pod otomatik Scaler](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods) kaynak talebini Izler ve pod çoğaltmalarınızı bunu karşılayacak şekilde otomatik olarak ölçeklendirir. Trafik arttıkça, hizmetlerinizin ölçeğini genişletmek için ek çoğaltmalar otomatik olarak sağlanır. Benzer şekilde, talep azaldıkça hizmetlerinizin ölçeklendirilmesine kaldırılır. Örneğin CPU kullanımı gibi ölçeklenmesi gereken ölçümü tanımlarsınız. Ayrıca, çalıştırılacak en düşük ve en fazla çoğaltma sayısını da belirtebilirsiniz. AKS, ölçüyü izler ve uygun şekilde ölçeklendirir.

Ardından [aks kümesi otomatik Scaler](https://docs.microsoft.com/azure/aks/cluster-autoscaler) özelliği, talebi karşılamak üzere bir Kubernetes kümesi genelinde işlem düğümlerini otomatik olarak ölçeklendirmenize olanak sağlar. Bununla birlikte, daha fazla işlem kapasitesi gerektiğinde, temel alınan Azure sanal makine ölçek kümesine yeni VM 'Leri otomatik olarak ekleyebilirsiniz. Artık gerekli olmadığında düğümleri da kaldırır.

Şekil 3-13, bu iki ölçeklendirme hizmeti arasındaki ilişkiyi gösterir.

![App Service planını ölçekleme.](./media/aks-cluster-autoscaler.png)

**Şekil 3-13**. App Service planını ölçekleme.

Birlikte çalışarak, her ikisi de en uygun sayıda kapsayıcı örneği ve işlem düğümü dalgalanmayı desteklemek için işlem düğümleri sağlar. Yatay Pod otomatik Scaler, gereken sayıda Pod 'yi iyileştirir. Küme otomatik yüklemesi, gerekli düğüm sayısını iyileştirir.

### <a name="scaling-azure-functions"></a>Azure Işlevlerini ölçeklendirme

Azure Işlevleri isteğe bağlı olarak otomatik olarak ölçeklendirilir. Sunucu kaynakları, tetiklenen olay sayısına göre dinamik olarak ayrılır ve kaldırılır. Yalnızca işlevleriniz çalıştırıldığında tüketilen işlem kaynakları için ücret ödersiniz. Faturalandırma, yürütme süresi ve kullanılan bellek sayısına bağlıdır.

Varsayılan tüketim planı çoğu uygulama için ekonomik ve ölçeklenebilir bir çözüm sağlarken Premium seçeneği, geliştiricilerin özel Azure Işlevleri gereksinimlerine yönelik esnekliğe olanak sağlar. Premium planına yükseltme, örnek boyutları üzerinde denetim, önceden çarpımış örnekler (soğuk başlangıç gecikmelerini önlemek için) ve adanmış VM 'Ler üzerinde denetim sağlar.

>[!div class="step-by-step"]
>[Önceki](deploy-containers-azure.md) 
> [Sonraki](other-deployment-options.md)
