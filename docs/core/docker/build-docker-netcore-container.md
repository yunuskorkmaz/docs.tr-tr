---
title: Docker öğreticisiyle bir uygulamayı kapsayıcılı hale getirme
description: Bu öğreticide bir Docker ile .NET Core uygulamasını kapsayıcılı hale getirme öğreneceksiniz.
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 518a2228bb23569689d56577f83b066a5d518be8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186933"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: Kapsayıcılı bir .NET Core uygulaması

Bu öğreticide, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretiyor. Görüntü, kapsayıcılar, yerel geliştirme ortamı, özel Bulut veya genel bulut oluşturmak için kullanılabilir.

Bu öğreticide şunları öğreneceksiniz nasıl yapılır:

> [!div class="checklist"]
> * Bir Dockerfile'ı oluşturma
> * Microsoft .NET Core Docker temel görüntüsünde çekme
> * Görüntüyü uygulamanızı dağıtma ve özelleştirme
> * Oluşturma ve kapsayıcı çalıştırma
> * Azure’a dağıtma

Bu öğreticide, Docker kapsayıcı derleme ve dağıtım görevleri bir .NET Core uygulaması için size öğretir. [Docker platformu](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısı](https://docs.docker.com/engine/docker-overview/#docker-engine) oluşturmayı ve uygulamaları olarak paketini [Docker görüntülerini](https://docs.docker.com/glossary/?term=image). Bu görüntüleri yazılan [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) dağıtılabilir ve çalışacak biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: Başlamanın en kolay yolu

Docker görüntüsünü oluşturmadan önce bir uygulamayı kapsayıcılı hale getirme için gerekir. Linux, MacOS veya Windows üzerinde oluşturabilirsiniz. Bunu yapmanın hızlı ve en kolay yolu, .NET Core kullanmaktır.

.NET Core CLI araç takımıyla bilmiyorsanız, okuma [.NET Core SDK'sı genel bakış](../tools/index.md).

İle hem Windows hem de Linux kapsayıcıları oluşturabilirsiniz [çok arch tabanlı etiketleri](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>İlk .NET Core Docker uygulamanızı

### <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

#### <a name="net-core-sdk"></a>.NET core SDK'sı

* Yükleme [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri.

Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında işletim sistemlerinin tam listesi, .NET Core 2.1 desteklenen.

* Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.

> [!TIP]
> Bir kod Düzenleyicisi'ni yüklemeniz gerekir? Deneyin [Visual Studio Code'u](https://code.visualstudio.com/download)!

#### <a name="installing-docker-client"></a>Docker istemcisi yükleme

Yükleme [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) veya Docker istemcinin sonraki bir sürümü.

Docker istemcisi yüklenebilir:

* Linux dağıtımları

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/).

### <a name="create-a-net-core-21-console-app-for-dockerization"></a>Dockerization için bir .NET Core 2.1 konsol uygulaması oluşturma

Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutları yazın:

```console
dotnet new console
dotnet run
```

Hızlı bir kılavuz inceleyelim:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak gerekli bağımlılıkları olan proje dosyası.  Ayrıca oluşturur bir `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya.

   `Hello.csproj`:

   Proje dosyası geri yükleme bağımlılıkları ve program oluşturmak için gerekli olan her şeyi belirtir.

   * `OutputType` Etiketini belirtir bir yürütülebilir dosya, başka bir deyişle bir konsol uygulaması oluşturuyorsunuz.
   * `TargetFramework` Hedefleyen hangi .NET uygulaması etiketini belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtin ve tek bir işlemde belirtilen çerçeveleri için oluşturun. Bu öğreticide, .NET Core 2.1 için ekleriz.

   `Program.cs`:

   Tarafından program başlar `using System`. Bu ifade anlamına gelir, "her şey Getir `System` ad alanına bu dosyası için kapsama girer." `System` Ad alanı içeren temel yapılarından gibi `string`, ya da sayısal türler.

   Ad alanı ardından tanımlarız `Hello`. Ad alanı için istediğiniz değişikliği yapabilirsiniz. Adlı bir sınıf `Program` ile bu ad alanı içinde tanımlanan bir `Main` dizisini kendi bağımsız değişkeni olarak alan yöntemi. Bu dizi, derlenmiş programın çağrılırken geçirilen bağımsız değişken listesini içerir. Bizim örneğimizde programı yalnızca "Hello World!" yazar. konsola.

   **Yeni dotnet** çalıştıran [ `dotnet restore` ](../tools/dotnet-restore.md) komutu. **DotNet restore** bağımlılıklarla ağacının yükler bir [NuGet](https://www.nuget.org/)(.NET Paket Yöneticisi) çağrısı.
   NuGet, aşağıdaki görevleri gerçekleştirir:
   * çözümler *Hello.csproj* dosya.
   * dosya yüklemeleri bağımlılıkları (veya Dallarınızla makine önbelleğinizden).
   * Yazar *obj/project.assets.json* dosya.

   *Project.assets.json* eksiksiz bir NuGet bağımlılıklarını grafiği, bağlama çözümler ve diğer uygulama meta veri dosyasıdır. Bu dosya kullanılan diğer araçlarla gibi gerekli [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), kaynak kodunu doğru şekilde işlemek için.

2. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) başarılı bir derleme ve çağrılarını doğrulamak için `dotnet <assembly.dll>` uygulamayı çalıştırın.

    ```console
    $ dotnet run

    Hello World!
    ```

    Gelişmiş senaryolar için bkz: [.NET Core uygulaması dağıtımını](../deploying/index.md) Ayrıntılar için.

## <a name="dockerize-the-net-core-application"></a>.NET Core uygulamasını docker kapsayıcılarında çalıştırın

Hello .NET Core konsol uygulamasının başarıyla yerel olarak çalışır. Şimdi github'dan bir adım ileri taşımak ve derleme ve uygulamayı Docker'da çalıştırma.

### <a name="your-first-dockerfile"></a>İlk Dockerfile

Metin Düzenleyicisi'ni açın ve başlayalım! Yine de uygulamayı oluşturduk Hello dizininden çalışıyoruz.

Ya da Linux aşağıdaki Docker yönergelerini ekleyin veya [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) yeni bir dosya için. İşiniz bittiğinde Hello dizininizin kökünde Kaydet **Dockerfile**, uzantı yoktur (dosya türünüze kümesine gerekebilir `All types (*.*)` veya benzer bir şey).

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Dockerfile, sıralı olarak çalışan Docker derleme yönergeleri içerir.

İlk yönerge olmalıdır [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Bu yönerge, yeni bir derleme aşaması başlatır ve yönergeleri için temel görüntüyü ayarlar. Çok yay etiketleri Windows veya Linux kapsayıcıları için Docker Windows bağlı olarak çekme [kapsayıcı modu](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). Bizim Örneğimiz için temel görüntüyü microsoft/dotnet deposundan sdk 2.1 görüntüdür,

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) yönergesi ayarlar çalışma dizini herhangi kalan çalışma, CMD, ENTRYPOINT, kopyalama ve Ekle Dockerfile için yönergeler. Dizin yoksa, oluşturulur. Bu durumda, dockerfile'da kendisinden sonra gelen uygulama dizinine ayarlanır.

```Dockerfile
WORKDIR /app
```

[ **Kopyalama** ](https://docs.docker.com/engine/reference/builder/#copy) yönergesi kaynak yolundan yeni dosyaları veya dizinleri kopyalar ve onları hedef kapsayıcı dosya sisteminde ekler. Bu yönerge ile size C# proje dosyası kapsayıcıya kopyalarsınız.

```Dockerfile
COPY *.csproj ./
```

[ **ÇALIŞTIRMA** ](https://docs.docker.com/engine/reference/builder/#run) yönerge tüm komutları geçerli görüntünün üzerindeki yeni bir katmanda yürütür ve sonuçları işleyin. Sonuçta elde edilen işlenmiş görüntü, Dockerfile'da bir sonraki adım için kullanılır. Çalıştırılmakta olan **dotnet restore** C# proje dosyası gerekli bağımlılıkları almak için.

```Dockerfile
RUN dotnet restore
```

Bu **kopyalama** yönerge kopyalar dosyaların geri kalanı bizim kapsayıcıya içine yeni [katmanları](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Biz bu uygulamayı yayımladığınız **ÇALIŞTIRMA** yönergesi. [ **Dotnet yayımlama** ](../tools/dotnet-publish.md) komut uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar. Uygulamamızı ile yayımlanan bir **yayın** yapılandırma ve çıkış için varsayılan dizin.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) yönerge bir yürütülebilir dosyayı çalıştırmak kapsayıcı sağlar.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Artık bir Dockerfile:

* Uygulamanızı bir resme kopyalar.
* Uygulamanızın bağımlılıklarına görüntüye
* yürütülebilir dosya olarak çalıştırmak için bir uygulama oluşturur.

### <a name="build-and-run-the-hello-net-core-app"></a>Hello .NET Core uygulaması derleyebilir ve çalıştırabilirsiniz

#### <a name="essential-docker-commands"></a>Temel Docker komutları

Bu Docker komutları büyük/küçük harf önemlidir:

* [docker derleme](https://docs.docker.com/engine/reference/commandline/build/)
* [docker Run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker durdurma](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Derleme ve çalıştırma

Dockerfile yazdığınız; Şimdi Docker uygulamanızı oluşturur ve kapsayıcı çalıştırır.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Çıkışı `docker build` komutu aşağıdaki konsol çıktısına benzer olmalıdır:

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

Docker altyapısı Dockerfile çıktısı görebileceğiniz gibi bizim kapsayıcı oluşturmak için kullanılır.

Çıkışı `docker run` komutu aşağıdaki konsol çıktısına benzer olmalıdır:

```console
Hello World!
```

Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Yerel .NET Core uygulaması oluşturuldu
> * Oluşturulan bir Dockerfile ilk kapsayıcınızı oluşturun
> * Yerleşik ve Dockerized uygulamanızı çalıştı

## <a name="next-steps"></a>Sonraki adımlar

Gerçekleştirebileceğiniz bazı sonraki adımlar şunlardır:

* [.NET Docker görüntüleri Video giriş](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker ve Azure Container Instances, birlikte daha iyi!](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [Azure Hızlı Başlangıç için docker](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Uygulamanızı Azure için Docker](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.

## <a name="docker-images-used-in-this-sample"></a>Bu örnekte kullanılan docker görüntüleri

Bu örnekte kullanılan aşağıdaki Docker görüntüleri

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>İlgili kaynaklar

* [.NET core Docker örnekleri](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [Dockerfile Windows kapsayıcıları hakkında](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET framework Docker örnekleri](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [DockerHub üzerinde ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/)
* [.NET Core uygulaması - Docker öğretici docker kapsayıcılarında çalıştırın](https://docs.docker.com/engine/examples/dotnetcore/)
* [Visual Studio Docker araçları ile çalışma](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)