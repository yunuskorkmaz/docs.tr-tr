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
# <a name="docker"></a><span data-ttu-id="0def0-103">Docker</span><span class="sxs-lookup"><span data-stu-id="0def0-103">Docker</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0def0-104">Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="0def0-104">This section will cover the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="0def0-105">ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="0def0-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="0def0-106">ASP.NET Core uygulamalar için Microsoft temel görüntüleri</span><span class="sxs-lookup"><span data-stu-id="0def0-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="0def0-107">Microsoft, .NET Core uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="0def0-108">ASP.NET Core 3,0 görüntüsü oluşturmak için iki temel görüntü kullanılır: uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü ve dağıtım için bir çalışma zamanı görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="0def0-108">To create an ASP.NET Core 3.0 image, two base images are used: an SDK image to build and publish the application, and a runtime image for deployment.</span></span>

| <span data-ttu-id="0def0-109">Görüntü</span><span class="sxs-lookup"><span data-stu-id="0def0-109">Image</span></span> | <span data-ttu-id="0def0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0def0-110">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="0def0-111">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="0def0-111">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="0def0-112">@No__t_0 ile uygulama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0def0-112">For building applications with `docker build`.</span></span> <span data-ttu-id="0def0-113">Üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0def0-113">Not to be used in production.</span></span> |
| [<span data-ttu-id="0def0-114">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="0def0-114">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="0def0-115">Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0def0-115">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="0def0-116">Üretim için.</span><span class="sxs-lookup"><span data-stu-id="0def0-116">For production.</span></span> |

<span data-ttu-id="0def0-117">Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="0def0-117">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="0def0-118">Resim etiketi (ler)</span><span class="sxs-lookup"><span data-stu-id="0def0-118">Image tag(s)</span></span> | <span data-ttu-id="0def0-119">Linux</span><span class="sxs-lookup"><span data-stu-id="0def0-119">Linux</span></span> | <span data-ttu-id="0def0-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="0def0-120">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="0def0-121">3,0-Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="0def0-121">3.0-buster, 3.0</span></span> | <span data-ttu-id="0def0-122">De, 10</span><span class="sxs-lookup"><span data-stu-id="0def0-122">Debian 10</span></span> | <span data-ttu-id="0def0-123">Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü.</span><span class="sxs-lookup"><span data-stu-id="0def0-123">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="0def0-124">3,0-alçam</span><span class="sxs-lookup"><span data-stu-id="0def0-124">3.0-alpine</span></span> | <span data-ttu-id="0def0-125">Alçam 3,9</span><span class="sxs-lookup"><span data-stu-id="0def0-125">Alpine 3.9</span></span> | <span data-ttu-id="0def0-126">Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="0def0-126">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="0def0-127">3,0-disco</span><span class="sxs-lookup"><span data-stu-id="0def0-127">3.0-disco</span></span> | <span data-ttu-id="0def0-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="0def0-128">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="0def0-129">3,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="0def0-129">3.0-bionic</span></span> | <span data-ttu-id="0def0-130">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="0def0-130">Ubuntu 18.04</span></span> | |

<span data-ttu-id="0def0-131">Alp temel görüntüsü 100 MB boyutunda, dekor ve Ubuntu görüntüleri için 200 MB ile karşılaştırılır, ancak bazı yazılım paketleri veya kitaplıkları alçam 'nın paket yönetiminde bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0def0-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images, but some software packages or libraries may not be available in Alpine's package management.</span></span> <span data-ttu-id="0def0-132">Hangi görüntünün kullanılacağı konusunda emin değilseniz, farklı bir dağın kullanılması için etkileyici bir ihtiyacınız yoksa varsayılan deki 'ya en iyi şekilde bakalım.</span><span class="sxs-lookup"><span data-stu-id="0def0-132">If you're not sure which image to use, it's best to stick to the default Debian unless you have a compelling need to use a different distro.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0def0-133">Derleme ve çalışma zamanı için aynı Linux türevini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0def0-133">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="0def0-134">Bir varyanta göre oluşturulan ve yayımlanan uygulamalar, başka bir değişkenle çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0def0-134">Applications built and published on one variant may not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="0def0-135">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0def0-135">Create a Docker image</span></span>

<span data-ttu-id="0def0-136">Docker görüntüsü, uygulamayı oluşturmak için gereken tüm komutları içeren bir *Dockerfile*tarafından tanımlanır ve uygulamayı oluşturmak veya çalıştırmak için gerekli tüm bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="0def0-136">A Docker image is defined by a *Dockerfile*, a text file that contains all the commands that are needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="0def0-137">Aşağıdaki örnekte, bir ASP.NET Core 3,0 uygulaması için en basit Dockerfile gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0def0-137">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="0def0-138">Dockerfile iki bölümden oluşur: ilki, uygulamayı derlemek ve yayımlamak için `sdk` temel görüntüsünü kullanır; İkincisi `aspnet` temel öğesinden bir çalışma zamanı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0def0-138">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="0def0-139">Bunun nedeni, `sdk` görüntüsünün 900 MB 'lık bir çalışma zamanı görüntüsü için 200 MB 'nin etrafında olması ve içeriğinin çoğunun çalışma zamanında gereksiz olması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="0def0-139">This is because the `sdk` image is around 900 MB compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="0def0-140">Derleme adımları</span><span class="sxs-lookup"><span data-stu-id="0def0-140">The build steps</span></span>

| <span data-ttu-id="0def0-141">Adım</span><span class="sxs-lookup"><span data-stu-id="0def0-141">Step</span></span> | <span data-ttu-id="0def0-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0def0-142">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0def0-143">Temel görüntüyü bildirir ve `builder` diğer adı atar (açıklama için sonraki bölüme bakın).</span><span class="sxs-lookup"><span data-stu-id="0def0-143">Declares the base image and assigns the `builder` alias (see next section for explanation).</span></span> |
| `WORKDIR /src` | <span data-ttu-id="0def0-144">@No__t_0 dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-144">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="0def0-145">Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="0def0-145">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="0def0-146">Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0def0-146">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="0def0-147">Bir yayın derlemesi oluşturur ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-147">Builds and publishes a Release build.</span></span> <span data-ttu-id="0def0-148">@No__t_0 bayrağının gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0def0-148">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="0def0-149">Çalışma zamanı görüntüsü adımları</span><span class="sxs-lookup"><span data-stu-id="0def0-149">The runtime image steps</span></span>

| <span data-ttu-id="0def0-150">Adım</span><span class="sxs-lookup"><span data-stu-id="0def0-150">Step</span></span> | <span data-ttu-id="0def0-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0def0-151">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0def0-152">Yeni bir temel görüntü bildirir.</span><span class="sxs-lookup"><span data-stu-id="0def0-152">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="0def0-153">@No__t_0 dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-153">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="0def0-154">Yayımlanan uygulamayı önceki görüntüden kopyalar, ilk `FROM` satırından `builder` diğer adını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0def0-154">Copies the published application from the previous image, using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="0def0-155">Kapsayıcı başladığında çalıştırılacak komutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-155">Sets the command to run when the container starts.</span></span> <span data-ttu-id="0def0-156">Çalışma zamanı görüntüsündeki `dotnet` komutu yalnızca DLL dosyalarını çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="0def0-156">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="0def0-157">Docker 'da HTTPS</span><span class="sxs-lookup"><span data-stu-id="0def0-157">HTTPS in Docker</span></span>

<span data-ttu-id="0def0-158">Microsoft 'un Docker için temel görüntüleri, bu bağlantı noktasında HTTPS olmadan çalışacağı anlamına gelen `ASPNETCORE_URLS` ortam değişkenini `http://+:80` olarak ayarladı.</span><span class="sxs-lookup"><span data-stu-id="0def0-158">Microsoft's base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel will run without HTTPS on that port.</span></span> <span data-ttu-id="0def0-159">HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [önceki bölümde](self-hosted.md)açıklandığı gibi), Dockerfile 'ın **çalışma zamanı görüntüsü oluşturma bölümünde** ortam değişkenini ayarlayarak bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0def0-159">If you're using HTTPS with a custom certificate (as described in [the previous section](self-hosted.md)), you should override this by setting the environment variable **in the runtime image creation part** of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="0def0-160">. Dockerıgnore dosyası</span><span class="sxs-lookup"><span data-stu-id="0def0-160">The .dockerignore file</span></span>

