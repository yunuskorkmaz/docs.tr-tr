---
title: Docker terimleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker terminolojisi
ms.date: 01/07/2019
ms.openlocfilehash: 2735188c508a7bbb0101946429faec122b13a17b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090047"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, Docker 'a daha ayrıntılı bir şekilde yararlanmak için bilmeniz gereken hüküm ve tanımlar listelenmektedir. Daha fazla tanım için bkz. Docker tarafından sağlanan kapsamlı [Sözlük](https://docs.docker.com/glossary/) .

**Kapsayıcı görüntüsü**: bir kapsayıcı oluşturmak için gereken tüm bağımlılıkları ve bilgileri içeren bir paket. Bir görüntü, bir kapsayıcı çalışma zamanı tarafından kullanılacak tüm bağımlılıkları (örneğin, çerçeveler) ve dağıtım ve yürütme yapılandırmasını içerir. Genellikle, bir görüntü kapsayıcının dosya sistemini biçimlendirmek için her bir katmanın üzerine yığılan birden çok temel görüntüden türetilir. Bir görüntü oluşturulduktan sonra sabittir.

**Dockerfile**: Docker görüntüsünün nasıl oluşturulacağı hakkında yönergeler içeren bir metin dosyası. Bir toplu iş betiği gibi, ilk satırda temel görüntünün başlaması ve ardından gerekli programları yüklemek, dosyaları kopyalamak ve daha sonra gereken çalışma ortamına ulaşana kadar yönergeleri takip etmeniz gerekir.

**Yapı**: Dockerfile tarafından belirtilen bilgileri ve bağlamı temel alan bir kapsayıcı görüntüsü oluşturma eylemi ve görüntünün oluşturulduğu klasördeki ek dosyalar. Docker **Docker Build** komutuyla görüntüleri oluşturabilirsiniz.

**Kapsayıcı**: Docker görüntüsünün bir örneği. Kapsayıcı, tek bir uygulama, işlem veya hizmetin yürütülmesini temsil eder. Docker görüntüsü, yürütme ortamı ve standart bir yönerge kümesi içeriğinden oluşur. Bir hizmeti ölçeklendirirken, aynı görüntüden bir kapsayıcının birden çok örneğini oluşturursunuz. Ya da bir toplu iş, her örneğe farklı parametreler geçirerek aynı görüntüden birden fazla kapsayıcı oluşturabilir.

**Birimler**: kapsayıcının kullanabileceği yazılabilir bir dosya sistemi sunun. Görüntüler salt okunurdur, ancak çoğu programın dosya sistemine yazması gerektiğinden, birimler kapsayıcı görüntüsünün üzerine yazılabilir bir katman ekleyerek programların yazılabilir bir dosya sistemine erişimi vardır. Program, katmanlı bir dosya sistemine eriştiğini bilmez, her zamanki gibi yalnızca dosya sistemi. Konak sisteminde bulunan ve Docker tarafından yönetilen birimler.

**Etiket**: görüntüler için uygulayabileceğiniz bir işaret veya etiket, aynı görüntünün farklı görüntülerinin veya sürümlerinin (sürüm numarasına veya hedef ortama göre) tanımlanabilmesi için kullanabilirsiniz.

**Çok aşamalı derleme**: docker 17,05 veya üzeri olduğundan, son görüntülerin boyutunu azaltmaya yardımcı olan bir özelliktir. Birkaç cümleden, çok aşamalı derleme ile, örneğin, uygulamayı derlemek ve yayımlamak için ve daha küçük bir son görüntü oluşturmak için yalnızca küçük bir çalışma zamanı temel görüntüsü ile yayımlama klasörünü kullanarak, örneğin, SDK içeren büyük bir temel görüntü kullanabilirsiniz.

**Depo (depo)** : görüntü sürümünü gösteren bir etiketle etiketlenmiş Ilgili Docker görüntülerinin koleksiyonu. Bazı depolarda, SDK (daha ağır) içeren bir görüntü, yalnızca çalışma zamanları içeren bir görüntü (daha açık) vb. gibi belirli bir görüntünün birden fazla çeşitlemesi bulunur. Bu çeşitler etiketlerle işaretlenebilir. Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.

