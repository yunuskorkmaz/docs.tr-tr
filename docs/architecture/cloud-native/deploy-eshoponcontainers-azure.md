---
title: EShopOnContainers 'ı Azure 'a dağıtma
description: Azure Kubernetes hizmeti, helk ve DevSpaces kullanarak eShopOnContainers uygulamasını dağıtma.
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183275"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>EShopOnContainers 'ı Azure 'a dağıtma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

EShopOnContainers uygulamasını destekleme mantığı, çeşitli hizmetler kullanılarak Azure tarafından desteklenebilir. Önerilen yaklaşım, Azure Kubernetes hizmeti (AKS) kullanarak Kubernetes 'ten faydalanmalıdır. Bu, kolayca tekrarlanabilir altyapı yapılandırması sağlamak için Held dağıtımıyla birleştirilebilir. İsteğe bağlı olarak, geliştiriciler geliştirme sürecinin bir parçası olarak Kubernetes Azure Dev Spaces faydalanabilir. Diğer bir seçenek de Azure Işlevleri ve Azure Logic Apps gibi Azure sunucusuz özellikleri kullanarak uygulama işlevselliğini barındırmanıza olanak sağlar.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

EShopOnContainers uygulamasını kendi AKS kümenizde barındırmak istiyorsanız, ilk adım kümenizin oluşturulması gerekir. Bunu, gerekli adımlarda size yol gösterecek olan Azure portal kullanarak yapabilirsiniz veya Azure CLı 'yı kullanarak, rol tabanlı Access Control (RBAC) ve uygulama yönlendirmeyi bu şekilde etkinleştirmenizi sağlamak için dikkatli olabilirsiniz. EShopOnContainers ' belgeleri kendi AKS kümenizi oluşturma ile ilgili adımları açıklamaktadır. Küme oluşturulduktan sonra, Kubernetes panosuna erişimi etkinleştirmeniz gerekir, bu noktada kümeyi yönetmek için Kubernetes panosuna gözatabilmeniz gerekir.

Küme oluşturulduktan ve yapılandırıldıktan sonra, Held ve Tiller kullanarak uygulamayı dağıtabilirsiniz.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Held kullanarak Azure Kubernetes hizmetine dağıtma

AKS 'e yönelik temel dağıtımlar özel CLı betikleri veya basit dağıtım dosyaları kullanabilir, ancak daha karmaşık uygulamaların Helm gibi bir bağımlılık yönetim aracı kullanması gerekir. Helk, bulut Yerel Bilgi Işlem altyapısı tarafından korunur ve Kubernetes uygulamalarını tanımlamanıza, yüklemenize ve yükseltmenize yardımcı olur. Held, Held grafiklerini ve bir küme içi bileşeni olan Tiller bir komut satırı istemcisinden oluşur. Hele grafikleri, ilişkili bir Kubernetes kaynağı kümesini ve genellikle tanımladıkları uygulamayla birlikte sürümlenmiş standart YAML biçimli dosyaları kullanır. Hele grafikleri, tanımladıkları yüklemenin gereksinimlerine bağlı olarak basit ile karmaşık arasında değişir.

EShopOnContainers Held grafiklerini/k8s/Held klasöründe bulabilirsiniz. Şekil 2-6, uygulamanın farklı bileşenlerinin, Held tarafından yönetilen dağıtımlar tanımlamak için kullanılan bir klasör yapısına nasıl düzenlendiğini gösterir.

![eshoponcontainers mimari](./media/eshoponcontainers-helm-folder.png)
**Şekil 2-6**. EShopOnContainers Held klasörü.

