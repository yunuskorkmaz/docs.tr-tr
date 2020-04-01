---
title: Docker terimleri
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Docker terminolojisi
ms.date: 01/30/2020
ms.openlocfilehash: fdcc5ec3603579c36d7339bd3ff651713b8eba88
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523343"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, Docker'a girmeden önce aşina olmanız gereken terimler ve tanımlar listelenebilmektedir. Diğer tanımlar için Docker tarafından sağlanan kapsamlı [sözlüklere](https://docs.docker.com/glossary/) bakın.

**Konteyner görüntüsü**: Bir kapsayıcı oluşturmak için gereken tüm bağımlılıkları ve bilgileri içeren bir paket. Görüntü, kapsayıcı çalışma zamanı tarafından kullanılacak tüm bağımlılıkları (çerçeveler gibi) ve dağıtım ve yürütme yapılandırmasını içerir. Genellikle, bir görüntü kapsayıcının dosya sistemini oluşturmak için üst üste yığılmış katmanlar olan birden çok temel görüntüden türetilir. Bir görüntü oluşturulduktan sonra değişmez.

**Dockerfile**: Docker görüntüsünün nasıl oluşturacağına dair yönergeler içeren bir metin dosyası. Bu bir toplu komut dosyası gibi, ilk satır ile başlamak ve daha sonra gerekli programları yüklemek için yönergeleri izleyin temel görüntü devletler, dosyaları kopyalamak ve benzeri, ihtiyacınız olan çalışma ortamı nı elde edene kadar.

**Yapı**: Dockerfile tarafından sağlanan bilgi ve içeriğe ve görüntünün oluşturulduğu klasördeki ek dosyalara dayalı bir kapsayıcı görüntüsü oluşturma eylemi. Docker komutu yla görüntüler oluşturabilirsiniz:

> `docker build`

**Konteyner**: Docker görüntüsünün bir örneği. Kapsayıcı, tek bir uygulamanın, işlemin veya hizmetin yürütülmesini temsil eder. Docker görüntüsünün, yürütme ortamının ve standart bir yönerge kümesinin içeriğinden oluşur. Bir hizmeti ölçeklerken, aynı görüntüden bir kapsayıcının birden çok örneğini oluşturursunuz. Veya bir toplu iş, her örne farklı parametreler geçirerek aynı görüntüden birden çok kapsayıcı oluşturabilir.

**Birimler**: Kapsayıcının kullanabileceği yazılabilir bir dosya sistemi sunun. Görüntüler salt okunur ancak çoğu programın dosya sistemine yazması gerektiğinden, birimler kapsayıcı görüntünün üstüne yazılabilir bir katman ekler, böylece programlar yazılabilir bir dosya sistemine erişebilir. Program katmanlı bir dosya sistemine erişiyor bilmiyor, her zamanki gibi sadece dosya sistemi. Birimler ana bilgisayar sisteminde yaşar ve Docker tarafından yönetilir.

**Etiket**: Görüntülere uygulayabileceğiniz bir işaret veya etiket, böylece aynı görüntünün farklı görüntüleri veya sürümleri (sürüm numarasına veya hedef ortama bağlı olarak) tanımlanabilir.

**Çok aşamalı Yapı**: Docker 17.05 veya daha yüksek olduğundan, son görüntülerin boyutunu azaltmaya yardımcı olan bir özelliktir. Birkaç cümlede, çok aşamalı yapıyla, örneğin, uygulamayı derlemek ve yayımlamak ve ardından yayımlama klasörünü küçük bir çalışma zamanı yalnızca temel görüntüyle kullanmak için çok daha küçük bir son görüntü oluşturmak için SDK içeren büyük bir temel görüntü kullanabilirsiniz.

**Depo (repo)**: Resim sürümünü gösteren bir etiketle etiketlenmiş ilgili Docker görüntülerinin koleksiyonu. Bazı repos'lar, SDK'lar (daha ağır), yalnızca çalışma süreleri (daha hafif) içeren bir görüntü gibi belirli bir görüntünün birden çok varyantını içerir. Bu türevleri etiketleri ile işaretlenmiş olabilir. Tek bir repo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.

**Kayıt Defteri**: Depolara erişim sağlayan bir hizmet. Çoğu genel görüntü için varsayılan kayıt defteri [Docker Hub'dır](https://hub.docker.com/) (kuruluş olarak Docker'a aittir). Kayıt defteri genellikle birden çok takımın depolarını içerir. Şirketlerin genellikle oluşturdukları görüntüleri depolamak ve yönetmek için özel kayıtları vardır. Azure Kapsayıcı Kayıt Defteri başka bir örnektir.

