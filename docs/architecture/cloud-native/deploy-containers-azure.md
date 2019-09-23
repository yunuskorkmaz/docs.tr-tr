---
title: Azure 'da kapsayıcı dağıtma
description: Azure Container Registry, Azure Kubernetes hizmeti ve Azure Dev Spaces Azure 'da kapsayıcı dağıtma.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183268"
---
# <a name="deploying-containers-in-azure"></a>Azure 'da kapsayıcı dağıtma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kapsayıcılar, biri taşınabilirlik olan birçok avantaj sağlar. Yerel olarak geliştirmiş ve test ettiğiniz kapsayıcıyı kolayca alabilir ve uygulamanızı hazırlama ve üretim ortamlarında çalıştırabilecekleri Azure 'a dağıtabilirsiniz. Azure, kapsayıcı tabanlı uygulama barındırmak için çeşitli seçenekler sağlar ve benzer şekilde birçok farklı dağıtım yöntemi destekler. En yaygın ve en esnek yaklaşım, kapsayıcıları Azure Container Registry (ACR) uygulamasına dağıtmaktır ve burada, bunları barındırmak için kullanmak istediğiniz hizmetler tarafından erişilebilir. Azure Kapsayıcılar için Web App, Azure Kubernetes Hizmetleri (AKS) ve Azure Container Instance (acı) hepsi ACR 'ye gönderilen kapsayıcı görüntülerine erişebilir.

## <a name="azure-container-registry"></a>Azure Container Registry

Azure Container Registry (ACR), tüm kapsayıcı dağıtımlarınız için görüntü oluşturmanıza, depolamanıza ve yönetmenize olanak sağlar. Kapsayıcıları dağıtabileceğiniz ortak ve özel başka kapsayıcı kayıt defterleri de vardır. Diğer seçeneklerin üzerinde ACR avantajı, görüntülerinizi üretim ortamınıza yakın tutabilirsiniz, derleme ve dağıtım sürelerini geliştirir. Ayrıca, Azure kaynaklarınızın geri kalanı için kullandığınız güvenlik yordamlarını kullanarak güvenli hale getirebilirsiniz, güvenliği artırır ve varlık yönetimi çabalarını azaltabilirsiniz.

Azure portalını veya [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) veya [PowerShell araçlarını](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)kullanarak [bir kapsayıcı kayıt defteri oluşturursunuz](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) . Yeni bir kapsayıcı kayıt defteri oluşturmak için yalnızca bir Azure aboneliği, bir kaynak grubu ve benzersiz bir ad gerekir. Şekil 3-11, kayıt defteri *adı*. azurecr.io adresinde barındırılacak bir kayıt defteri oluşturmaya yönelik temel seçenekleri gösterir.

![Kapsayıcı kayıt defteri](./media/create-container-registry.png)
**Şekil 3-11**oluşturun. Kapsayıcı kayıt defteri oluştur

Bir kayıt defteri oluşturduktan sonra, kullanabilmeniz için kimlik doğrulaması yapmanız gerekir. Genellikle, Azure CLı komutunu kullanarak kayıt defterinde oturum açmanız gerekir:

```azurecli
az acr login --name *registryname*
```

Azure Container Registry bir kayıt defteri oluşturduktan sonra, kapsayıcı görüntülerini buna göndermek için Docker komutlarını kullanabilirsiniz. Bununla birlikte, bunu yapabilmeniz için önce görüntünüzü ACR oturum açma sunucunuzun tam adı (URL) ile etiketlemelisiniz. Bu, *registryname*. azurecr.io biçiminde olacaktır.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Görüntüyü etiketledikten sonra, görüntüyü ACR örneğinize `docker push` göndermek için komutunu kullanın.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Bir görüntüyü kayıt defterine gönderdikten sonra, bu komutu kullanarak görüntüyü yerel Docker ortamınızdan kaldırmak iyi bir fikirdir:

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

