---
title: .NET Core Docker görüntülerinizi oluşturmak
description: Docker görüntüler ve .NET Core anlama
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: dotnet-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.custom: mvc
manager: wpickett
ms.workload:
- dotnetcore
ms.openlocfilehash: c1983be59b4a961cabd94915852e0cab7811682c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-docker-images-for-net-core-applications"></a>.NET Core uygulamaları için Docker görüntülerinizi oluşturmak

 Bu öğreticide, biz .NET Core üzerinde Docker kullanma odaklanılmaktadır. İlk olarak sunulan ve Microsoft ve kullanım örnekleri tarafından tutulan farklı Docker görüntüleri keşfedin. Biz sonra yapı ve ASP.NET Core uygulama dockerize hakkında bilgi edinin.

Bu öğreticinin sürecinde size bilgi edinin:
> [!div class="checklist"]
> * Microsoft .NET Core Docker görüntüler hakkında bilgi edinin 
> * Bir ASP.NET Core Dockerize için örnek uygulamayı Al
> * ASP.NET örnek uygulamayı yerel olarak çalıştırma
> * Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma
> * Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma

## <a name="docker-image-optimizations"></a>Docker resmi en iyi duruma getirme

Geliştiriciler için Docker görüntülerinizi oluşturmak, biz üzerinde üç ana senaryo odaklanır:

* .NET Core uygulamaları geliştirmek için kullanılan görüntü
* .NET Core uygulamaları oluşturmak için kullanılan görüntü
* .NET Core uygulamaları çalıştırmak için kullanılan görüntü

Neden üç görüntüleri?
Geliştirme, derleme ve kapsayıcılı uygulamaları çalıştıran farklı önceliklere sahip olduğumuz.

* **Geliştirme:** değişiklikleri ve değişiklikleri hata ayıklama özelliği öncelik odaklanır hızla yineleme. Görüntünün boyutuna kadar önemli değilse, bunun yerine, değişiklik kodunuzu yapabilir ve hızlıca görmek?

* **Derleme:** bu görüntü derleyici ve ikili dosyaları iyileştirmek için başka bir bağımlılık içerir, uygulamanızın derlemek için gereken her şeyi içerir.  Yapı görüntünün bir üretim görüntüsüne yerleştirin varlıklar oluşturmak için kullanın. Yapı görüntü sürekli tümleştirme için veya bir yapı ortamında kullanılır. Bu yaklaşım derlemek ve uygulamada (tüm gerekli bağımlılıkları olan) bir yapı görüntü örneği oluşturmak derleme aracısı sağlar. Derleme aracınızı, yalnızca bu Docker görüntü çalıştırma bilmesi gerekir.

* **Üretim:** ne kadar hızlı dağıtma ve görüntü başlatma? Bu görüntü, Docker ana bilgisayarlarınız için Docker kayıt defterinden ağ performansı en iyi duruma getirilmiş şekilde küçüktür. İçeriği Docker sonuçları işleme için Çalıştır'dan en iyi süreye etkinleştirme çalıştırmaya hazırsınız. Dinamik kod derleme Docker modelinde gerekli değildir. Bu görüntüde yerleştirin içeriği ikili dosyaları ve uygulamayı çalıştırmak için gereken içerik için sınırlı olacaktır.

    Örneğin, `dotnet publish` çıktı içerir:

    * derlenmiş ikili dosyalar
    * .js ve .css dosyaları


Eklenecek neden `dotnet publish` üretim görüntünüzü komut çıktısında olduğu tutmak için ' minimum boyut.

Bazı .NET Core görüntüleri katmanları son etiket indirme oldukça basit bir işlemdir şekilde farklı etiketler arasında paylaşın. Makinenizde zaten daha eski bir sürümü varsa, bu mimarinin gerekli disk alanı azaltır.

Birden çok uygulama aynı makinede ortak görüntüleri kullandığınızda, bellek ortak görüntülerin arasında paylaşılır. Görüntüleri paylaşılması için aynı olması gerekir.

## <a name="docker-image-variations"></a>Docker görüntü farklılıkları

Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflerinize ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Bu görüntü .NET Core ve komut satırı araçları (CLI) içeren .NET Core SDK'sı içerir. Bu görüntü eşlendiği **geliştirme senaryosu**. Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın. Bu görüntü için de kullanılabilir, **yapı** senaryoları. Kullanarak `microsoft/dotnet:sdk` her zaman en son sürümünü sağlar.

> [!TIP]
> Kullanmak istediğiniz, gereksinimleriniz hakkında konusunda emin değilseniz `microsoft/dotnet:<version>-sdk` görüntü. "Gerçek" görüntüsü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodu bağlayın ve kapsayıcı uygulamanızı başlatmak için Başlat) ve diğer görüntüleri oluşturmak için temel görüntü olarak.

* `microsoft/dotnet:<version>-runtime`: Bu görüntü .NET Core (çalışma zamanı ve kitaplıklar) içerir ve .NET Core uygulamaları çalıştırmak için optimize edilmiştir **üretim**.

## <a name="alternative-images"></a>Alternatif görüntüleri

Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryolara ek olarak, ek görüntüleri sağlar:

* `microsoft/dotnet:<version>-runtime-deps`**Çalışma zamanı deps** görüntü tüm .NET Core tarafından gerekli yerel bağımlılıklarını ile işletim sistemi içerir. Bu görüntü içindir [kendi içinde bulunan uygulamalar](../deploying/index.md).

