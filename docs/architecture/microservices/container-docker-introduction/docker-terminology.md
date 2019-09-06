---
title: Docker terimleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker terminolojisi
ms.date: 01/07/2019
ms.openlocfilehash: 700cd9a00c30b0a5fc87f9ffcd63821bb578b0cc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296180"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, Docker 'a daha ayrıntılı bir şekilde yararlanmak için bilmeniz gereken hüküm ve tanımlar listelenmektedir. Daha fazla tanım için bkz. Docker tarafından sağlanan kapsamlı [Sözlük](https://docs.docker.com/glossary/) .

**Kapsayıcı görüntüsü**: Bir kapsayıcı oluşturmak için gereken tüm bağımlılıkları ve bilgileri içeren bir paket. Bir görüntü, bir kapsayıcı çalışma zamanı tarafından kullanılacak tüm bağımlılıkları (örneğin, çerçeveler) ve dağıtım ve yürütme yapılandırmasını içerir. Genellikle, bir görüntü kapsayıcının dosya sistemini biçimlendirmek için her bir katmanın üzerine yığılan birden çok temel görüntüden türetilir. Bir görüntü oluşturulduktan sonra sabittir.

**Dockerfile**: Docker görüntüsü oluşturma yönergelerini içeren bir metin dosyası. Bir toplu iş betiği gibi, ilk satırda temel görüntünün başlaması ve ardından gerekli programları yüklemek, dosyaları kopyalamak ve daha sonra gereken çalışma ortamına ulaşana kadar yönergeleri takip etmeniz gerekir.

**Oluşturma**: Bir kapsayıcı görüntüsünü, Dockerfile tarafından belirtilen bilgileri ve bağlamı ve görüntünün oluşturulduğu klasördeki ek dosyaları temel alarak oluşturma eylemi. Docker **Docker Build** komutuyla görüntüleri oluşturabilirsiniz. 

**Kapsayıcı**: Docker görüntüsünün bir örneği. Kapsayıcı, tek bir uygulama, işlem veya hizmetin yürütülmesini temsil eder. Docker görüntüsü, yürütme ortamı ve standart bir yönerge kümesi içeriğinden oluşur. Bir hizmeti ölçeklendirirken, aynı görüntüden bir kapsayıcının birden çok örneğini oluşturursunuz. Ya da bir toplu iş, her örneğe farklı parametreler geçirerek aynı görüntüden birden fazla kapsayıcı oluşturabilir.

**Birimler**: Kapsayıcının kullanabileceği yazılabilir bir dosya sistemi sunun. Görüntüler salt okunurdur, ancak çoğu programın dosya sistemine yazması gerektiğinden, birimler kapsayıcı görüntüsünün üzerine yazılabilir bir katman ekleyerek programların yazılabilir bir dosya sistemine erişimi vardır. Program, katmanlı bir dosya sistemine eriştiğini bilmez, her zamanki gibi yalnızca dosya sistemi. Konak sisteminde bulunan ve Docker tarafından yönetilen birimler.

**Etiket**: Görüntülere uygulayabileceğiniz bir işaret veya etiket, aynı görüntünün farklı görüntülerinin veya sürümlerinin (sürüm numarasına veya hedef ortama göre) tanımlanabilmesi için kullanabilirsiniz.

**Çok aşamalı derleme**: , Docker 17,05 veya üzeri bu yana son görüntülerin boyutunu azaltmaya yardımcı olan bir özelliktir. Birkaç cümleden, çok aşamalı derleme ile, örneğin, uygulamayı derlemek ve yayımlamak için ve daha küçük bir son görüntü oluşturmak için yalnızca küçük bir çalışma zamanı temel görüntüsü ile yayımlama klasörünü kullanarak, örneğin, SDK içeren büyük bir temel görüntü kullanabilirsiniz.

**Depo (depo)** : Görüntü sürümünü gösteren bir etiketle etiketlenmiş ilgili Docker görüntülerinin koleksiyonu. Bazı depolarda, SDK (daha ağır) içeren bir görüntü, yalnızca çalışma zamanları içeren bir görüntü (daha açık) vb. gibi belirli bir görüntünün birden fazla çeşitlemesi bulunur. Bu çeşitler etiketlerle işaretlenebilir. Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.

