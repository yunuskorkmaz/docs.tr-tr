---
title: Docker - WCF Geliştiricileri için gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148120"
---
# <a name="create-docker-images"></a>Docker görüntüleri oluşturma

Bu bölüm, Docker, Kubernetes veya diğer konteyner ortamlarında çalışmaya hazır ASP.NET Core gRPC uygulamaları için Docker görüntülerinin oluşturulmasını kapsar. Kullanılan örnek uygulama, bir ASP.NET Core MVC web uygulaması ve bir gRPC hizmeti ile, [github üzerinde dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda mevcuttur.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET Core uygulamaları için Microsoft temel görüntüleri

Microsoft, .NET Core uygulamaları oluşturmak ve çalıştırmak için bir dizi temel görüntü sağlar. ASP.NET Core 3.0 görüntüsü oluşturmak için iki temel resim kullanırsınız:

- Uygulamayı oluşturmak ve yayımlamak için bir SDK görüntüsü.
- Dağıtım için çalışma zamanı görüntüsü.

| Görüntü | Açıklama |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | ' ile `docker build`bina uygulamaları için. Üretimde kullanılmamalıdır. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Çalışma zamanı ve ASP.NET Temel bağımlılıkları içerir. Üretim için. |

Her görüntü için, etiketlerle ayırt edilen farklı Linux dağılımlarına dayalı dört türevi vardır.

| Resim etiketi(ler) | Linux | Notlar |
| --------- | ----- | ----- |
| 3.0-buster, 3.0 | Debian 10 | İşletim sistemi varyantı belirtilmemişse varsayılan görüntü. |
| 3.0-alp in | Alp 3.9 | Alp temel görüntüleri Debian veya Ubuntu olanlardan çok daha küçüktür. |
| 3.0-disko | Ubuntu 19.04 | |
| 3.0-biyonik | Ubuntu 18.04 | |

Alp taban görüntü debian ve Ubuntu görüntüleri için 200 MB ile karşılaştırıldığında, yaklaşık 100 MB. Alpine'nin paket yönetiminde bazı yazılım paketleri veya kitaplıklar kullanılamayabilir. Hangi görüntüyü kullanacağından emin değilseniz, varsayılan Debian'ı seçmelisiniz.

> [!IMPORTANT]
> Yapı ve çalışma süresi için Linux'un aynı varyantını kullandığınızdan emin olun. Bir varyantüzerinde oluşturulmuş ve yayımlanmış uygulamalar başka bir türde çalışmayabilir.

## <a name="create-a-docker-image"></a>Docker görüntüsü oluşturma

Docker görüntüsü *Dockerdosyası*tarafından tanımlanır. Bu, uygulamayı oluşturmak ve uygulamayı oluşturmak veya çalıştırmak için gereken bağımlılıkları yüklemek için gereken tüm komutları içeren bir metin dosyasıdır. Aşağıdaki örnek, ASP.NET Core 3.0 uygulaması için en basit Dockerfile'ı gösterir:

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

Dockerfile iki bölümden oluşur: `sdk` ilk oluşturmak ve uygulama yayınlamak için temel görüntü kullanır; `aspnet` ikincisi, tabandan bir çalışma zamanı görüntüsü oluşturur. Bunun nedeni, `sdk` görüntünün çalışma zamanı görüntüsü için yaklaşık 200 MB ile karşılaştırıldığında 900 MB civarında olması ve içeriğinin çoğunun çalışma zamanında gereksiz olmasıdır.

### <a name="the-build-steps"></a>Yapı adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Temel görüntüyü bildirir ve `builder` diğer adı atar. |
| `WORKDIR /src` | Dizini `/src` oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY . .` | Ana bilgisayardaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar. |
| `RUN dotnet restore` | Harici paketleri geri yükler (ASP.NET Core 3.0 çerçevesi SDK ile önceden yüklenir). |
| `RUN dotnet publish ...` | Sürüm oluşturma yı oluşturur ve yayımlar. Bayrağın `--runtime` gerekli olmadığını unutmayın. |

### <a name="the-runtime-image-steps"></a>Çalışma zamanı görüntü adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Yeni bir temel görüntü bildirir. |
| `WORKDIR /app` | Dizini `/app` oluşturur ve geçerli çalışma dizini olarak ayarlar. |
| `COPY --from=builder ...` | Yayınlanan uygulamayı önceki resimden, ilk `builder` `FROM` satırdaki diğer adı kullanarak kopyalar. |
| `ENTRYPOINT [ ... ]` | Kapsayıcı başladığında çalışacak komutu ayarlar. Çalışma `dotnet` zamanı görüntüsündeki komut yalnızca DLL dosyalarını çalıştırabilir. |

### <a name="https-in-docker"></a>Docker'da HTTPS

Docker için Microsoft temel `ASPNETCORE_URLS` görüntüleri, `http://+:80`ortam değişkenini ,kestrel'in bu bağlantı noktasında HTTPS olmadan çalıştığı anlamına gelir. ÖZEL bir sertifikayla HTTPS kullanıyorsanız [(Kendi barındırılan gRPC uygulamalarında](self-hosted.md)açıklandığı gibi), bunu geçersiz kılmanız gerekir. Dockerfile'Nizin çalışma zamanı görüntü oluşturma bölümünde ortam değişkenini ayarlayın.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>.dockerignore dosyası

Belirli `.gitignore` dosyaları ve dizinleri kaynak denetiminden `.dockerignore` dışlayan dosyalar gibi, dosya da yapı sırasında görüntüye kopyalanmasını engellemek için kullanılabilir. Bu yalnızca zaman kopyalama dan tasarruf sağlar, ama aynı zamanda `obj` pc'nizden dizin görüntü içine kopyalanmış olan kaynaklanan bazı hataları önleyebilirsiniz. En azından dosyanız için `bin` ve `obj` dosyanıza giriş eklemeniz `.dockerignore` gerekir.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Görüntü oluşturma

Tek bir uygulama ile bir çözüm için, ve böylece tek bir Dockerfile, temel dizine Dockerfile koymak en basit. Başka bir deyişle, `.sln` dosyayla aynı dizine koyun. Bu durumda, görüntüyü oluşturmak için Dockerfile'ı içeren dizinden aşağıdaki `docker build` komutu kullanın.

```console
docker build --tag stockdata .
```

Kafa karıştırıcı `--tag` adlandırılmış bayrak `-t`(kısaltılabilir) belirtilmişse gerçek etiketi de dahil olmak üzere görüntünün tüm adını belirtir. Sonunda `.` yapının çalıştırılan bağlamı belirtir; Dockerfile'deki `COPY` komutların geçerli çalışma dizini.

Tek bir çözüm içinde birden çok uygulamanız varsa, her uygulama için Dockerfile'ı dosyanın yanında kendi klasöründe `.csproj` tutabilirsiniz. Çözümün ve tüm `docker build` projelerin görüntüye kopyalandığından emin olmak için komutu yine de temel dizinden çalıştırmanız gerekir. `--file` (veya) `-f`bayrağını kullanarak geçerli dizinin altında bir Dockerdosyası belirtebilirsiniz.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Görüntüyü makinenizdeki bir kapta çalıştırma

Resmi yerel Docker örneğinde çalıştırmak için `docker run` komutu kullanın.

```console
docker run -ti -p 5000:80 stockdata
```

Bayrak, `-ti` geçerli terminalinizi konteynerterminaline bağlar ve etkileşimli modda çalışır. Yayımlar `-p 5000:80` (bağlantılar) port 80 yerel barındırma ağ arabiriminde bağlantı noktası 5000 için kapsayıcı üzerinde.

## <a name="push-the-image-to-a-registry"></a>Görüntüyü kayıt defterine itme

Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için onu Docker kayıt defterine itin. Dahili ağların docker kayıt defteri sağlaması gerekir. Bu [docker kendi `registry` görüntü](https://docs.docker.com/registry/deploying/) (Docker kayıt bir Docker konteyner çalışır) çalışan kadar basit olabilir, ancak çeşitli daha kapsamlı çözümler mevcuttur. Dış paylaşım ve bulut kullanımı için [Azure Kapsayıcı Kayıt Defteri](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.

Docker Hub'a gitmek için, kullanıcı veya kuruluş adınız ile görüntü adını öneleyin.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Özel bir kayıt defterine itmek için, resim adını kayıt sahibi adı ve kuruluş adı ile önek.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Görüntü bir kayıt defterinde olduktan sonra, tek tek Docker ana bilgisayarlarına veya Kubernetes gibi bir konteyner düzenleme motoruna dağıtabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](self-hosted.md)
>[Sonraki](kubernetes.md)
