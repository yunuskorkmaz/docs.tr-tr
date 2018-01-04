---
title: ".NET Core ile Docker temellerini öğrenin"
description: "Docker ve .NET Core temel Öğreticisi"
keywords: ".NET, .NET core, Docker, öğretici"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a>.NET Core ile Docker temellerini öğrenin

Bu öğretici, Docker kapsayıcısı derleme ve görevler için bir .NET Core uygulaması dağıtma öğretir. Bu öğreticinin sürecinde size bilgi edinin:

> [!div class="checklist"]
> * Bir Dockerfile oluşturma
> * Bir .NET Core uygulaması oluşturma
> * Docker kapsayıcıya uygulamanızı dağıtmak nasıl.

[Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısına](https://docs.docker.com/engine/docker-overview/#docker-engine) hızlı bir şekilde oluşturmak ve uygulamaları olarak paketlemek için [Docker görüntüleri](https://docs.docker.com/glossary/?term=image). Bu görüntüleri yazılmış [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) dağıtılması ve çalıştırmak için biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: başlamak için en kolay yolu

Docker görüntü oluşturmadan önce uygulamanın containerize gerekir. Linux, MacOS veya Windows oluşturabilirsiniz. Bunu yapmak için hızlı ve en kolay yolu, .NET Core kullanmaktır.

.NET Core CLI araç takımı değilseniz, okuma [.NET Core SDK Genel Bakış](../tools/index.md).

Hem Windows hem de Linux kapsayıcılarıyla yapı [çok arch dayalı etiketleri](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>İlk .NET Core Docker uygulamanızı

### <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

#### <a name="net-core-20-sdk"></a>.NET core 2.0 SDK'sı

* Yükleme [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

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

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Dockerization için bir .NET Core 2.0 konsol uygulaması oluşturma

Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutları yazın:

```console
dotnet new console
dotnet run
```

Şimdi hızlı bir kılavuz yapın:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md)güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak için gereken bağımlılıkları olan proje dosyası.  Ayrıca oluşturur bir `Program.cs`, uygulama için giriş noktası içeren temel bir dosya.
   
   `Hello.csproj`:

   Proje dosyası bağımlılıkları geri yükleyin ve programı oluşturmak için gerekli olan her şeyi belirtir.

   * `OutputType` Etiketi bir yürütülebilir dosya, diğer bir deyişle bir konsol uygulaması oluşturduğunuz belirtir.
   * `TargetFramework` Etiketi hedefleme hangi .NET uygulaması belirtir. Gelişmiş bir senaryo da birden çok hedef çerçeveyi belirtin ve tek bir işlem içinde belirtilen çerçeve için oluşturun. Bu öğreticide, .NET Core 2.0 için oluşturun.

   `Program.cs`:

   Tarafından programı başlatan `using System`. Bu bildirimi anlamına gelir, "her şeyi Getir `System` ad alanı bu dosya için kapsam içine." `System` Ad alanı içeren temel yapıları gibi `string`, veya sayısal türler.

   Ardından adlı bir ad alanı tanımlarız `Hello`. Ad alanı için istediğiniz değişikliği yapabilirsiniz. Adlı bir sınıf `Program` ad alanında, ile tanımlanmış bir `Main` yönteminin dizisini kendi bağımsız değişken olarak alan. Bu dizi derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir. Bizim örneğimizde, programın yalnızca "Hello World!" yazar. konsola.

2. `$ dotnet restore`

   .NET Core içinde 2.x **dotnet yeni** çalıştıran [ `dotnet restore` ](../tools/dotnet-restore.md) komutu. **DotNet geri yükleme** bağımlılıkları ile ağacının yükler bir [NuGet](https://www.nuget.org/)(.NET Paket Yöneticisi) çağrısı.
   NuGet aşağıdaki görevleri gerçekleştirir:
   * çözümler *Hello.csproj* dosyası 
   * dosya yüklemeleri bağımlılıkları (veya alan, makine önbelleğinden)
   * Yazar *obj/project.assets.json* dosyası

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json* NuGet bağımlılıkları grafiği, bağlama çözümleri ve diğer uygulama meta verileri eksiksiz bir dosyadır. Bu dosya kullanılır diğer araçları tarafından gibi gerekli [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), kaynak kodu doğru şekilde işleyemedi.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)çağrıları [ `dotnet build` ](../tools/dotnet-build.md) başarılı bir yapı ve çağrılarını doğrulamak için `dotnet <assembly.dll>` uygulamayı çalıştırın.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Gelişmiş senaryolar için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) Ayrıntılar için.

## <a name="dockerize-the-net-core-application"></a>.NET Core uygulama dockerize

Merhaba .NET Core konsol uygulaması başarıyla yerel olarak çalışır. Şimdi şirketinizdeki başka bir adım yapmanıza ve derleme ve Docker içinde uygulamayı çalıştırın.

### <a name="your-first-dockerfile"></a>İlk Dockerfile

Metin Düzenleyicisi'ni açın ve başlayalım! Hala uygulama oluşturduğumuz Hello dizininden çalışıyoruz.

Ya da Linux aşağıdaki Docker yönergelerini ekleyin veya [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) yeni bir dosyaya. Tamamlandığında, kök Hello dizininizin kaydedin **Dockerfile**, uzantısı olmayan (dosya türü kümesine gerekebilir `All types (*.*)` veya benzeri).

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Dockerfile sırayla çalışır Docker derleme yönergeleri içerir.

İlk yönergenin olmalıdır [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Bu yönerge, yeni bir derleme aşama başlatır ve temel görüntü yönergeleri için ayarlar. Birden çok yay etiketleri Windows veya Linux kapsayıcıları için Docker Windows bağlı olarak çekme [kapsayıcı modu](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). 2.0 sdk görüntünün microsoft/dotnet depodan bizim örnek için temel görüntüdür,

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) yönerge ayarlar çalışma dizini herhangi kalan çalışma, CMD, ENTRYPOINT, kopyalama ve Ekle Dockerfile için yönergeler. Dizin yoksa, oluşturulur. Bu durumda, WORKDIR uygulama dizinine ayarlanır.

```Dockerfile
WORKDIR /app
```

[ **Kopya** ](https://docs.docker.com/engine/reference/builder/#copy) yönerge yeni dosya veya dizinlerin kaynak yolundan kopyalar ve hedef kapsayıcı dosya sisteminde ekler. Bu yönerge ile biz kapsayıcıya C# proje dosyası konumuna kopyalarsınız.

```Dockerfile
COPY *.csproj ./
```

[ **Çalıştırmak** ](https://docs.docker.com/engine/reference/builder/#run) yönergesi geçerli görüntü üzerinde yeni bir katman içinde herhangi bir komut çalıştırır ve sonuçları uygulayın. Sonuçta elde edilen taahhüt edilen görüntü Dockerfile sonraki adımda kullanılır. Çalıştırılmakta olan **dotnet geri yükleme** C# proje dosyası gerekli bağımlılıkları alınamıyor. 

```Dockerfile
RUN dotnet restore
```

Bu **kopya** yönerge kopyalar dosyaların geri kalanını bizim kapsayıcıya içine yeni [katmanları](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Biz bu uygulamayla yayımlama **çalıştırmak** yönergesi. [ **Dotnet yayımlama** ](../tools/dotnet-publish.md) komutu uygulama derler, proje dosyasında belirtilen bağımlılıklarını aracılığıyla okur ve bir dizine dosyaları sonuç kümesini yayımlar. Bizim uygulama ile yayımlanan bir **sürüm** yapılandırması ve varsayılan dizinine çıktı.

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) yönerge bir yürütülebilir dosyayı çalıştırmak için kapsayıcı sağlar.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Bir Dockerfile var. Bu:

* Uygulamanızı görüntüye kopyalar.
* görüntüye uygulamanızın bağımlılıkları
* bir yürütülebilir dosya çalıştırmak için uygulamayı derlemeler

### <a name="build-and-run-the-hello-net-core-20-app"></a>Derleme ve Hello .NET Core 2.0 uygulamayı çalıştırma

#### <a name="essential-docker-commands"></a>Temel Docker komutları

Bu Docker komutları gereklidir:

* [docker derleme](https://docs.docker.com/engine/reference/commandline/build/)
* [docker Çalıştır](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker Durdur](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Derleme ve çalıştırma

Dockerfile yazdı; Şimdi Docker uygulamanızı oluşturur ve ardından kapsayıcı çalıştırır.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

Çıktısını `docker build` komutu aşağıdaki konsol çıktısı benzer:

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
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
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

Çıktısını gördüğünüz gibi Docker altyapısına Dockerfile bizim kapsayıcı oluşturmak için kullanılır.

Çıktısını `docker run` komutu aşağıdaki konsol çıktısı benzer:

```console
Hello World!
```

Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Yerel bir .NET Core uygulaması oluşturuldu
> * İlk kapsayıcı oluşturmak için bir Dockerfile oluşturuldu
> * Yerleşik ve Dockerized uygulamanızı çalıştı



## <a name="next-steps"></a>Sonraki Adımlar

Uygulayabileceğiniz bazı sonraki adımlar şunlardır:

* [.NET Docker görüntüleri Video giriş](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker & Azure kapsayıcı örnekleri birlikte daha iyi!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Azure Quickstarts için docker](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Uygulamanızı Azure için Docker üzerinde dağıtma](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.

## <a name="docker-images-used-in-this-sample"></a>Bu örnekte kullanılan docker görüntüleri

Bu örnekte kullanılan aşağıdaki Docker yansımaları

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>İlgili Kaynaklar

* [.NET core Docker örnekleri](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Windows kapsayıcılarında Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET framework Docker örnekleri](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core DockerHub üzerinde](https://hub.docker.com/r/microsoft/aspnetcore/)
* [.NET Core uygulama - Docker öğretici dockerize](https://docs.docker.com/engine/examples/dotnetcore/)
* [Visual Studio Docker araçları ile çalışma](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)