**Kayıt defteri**: depolara erişim sağlayan bir hizmet. Çoğu ortak görüntü için varsayılan kayıt defteri, [Docker Hub](https://hub.docker.com/) ' dır (kuruluş olarak Docker tarafından sahiplenilir). Kayıt defteri genellikle birden çok ekipten depoları içerir. Şirketler genellikle oluşturdukları görüntüleri depolamak ve yönetmek için özel kayıt defterlerine sahiptir. Azure Container Registry başka bir örnektir.

**Multi-Arch Image**: Multi-Architecture için, uygun görüntünün seçimini kolaylaştıran bir özelliktir, Docker 'ın çalıştığı platforma göre, bir Dockerfile, Docker 'ın çalıştırıldığı işletim sistemine ve sürümüne bağlı olarak, **MCR.Microsoft.com/DotNet/Core/SDK:2.2 'den** bir temel görüntü istediğinde, gerçekten **2,2-SDK-nanoserver-1709**, **2,2-SDK-nanoserver-1803**, **2,2-SDK-nanoserver-1809** veya **2,2-SDK-uzat**.

**Docker Hub**: görüntüleri karşıya yüklemek ve bunlarla çalışmak için ortak bir kayıt defteri. Docker Hub, Docker görüntüsü barındırma, genel veya özel kayıt defterleri, derleme Tetikleyicileri ve Web kancaları, GitHub ve BitBucket ile tümleştirme sağlar.

**Azure Container Registry**: Docker görüntüleriyle ve Azure 'daki bileşenleriyle çalışmak için ortak bir kaynak. Bu, Azure 'daki dağıtımlarınıza yakın bir kayıt defteri sağlar ve erişim üzerinde denetim sağlayarak Azure Active Directory gruplarınızı ve izinlerinizi kullanmayı mümkün kılar.

**Docker güvenilir kayıt defteri (DTR)** : kuruluşun veri merkezinde ve ağında yer alması için şirket içinde yüklenebilen bir Docker kayıt defteri hizmeti (Docker 'dan). Kuruluş dahilinde yönetilmesi gereken özel görüntüler için kullanışlıdır. Docker güvenilen kayıt defteri, Docker Datacenter ürününün bir parçası olarak dahil edilmiştir. Daha fazla bilgi için bkz. [Docker güvenilir kayıt defteri (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)** : yerel olarak kapsayıcı oluşturma, çalıştırma ve test etme için Windows ve MacOS için geliştirme araçları. Docker CE for Windows hem Linux hem de Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerindeki Linux Docker ana bilgisayarı bir [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makinesini temel alır. Windows kapsayıcıları için ana bilgisayar, doğrudan Windows 'a dayalıdır. Mac için Docker CE, Apple hiper yönetici çerçevesini ve Mac OS X bir Linux Docker konak sanal makinesi sağlayan [xhyve hiper yönetici](https://github.com/mist64/xhyve)'yi temel alır. Docker CE for Windows ve Mac Için, Oracle VirtualBox tabanlı olan Docker araç kutusu bulunur.

**Docker Enterprise Edition (ee)** : Linux ve Windows geliştirme Için Docker araçlarının kurumsal ölçekli bir sürümüdür.

**Oluştur**: çok Kapsayıcılı uygulamalar tanımlamak ve çalıştırmak için meta veriler içeren bir komut satırı aracı ve YAML dosya biçimi. Ortama bağlı olarak değerleri geçersiz kılabileceğiniz bir veya daha fazla............... Tanımları oluşturduktan sonra, Docker konağında görüntü başına kapsayıcı oluşturan tek bir komutla (Docker-Compose) tüm çok Kapsayıcılı uygulamayı dağıtabilirsiniz.

**Küme**: tek bir sanal Docker ana bilgisayarı gibi kullanıma sunulan Docker konaklarının bir koleksiyonu, uygulamanın birden fazla hizmetin kümedeki birden fazla örneğine yayılabilmesini sağlamak için, bu, uygulamanın birden çok hizmet örneğine ölçeklenebilmesini sağlar. Docker kümeleri, Kubernetes, Azure Service Fabric, Docker Sısınma ve Mesosphere DC/OS ile oluşturulabilir.

**Orchestrator**: kümelerin ve Docker konaklarının yönetimini kolaylaştıran bir araç. Düzenleyiciler, bir komut satırı arabirimi (CLı) veya grafik kullanıcı arabirimi aracılığıyla görüntülerini, kapsayıcıları ve konaklarını yönetmenizi sağlar. Kapsayıcı ağ, yapılandırma, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir Orchestrator, bir düğüm koleksiyonunda çalıştırma, dağıtma, ölçekleme ve düzeltme yüklerini çalıştırmaktan sorumludur. Genellikle, Orchestrator ürünleri, piyasadaki diğer tekliflerin yanı sıra Kubernetes ve Azure Service Fabric gibi küme altyapısı sağlayan ürünlerdir.

>[!div class="step-by-step"]
>[Önceki](docker-defined.md)
>[İleri](docker-containers-images-registries.md)