Her bir bileşen, bir `helm install` komut kullanılarak yüklenir. Bu komutlar kolayca betikleştirilmiş ve eShopOnContainers, farklı bileşenler arasında döngü yapan ve bunları ilgili Helu grafiklerini kullanarak yükleyen bir "tümünü dağıt" betiği sağlar. Sonuç, kaynak denetimindeki uygulamayla sürümlü, ekip üzerindeki herkesin tek satırlık bir betik komutuyla bir AKS kümesine dağıtabileceği, tekrarlanabilir bir işlemdir. Özellikle de Azure Dev Spaces birleştirildiğinde, bu, geliştiricilerin kendi mikro hizmet tabanlı bulut Yerel uygulamalarında yaptığı değişiklikleri tanılamalarını ve test etmelerini kolaylaştırır.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces, bireysel geliştiricilerin geliştirme sırasında Azure 'da AKS kümelerinin kendi benzersiz sürümlerini barındırmalarına yardımcı olur. Bu, yerel makine gereksinimlerini en aza indirir ve takım üyelerinin, değişikliklerinin gerçek bir AKS ortamında nasıl davranacağını hızla görüntülemesine olanak tanır. Azure Dev Spaces, geliştiricilerin dev alanlarını yönetmek ve gerektiğinde belirli bir alt dev alanına dağıtmak üzere kullanması için bir CLı sunar. Her bir alt dev alanına benzersiz bir URL alt etki alanı kullanılarak başvurulur. bu sayede, tek tek geliştiricilerin devam eden her iş ile çakışmaktan kaçınmak için, değiştirilen kümelerin yan yana dağıtımına izin verilir. Şekil 2-7 ' de, geliştirici Susıe 'nin kendi Bisiklet mikro hizmetinin kendi sürümünü geliştirme alanına dağıttığının nasıl yapıldığını görebilirsiniz. Daha sonra kendi alan adı (susie.s.dev.myapp.eus.azds.io) ile başlayan özel bir URL 'YI kullanarak yaptığı değişiklikleri test edebilir.

![eshoponcontainers mimari](./media/azure-devspaces-one.png)
**Şekil 2-7**. Geliştirici Susie, Bisiklet mikro hizmetinin kendi sürümünü dağıtır ve test eder.

Aynı zamanda, geliştirici John, rezervasyonlar mikro hizmetini özelleştirip değişiklikleri test etmek için gereklidir. Şekil 2-8 ' de gösterildiği gibi, Susie değişiklikleri ile çakışmadan kendi geliştirme alanı üzerinde değişiklikleri dağıtabiyor. Kendi URL 'sini kullanarak değişikliklerini test edebilir. Bu, alan adı (john.s.dev.myapp.eus.azds.io) önekini kullanır.

![eshoponcontainers mimari](./media/azure-devspaces-two.png)
**Şekil 2-8**. Geliştirici John, rezervasyonlar mikro hizmetinin kendi sürümünü dağıtır ve diğer geliştiricilerle çakışmadan test eder.

Azure Dev Spaces kullanarak takımlar, değişiklikleri bağımsız olarak değiştirirken, dağıttığınızda ve test ederken doğrudan AKS ile çalışabilir. Bu yaklaşım, her geliştiricinin kendi AKS ortamları etkin olduğundan, ayrı ayrı barındırılan ortamların gereksinimini azaltır. Geliştiriciler, CLı kullanarak Azure Dev Spaces çalışabilir veya doğrudan Visual Studio 'dan Azure Dev Spaces için uygulamasını başlatabilir. [Azure Dev Spaces nasıl çalıştığı ve yapılandırıldığı hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Işlevleri ve Logic Apps (sunucusuz)

EShopOnContainers örneği, çevrimiçi pazarlama kampanyalarının izlenmesi için destek içerir. Belirli bir kampanya KIMLIĞI için pazarlama kampanyası ayrıntılarını çekmek üzere bir Azure Işlevi kullanılır. Bu amaçla bir bütün ASP.NET Core uygulama oluşturmak yerine, tek bir Azure Işlev uç noktası daha basit ve yeterlidir. Azure Işlevleri, özellikle Kubernetes 'te çalışacak şekilde yapılandırıldığında tam ASP.NET Core uygulamalardan çok daha basit bir derleme ve dağıtım modeline sahiptir. İşlevin dağıtımı Azure Resource Manager (ARM) şablonları ve Azure CLı kullanılarak komut dosyası oluşturulur. Bu kampanya ayrıntıları mikro hizmeti müşteriye yönelik değildir ve çevrimiçi mağazanızlarla aynı gereksinimlere sahip değildir ve Azure Işlevleri için iyi bir aday haline gelir. İşlev, veritabanı bağlantı dizesi verileri ve görüntü tabanı URI 'SI ayarları gibi bazı yapılandırmanın düzgün şekilde çalışmasını gerektirir. Azure Işlevleri 'ni Azure portalında yapılandırırsınız.

## <a name="references"></a>Referanslar

- [eShopOnContainers: AKS 'te Kubernetes kümesi oluşturma](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure geliştirme alanları](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Önceki](map-eshoponcontainers-azure-services.md)
>[İleri](centralized-configuration.md)
