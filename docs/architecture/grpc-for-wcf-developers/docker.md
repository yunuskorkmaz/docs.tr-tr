---
title: WCF geliştiricileri için Docker-gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970095"
---
# <a name="create-docker-images"></a><span data-ttu-id="8927c-103">Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8927c-103">Create Docker images</span></span>

<span data-ttu-id="8927c-104">Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8927c-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="8927c-105">ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8927c-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="8927c-106">ASP.NET Core uygulamalar için Microsoft temel görüntüleri</span><span class="sxs-lookup"><span data-stu-id="8927c-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="8927c-107">Microsoft, .NET uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-107">Microsoft provides a range of base images for building and running .NET applications.</span></span> <span data-ttu-id="8927c-108">ASP.NET Core 5,0 görüntüsü oluşturmak için iki temel görüntü kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="8927c-108">To create an ASP.NET Core 5.0 image, you use two base images:</span></span>

- <span data-ttu-id="8927c-109">Uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="8927c-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="8927c-110">Dağıtım için bir çalışma zamanı görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="8927c-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="8927c-111">Görüntü</span><span class="sxs-lookup"><span data-stu-id="8927c-111">Image</span></span> | <span data-ttu-id="8927c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8927c-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="8927c-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="8927c-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="8927c-114">İle uygulama oluşturmak için `docker build` .</span><span class="sxs-lookup"><span data-stu-id="8927c-114">For building applications with `docker build`.</span></span> <span data-ttu-id="8927c-115">Üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8927c-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="8927c-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="8927c-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="8927c-117">Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8927c-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="8927c-118">Üretim için.</span><span class="sxs-lookup"><span data-stu-id="8927c-118">For production.</span></span> |

<span data-ttu-id="8927c-119">Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="8927c-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="8927c-120">Resim etiketi (ler)</span><span class="sxs-lookup"><span data-stu-id="8927c-120">Image tag(s)</span></span> | <span data-ttu-id="8927c-121">Linux</span><span class="sxs-lookup"><span data-stu-id="8927c-121">Linux</span></span> | <span data-ttu-id="8927c-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="8927c-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="8927c-123">5,0-Buster-Slim, 5,0</span><span class="sxs-lookup"><span data-stu-id="8927c-123">5.0-buster-slim, 5.0</span></span> | <span data-ttu-id="8927c-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="8927c-124">Debian 10</span></span> | <span data-ttu-id="8927c-125">Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü.</span><span class="sxs-lookup"><span data-stu-id="8927c-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="8927c-126">5,0-alçam</span><span class="sxs-lookup"><span data-stu-id="8927c-126">5.0-alpine</span></span> | <span data-ttu-id="8927c-127">Alçam 3,12</span><span class="sxs-lookup"><span data-stu-id="8927c-127">Alpine 3.12</span></span> | <span data-ttu-id="8927c-128">Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="8927c-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="8927c-129">5,0-odak</span><span class="sxs-lookup"><span data-stu-id="8927c-129">5.0-focal</span></span>| <span data-ttu-id="8927c-130">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="8927c-130">Ubuntu 20.04</span></span> | |

<span data-ttu-id="8927c-131">Alp temel görüntüsü 100 MB boyutunda, de, ve Ubuntu görüntüleri için 200 MB ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="8927c-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="8927c-132">Bazı yazılım paketleri veya kitaplıkları alp 'nin paket yönetiminde bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8927c-132">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="8927c-133">Hangi görüntünün kullanılacağı konusunda emin değilseniz, muhtemelen varsayılan deni seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8927c-133">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8927c-134">Derleme ve çalışma zamanı için aynı Linux türevini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8927c-134">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="8927c-135">Bir çeşit üzerinde oluşturulan ve yayımlanan uygulamalar, başka bir değişkenle çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8927c-135">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="8927c-136">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8927c-136">Create a Docker image</span></span>

