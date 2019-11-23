---
title: Kapsayıcıları ve sunucusuz uygulamaları ölçeklendirme
description: Bulut Yerel uygulamalarını Azure Kubernetes hizmeti ile ölçeklendirerek, tek tek makine kaynaklarını artırarak veya bir uygulama kümesindeki makinelerin sayısını artırarak Kullanıcı taleplerini karşılayın.
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184801"
---
# <a name="scaling-containers-and-serverless-applications"></a>Kapsayıcıları ve sunucusuz uygulamaları ölçeklendirme

Bir uygulamayı ölçeklendirmenin iki genel yolu vardır: ölçeği artırma ve genişletme. İlki, bir konağa özellik eklemek anlamına gelir, ikincisi ise toplam konak sayısına ekleme anlamına gelir. Bunu öğrenmek için kullanılan yaygın bir benzerleme vurguladı, kendinizi ve kasaların şehir genelinde nasıl ele alınacağını öğrenin. Tek bir arkadaşınız varsa, iki özellikli yarış arabasın üzerinden yarışalım yapabilirsiniz. Ancak üç veya dört ise, kapasiteyi artırmak için SUVs veya bir mini Van 'den birini almanız gerekebilir. Toplam numaranız bir düzine veya daha fazla atlama yaparken, muhtemelen daha fazla örnek (Bu durumda, daha fazla araçlar) ekleyerek ölçeği genişletme kavramını gösteren birden çok araçlar almanız (birisi bir veri yolu olmadığı müddetçe) gerekir. Bunun uygulamalarımız için nasıl uygulanacağını görelim.

## <a name="the-simple-solution-scaling-up"></a>Basit çözüm: ölçeği artırma

Var olan sunucuları daha fazla kaynak (CPU, bellek, disk g/ç hızı, ağ g/ç hızı) vermek için yükseltme işlemi, *Ölçek artırma*olarak bilinir. Bulutta yerel uygulamalarda, ölçek artırma, genellikle fiziksel makinelerde gerçek donanımların satın alınması ve yüklenmesi ve bu sayede kullanılabilir seçenekler listesinden daha yetenekli bir plan seçilmesi anlamına gelmiyor. Bulutta yerel uygulamalar genellikle, Kubernetes düğüm havuzundaki tek tek düğümleri barındırmak için kullanılan sanal makine (VM) boyutunu değiştirerek ölçeği atlar. Düğümler, kümeler ve düğüm gibi Kubernetes kavramları, [sonraki bölümde](leverage-containers-orchestrators.md)daha ayrıntılı olarak açıklanmıştır. Azure, hem [Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) hem de [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes)çalıştıran çok çeşitli VM boyutlarını destekler. Uygulamanızı dikey olarak ölçeklendirmek için, daha büyük bir düğüm VM boyutuyla yeni bir düğüm havuzu oluşturun ve sonra iş yüklerini yeni havuza geçirin. Bu, şu anda Önizlemedeki bir özellik olan [AKS kümeniz için birden çok düğüm havuzu](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)gerektirir. Sunucusuz uygulamalar, [Premium bir plan](https://docs.microsoft.com/azure/azure-functions/functions-scale) ve Premium örnek boyutları seçerek veya farklı bir adanmış App Service planı seçerek ölçeği artırma.

## <a name="scaling-out-cloud-native-apps"></a>Bulutta yerel uygulamaların ölçeğini genişletme

Bulutta yerel uygulamalar, hizmet isteklerine ek düğümler veya Pod ekleyerek ölçeklendirmeyi destekler. Bu, uygulamanın yapılandırma ayarları ayarlanarak (örneğin, [bir düğüm havuzu ölçeklendirilirken](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) veya *Otomatik ölçeklendirilirken*el ile gerçekleştirilebilir. Otomatik ölçeklendirme, bir uygulama tarafından isteğe yanıt vermek için kullanılan kaynakları ayarlar ve bu da ek Isıtma veya soğutma için çağrı yaparak bir termostat 'nın sıcaklığa nasıl yanıt vereceğini de benzer. Otomatik ölçeklendirme kullanırken el ile ölçekleme devre dışıdır.

AKS kümeleri, iki şekilde ölçeklendirebilir:

- [Küme otomatik yüklemesi](https://docs.microsoft.com/azure/aks/cluster-autoscaler) , kaynak kısıtlamaları nedeniyle düğümlerde zamanlanabilecek düğüm sayısını izler. Gerektiğinde ek düğümler ekler.
- **Yatay Pod otomatik Scaler** , Kubernetes kümesinde ölçüm sunucusunu kullanarak pods 'nin kaynak taleplerini izler. Bir hizmette daha fazla kaynak gerekiyorsa, otomatik, sayı sayısını artırır.

Şekil 3-13, bu iki ölçeklendirme hizmeti arasındaki ilişkiyi gösterir.

![App Service planını ölçekleme.](./media/aks-cluster-autoscaler.png)

**Şekil 3-13**. App Service planını ölçekleme.

Bu hizmetler Ayrıca, gereken sayıda düğüm veya düğüm sayısını azaltabilir. Bu iki hizmet birlikte çalışabilir ve genellikle bir kümede birlikte dağıtılır. Birleştirildiğinde, yatay Pod otomatik Scaler, uygulama talebini karşılamak için gereken sayıda Pod çalıştırmaya odaklanılmıştır. Küme otomatik yüklemesi, zamanlanmış pods 'yi desteklemek için gereken düğüm sayısını çalıştırmaya odaklanır.

### <a name="scaling-azure-functions"></a>Azure Işlevlerini ölçeklendirme

Azure Işlevleri ölçeklendirmeyi otomatik olarak destekler. Varsayılan tüketim planı, içinde gelen tetikleme olaylarının sayısına göre dinamik olarak kaynakları ekler (ve kaldırır). Yalnızca işlevleriniz çalışırken kullanılan işlem kaynakları, yürütme süresi ve kullanılan bellek sayısına göre ücretlendirilirsiniz. Premium planı kullanarak, bu özellikleri de aynı özelliklere sahip olursunuz, ancak kullanılan örnek boyutlarını denetleyebilir, örnekleri zaten çarpımış olabilir (soğuk başlangıç gecikmelerinden kaçınmak için) ve işlevlerinizin çalıştırılacağı adanmış VM 'Leri yapılandırabilirsiniz. Varsayılan yapılandırma birçok uygulama için ekonomik ve ölçeklenebilir bir çözüm sağlamalıdır, ancak Premium seçeneği, geliştiricilerin özel Azure Işlevleri gereksinimleri için esneklik sağlamasına izin verir.

## <a name="references"></a>Referanslar

- [Birden çok düğüm havuzu](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [AKS kümesi otomatik Scaler](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Öğretici: AKS 'de Uygulamaları ölçeklendirme](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure Işlevleri ölçeklendirme ve barındırma](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[Önceki](deploy-containers-azure.md)
>[İleri](other-deployment-options.md)
