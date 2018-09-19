---
title: Docker terimleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker terimleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 39a3c0e0aac2980e67a1c87a472d1a77baed6113
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000628"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, terimleri ve tanımları Docker derin almadan önce bilmeniz listelenir. Daha fazla tanımları için kapsamlı bakın [sözlüğü](https://docs.docker.com/glossary/) Docker tarafından sağlanan.

**Kapsayıcı görüntüsü**: tüm bağımlılıkları ve kapsayıcı oluşturmak için gereken bilgileri içeren bir paket. Görüntüyü bir kapsayıcı çalışma zamanı tarafından kullanılacak dağıtım ve yürütme yapılandırması artı (örneğin, çerçeveler) tüm bağımlılıkları içerir. Genellikle, görüntüyü kapsayıcının dosya sistemi oluşturmak için birbirinin Yığılmış katmanlardır birden çok temel görüntüleri türetir. Görüntü oluşturulduktan sonra sabittir.

**Dockerfile**: bir Docker görüntüsü oluşturma hakkında yönergeler içeren bir metin dosyası. Bir toplu betik gibi olan ilk satırını başından itibaren temel görüntü durumları ve ardından gerekli programları yüklemek, vb. dosyaları kopyalamak için yönergeleri izleyin, çalışma ortamı elde edene kadar ihtiyacınız.

**Derleme**: bir kapsayıcı görüntüsü oluşturma eylemini temel bilgileri ve kendi Dockerfile, artı ek görüntünün nerede üretilmiştir klasördeki dosyaları tarafından sağlanan bağlam. Docker görüntüleri oluşturabileceğinizi **docker derleme** komutu. 

**Kapsayıcı**: bir Docker görüntüsü örneği. Bir kapsayıcıyı tek bir uygulama, işlem veya hizmet yürütülmesini temsil eder. Bu, bir Docker görüntüsü, bir yürütme ortamı ve standart bir yönerge içeriğini oluşur. Hizmet ölçeklendirme aynı görüntüsünden bir kapsayıcı birden çok örneğini oluşturun. Veya toplu iş için her örnek farklı parametre geçirme aynı görüntüden birden çok kapsayıcı oluşturabilirsiniz.

**Birimleri**: kapsayıcı kullanabileceğiniz bir yazılabilir dosya sistemi sağlar. Program bir yazılabilir dosya sistemi erişimi için birimler görüntüleri salt okunurdur ancak çoğu program, dosya sisteminde yazmanıza gerek olmadığından, kapsayıcı görüntüsü üzerine yazılabilir bir katman ekleyin. Program, katmanlı bir dosya sistemi erişim, yalnızca dosya sistemi zamanki olduğunu bilmez. Birimler, konak sisteminde canlı ve Docker tarafından yönetilir.

**Etiket**: işareti ya da etiket böylece farklı bir görüntü veya aynı görüntünün (bağlı olarak sürüm numarasını veya hedef ortamı) sürümü tanımlanabilir görüntüleri uygulayabilirsiniz.

**Çok aşamalı derleme**: son görüntü boyutunu küçültmek için yardımcı olan bir özellik, Docker 17.05 veya üzeri. Birkaç cümle ile sorunu çok aşamalı derleme ile Örneğin, büyük bir temel görüntüsü derleme ve uygulamayı yayımlama ve ardından yayımlama klasörüne bir çok daha küçük son görüntü oluşturmak için bir küçük yalnızca çalışma zamanı temel görüntü ile kullanmak için SDK'sını içeren kullanabilirsiniz

**Depo (depo)**: görüntü sürümünü belirtir bir etiketle etiketlenmiş ilgili Docker görüntülerini koleksiyonu. Bazı depolar, bir SDK'ları (Ağır), yalnızca çalışma zamanları (açık) içeren bir görüntü içeren görüntüsü, vb. gibi belirli bir görüntünün birden fazla çeşitlemelerini içerir. Bu çeşitleri etiketlerle işaretlenebilir. Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.