<span data-ttu-id="8927c-137">Docker görüntüsü bir *Dockerfile* tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8927c-137">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="8927c-138">Bu *Dockerfile* , uygulamayı oluşturmak için gereken tüm komutları içeren bir metin dosyasıdır ve uygulamayı oluşturmak ya da çalıştırmak için gerekli olan tüm bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="8927c-138">This *Dockerfile* is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="8927c-139">Aşağıdaki örnekte, bir ASP.NET Core 5,0 uygulaması için en basit Dockerfile gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8927c-139">The following example shows the simplest Dockerfile for an ASP.NET Core 5.0 application:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="8927c-140">Dockerfile iki bölümden oluşur: ilki `sdk` uygulamayı derlemek ve yayımlamak için temel görüntüyü kullanır; ikincisi ise temelden bir çalışma zamanı görüntüsü oluşturur `aspnet` .</span><span class="sxs-lookup"><span data-stu-id="8927c-140">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="8927c-141">Bunun nedeni, `sdk` görüntünün 900 MB 'ın etrafında, çalışma zamanı görüntüsü için 200 MB 'nin etrafında, ve içeriğinin çoğunun çalışma zamanında gereksiz olmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="8927c-141">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="8927c-142">Derleme adımları</span><span class="sxs-lookup"><span data-stu-id="8927c-142">The build steps</span></span>

| <span data-ttu-id="8927c-143">Adım</span><span class="sxs-lookup"><span data-stu-id="8927c-143">Step</span></span> | <span data-ttu-id="8927c-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8927c-144">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="8927c-145">Temel görüntüyü bildirir ve `builder` diğer adı atar.</span><span class="sxs-lookup"><span data-stu-id="8927c-145">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="8927c-146">Dizini oluşturur `/src` ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-146">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="8927c-147">Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="8927c-147">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="8927c-148">Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler.</span><span class="sxs-lookup"><span data-stu-id="8927c-148">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="8927c-149">Bir yayın derlemesi oluşturur ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-149">Builds and publishes a Release build.</span></span> <span data-ttu-id="8927c-150">`--runtime`Bayrağın gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8927c-150">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="8927c-151">Çalışma zamanı görüntüsü adımları</span><span class="sxs-lookup"><span data-stu-id="8927c-151">The runtime image steps</span></span>

| <span data-ttu-id="8927c-152">Adım</span><span class="sxs-lookup"><span data-stu-id="8927c-152">Step</span></span> | <span data-ttu-id="8927c-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8927c-153">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="8927c-154">Yeni bir temel görüntü bildirir.</span><span class="sxs-lookup"><span data-stu-id="8927c-154">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="8927c-155">Dizini oluşturur `/app` ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-155">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="8927c-156">`builder`İlk satırdaki diğer adı kullanarak yayımlanmış uygulamayı önceki görüntüden kopyalar `FROM` .</span><span class="sxs-lookup"><span data-stu-id="8927c-156">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="8927c-157">Kapsayıcı başladığında çalıştırılacak komutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-157">Sets the command to run when the container starts.</span></span> <span data-ttu-id="8927c-158">`dotnet`Çalışma zamanı görüntüsündeki komutu yalnızca dll dosyalarını çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="8927c-158">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="8927c-159">Docker 'da HTTPS</span><span class="sxs-lookup"><span data-stu-id="8927c-159">HTTPS in Docker</span></span>

<span data-ttu-id="8927c-160">Docker için Microsoft temel görüntüleri, `ASPNETCORE_URLS` ortam değişkenini, `http://+:80` Kestrel Bu bağlantı noktasında HTTPS olmadan çalıştığı anlamına gelen olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-160">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="8927c-161">HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [Şirket içinde barındırılan gRPC uygulamalarında](self-hosted.md)açıklandığı gibi), bu yapılandırmayı geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8927c-161">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this configuration.</span></span> <span data-ttu-id="8927c-162">Dockerfile 'ın çalışma zamanı görüntüsü oluşturma bölümünde ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8927c-162">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="8927c-163">. Dockerıgnore dosyası</span><span class="sxs-lookup"><span data-stu-id="8927c-163">The .dockerignore file</span></span>

<span data-ttu-id="8927c-164">`.gitignore`Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutmakta olan dosyalar, `.dockerignore` dosya ve dizinlerin derleme sırasında görüntüye kopyalanmasını hariç tutmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8927c-164">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="8927c-165">Bu dosya, yalnızca kopyalama zamandan tasarruf etmez, ancak `obj` bilgisayarınızdaki bir dizinin görüntüye kopyalanmasını gerektiren bazı hatalardan da kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8927c-165">This file not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="8927c-166">En azından, dosyanıza ve için girdi eklemeniz gerekir `bin` `obj` `.dockerignore` .</span><span class="sxs-lookup"><span data-stu-id="8927c-166">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="8927c-167">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8927c-167">Build the image</span></span>

