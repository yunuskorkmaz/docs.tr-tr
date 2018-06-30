---
title: Docker terminolojisi
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 0b13f28f4314ef72fbcaffe894bf823486665d3f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106103"
---
# <a name="docker-terminology"></a>Docker terminolojisi

Terimleri ve tanımları ile hale aşina Docker daha derin delving önce bu bölümde listelenmektedir (daha fazla tanımları için kapsamlı bakın [sözlüğü](https://docs.docker.com/glossary/) Docker tarafından sağlanan <https://docs.docker.com/glossary/>:

-   **Kapsayıcı görüntü** tüm bağımlılıkları ve bir kapsayıcı oluşturmak için gereken bilgileri olan bir paket. Görüntüyü tüm bağımlılıkları (örneğin, çerçeveler) yanı sıra dağıtım ve kapsayıcı çalışma zamanı tarafından kullanılacak yapılandırma içerir. Genellikle, görüntüyü birden fazla temel görüntülerden Katmanlar bir kapsayıcının dosya sistemi oluşturmak için diğer üzerinde yığılma türer. Oluşturulduktan sonra görüntüyü sabittir.

-   **Kapsayıcı** Docker görüntü örneği. Bir çalışma zamanı tek bir uygulama, işlem veya hizmet için bir kapsayıcıyı temsil eder. Docker görüntüsü, bir çalışma zamanı ortamı ve standart bir yönerge içeriğini oluşur. Bir hizmet ölçekleme sırasında bir kapsayıcı birden çok örneğini aynı görüntüden oluşturun. Ya da toplu iş her bir örneğine farklı parametreleri geçirme ile aynı görüntüden, birden çok kapsayıcı oluşturabilirsiniz.

-   **Etiket** işareti veya görüntülere uygulayabilirsiniz ve böylece farklı görüntü veya aynı görüntünün (bağlı olarak sürüm numarasını veya hedef ortam) sürümü tanımlanabilir etiketi.

-   **Dockerfile** Docker yansımasının nasıl oluşturulacağına ilişkin yönergeler içeren bir metin dosyası.

-   **Yapı** kapsayıcı görüntü oluşturma işlemi temel bilgileri ve görüntünün nerede üretilmiştir klasöründeki ek dosyaların yanı sıra kendi Dockerfile tarafından sağlanan bağlamı. Docker docker yapı komutunu kullanarak görüntüleri oluşturabilirsiniz.

-   **Depo (deposu olarak da bilinir)** resim sürümünü belirten bir etiketi etiketli ilgili Docker resimler koleksiyonu. SDK'ları (daha ağır), çalışma zamanları (açık), yalnızca içeren bir görüntü içeren bir görüntü gibi belirli bir resim birden çok çeşitlemelerini bazı depoları içeren ve benzeri. Bu çeşitleri etiketleriyle işaretlenebilir. Tek bir depo Linux görüntüsü ve bir Windows görüntüsü gibi platform çeşitleri içerebilir.

-   **Kayıt defteri** depoları için erişim sağlayan bir hizmet. Varsayılan kayıt defteri en ortak görüntüleri [Docker hub'a](https://hub.docker.com/) (kuruluş olarak Docker sahibi). Bir kayıt defteri genellikle birden çok ekibin depoları içerir. Şirketler genellikle depolamak ve oluşturmuş olduğunuz görüntülerini yönetmek için özel kayıt defterleri sahiptir. *Azure kapsayıcı kayıt defteri* başka bir örnektir.

-   **Docker hub'a** resimler yükleyin ve bunlarla çalışmak için ortak bir kayıt defteri. Docker hub'a Docker görüntü barındırma, genel veya özel kayıt defterleri, yapı tetikleyicileri ve web kancaları ve GitHub ve Bitbucket ile tümleştirme sağlar.

-   **Azure kapsayıcı kayıt defteri** Docker görüntüler ve bileşenlerinin Azure ile çalışmak için genel kaynağı. Bu Azure dağıtımlarınızda yakın olan ve erişim için olası hale getirerek, denetime verir bir kayıt defteri sunar Azure Active Directory grupları ve izinleri kullanın.

-   **Docker güvenilen kayıt defteri (DTR)** yükleyebileceğiniz bir Docker kayıt Hizmeti'nden (Docker) şirket içi böylece kuruluşunuzun veri merkezi ve ağ içinde bulunur. Kuruluş içinde yönetilmelidir özel görüntüleri için uygundur. Docker güvenilen kayıt defteri Docker Datacenter ürününü bir parçası olarak dahil edilir. Daha fazla bilgi için Git [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** Windows ve oluşturmak, çalıştırmak ve kapsayıcıları yerel olarak test etme için macOS için geliştirme araçları. Windows CE docker, Linux ve Windows kapsayıcıları için geliştirme ortamları sağlar. Windows'da Linux Docker ana dayalı bir [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM. Ana bilgisayar Windows kapsayıcıları için doğrudan Windows tabanlı. Mac için docker CE Apple hiper yönetici Framework'te temel alır ve [xhyve hiper yönetici](https://github.com/mist64/xhyve), Mac OS x Docker Windows CE ve Mac için Linux Docker ana VM sağlayan Oracle VirtualBox üzerinde temel Docker araç yerini alır.

-   **Docker Enterprise Edition (EE)** Linux ve Windows geliştirme için Docker araçları Kurumsal ölçekte sürümü.

-   **Oluşturan** bir komut satırı aracı ve YAML dosya tanımlama ve multicontainer uygulamaları çalıştırmak için meta veri biçimi. Birden çok ortama bağlı olarak değerleri geçersiz kılabilir bir veya daha fazla .yml dosyaları görüntülerle göre tek bir uygulama tanımlayın. Tanımları oluşturduktan sonra tek bir komut kullanarak tüm multicontainer uygulama dağıtabilirsiniz (docker-oluşturmanıza) Docker ana bilgisayarda görüntü her bir kapsayıcı oluşturur.

-   **Küme** Docker ana uygulama hizmetleri birden çok örneğini ölçeklendirmek tek bir sanal Docker ana oldukları gibi kullanıma sunulan koleksiyonu yayılan küme içindeki birden çok konak genelinde. Docker Swarm, Mesosphere DC/OS, Kubernetes ve Azure Service Fabric kullanarak Docker kümeleri oluşturabilirsiniz. (Bir kümeyi yönetmek için Docker Swarm'ı kullanırsanız, tipik olarak başvurmak bir *swarm* bir küme yerine.)

-   **Orchestrator** kümeleri ve Docker ana bilgisayarların yönetimini basitleştirir bir araç. Orchestrators kullanarak, kendi görüntüleri, kapsayıcıları ve konaklarını bir CLI ya da bir grafik kullanıcı arabirimi aracılığıyla yönetebilirsiniz. Kapsayıcı ağ, yapılandırmaları, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orchestrator, çalışan, dağıtma, ölçeklendirme ve iş yükleri düğümleri koleksiyonunda iyileştirme sorumludur. Genellikle, orchestrator ürün Mesosphere DC/OS, Kubernetes, Docker Swarm ve Azure Service Fabric gibi küme altyapısı sağlar aynı ürün değil.


>[!div class="step-by-step"]
[Önceki](what-is-docker.md)
[sonraki](docker-containers-images-and-registries.md)