**Kayıt defteri**: Depolara erişim sağlayan bir hizmet. Çoğu ortak görüntü için varsayılan kayıt defteri, [Docker Hub](https://hub.docker.com/) ' dır (kuruluş olarak Docker tarafından sahiplenilir). Kayıt defteri genellikle birden çok ekipten depoları içerir. Şirketler genellikle oluşturdukları görüntüleri depolamak ve yönetmek için özel kayıt defterlerine sahiptir. Azure Container Registry başka bir örnektir.

**Çoklu mimari görüntü**: Çoklu mimari için, Docker 'ın çalıştırıldığı platforma göre uygun görüntünün seçimini basitleştiren bir özelliktir; Örneğin, bir Dockerfile, kayıt defterinden **MCR.Microsoft.com/DotNet/Core/SDK:2.2 öğesinden** bir temel görüntü istediğinde Bu işlem, Docker 'ın çalıştırıldığı işletim sistemine ve sürümüne bağlı olarak **2,2-SDK-nanoserver-1709**, **2,2-SDK-nanoserver-1803**, **2,2-SDK-nanoserver-1809** veya **2,2-SDK-Esnetme**alır.

**Docker Hub**: Görüntüleri karşıya yüklemek ve bunlarla çalışmak için ortak bir kayıt defteri. Docker Hub, Docker görüntüsü barındırma, genel veya özel kayıt defterleri, derleme Tetikleyicileri ve Web kancaları, GitHub ve BitBucket ile tümleştirme sağlar.

**Azure Container Registry**: Azure 'daki Docker görüntüleri ve bileşenleri ile çalışmaya yönelik ortak bir kaynak. Bu, Azure 'daki dağıtımlarınıza yakın bir kayıt defteri sağlar ve erişim üzerinde denetim sağlayarak Azure Active Directory gruplarınızı ve izinlerinizi kullanmayı mümkün kılar.

**Docker güvenilir kayıt defteri (DTR)** : Kuruluşun veri merkezinde ve ağında yer alması için şirket içinde yüklenebilen bir Docker kayıt defteri hizmeti (Docker 'dan). Kuruluş dahilinde yönetilmesi gereken özel görüntüler için kullanışlıdır. Docker güvenilen kayıt defteri, Docker Datacenter ürününün bir parçası olarak dahil edilmiştir. Daha fazla bilgi için bkz. [Docker güvenilir kayıt defteri (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)** : Kapsayıcıları yerel olarak oluşturmaya, çalıştırmaya ve test etmeye yönelik Windows için geliştirme araçları ve macOS. Docker CE for Windows hem Linux hem de Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerindeki Linux Docker ana bilgisayarı bir [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makinesini temel alır. Windows kapsayıcıları için ana bilgisayar, doğrudan Windows 'a dayalıdır. Mac için Docker CE, Apple hiper yönetici çerçevesini ve Mac OS X bir Linux Docker konak sanal makinesi sağlayan [xhyve hiper yönetici](https://github.com/mist64/xhyve)'yi temel alır. Docker CE for Windows ve Mac Için, Oracle VirtualBox tabanlı olan Docker araç kutusu bulunur.

**Docker Enterprise Edition (ee)** : Linux ve Windows geliştirme için Docker Araçları 'nın kurumsal ölçekli bir sürümü.

**Oluştur**: Çok Kapsayıcılı uygulamalar tanımlamak ve çalıştırmak için meta verileri içeren bir komut satırı aracı ve YAML dosya biçimi. Ortama bağlı olarak değerleri geçersiz kılabileceğiniz bir veya daha fazla............... Tanımları oluşturduktan sonra, Docker konağında görüntü başına kapsayıcı oluşturan tek bir komutla (Docker-Compose) tüm çok Kapsayıcılı uygulamayı dağıtabilirsiniz.

**Küme**: Tek bir sanal Docker ana bilgisayarı gibi sunulan Docker konaklarının bir koleksiyonu, uygulamanın birden fazla hizmetin kümedeki birden fazla örneğine yayılabilmesini sağlamak için, bu, bir sanal Docker Konağı olarak sunulur. Docker kümeleri, Kubernetes, Azure Service Fabric, Docker Sısınma ve Mesosphere DC/OS ile oluşturulabilir.

**Orchestrator**: Kümelerin ve Docker konaklarının yönetimini kolaylaştıran bir araç. Düzenleyiciler, bir komut satırı arabirimi (CLı) veya grafik kullanıcı arabirimi aracılığıyla görüntülerini, kapsayıcıları ve konaklarını yönetmenizi sağlar. Kapsayıcı ağ, yapılandırma, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir Orchestrator, bir düğüm koleksiyonunda çalıştırma, dağıtma, ölçekleme ve düzeltme yüklerini çalıştırmaktan sorumludur. Genellikle, Orchestrator ürünleri, piyasadaki diğer tekliflerin yanı sıra Kubernetes ve Azure Service Fabric gibi küme altyapısı sağlayan ürünlerdir. 

>[!div class="step-by-step"]
>[Önceki](docker-defined.md)İleri
>[](docker-containers-images-registries.md)
