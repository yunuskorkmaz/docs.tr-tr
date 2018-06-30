---
title: Docker terminolojisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker terminolojisi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 95f073a7db763abd295647d41d2e96e6d6d71067
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106794"
---
# <a name="docker-terminology"></a>Docker terminolojisi

Bu bölümde, terimleri ve tanımları, Docker daha derin almadan önce aşina olmalısınız listelenir. Daha fazla tanımları için kapsamlı bakın [sözlüğü](https://docs.docker.com/glossary/) Docker tarafından sağlanan.

**Kapsayıcı görüntü**: tüm bağımlılıkları ve bir kapsayıcı oluşturmak için gereken bilgileri olan bir paket. Görüntü kapsayıcısı çalışma zamanı tarafından kullanılacak dağıtım ve yürütme yapılandırması artı (örneğin, çerçeveler) tüm bağımlılıkları içerir. Genellikle, bir görüntü birbirlerine üstünde kapsayıcının filesystem form Yığılmış katmanlardır birden fazla temel görüntü türetir. Oluşturulduktan sonra görüntüyü sabittir.

**Kapsayıcı**: Docker görüntü örneği. Tek bir uygulama, işlem veya hizmet yürütülmesini bir kapsayıcıyı temsil eder. Docker görüntü, yürütme ortamı ve standart bir yönerge içeriğini oluşur. Bir hizmet ölçekleme sırasında bir kapsayıcı birden çok örneğini aynı görüntüden oluşturun. Veya toplu iş her bir örneğine farklı parametreleri geçirme ile aynı görüntüden, birden çok kapsayıcı oluşturabilirsiniz.

**Etiket**: işareti ya da farklı görüntü veya aynı görüntünün (bağlı olarak sürüm numarasını veya hedef ortam) sürümü tanımlanabilir böylece görüntülere uygulayabileceğiniz etiketi.

**Dockerfile**: Docker yansımasının nasıl oluşturulacağına ilişkin yönergeler içeren bir metin dosyası.

**Yapı**: kapsayıcı görüntü oluşturma işlemi temel bilgileri ve kendi Dockerfile artı görüntüsü oluşturulan burada klasöründeki ek dosyalar tarafından sağlanan bağlamı. Docker docker yapı komutu görüntülerle oluşturabilirsiniz.

**Depo (depo)**: resim sürümünü belirten bir etiketi etiketli ilgili Docker resimler koleksiyonu. Bazı depoları bir SDK'ları (daha ağır), yalnızca çalışma zamanları (açık) içeren bir görüntü içeren görüntüsü, vb. gibi belirli bir resim birden çok çeşitlemelerini içerir. Bu çeşitleri etiketleriyle işaretlenebilir. Tek bir depodaki Linux görüntüsü ve bir Windows görüntüsü gibi platform çeşitleri içerebilir.

**Kayıt defteri**: depoları için erişim sağlayan bir hizmet. Varsayılan kayıt defteri en ortak görüntüleri [Docker hub'a](https://hub.docker.com/) (kuruluş olarak Docker sahibi). Bir kayıt defteri genellikle birden çok ekibin depoları içerir. Şirketler genellikle depolamak ve oluşturmuş olduğunuz görüntülerini yönetmek için özel kayıt defterleri sahiptir. Azure kapsayıcı kayıt defteri başka bir örnektir.

**Docker hub'a**: resimler yükleyin ve bunlarla çalışmak için ortak bir kayıt defteri. Docker hub'a Docker görüntü barındırma, genel veya özel kayıt defterleri, yapı tetikleyicileri ve web kancaları ve GitHub ve Bitbucket ile tümleştirme sağlar.

**Azure kapsayıcı kayıt defteri**: Docker görüntüler ve bileşenlerinin Azure ile çalışmak için genel kaynağı. Bu Azure dağıtımlarınızda yakın olan ve erişim için olası hale getirerek, denetime verir bir kayıt defteri sunar Azure Active Directory grupları ve izinleri kullanın.

**Docker güvenilen kayıt defteri (DTR)**: olabilecek bir Docker kayıt Hizmeti'nden (Docker), kuruluşunuzun veri merkezi ve ağ içinde bulunduğu için şirket içi yüklü. Kuruluş içinde yönetilmelidir özel görüntüleri için uygundur. Docker güvenilen kayıt defteri Docker Datacenter ürününü bir parçası olarak dahil edilir. Daha fazla bilgi için bkz: [Docker güvenilen kayıt defteri (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: Windows ve oluşturmak, çalıştırmak ve kapsayıcıları yerel olarak test etme için macOS için geliştirme araçları. Windows CE docker, Linux ve Windows kapsayıcıları için geliştirme ortamları sağlar. Windows'da Linux Docker ana dayalı bir [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) sanal makine. Ana bilgisayar Windows kapsayıcıları için doğrudan Windows tabanlı. Mac için docker CE Apple hiper yönetici Framework'te temel alır ve [xhyve hiper yönetici](https://github.com/mist64/xhyve), Mac OS x Docker Windows CE ve Mac için Linux Docker ana bilgisayar sanal makine sağlayan Oracle üzerinde temel Docker araç değiştirir VirtualBox.

**Docker Enterprise Edition (EE)**: Linux ve Windows geliştirme için Docker araçları Kurumsal ölçekte sürümü.

**Oluşturan**: bir komut satırı aracı ve YAML dosya tanımlama ve birden çok kapsayıcı uygulamaları çalıştırmak için meta veri biçimi. Birden çok ortama bağlı olarak değerleri geçersiz kılabilir bir veya daha fazla .yml dosyaları görüntülerle göre tek bir uygulama tanımlayın. Tanımları oluşturduktan sonra tek bir komutla tüm çok kapsayıcı uygulama dağıtabilirsiniz (docker-oluşturmanıza) Docker ana bilgisayarda görüntü her bir kapsayıcı oluşturur.

**Küme**: Docker ana bilgisayarları bir tek sanal Docker ana değilmiş gibi uygulama hizmetleri birden çok örneğini ölçeklendirmek kullanıma sunulan bir koleksiyon yayılan küme içindeki birden çok konak genelinde. Docker kümeleri, Docker Swarm, Mesosphere DC/OS, Kubernetes ve Azure Service Fabric ile oluşturulabilir. (Bir kümeyi yönetmek için Docker Swarm'ı kullanırsanız, tipik olarak başvurmak bir *swarm* bir küme yerine.)

**Orchestrator**: kümeleri ve Docker ana bilgisayarların yönetimini basitleştirir bir araç. Orchestrators kendi görüntüleri, kapsayıcıları ve konaklarını bir komut satırı arabirimi (CLI) aracılığıyla yönetmek etkinleştirmek ya da bir grafik kullanıcı Arabirimi. Kapsayıcı ağ, yapılandırmaları, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orchestrator, çalışan, dağıtma, ölçeklendirme ve iş yükleri düğümleri koleksiyonunda iyileştirme sorumludur. Genellikle, orchestrator ürün Mesosphere DC/OS, Kubernetes, Docker Swarm ve Azure Service Fabric gibi küme altyapısı sağlar aynı ürün değil.


>[!div class="step-by-step"]
[Önceki](docker-defined.md)
[sonraki](docker-containers-images-registries.md)
