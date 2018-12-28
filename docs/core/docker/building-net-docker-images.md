---
title: Docker görüntülerini genel bakış
description: Docker kayıt defterinden yayımlanan .NET Core Docker görüntüleri kullanmayı öğrenin. Ayrıca, görüntüleri çekmek ve kendi görüntülerinizi oluşturmayı öğreneceksiniz.
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: dd8c6c500dc2177768e6cba0c1e303950e20d4f3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656043"
---
# <a name="learn-about-docker-images-for-net-core"></a>.NET Core için Docker görüntüleri hakkında bilgi edinin

Bu öğreticide, .NET Core üzerinde Docker nasıl odaklanıyoruz. İlk olarak sunulur ve Microsoft ve kullanım örnekleri tarafından tutulan farklı bir Docker görüntüleri keşfedin. Biz, daha sonra nasıl oluşturacağınızı ve ASP.NET Core uygulaması docker kapsayıcılarında çalıştırın öğrenin.

Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:
> [!div class="checklist"]
> * Microsoft .NET Core Docker görüntüleri hakkında bilgi edinin 
> * Bir ASP.NET Core Dockerize örnek uygulaması alma
> * ASP.NET örnek uygulamayı yerel olarak çalıştırma
> * Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma
> * Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma

## <a name="docker-image-optimizations"></a>Docker görüntüsünü en iyi duruma getirme

Geliştiriciler için Docker görüntülerini oluştururken, biz üç ana senaryo üzerinde odaklanır:

* .NET Core uygulamaları geliştirmek için kullanılan görüntü
* .NET Core uygulamaları oluşturmak için kullanılan görüntü
* .NET Core uygulamaları çalıştırmak için kullanılan görüntü

Neden üç görüntüleri?
Geliştirme, derleme ve kapsayıcılı uygulamalar çalıştırmak, farklı önceliklere sahibiz.

* **Geliştirme:**  Öncelik odaklanır, değişiklikler ve değişiklikleri hata ayıklama özelliği hızla yineleyin. Resmin boyutu önemli değildir, bunun yerine, değişiklikler kodunuza yapabilir ve bunları hızlıca görmek?

* **Derleme:** Bu görüntü derleyici ve ikili dosyaları iyileştirmek için diğer herhangi bir bağımlılığın içeren uygulamanızı derlemek için gereken her şeyi içerir.  Derleme görüntüyü bir üretim görüntüsüne yerleştirdiğiniz varlıkları oluşturmak için kullanın. Derleme görüntüsünü veya bir yapı ortamı sürekli tümleştirme için kullanılır. Bu yaklaşım, derlemek ve bir yapı görüntü örneği (tüm gerekli bağımlılıkları olan) uygulamasında oluşturmak bir yapı aracısını sağlar. Yapı aracınız, yalnızca bu Docker görüntüsünü çalıştırma bilmesi gerekir.

* **Üretim:** Ne kadar hızlı dağıtma ve başlatma, resmi? Bu görüntü, Docker kayıt defterinizin Docker konaklarınız için ağ performansı en iyi duruma getirilmiş şekilde küçüktür. İçeriği, Docker run sonuçları işlemek için hızlı süreye etkinleştirme çalıştırmaya hazırsınız. Dinamik kod derlemesi, Docker modelde gerek yoktur. Bu görüntüde yerleştirdiğiniz içeriği ikili dosyaları ve uygulamayı çalıştırmak için gerekli içeriklere sınırlı olacaktır.

    Örneğin, `dotnet publish` çıktı içerir:

    * derlenmiş ikili dosyaları
    * .js ve .css dosyaları


Eklenecek nedeni `dotnet publish` üretim görüntünüzü komut çıktısında boyutuna dürüst etmektir.

Bazı .NET Core görüntüleri Katmanlar oldukça basit bir işlem en son etiket indiriliyor, bu nedenle farklı etiketler arasında paylaşın. Makinenizde zaten daha eski bir sürümü varsa, bu mimaride gerekli disk alanını azaltır.

Birden çok uygulama aynı makinede genel görüntülerden kullandığınızda, bellek ortak görüntülerin arasında paylaşılır. Görüntüleri paylaşılması için aynı olması gerekir.

## <a name="docker-image-variations"></a>Docker görüntüsü farklılıkları