Her değişken en son sürümleri:

* `microsoft/dotnet` veya `microsoft/dotnet:latest` (diğer ad SDK görüntüsü için)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Keşfetmek için örnekleri

* [Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir. Örnek, Linux ve Windows kapsayıcılarını ile çalışır.

* Bu .NET Core Docker örneği için en iyi yöntem deseni gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>İlk ASP.NET Core Docker uygulamanızı

Bu öğretici için dockerize istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanarak olanak sağlar. Bu ASP.NET Core Docker örnek uygulama Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir. Örnek, Linux ve Windows kapsayıcılarını ile çalışır.

Dockerfile örnek dışına ASP.NET çekirdeği çalışma zamanı Docker temel görüntü tabanlı bir ASP.NET Core uygulama Docker görüntüsü oluşturur.

Kullandığı [Docker çok aşama yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:

* bağlı bir kapsayıcıdaki örneği oluşturmak **büyük** ASP.NET Core yapı Docker temel görüntüsü 
* temel bir Docker görüntüye son derleme sonucu kopyalar **küçük** ASP.NET çekirdeği Docker çalışma zamanı temel görüntüsü

> [!NOTE]
> Yapı görüntüsü çalışma zamanı görüntü çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.

### <a name="prerequisites"></a>Önkoşullar

Derlemek ve çalıştırmak için aşağıdaki öğeleri yükleyin:

#### <a name="net-core-20-sdk"></a>.NET core 2.0 SDK'sı

* Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

* Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.

> [!TIP]
> Kod Düzenleyicisi yüklemeniz gerekiyor? Deneyin [Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Docker istemcisi yükleme

Yükleme [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki.

Docker istemci yüklenebilir:

* Linux dağıtımları

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

#### <a name="installing-git-for-sample-repository"></a>Örnek depo için Git yükleme

* Yükleme [git](https://git-scm.com/download) depoyu kopyalayın istiyorsanız.

### <a name="getting-the-sample-application"></a>Örnek uygulama alma

Kopyalama işlemi tarafından örnek almak için en kolay yolu olan [örnekleri depo](https://github.com/dotnet/dotnet-docker-samples) git ile aşağıdaki yönergeleri kullanarak: 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

.NET Core Docker örnekleri depodan bir zip olarak (küçük) deposu de indirebilirsiniz.

### <a name="run-the-aspnet-app-locally"></a>ASP.NET uygulama yerel olarak çalıştırma

Biz uygulama containerize önce bir başvuru noktası için ilk uygulama yerel olarak çalıştırın.

Derleme ve uygulamayı .NET Core 2.0 (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak SDK ile yerel olarak çalıştırın:

```console
cd aspnetapp
dotnet run
```

Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma

Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanma Docker içinde çalıştırın:

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` '-P' bağımsız değişkeni eşlemeleri bağlantı noktası 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde (bağlantı noktası eşleme form `host:container`). Daha fazla bilgi için bkz: [çalıştırmak docker](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri başvuru.

Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Derleme ve örnek ile Windows için Docker kapsayıcıları çalıştırma

Derleme ve örnek (yönergeleri depo kök varsayılmıştır) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanma Docker içinde çalıştırın:

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> İçin gezinmesi gereken **kapsayıcı IP adresi** (tersine http://localhost) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken. Aşağıdaki adımlarla, kapsayıcı IP adresini elde edebilirsiniz:

* Başka bir komut istemi açın.
* Çalıştırma `docker ps` çalışan kapsayıcıları görmek için. "Aspnetcore_sample" kapsayıcı olması.
* Çalıştırma `docker exec aspnetcore_sample ipconfig`.
* Kapsayıcı IP adresi kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).

> [!NOTE]
> Docker exec adı ya da karma ile tanımlayıcı kapsayıcıları destekler. Bizim örneğimizde (aspnetcore_sample) adı kullanılır.

Çalışan bir Windows kapsayıcısının IP adresini almak nasıl aşağıdaki örneğe bakın.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır. Daha fazla bilgi için bkz: [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.

Kullanarak yerel olarak üretime dağıtmaya hazır bir uygulama oluşturmak üzere [dotnet yayımlama](../tools/dotnet-publish.md) komutu.

```console
dotnet publish -c release -o published
```

> [!NOTE]
> -C yayın bağımsız değişkeni uygulama yayın modunda (hata ayıklama modu varsayılandır) oluşturur. Daha fazla bilgi için bkz: [dotnet çalıştırmak başvuru](../tools/dotnet-run.md) komut satırı parametreleri.

Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.

```console
dotnet published\aspnetapp.dll
```

Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Bu örnekte kullanılan docker görüntüleri

Bu örnekte kullanılan aşağıdaki Docker yansımaları

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Microsoft .NET Core Docker görüntüler hakkında öğrendiniz
> * Bir ASP.NET Core Dockerize için örnek uygulama var
> * ASP.NET örnek uygulamayı yerel olarak çalışan
> * Yerleşik ve örnek Docker ile Linux kapsayıcıları için çalıştı.
> * Yerleşik ve örnek ile Windows için Docker kapsayıcıları çalıştı


**Sonraki adımlar**

Uygulayabileceğiniz bazı sonraki adımlar şunlardır:

* [Visual Studio Docker araçları ile çalışma](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio Code ile hata ayıklama](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Ellere Visual Studio ile Mac, kapsayıcıları ve sunucusuz kodu bulutta hakkında alma](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.