<span data-ttu-id="0def0-161">Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutulan dosyaları `.gitignore` benzer şekilde, `.dockerignore` dosyası, derleme sırasında dosya ve dizinlerin görüntüye kopyalanmasını hariç tutmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0def0-161">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="0def0-162">Bu, yalnızca kopyalama zamandan tasarruf etmez, ancak BILGISAYARıNıZDAKI `obj` Directory 'nin görüntüye kopyalanmasından kaynaklanan bazı karmaşık hatalardan da kaçınabilir.</span><span class="sxs-lookup"><span data-stu-id="0def0-162">This not only saves time copying, but can also avoid some confusing errors that arise from having (particularly) the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="0def0-163">@No__t_2 dosyanıza `bin` ve `obj` için en az girdi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0def0-163">You should add at least entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="0def0-164">Görüntüyü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0def0-164">Build the image</span></span>

<span data-ttu-id="0def0-165">Tek bir uygulama ve bu nedenle tek bir Dockerfile içeren bir çözüm için, Dockerfile 'ı temel dizine koymak en iyisidir; diğer bir deyişle, `.sln` dosyasıyla aynı dizindir.</span><span class="sxs-lookup"><span data-stu-id="0def0-165">For a solution with a single application, and thus a single Dockerfile, it is simplest to put the Dockerfile in the base directory; that is, the same directory as the `.sln` file.</span></span> <span data-ttu-id="0def0-166">Bu durumda, görüntüyü oluşturmak için Dockerfile dosyasını içeren dizinden aşağıdaki `docker build` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0def0-166">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="0def0-167">@No__t_0 bayrağını (`-t` kısaltabilen), belirtilen gerçek etiket *dahil olmak üzere* görüntünün tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0def0-167">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, *including* the actual tag if specified.</span></span> <span data-ttu-id="0def0-168">Sonundaki `.`, yapı çalıştırılacağı *bağlamı* belirtir; Dockerfile içindeki `COPY` komutları için geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="0def0-168">The `.` at the end specifies the *context* in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="0def0-169">Tek bir çözümde birden çok uygulamanız varsa, her bir uygulama için Dockerfile dosyasını, `.csproj` dosyasının yanına, kendi klasöründe tutabilirsiniz, `docker build` ancak çözümün ve tüm projeler görüntüye kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0def0-169">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file, but you should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="0def0-170">@No__t_0 (veya `-f`) bayrağını kullanarak geçerli dizinin altına bir Dockerfile belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0def0-170">You can specify a Dockerfile below the current directory using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="0def0-171">Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="0def0-171">Run the image in a container on your machine</span></span>