Görüntü çeşitleri altında sağladığımız yukarıdaki hedeflere ulaşmak için [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Bu görüntü .NET Core ve komut satırı araçları'nı (CLI) içerir .NET Core SDK'sı içerir. Bu görüntü eşlendiği **geliştirme senaryosu**. Bu görüntü, yerel geliştirme, hata ayıklama ve birim testi için kullanın. Bu görüntü için de kullanılabilir, **derleme** senaryoları. Kullanarak `microsoft/dotnet:sdk` , en son sürümü her zaman verir.

> [!TIP]
> Gereksinimlerinizi hakkında konusunda emin değilseniz, kullanmak istediğiniz `microsoft/dotnet:<version>-sdk` görüntü. "Pratikte" görüntü olarak throw kullanılmak üzere tasarlanmıştır koyma kapsayıcı (kaynak kodunuzu bağlayın ve uygulamanızı başlatmak için bir kapsayıcı başlatma) ve diğer görüntüleri oluşturmak için temel görüntü olarak.

* `microsoft/dotnet:<version>-runtime`: Bu görüntü, .NET Core (çalışma zamanı ve kitaplıklarda) içerir ve .NET Core uygulamaları çalıştırma için optimize edilmiştir **üretim**.

## <a name="alternative-images"></a>Alternatif resimleri

Geliştirme, derleme ve üretim en iyi duruma getirilmiş senaryoların yanı sıra ek görüntüleri sağlıyoruz:

* `microsoft/dotnet:<version>-runtime-deps`: **Çalışma zamanı deps** görüntü, tüm yerel .NET Core tarafından gerekli bağımlılıkları ile işletim sistemi içerir. Bu görüntü içindir [kendi içindeki uygulamaları](../deploying/index.md).

Her değişken en son sürümleri:

* `microsoft/dotnet` veya `microsoft/dotnet:latest` (diğer ad SDK görüntü için)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Araştırılacak örnekleri

* [Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi uygulama desenini gösterir. Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.

* Bu .NET Core Docker örnek bir en iyi uygulama desenini gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)

## <a name="forward-the-request-scheme-and-original-ip-address"></a>İstek düzeni ve özgün IP iletme

Proxy sunucuları, yük Dengeleyiciler ve diğer ağ Gereçleri, bir istek hakkındaki bilgiler genellikle kapsayıcılı uygulama ulaşmadan önce gizlememeniz:

* HTTPS isteklerini HTTP üzerinden taşınır, özgün şeması (HTTPS) kaybolur ve bir üst bilgisinde iletilmesi gerekir.
* Uygulama proxy'si ve doğru kaynağına değil Internet veya kurumsal ağ üzerindeki bir istek aldığından, özgün istemci IP adresi de üst bilgisinde gönderilmelidir.

Bu bilgiler, örneğin yeniden yönlendirmeleri, kimlik doğrulaması, bağlama oluşturmayı, ilke değerlendirmesi ve istemci coğrafi konum isteği işleme önemli olabilir.

Şema ve kapsayıcılı bir ASP.NET Core uygulaması orijinal IP adresine iletmek için iletilen üstbilgileri ara yazılımı kullanın. Daha fazla bilgi için [proxy sunucuları ile çalışma ve yük Dengeleyiciler için ASP.NET Core yapılandırma](/aspnet/core/host-and-deploy/proxy-load-balancer).

## <a name="your-first-aspnet-core-docker-app"></a>İlk ASP.NET Core Docker uygulamanızı

Bu öğretici için docker kapsayıcılarında çalıştırın istiyoruz uygulama için bir ASP.NET Core Docker örnek uygulama kullanma olanak tanır. Bu ASP.NET Core Docker örnek uygulama, Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi bir uygulama desenini gösterir. Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.

Örnek Dockerfile, ASP.NET Core çalışma zamanı Docker temel görüntüsünde alanlarını temel alan bir ASP.NET Core uygulamasını Docker görüntü oluşturur.

Kullandığı [Docker çok aşamalı yapı özelliği](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) için:

* temel bir kapsayıcıda örneği oluşturmak **büyük** ASP.NET Core derleme Docker temel görüntüsünde 
* temel bir Docker görüntüsü son yapı sonucu kopyalar **daha küçük** ASP.NET Core Docker çalışma zamanı temel görüntü

> [!NOTE]
> Derleme görüntü, çalışma zamanı yansıma çalışmazken uygulamaları geliştirmek için gerekli araçları içerir.

### <a name="prerequisites"></a>Önkoşullar

Derlemek ve çalıştırmak için aşağıdakileri yükleyin:

#### <a name="net-core-21-sdk"></a>.NET core 2.1 SDK'sı

* Yükleme [.NET Core SDK'sını 2.1](https://www.microsoft.com/net/core).

* Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.

> [!TIP]
> Bir kod Düzenleyicisi'ni yüklemeniz gerekir? Deneyin [Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Docker istemcisi yükleme

Yükleme [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.

Docker istemcisi yüklenebilir:

* Linux dağıtımları

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/).

#### <a name="installing-git-for-sample-repository"></a>Örnek deposu için Git yükleme

* Yükleme [git](https://git-scm.com/download) depoyu kopyalamak istiyorsanız.

### <a name="getting-the-sample-application"></a>Örnek uygulamayı alma

Kopyalayarak örnek almak için en kolay yolu olan [.NET Core Docker deposunda](https://github.com/dotnet/dotnet-docker) git ile aşağıdaki yönergeleri kullanarak: 

```console
git clone https://github.com/dotnet/dotnet-docker
```

(Küçük) depo, .NET Core Docker depodan bir zip olarak da indirebilirsiniz.

### <a name="run-the-aspnet-app-locally"></a>ASP.NET uygulamasını yerel olarak çalıştırma

Biz uygulamayı kapsayıcılı hale getirme önce bir başvuru noktası için öncelikle uygulamayı yerel olarak çalıştırın.

Derleme ve uygulamayı yerel olarak .NET Core 2.1 (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak SDK ile çalıştırın:

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Derleme ve örnek Linux kapsayıcıları için Docker ile çalıştırma

Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Linux kapsayıcıları kullanarak örneği çalıştırın:

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` '-P' bağımsız değişkeni haritalar 5000 kapsayıcının 80 numaralı bağlantı noktasına yerel makinenizde bağlantı noktası (bağlantı noktası eşleme formu `host:container`). Daha fazla bilgi için [docker run](https://docs.docker.com/engine/reference/commandline/exec/) başvuru komut satırı parametreleri.

Uygulama başlatıldıktan sonra ziyaret **http://localhost:5000** web tarayıcınızda.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Derleme ve örnek için Docker Windows kapsayıcıları ile çalıştırma

Derleme ve Docker (depo kökünde yönergeleri olduğunu varsayın) aşağıdaki komutları kullanarak Windows kapsayıcıları kullanarak örneği çalıştırın:

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> İçin gezinmesi gereken **kapsayıcı IP adresi** (başlangıcı yerine sonundan `http://localhost`) doğrudan tarayıcınızda Windows kapsayıcıları kullanırken. Aşağıdaki adımlarla kapsayıcınızı IP adresini alabilirsiniz:

* Başka bir komut istemi açın.
* Çalıştırma `docker ps` , çalışan kapsayıcıları görmek için. "Aspnetcore_sample" kapsayıcı olması.
* `docker exec aspnetcore_sample ipconfig`'i çalıştırın.
* Kapsayıcı IP adresini kopyalayıp tarayıcınıza (örneğin, 172.29.245.43).

> [!NOTE]
> Docker exec adı ya da karma değeri ile tanımlama kapsayıcıları destekler. Bizim örneğimizde (aspnetcore_sample) adı kullanılır.

Çalışan bir Windows kapsayıcısına IP adresini alma, aşağıdaki örneğe bakın.

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
> Docker exec çalışan bir kapsayıcıda yeni bir komut çalıştırır. Daha fazla bilgi için [docker exec başvuru](https://docs.docker.com/engine/reference/commandline/exec/) komut satırı parametreleri.

Yerel olarak kullanarak üretime dağıtmaya hazır bir uygulama oluşturabilir [dotnet yayımlama](../tools/dotnet-publish.md) komutu.

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> - C sürüm bağımsız uygulamayı (hata ayıklama modu varsayılandır) yayın modunda oluşturur. Daha fazla bilgi için [dotnet çalıştırma başvuru](../tools/dotnet-run.md) komut satırı parametreleri.

Uygulamayı çalıştırmak **Windows** aşağıdaki komutu kullanarak.

```console
dotnet published\aspnetapp.dll
```

Uygulamayı çalıştırmak **Linux** veya **macOS** aşağıdaki komutu kullanarak.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Bu örnekte kullanılan docker görüntüleri

Bu örnek 's dockerfile içinde aşağıdaki Docker görüntüleri kullanılır.

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Microsoft .NET Core Docker görüntüleri hakkında bilgi edindiniz
> * Bir ASP.NET Core Dockerize örnek uygulaması alındı
> * Örnek ASP.NET uygulamasını yerel olarak çalıştı
> * Yerleşik ve örnek Linux kapsayıcıları için Docker ile çalıştırıldı.
> * Yerleşik ve örnek için Docker Windows kapsayıcıları ile çalıştırıldı

**Sonraki adımlar**

Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:

* [Visual Studio Docker araçları ile çalışma](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio kodu ile hata ayıklama](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Bire bir Visual Studio ile Mac, kapsayıcılar ve sunucusuz kod için bulutta hakkında edinme](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.
