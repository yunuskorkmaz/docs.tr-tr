---
title: Docker terimleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker terimleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9cfb8ceb4fa1b95603ccc9aa006dd6ee3e8e8b3a
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920980"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, terimleri ve tanımları Docker derin almadan önce bilmeniz listelenir. Daha fazla tanımları için kapsamlı bakın [sözlüğü](https://docs.docker.com/glossary/) Docker tarafından sağlanan.

**Kapsayıcı görüntüsü**: Tüm bağımlılıkları ve kapsayıcı oluşturmak için gereken bilgileri içeren bir paket. Görüntüyü bir kapsayıcı çalışma zamanı tarafından kullanılacak dağıtım ve yürütme yapılandırması artı (örneğin, çerçeveler) tüm bağımlılıkları içerir. Genellikle, görüntüyü kapsayıcının dosya sistemi oluşturmak için birbirinin Yığılmış katmanlardır birden çok temel görüntüleri türetir. Görüntü oluşturulduktan sonra sabittir.

**Dockerfile**: Bir Docker görüntüsü oluşturma hakkında yönergeler içeren bir metin dosyası. Bir toplu betik gibi olan ilk satırını başından itibaren temel görüntü durumları ve ardından gerekli programları yüklemek, vb. dosyaları kopyalamak için yönergeleri izleyin, çalışma ortamı elde edene kadar ihtiyacınız.

**Derleme**: Bilgi ve kendi Dockerfile, artı ek görüntünün nerede oluşturulmuştur klasördeki dosyaları tarafından sağlanan bağlam temelinde bir kapsayıcı görüntüsü oluşturma eylem. Docker görüntüleri oluşturabileceğinizi **docker derleme** komutu. 

**kapsayıcı**: Bir Docker görüntüsü örneği. Bir kapsayıcıyı tek bir uygulama, işlem veya hizmet yürütülmesini temsil eder. Bu, bir Docker görüntüsü, bir yürütme ortamı ve standart bir yönerge içeriğini oluşur. Hizmet ölçeklendirme aynı görüntüsünden bir kapsayıcı birden çok örneğini oluşturun. Veya toplu iş için her örnek farklı parametre geçirme aynı görüntüden birden çok kapsayıcı oluşturabilirsiniz.

**Birimleri**: Kapsayıcı kullanabileceğiniz bir yazılabilir dosya sistemi sağlar. Program bir yazılabilir dosya sistemi erişimi için birimler görüntüleri salt okunurdur ancak çoğu program, dosya sisteminde yazmanıza gerek olmadığından, kapsayıcı görüntüsü üzerine yazılabilir bir katman ekleyin. Program, katmanlı bir dosya sistemi erişim, yalnızca dosya sistemi zamanki olduğunu bilmez. Birimler, konak sisteminde canlı ve Docker tarafından yönetilir.

**Etiket**: İşareti veya etiket böylece farklı bir görüntü veya aynı görüntünün (bağlı olarak sürüm numarasını veya hedef ortamı) sürümü tanımlanabilir görüntüleri uygulayabilirsiniz.

**Çok aşamalı derleme**: Son görüntü boyutunu küçültmek için yardımcı olan bir Docker 17.05 veya üzeri özelliğidir. Birkaç cümle ile sorunu çok aşamalı derleme ile Örneğin, büyük bir temel görüntüsü derleme ve uygulamayı yayımlama ve ardından yayımlama klasörüne bir çok daha küçük son görüntü oluşturmak için bir küçük yalnızca çalışma zamanı temel görüntü ile kullanmak için SDK'sını içeren kullanabilirsiniz

**Depo (depo)**: Etiketli Görüntü sürümünü belirtir bir etiketle ilgili Docker görüntüleri koleksiyonudur. Bazı depolar, bir SDK'ları (Ağır), yalnızca çalışma zamanları (açık) içeren bir görüntü içeren görüntüsü, vb. gibi belirli bir görüntünün birden fazla çeşitlemelerini içerir. Bu çeşitleri etiketlerle işaretlenebilir. Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.