<span data-ttu-id="0def0-172">Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0def0-172">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="0def0-173">@No__t_0 bayrağı geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="0def0-173">The `-ti` flag connects your current terminal to the container's terminal and runs in interactive mode.</span></span> <span data-ttu-id="0def0-174">@No__t_0, kapsayıcıda bağlantı noktası 80 ' i localhost ağ arabirimindeki bağlantı noktası 80 ' e yayınlar.</span><span class="sxs-lookup"><span data-stu-id="0def0-174">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="0def0-175">Görüntüyü bir kayıt defterine gönderme</span><span class="sxs-lookup"><span data-stu-id="0def0-175">Push the image to a registry</span></span>

<span data-ttu-id="0def0-176">Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için onu bir Docker kayıt defterine göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0def0-176">Once you've verified that the image works, you need to push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="0def0-177">İç ağların bir Docker kayıt defteri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0def0-177">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="0def0-178">Bu, [Docker 'ın kendi `registry` görüntüsünü](https://docs.docker.com/registry/deploying/) (yani, Docker kayıt defteri bir Docker kapsayıcısında çalıştırılır) çalıştırmak kadar basit olabilir, ancak daha kapsamlı çok sayıda çözüm mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="0def0-178">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (that's right, the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="0def0-179">Dış paylaşım ve bulut kullanımı için [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="0def0-179">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="0def0-180">Docker Hub 'ına göndermek için, görüntü adını Kullanıcı veya kuruluş adınızla ön eki olarak yapın.</span><span class="sxs-lookup"><span data-stu-id="0def0-180">To push to the Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="0def0-181">Özel bir kayıt defterine göndermek için, görüntü adını kayıt defteri ana bilgisayar adı ve kuruluş adı ile önek olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0def0-181">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="0def0-182">Görüntü bir kayıt defterinden olduktan sonra, tek tek Docker konaklarına veya Kubernetes gibi bir kapsayıcı düzenleme altyapısına dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0def0-182">Once the image is in a registry, you can deploy it to individual Docker hosts or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0def0-183">[Önceki](self-hosted.md)
>[İleri](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0def0-183">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