<span data-ttu-id="8927c-168">`StockKube.sln`İki farklı uygulama içeren bir çözüm için `StockData` `StockWeb` , dockerfile 'ın her biri için temel dizine yerleştirilmeleri en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="8927c-168">For a `StockKube.sln` solution containing two different applications `StockData` and `StockWeb`, it's simplest to put the Dockerfile for each one of them in the base directory.</span></span> <span data-ttu-id="8927c-169">Bu durumda, görüntüyü derlemek için `docker build` dosyanın bulunduğu dizinden aşağıdaki komutu kullanın `.sln` .</span><span class="sxs-lookup"><span data-stu-id="8927c-169">In that case, to build the image, use the following `docker build` command from the same directory where `.sln` file resides.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

<span data-ttu-id="8927c-170">`--tag`Tam adlandırılmış bayrak (kısaltıldı `-t` ), belirtilmişse gerçek etiket dahil olmak üzere görüntünün tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8927c-170">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="8927c-171">`.`Sonda, yapı çalıştırılacağı bağlamı ve `COPY` Dockerfile içindeki komutlar için geçerli çalışma dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8927c-171">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="8927c-172">Tek bir çözümde birden çok uygulamanız varsa, dosyanın yanında her bir uygulama için Dockerfile dosyasını kendi klasöründe tutabilirsiniz `.csproj` .</span><span class="sxs-lookup"><span data-stu-id="8927c-172">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="8927c-173">`docker build`Çözümün ve tüm projelerin görüntüye kopyalandığından emin olmak için komutu yine de temel dizinden çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8927c-173">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="8927c-174">`--file`(Veya) bayrağını kullanarak geçerli dizinin altına bir Dockerfile belirtebilirsiniz `-f` .</span><span class="sxs-lookup"><span data-stu-id="8927c-174">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="8927c-175">Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8927c-175">Run the image in a container on your machine</span></span>

<span data-ttu-id="8927c-176">Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8927c-176">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

<span data-ttu-id="8927c-177">`-ti`Bayrak geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="8927c-177">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="8927c-178">`-p 5000:80`Kapsayıcıda, localhost ağ arabirimindeki bağlantı noktası 5000 ' e bağlantı noktası 80 ' ü yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8927c-178">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="8927c-179">Görüntüyü bir kayıt defterine gönderme</span><span class="sxs-lookup"><span data-stu-id="8927c-179">Push the image to a registry</span></span>

<span data-ttu-id="8927c-180">Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için bir Docker kayıt defterine gönderin.</span><span class="sxs-lookup"><span data-stu-id="8927c-180">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="8927c-181">İç ağların bir Docker kayıt defteri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8927c-181">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="8927c-182">Bu etkinlik, [Docker 'ın kendi `registry` görüntüsünü](https://docs.docker.com/registry/deploying/) (Docker kayıt defteri bir Docker kapsayıcısında çalıştırılır) çalıştırmak kadar basit olabilir, ancak daha kapsamlı çeşitli çözümler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="8927c-182">This activity can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="8927c-183">Dış paylaşım ve bulut kullanımı için [Azure Container Registry](/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="8927c-183">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="8927c-184">Docker Hub 'ına göndermek için, görüntü adını Kullanıcı veya kuruluş adınızla ön eke koyun.</span><span class="sxs-lookup"><span data-stu-id="8927c-184">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

<span data-ttu-id="8927c-185">Özel bir kayıt defterine göndermek için, görüntü adını kayıt defteri ana bilgisayar adı ve kuruluş adı ile önek olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8927c-185">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

<span data-ttu-id="8927c-186">Görüntü bir kayıt defterinden olduktan sonra, tek tek Docker konaklarına veya Kubernetes gibi bir kapsayıcı düzenleme altyapısına dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8927c-186">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8927c-187">[Önceki](self-hosted.md) 
> [Sonraki](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="8927c-187">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
