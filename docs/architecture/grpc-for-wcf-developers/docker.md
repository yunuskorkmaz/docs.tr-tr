---
title: WCF geliştiricileri için Docker-gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184479"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınacaktır. ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [Rendlilabs/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET Core uygulamalar için Microsoft temel görüntüleri

Microsoft, .NET Core uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar. ASP.NET Core 3,0 görüntüsü oluşturmak için iki temel görüntü kullanılır: uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü ve dağıtım için bir çalışma zamanı görüntüsü.

| Görüntü | Açıklama |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | İle `docker build`uygulama oluşturmak için. Üretimde kullanılmamalıdır. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir. Üretim için. |

Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.

| Resim etiketi (ler) | Linux | Notlar |
| --------- | ----- | ----- |
| 3,0-Buster, 3,0 | De, 10 | Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü. |
| 3,0-alçam | Alçam 3,9 | Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür. |
| 3,0-disco | Ubuntu 19,04 | |
| 3,0-Bionic | Ubuntu 18.04 | |

Alp temel görüntüsü 100 MB boyutunda, dekor ve Ubuntu görüntüleri için 200 MB ile karşılaştırılır, ancak bazı yazılım paketleri veya kitaplıkları alçam 'nın paket yönetiminde bulunmayabilir. Hangi görüntünün kullanılacağı konusunda emin değilseniz, farklı bir dağın kullanılması için etkileyici bir ihtiyacınız yoksa varsayılan deki 'ya en iyi şekilde bakalım.

> [!IMPORTANT]
> Derleme ve çalışma zamanı için aynı Linux türevini kullandığınızdan emin olun. Bir varyanta göre oluşturulan ve yayımlanan uygulamalar, başka bir değişkenle çalışmayabilir.

## <a name="create-a-docker-image"></a>Docker görüntüsü oluşturma

Docker görüntüsü, uygulamayı oluşturmak için gereken tüm komutları içeren bir *Dockerfile*tarafından tanımlanır ve uygulamayı oluşturmak veya çalıştırmak için gerekli tüm bağımlılıkları yükler. Aşağıdaki örnekte, bir ASP.NET Core 3,0 uygulaması için en basit Dockerfile gösterilmektedir:

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile iki bölümden oluşur: ilki uygulamayı derlemek ve yayımlamak `sdk` için temel görüntüyü kullanır; ikincisi ise temelden bir çalışma zamanı görüntüsü `aspnet` oluşturur. Bunun nedeni, `sdk` görüntünün 900 MB 'lık bir çalışma zamanı görüntüsü için 200 MB 'nin etrafında olmasından kaynaklanır ve çoğu içeriği çalışma zamanında gereksizdir.

### <a name="the-build-steps"></a>Derleme adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Temel görüntüyü bildirir ve `builder` diğer adı atar (açıklama için sonraki bölüme bakın). |
| `WORKDIR /src` | `/src` Dizini oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY . .` | Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar. |
| `RUN dotnet restore` | Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler. |
| `RUN dotnet publish ...` | Bir yayın derlemesi oluşturur ve yayımlar. `--runtime` Bayrağın gerekli olmadığını unutmayın. |

### <a name="the-runtime-image-steps"></a>Çalışma zamanı görüntüsü adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Yeni bir temel görüntü bildirir. |
| `WORKDIR /app` | `/app` Dizini oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY --from=builder ...` | `builder` İlk`FROM` satırdaki diğer adı kullanarak yayımlanmış uygulamayı önceki görüntüden kopyalar. |
| `ENTRYPOINT [ ... ]` | Kapsayıcı başladığında çalıştırılacak komutu ayarlar. Çalışma zamanı görüntüsündeki komutu yalnızca dll dosyalarını çalıştırabilir. `dotnet` |

### <a name="https-in-docker"></a>Docker 'da HTTPS

Microsoft 'un Docker için temel görüntüleri, `ASPNETCORE_URLS` ortam değişkenini, Kestrel Bu bağlantı noktasında HTTPS olmadan çalışacağı anlamına gelen olarak `http://+:80`ayarlar. HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [önceki bölümde](self-hosted.md)açıklandığı gibi), Dockerfile 'ın **çalışma zamanı görüntüsü oluşturma bölümünde** ortam değişkenini ayarlayarak bunu geçersiz kılmanız gerekir.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>. Dockerıgnore dosyası

Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutmakta olan `.dockerignore` dosyalar,dosyavedizinlerinderlemesırasındagörüntüyekopyalanmasınıhariçtutmakiçinkullanılabilir.`.gitignore` Bu, yalnızca kopyalama zamandan tasarruf etmez, ancak bilgisayarınızdan (özellikle) `obj` bilgisayarınızdaki dizinden görüntüye kopyalanmasından kaynaklanan bazı karmaşık hatalardan de kaçınabilir. Dosyanıza ve `bin` `obj` için en az giriş eklemeniz gerekir. `.dockerignore`

```console
bin/
obj/
```

## <a name="build-the-image"></a>Görüntüyü oluşturma

Tek bir uygulama ve bu nedenle tek bir Dockerfile içeren bir çözüm için, Dockerfile 'ı temel dizine koymak en iyisidir; diğer bir deyişle, `.sln` dosyayla aynı dizindir. Bu durumda, görüntüyü oluşturmak için dockerfile dosyasını içeren dizinden `docker build` aşağıdaki komutu kullanın.

```console
docker build --tag stockdata .
```

Tam adlandırılmış `--tag` bayrak ( `-t`kısaltıldı), belirtilmişse gerçek etiket *dahil olmak üzere* görüntünün tam adını belirtir. Sonda `.` , yapı çalıştırılacağı *bağlamı* ve dockerfile içindeki `COPY` komutlar için geçerli çalışma dizinini belirtir.

Tek bir çözümde birden çok uygulamanız varsa, her bir uygulama için dockerfile `.csproj` dosyasını dosyanın yanında, kendi klasöründe tutabilirsiniz, ancak yine de `docker build` çözümün ve Tüm projeler görüntüye kopyalanır. `--file` ( Veya`-f`) bayrağını kullanarak geçerli dizinin altına bir dockerfile belirtebilirsiniz.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın

Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.

```console
docker run -ti -p 5000:80 stockdata
```

`-ti` Bayrak geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır. Kapsayıcıda, localhost ağ arabirimindeki bağlantı noktası 80 ' e bağlantı noktası 80 ' ü yayınlar.`-p 5000:80`

## <a name="push-the-image-to-a-registry"></a>Görüntüyü bir kayıt defterine gönderme

Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için onu bir Docker kayıt defterine göndermeniz gerekir. İç ağların bir Docker kayıt defteri sağlaması gerekir. Bu, [Docker 'ın `registry` kendi görüntüsünü](https://docs.docker.com/registry/deploying/) çalıştırmak kadar basit olabilir (yani, Docker kayıt defteri bir Docker kapsayıcısında çalışır), ancak daha kapsamlı çeşitli çözümler mevcuttur. Dış paylaşım ve bulut kullanımı için [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.

Docker Hub 'ına göndermek için, görüntü adını Kullanıcı veya kuruluş adınızla ön eki olarak yapın.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Özel bir kayıt defterine göndermek için, görüntü adını kayıt defteri ana bilgisayar adı ve kuruluş adı ile önek olarak ekleyin.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Görüntü bir kayıt defterinden olduktan sonra, tek tek Docker konaklarına veya Kubernetes gibi bir kapsayıcı düzenleme altyapısına dağıtabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](self-hosted.md)
>[İleri](kubernetes.md)
