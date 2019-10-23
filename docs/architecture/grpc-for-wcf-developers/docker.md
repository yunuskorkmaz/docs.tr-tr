---
title: WCF geliştiricileri için Docker-gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2ed3e823c83d8f11fb7290ba6c343b4b47e68e0b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770545"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınacaktır. ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET Core uygulamalar için Microsoft temel görüntüleri

Microsoft, .NET Core uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar. ASP.NET Core 3,0 görüntüsü oluşturmak için iki temel görüntü kullanılır: uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü ve dağıtım için bir çalışma zamanı görüntüsü.

| Görüntü | Açıklama |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | @No__t_0 ile uygulama oluşturma. Üretimde kullanılmamalıdır. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir. Üretim için. |

Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.

| Resim etiketi (ler) | Linux | Notlar |
| --------- | ----- | ----- |
| 3,0-Buster, 3,0 | De, 10 | Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü. |
| 3,0-alçam | Alçam 3,9 | Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür. |
| 3,0-disco | Ubuntu 19,04 | |
| 3,0-Bionic | Ubuntu 18,04 | |

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

Dockerfile iki bölümden oluşur: ilki, uygulamayı derlemek ve yayımlamak için `sdk` temel görüntüsünü kullanır; İkincisi `aspnet` temel öğesinden bir çalışma zamanı görüntüsü oluşturur. Bunun nedeni, `sdk` görüntüsünün 900 MB 'lık bir çalışma zamanı görüntüsü için 200 MB 'nin etrafında olması ve içeriğinin çoğunun çalışma zamanında gereksiz olması nedeniyle oluşur.

### <a name="the-build-steps"></a>Derleme adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Temel görüntüyü bildirir ve `builder` diğer adı atar (açıklama için sonraki bölüme bakın). |
| `WORKDIR /src` | @No__t_0 dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY . .` | Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar. |
| `RUN dotnet restore` | Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler. |
| `RUN dotnet publish ...` | Bir yayın derlemesi oluşturur ve yayımlar. @No__t_0 bayrağının gerekli olmadığını unutmayın. |

### <a name="the-runtime-image-steps"></a>Çalışma zamanı görüntüsü adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Yeni bir temel görüntü bildirir. |
| `WORKDIR /app` | @No__t_0 dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY --from=builder ...` | Yayımlanan uygulamayı önceki görüntüden kopyalar, ilk `FROM` satırından `builder` diğer adını kullanarak. |
| `ENTRYPOINT [ ... ]` | Kapsayıcı başladığında çalıştırılacak komutu ayarlar. Çalışma zamanı görüntüsündeki `dotnet` komutu yalnızca DLL dosyalarını çalıştırabilir. |

### <a name="https-in-docker"></a>Docker 'da HTTPS

Microsoft 'un Docker için temel görüntüleri, bu bağlantı noktasında HTTPS olmadan çalışacağı anlamına gelen `ASPNETCORE_URLS` ortam değişkenini `http://+:80` olarak ayarladı. HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [önceki bölümde](self-hosted.md)açıklandığı gibi), Dockerfile 'ın **çalışma zamanı görüntüsü oluşturma bölümünde** ortam değişkenini ayarlayarak bunu geçersiz kılmanız gerekir.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>. Dockerıgnore dosyası

Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutulan dosyaları `.gitignore` benzer şekilde, `.dockerignore` dosyası, derleme sırasında dosya ve dizinlerin görüntüye kopyalanmasını hariç tutmak için kullanılabilir. Bu, yalnızca kopyalama zamandan tasarruf etmez, ancak BILGISAYARıNıZDAKI `obj` Directory 'nin görüntüye kopyalanmasından kaynaklanan bazı karmaşık hatalardan da kaçınabilir. @No__t_2 dosyanıza `bin` ve `obj` için en az girdi eklemeniz gerekir.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Görüntüyü oluşturma

Tek bir uygulama ve bu nedenle tek bir Dockerfile içeren bir çözüm için, Dockerfile 'ı temel dizine koymak en iyisidir; diğer bir deyişle, `.sln` dosyasıyla aynı dizindir. Bu durumda, görüntüyü oluşturmak için Dockerfile dosyasını içeren dizinden aşağıdaki `docker build` komutunu kullanın.

```console
docker build --tag stockdata .
```

@No__t_0 bayrağını (`-t` kısaltabilen), belirtilen gerçek etiket *dahil olmak üzere* görüntünün tam adını belirtir. Sonundaki `.`, yapı çalıştırılacağı *bağlamı* belirtir; Dockerfile içindeki `COPY` komutları için geçerli çalışma dizini.

Tek bir çözümde birden çok uygulamanız varsa, her bir uygulama için Dockerfile dosyasını, `.csproj` dosyasının yanına, kendi klasöründe tutabilirsiniz, `docker build` ancak çözümün ve tüm projeler görüntüye kopyalanır. @No__t_0 (veya `-f`) bayrağını kullanarak geçerli dizinin altına bir Dockerfile belirtebilirsiniz.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın

Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.

```console
docker run -ti -p 5000:80 stockdata
```

@No__t_0 bayrağı geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır. @No__t_0, kapsayıcıda bağlantı noktası 80 ' i localhost ağ arabirimindeki bağlantı noktası 80 ' e yayınlar.

## <a name="push-the-image-to-a-registry"></a>Görüntüyü bir kayıt defterine gönderme

Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için onu bir Docker kayıt defterine göndermeniz gerekir. İç ağların bir Docker kayıt defteri sağlaması gerekir. Bu, [Docker 'ın kendi `registry` görüntüsünü](https://docs.docker.com/registry/deploying/) (yani, Docker kayıt defteri bir Docker kapsayıcısında çalıştırılır) çalıştırmak kadar basit olabilir, ancak daha kapsamlı çok sayıda çözüm mevcuttur. Dış paylaşım ve bulut kullanımı için [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.

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
