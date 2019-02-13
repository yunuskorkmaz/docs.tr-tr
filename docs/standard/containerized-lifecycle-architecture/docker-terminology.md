---
title: Docker terimleri
description: Docker ile çalışırken, her gün kullanılan bazı temel terminoloji öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1514a2199efe52a411f61649fc21e906bba5b13c
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218729"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, terimleri ve tanımları ile hale gelmelidir aşina Docker derin delving önce listelenir (daha fazla tanımları için kapsamlı bakın [sözlüğü](https://docs.docker.com/glossary/) Docker tarafından sağlanan <https://docs.docker.com/glossary/>:

-   **Kapsayıcı görüntüsü** tüm bağımlılıkları ve kapsayıcı oluşturmak için gereken bilgileri içeren bir paket. Tüm bağımlılıkları (örneğin, çerçeveler) yanı sıra dağıtım ve yapılandırma, bir kapsayıcı çalışma zamanı tarafından kullanılacak bir görüntü içerir. Genellikle görüntü, bir kapsayıcının dosya sistemine oluşturmak için diğer üzerine dizilir katmanları birden çok temel görüntülerinden türetilir. Görüntü oluşturulduktan sonra sabittir.

-   **Kapsayıcı** bir Docker görüntüsü örneği. Bir kapsayıcıyı tek bir uygulama, işlem veya hizmet için bir çalışma zamanı temsil eder. Bu, bir Docker görüntüsü, bir çalışma zamanı ortamı ve standart bir yönerge içeriğini oluşur. Hizmet ölçeklendirme aynı görüntüsünden bir kapsayıcı birden çok örneğini oluşturun. Veya toplu iş için her örnek farklı parametre geçirme aynı görüntüden birden çok kapsayıcı oluşturabilirsiniz.

-   **Etiket** işareti ya da görüntülerini uygulayabilirsiniz ve böylece farklı bir görüntü veya aynı görüntünün (bağlı olarak sürüm numarasını veya hedef ortam) sürümü tanımlanabilir etiketi.

-   **Dockerfile** bir Docker görüntüsü oluşturma hakkında yönergeler içeren bir metin dosyası.

-   **Derleme** bir kapsayıcı görüntüsü oluşturma eylemini temel bilgileri ve ek dosyaları görüntü oluşturulan burada klasöre yanı sıra, Dockerfile tarafından sağlanan bağlam. Docker docker derleme komutunu kullanarak görüntüleri oluşturabilirsiniz.

-   **Depo (depo olarak da bilinir)** ilgili Docker görüntüleri görüntü sürümünü belirtir bir etiketle etiketlenmiş koleksiyonu. Bazı depolar, SDK'ları (Ağır), çalışma zamanları (açık) yalnızca içeren bir görüntü içeren bir görüntü gibi belirli bir görüntünün birden fazla çeşitlemelerini içerir ve benzeri. Bu çeşitleri etiketlerle işaretlenebilir. Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.

-   **Kayıt defteri** depolarına erişimi sağlayan bir hizmet. Varsayılan kayıt defteri en genel görüntülerde [Docker Hub](https://hub.docker.com/) (kuruluş olarak Docker tarafından sahip olunan). Bir kayıt defteri, genellikle birden çok takımı depolarından içerir. Şirketler genellikle oluşturmuş olduğunuz görüntülerini depolayıp yönetin için özel kayıt defterleri sahiptir. *Azure Container Registry* başka bir örnektir.

-   **Docker Hub** görüntüleri karşıya yüklemek ve bunlarla çalışmak için genel bir kayıt defteri. Docker Hub, Docker görüntüsünü barındıran, genel veya özel kayıt defterleri, yapı tetikleyicilerini ve web kancaları ve GitHub ve Bitbucket ile tümleştirme sağlar.

-   **Azure Container Registry** Docker görüntülerini ve bileşenlerinin azure'da çalışmaya yönelik bir genel kaynağı. Bu mümkün hale erişimi denetlemenizi sağlar ve Azure dağıtımlarınızı yakın olan bir kayıt defteri sağlar, Azure Active Directory grupları ve izinleri kullanın.

-   **Docker Trusted Registry (DTR)** yükleyebileceğiniz bir Docker kayıt defteri hizmetinden (Docker) şirket içi böylece kuruluşunuzun veri merkezi ve ağ içinde yer alıyor. Kuruluş içinde yönetilen özel görüntüleri uygundur. Docker Trusted Registry, Docker Datacenter ürünün bir parçası olarak dahil edilir. Daha fazla bilgi için Git [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition'ı (CE)** geliştirme araçları, Windows ve macOS için oluşturma, çalıştırma ve kapsayıcıları yerel olarak test etmek için. İçin docker CE Windows, Linux ve Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerinde Linux Docker konağı dayalı bir [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM. Windows kapsayıcıları için konak, doğrudan Windows üzerinde temel alır. Mac için docker CE Apple hiper yönetici Framework'te temel alır ve [xhyve hiper yönetici](https://github.com/mist64/xhyve), üzerinde Oracle VirtualBox temel Docker araç için Mac OS x Docker CE Windows ve Mac için Linux Docker konağı VM sağlayan değiştirir.

-   **Docker Enterprise Edition (EE)** bir geliştirme Linux ve Windows için Docker araçları kurumsal ölçekli sürümü.

-   **Compose** tanımlama ve çok kapsayıcılı uygulamaları çalıştırmak için meta veri biçimiyle bir komut satırı aracı ve YAML dosyası. Birden çok ortama bağlı olarak değerleri geçersiz kılabilir bir veya daha fazla .yml dosyaları görüntülerle dayalı tek bir uygulama tanımlarsınız. Tanımları oluşturduktan sonra tek bir komut kullanarak çok kapsayıcılı uygulamanın tamamı dağıtabilirsiniz (docker-oluşturmanıza) Docker ana bilgisayarda görüntü her bir kapsayıcı oluşturur.

-   **Küme** Hizmetleri birden fazla örneğe ölçeklendirebilir, böylece bunlar gibi tek bir sanal Docker ana kullanıma sunulan Docker ana bilgisayarları koleksiyonunu yayılan küme içindeki birden çok konak genelinde. Docker Swarm, Mesosphere DC/OS, Kubernetes ve Azure Service Fabric kullanarak Docker kümeleri oluşturabilirsiniz. (Bir kümeyi yönetmek için Docker Swarm'ı kullanırsanız, genellikle kümesi olarak başvurduğu bir *swarm* yerine bir küme.)

-   **Orchestrator** Docker konakları ve kümeleri yönetimini kolaylaştıran bir araç. Düzenleyicileri kullanarak, kendi görüntülerini, kapsayıcılar ve konaklarını bir CLI ya da bir grafik kullanıcı arabirimi aracılığıyla yönetebilirsiniz. Kapsayıcı ağ iletişimi, yapılandırmaları, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker konağı yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orchestrator çalıştıran, dağıtma, ölçeklendirme ve iş yüklerini düğümleri koleksiyonu düzeltme sorumludur. Genellikle, Mesosphere DC/OS, Kubernetes, Docker Swarm ve Azure Service Fabric gibi küme altyapısı sağlayan aynı ürünler olan orchestrator ürünler.

>[!div class="step-by-step"]
>[Önceki](what-is-docker.md)
>[İleri](docker-containers-images-and-registries.md)