**Kayıt defteri**: depolarına erişimi sağlayan bir hizmet. Varsayılan kayıt defteri en genel görüntülerde [Docker Hub](https://hub.docker.com/) (kuruluş olarak Docker tarafından sahip olunan). Bir kayıt defteri, genellikle birden çok takımı depolarından içerir. Şirketler genellikle oluşturmuş olduğunuz görüntülerini depolayıp yönetin için özel kayıt defterleri sahiptir. Azure Container Registry, başka bir örnektir.

**Çok yay görüntü**: çok mimari için uygun görüntü seçimi basitleştiren bir özelliktir Docker çalıştırdığı platforma göre örneğin bir Dockerfile istediğinde bir temel görüntü **microsoft/dotnet gelen : 2.1-sdk** gerçekten alır kayıt defterinden **2.1-sdk-nanoserver-1709**, **2.1-sdk-nanoserver-1803** veya **2.1-sdk-alpine**bağlı olarak işletim sistemi ve Docker'ın çalıştığı sürümü.

**Docker Hub**: görüntüleri karşıya yüklemek ve bunlarla çalışmak için genel bir kayıt defteri. Docker Hub, Docker görüntüsünü barındıran, genel veya özel kayıt defterleri, yapı tetikleyicilerini ve web kancaları ve GitHub ve Bitbucket ile tümleştirme sağlar.

**Azure Container Registry**: Docker görüntülerini ve bileşenlerinin azure'da çalışmaya yönelik bir genel kaynağı. Bu mümkün hale erişimi denetlemenizi sağlar ve Azure dağıtımlarınızı yakın olan bir kayıt defteri sağlar, Azure Active Directory grupları ve izinleri kullanın.

**Docker Trusted Registry (DTR)**: olabilecek bir Docker kayıt defteri hizmetinden (Docker), kuruluşunuzun veri merkezi ve ağ içinde bulunduğu için şirket içi yüklü. Kuruluş içinde yönetilen özel görüntüleri uygundur. Docker Trusted Registry, Docker Datacenter ürünün bir parçası olarak dahil edilir. Daha fazla bilgi için [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition'ı (CE)**: Windows ve macOS için oluşturma, çalıştırma ve kapsayıcıları yerel olarak test etme için geliştirme araçları. İçin docker CE Windows, Linux ve Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerinde Linux Docker konağı dayalı bir [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makine. Windows kapsayıcıları için konak, doğrudan Windows üzerinde temel alır. Mac için docker CE Apple hiper yönetici Framework'te temel alır ve [xhyve hiper yönetici](https://github.com/mist64/xhyve), üzerinde Oracle temel Docker araç değiştirir Linux Docker konak sanal makine için Mac OS x Docker CE Windows ve Mac sağlar VirtualBox.

**Docker Enterprise Edition (EE)**: bir geliştirme Linux ve Windows için Docker araçları kurumsal ölçekli sürümü.

**Compose**: tanımlama ve çok kapsayıcılı uygulamalar çalıştırmak için meta veri biçimiyle bir komut satırı aracı ve YAML dosyası. Birden çok ortama bağlı olarak değerleri geçersiz kılabilir bir veya daha fazla .yml dosyaları görüntülerle dayalı tek bir uygulama tanımlarsınız. Tanımları oluşturduktan sonra tüm çok kapsayıcılı bir uygulama tek bir komutla dağıtabilirsiniz (docker-oluşturmanıza) Docker ana bilgisayarda görüntü her bir kapsayıcı oluşturur.

**Küme**: Docker ana bilgisayarları bir tek sanal Docker konağı değilmiş gibi uygulama hizmetleri birden fazla örneğe genişletebilir, kullanıma sunulan koleksiyonunu yayılan küme içindeki birden çok konak genelinde. Kubernetes, Azure Service Fabric, Docker Swarm ve Mesosphere DC/OS ile docker kümeleri oluşturulabilir.

**Orchestrator**: Docker konakları ve kümeleri yönetimini kolaylaştıran bir araç. Düzenleyiciler, görüntüler, kapsayıcılar ve konaklarını bir komut satırı arabirimi (CLI) aracılığıyla yönetmek etkinleştirmek ya da bir grafik kullanıcı Arabirimi. Kapsayıcı ağ iletişimi, yapılandırmaları, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker konağı yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orchestrator çalıştıran, dağıtma, ölçeklendirme ve iş yüklerini düğümleri koleksiyonu düzeltme sorumludur. Genellikle, orchestrator ürün küme altyapısı, Kubernetes ve Azure Service Fabric gibi arasında pazardaki diğer teklifler sunan aynı ürünleri değil. 


>[!div class="step-by-step"]
[Önceki](docker-defined.md)
[İleri](docker-containers-images-registries.md)