Geliştiriciler, doğrudan makinelerinden bir kapsayıcı kayıt defterine nadiren gönderim yapmanız gerekir. Bunun yerine, bu işlemden sonra Azure DevOps gibi bir araçta tanımlanan derleme işlem hattı sorumludur. [Cloud-Native DevOps](devops.md)bölümünde daha fazla bilgi edinin.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Kapsayıcı tabanlı uygulamanız birden çok kapsayıcı içeriyorsa, Kubernetes gibi bir *Orchestrator* kullanarak kapsayıcılar arasındaki etkileşimleri tanımlamak ve yönetmek isteyeceksiniz. Kapsayıcı görüntülerinizi ACR 'ye dağıttıktan sonra, Azure Kubernetes hizmetlerini, güncelleştirilmiş görüntüleri ACR 'den otomatik olarak dağıtmak üzere kolayca yapılandırabilirsiniz. Eksiksiz bir CI/CD işlem hattı sayesinde, güncelleştirmeleri hızlı bir şekilde dağıtmaya yönelik riskleri en aza indirmek için bir [kanarya yayın](https://martinfowler.com/bliki/CanaryRelease.html) stratejisi yapılandırabilirsiniz. Uygulamanın yeni sürümü başlangıçta hiçbir trafik yönlendirilmeden üretimde yapılandırılır ve ardından az sayıda kullanıcı uygulamanın yeni dağıtılan sürümüne yönlendirilir. Ekip yazılımın yeni sürümünde güven kazandığında, yeni sürümün daha fazla örneği kullanıma alınır ve önceki sürümün örnekleri kullanımdan kalkmıştır. AKS bu dağıtım stilini kolayca destekler.

Azure 'daki kaynakların çoğunda olduğu gibi, portalı kullanarak Azure Kubernetes kümeleri oluşturabilir veya Helm ya da Terkform gibi komut satırı araçları ya da altyapı Otomasyonu araçlarını kullanabilirsiniz. Yeni bir kümeye başlamak için aşağıdaki bilgileri sağlamanız gerekir:

- Azure aboneliği
- Resource group
- Kubernetes küme adı
- Bölge
- Kubernetes sürümü
- DNS adı ön eki
- Düğüm boyutu
- Düğüm sayısı

Bu bilgiler başlamak için yeterlidir. Azure portalında oluşturma sürecinin bir parçası olarak, kümenizin aşağıdaki özelliklerine ilişkin seçenekleri de yapılandırabilirsiniz:

- Ölçek
- Kimlik doğrulaması
- Ağ Oluşturma
- İzleme
- Etiketler

Bu [hızlı başlangıçta Azure Portal kullanarak bir AKS kümesi dağıtma işlemi adım adım](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)açıklanmaktadır.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Karmaşık Kubernetes kümeleri barındırmak için önemli kaynaklar gerektirebilir, bu da geliştiricilerin tüm uygulamayı tek bir makinede (özellikle bir dizüstü bilgisayar) çalıştırmasını zorlaştırır. Azure Dev Spaces, geliştiricilerin Azure 'da barındırılan Azure Kubernetes kümelerinin kendi sürümleriyle çalışmasına izin vererek buna bir çözüm sunar. Azure Dev Spaces, AKS kullanan mikro hizmet tabanlı uygulamaların geliştirilmesini kolaylaştırmak için tasarlanmıştır.

Azure Dev Spaces değerini anlamak için, bu teklifi Gato Monroy 'tan paylaşalım, Microsoft Azure kapsayıcıların zaman adayı:

"Her biri kendi yapılandırma ve Destek Hizmetleri olan onlarca bileşenden oluşan karmaşık mikro hizmetler uygulamasındaki bir hatayı gidermeye çalışan yeni bir çalışan olduğunu düşünün. Başlamak için, yerel geliştirme ortamınızı, IDE 'nizi ayarlama, araç zinciri oluşturma, Kapsayıcılı hizmet bağımlılıkları, yerel bir Kubernetes ortamı, hizmet yedekleme için molar ve daha fazlasını içeren üretime benzetebilmek üzere yapılandırmanız gerekir. Geliştirme ortamınızı ayarlamaya yönelik tüm zamanlı olarak, ilk hatanın bu kadar gün sürebiliyor.

> Ya da dev Spaces ve AKS kullanabilirsiniz. "

Azure Dev Spaces ile çalışma işlemi aşağıdaki adımları içerir:

1. Geliştirme alanını oluşturun.
2. Kök dev alanını yapılandırın.
3. Bir alt dev alanı yapılandırın (sisteminizin kendi sürümünüz için).
4. Geliştirme alanına bağlanın.

Bu adımların tümü, Azure CLI ve yeni `azds` komut satırı araçları kullanılarak gerçekleştirilebilir. Örneğin, belirli bir Kubernetes kümesi için yeni bir Azure dev alanı oluşturmak için, şöyle bir komut kullanacaksınız:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Ardından, uygulamayı çalıştırmak için gerekli `azds prep` Docker ve hele grafik varlıklarını oluşturmak için komutunu kullanabilirsiniz. Ardından, kodunuzu kullanarak `azds up`aks 'de çalıştırırsınız. Bu komutu ilk kez çalıştırdığınızda helk grafiği yüklenir ve kapsayıcı (ler), yönergelerinizi temel alarak oluşturulup dağıtılır. İlk kez çalıştırıldığında bu işlem birkaç dakika sürebilir. Bununla birlikte, değişiklikleri yaptıktan sonra kendi alt geliştirme alanınıza `azds space select` bağlanarak bunları yalıtılmış alt geliştirme alanınızda dağıtıp hata ayıklaması yapabilirsiniz. Geliştirme alanınızı çalışır durumda yaptıktan sonra, `azds up` komutu yeniden yayımlayarak bu güncelleştirme gönderebilirsiniz ya da Visual Studio 'da veya Visual Studio Code yerleşik araçları kullanabilirsiniz. VS Code, geliştirme alanınıza bağlanmak için komut paletini kullanın. Şekil 3-12, Visual Studio 'da Azure Dev Spaces kullanarak Web uygulamanızı nasıl başlatacağınızı gösterir.

![Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**Şekil 3-12**' de Azure dev Spaces bağlanın. Visual Studio 'da Azure Dev Spaces bağlanma

## <a name="references"></a>Referanslar

- [Canary yayını](https://martinfowler.com/bliki/CanaryRelease.html)
- [VS Code Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Visual Studio ile Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[Önceki](combine-containers-serverless-approaches.md)
>[İleri](scale-containers-serverless.md)