**Çok yönlü görüntü**: Çok mimari için Docker'ın çalıştığı platforma göre uygun görüntünün seçimini kolaylaştıran bir özelliktir. Örneğin, bir Dockerfile kayıt **defterinden mcr.microsoft.com/dotnet/core/sdk:3.1** bir temel görüntü istediğinde, aslında docker'ın çalıştığı işletim sistemine ve sürümüne bağlı olarak **3.1-sdk-nanoserver-1909**, **3.1-sdk-nanoserver-1809** veya **3.1-sdk-buster-slim**alır.

**Docker Hub**: Resim yüklemek ve onlarla çalışmak için genel kayıt defteri. Docker Hub Docker görüntü barındırma, kamu veya özel kayıt defteri, tetikleyiciler ve web kancaları oluşturmak ve GitHub ve Bitbucket ile entegrasyon sağlar.

**Azure Kapsayıcı Kayıt Defteri**: Azure'da Docker görüntüleri ve bileşenleriyle çalışmak için genel kaynak. Bu, Azure'daki dağıtımlarınıza yakın olan ve size erişim üzerinde denetim sağlayan bir kayıt defteri sağlayarak Azure Etkin Dizin gruplarınızı ve izinlerinizi kullanmanızı mümkün kılar.

**Docker Trusted Registry (DTR)**: Kuruluşun veri merkezi ve ağında yaşayabilmesi için şirket içinde kurulabilen Docker kayıt hizmeti (Docker'dan). Bu kuruluş içinde yönetilmesi gereken özel görüntüler için uygundur. Docker Trusted Registry, Docker Datacenter ürününün bir parçası olarak yer almaktadır. Daha fazla bilgi için [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/)adresine bakın.

**Docker Community Edition (CE)**: Kapsayıcıları yerel olarak oluşturmak, çalıştırmak ve test etmek için Windows ve macOS için geliştirme araçları. Windows için Docker CE, hem Linux hem de Windows Kapsayıcıları için geliştirme ortamları sağlar. Windows'daki Linux Docker ana bilgisayar, [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makinesini temel alın. Windows Kapsayıcıları için ana bilgisayar doğrudan Windows'a dayanır. Mac için Docker CE Apple Hypervisor çerçeve ve [xhyve hypervisor](https://github.com/mist64/xhyve)dayanmaktadır , Mac OS X. Docker CE Windows için bir Linux Docker ana bilgisayar sanal makine sağlar ve Mac için Docker Toolbox değiştirir, Oracle VirtualBox dayalı.

**Docker Enterprise Edition (EE)**: Linux ve Windows geliştirme için Docker araçlarının kurumsal ölçekli bir sürümü.

**Beste**: Çoklu kapsayıcı uygulamalarıtanımlamak ve çalıştırmak için meta verilere sahip bir komut satırı aracı ve YAML dosya biçimi. Ortama bağlı olarak değerleri geçersiz kılabilen bir veya daha fazla .yml dosyasına sahip birden çok görüntüye dayalı tek bir uygulama tanımlarsınız. Tanımları oluşturduktan sonra, Docker ana bilgisayarda görüntü başına bir kapsayıcı oluşturan tek bir komutla (docker-createcreate up) tüm çok kapsayıcı uygulamasını dağıtabilirsiniz.

**Küme**: Tek bir sanal Docker ana bilgisayar gibi maruz kalan Docker ana bilgisayarları topluluğu, böylece uygulama küme içinde birden çok ana bilgisayara yayılmış hizmetlerin birden çok örneğine ölçeklenebilir. Docker kümeleri Kubernetes, Azure Service Fabric, Docker Swarm ve Mezosphere DC/OS ile oluşturulabilir.

**Orchestrator**: Kümelerin ve Docker ana bilgisayarlarının yönetimini kolaylaştıran bir araçtır. Orkestratörler, görüntülerini, konteynerlerini ve ana bilgisayarlarını CLI veya grafiksel bir web-posta yoluyla yönetmenize olanak tanır. Konteyner ağlarını, yapılandırmaları, yük dengelemeyi, hizmet bulmayı, yüksek kullanılabilirliği, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir orkestratör, düğüm koleksiyonunda iş yüklerini çalıştırmaktan, dağıtmaktan, ölçeklemekten ve iyileştirir. Tipik olarak, orkestratör ürünleri, pazardaki diğer tekliflerin yanı sıra Kubernetes ve Azure Hizmet Kumaşı gibi küme altyapısı sağlayan ürünlerle aynıdır.

>[!div class="step-by-step"]
>[Önceki](docker-defined.md)
>[Sonraki](docker-containers-images-registries.md)