**Kayıt defteri**: Depolarına erişimi sağlayan bir hizmet. Varsayılan kayıt defteri en genel görüntülerde [Docker Hub](https://hub.docker.com/) (kuruluş olarak Docker tarafından sahip olunan). Bir kayıt defteri, genellikle birden çok takımı depolarından içerir. Şirketler genellikle oluşturmuş olduğunuz görüntülerini depolayıp yönetin için özel kayıt defterleri sahiptir. Azure Container Registry, başka bir örnektir.

**Çok yay görüntü**: Birden fazla mimari için uygun görüntü seçimi basitleştiren bir özelliktir Docker çalıştırdığı platforma göre örneğin bir Dockerfile istediğinde bir temel görüntü **mcr.microsoft.com/dotnet/core/sdk:2.2gelen**gerçekten alır kayıt defterinden **2.2-sdk-nanoserver-1709**, **2.2-sdk-nanoserver-1803**, **2.2-sdk-nanoserver-1809** veya **2.2 - SDK'sı-esnetme**, Docker çalıştığı sürümü ve işletim sistemine bağlı olarak.

**Docker Hub**: Görüntüleri karşıya yüklemek ve bunlarla çalışmak için ortak bir kayıt. Docker Hub, Docker görüntüsünü barındıran, genel veya özel kayıt defterleri, yapı tetikleyicilerini ve web kancaları ve GitHub ve Bitbucket ile tümleştirme sağlar.

**Azure kapsayıcı kayıt defteri**: Docker görüntülerini ve bileşenlerinin Azure ile çalışmaya genel bir kaynaktır. Bu mümkün hale erişimi denetlemenizi sağlar ve Azure dağıtımlarınızı yakın olan bir kayıt defteri sağlar, Azure Active Directory grupları ve izinleri kullanın.

**Docker kayıt defteri (DTR) güvenilen**: Kuruluşunuzun veri merkezi ve ağ içinde yer alan olabilecek bir Docker kayıt defteri hizmetinden (Docker) şirket içi yüklendi. Kuruluş içinde yönetilen özel görüntüleri uygundur. Docker Trusted Registry, Docker Datacenter ürünün bir parçası olarak dahil edilir. Daha fazla bilgi için [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: Windows ve macOS için oluşturma, çalıştırma ve kapsayıcıları yerel olarak test etme için geliştirme araçları. İçin docker CE Windows, Linux ve Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerinde Linux Docker konağı dayalı bir [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makine. Windows kapsayıcıları için konak, doğrudan Windows üzerinde temel alır. Mac için docker CE Apple hiper yönetici Framework'te temel alır ve [xhyve hiper yönetici](https://github.com/mist64/xhyve), üzerinde Oracle temel Docker araç değiştirir Linux Docker konak sanal makine için Mac OS x Docker CE Windows ve Mac sağlar VirtualBox.

**Docker Enterprise Edition (EE)**: Bir geliştirme Linux ve Windows için Docker araçları kurumsal ölçekli sürümü.

**Compose**: Bir komut satırı aracı ve YAML dosya tanımlama ve çok kapsayıcılı uygulamalar çalıştırmak için meta veri biçimi. Birden çok ortama bağlı olarak değerleri geçersiz kılabilir bir veya daha fazla .yml dosyaları görüntülerle dayalı tek bir uygulama tanımlarsınız. Tanımları oluşturduktan sonra tüm çok kapsayıcılı bir uygulama tek bir komutla dağıtabilirsiniz (docker-oluşturmanıza) Docker ana bilgisayarda görüntü her bir kapsayıcı oluşturur.

**Küme**: Küme içindeki birden çok konak genelinde bir tek sanal Docker konağı değilmiş gibi kullanıma sunulan hizmetlerin birden fazla örneğe ölçeklendirebilir, böylece Docker ana bilgisayarları koleksiyonunu yayılır. Kubernetes, Azure Service Fabric, Docker Swarm ve Mesosphere DC/OS ile docker kümeleri oluşturulabilir.

**Orchestrator**: Docker konakları ve kümeleri yönetimini kolaylaştıran bir araç. Düzenleyiciler, görüntüler, kapsayıcılar ve konaklarını bir komut satırı arabirimi (CLI) aracılığıyla yönetmek etkinleştirmek ya da bir grafik kullanıcı Arabirimi. Kapsayıcı ağ iletişimi, yapılandırmaları, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker konağı yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orchestrator çalıştıran, dağıtma, ölçeklendirme ve iş yüklerini düğümleri koleksiyonu düzeltme sorumludur. Genellikle, orchestrator ürün küme altyapısı, Kubernetes ve Azure Service Fabric gibi arasında pazardaki diğer teklifler sunan aynı ürünleri değil. 

>[!div class="step-by-step"]
>[Önceki](docker-defined.md)
>[İleri](docker-containers-images-registries.md)