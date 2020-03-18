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
# <a name="create-docker-images"></a><span data-ttu-id="c3628-103">Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3628-103">Create Docker images</span></span>

<span data-ttu-id="c3628-104">Bu bölüm, Docker, Kubernetes veya diğer konteyner ortamlarında çalışmaya hazır ASP.NET Core gRPC uygulamaları için Docker görüntülerinin oluşturulmasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="c3628-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="c3628-105">Kullanılan örnek uygulama, bir ASP.NET Core MVC web uygulaması ve bir gRPC hizmeti ile, [github üzerinde dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c3628-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="c3628-106">ASP.NET Core uygulamaları için Microsoft temel görüntüleri</span><span class="sxs-lookup"><span data-stu-id="c3628-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="c3628-107">Microsoft, .NET Core uygulamaları oluşturmak ve çalıştırmak için bir dizi temel görüntü sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3628-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="c3628-108">ASP.NET Core 3.0 görüntüsü oluşturmak için iki temel resim kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="c3628-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="c3628-109">Uygulamayı oluşturmak ve yayımlamak için bir SDK görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="c3628-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="c3628-110">Dağıtım için çalışma zamanı görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="c3628-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="c3628-111">Görüntü</span><span class="sxs-lookup"><span data-stu-id="c3628-111">Image</span></span> | <span data-ttu-id="c3628-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3628-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="c3628-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="c3628-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="c3628-114">' ile `docker build`bina uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="c3628-114">For building applications with `docker build`.</span></span> <span data-ttu-id="c3628-115">Üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3628-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="c3628-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="c3628-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="c3628-117">Çalışma zamanı ve ASP.NET Temel bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="c3628-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="c3628-118">Üretim için.</span><span class="sxs-lookup"><span data-stu-id="c3628-118">For production.</span></span> |

<span data-ttu-id="c3628-119">Her görüntü için, etiketlerle ayırt edilen farklı Linux dağılımlarına dayalı dört türevi vardır.</span><span class="sxs-lookup"><span data-stu-id="c3628-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="c3628-120">Resim etiketi(ler)</span><span class="sxs-lookup"><span data-stu-id="c3628-120">Image tag(s)</span></span> | <span data-ttu-id="c3628-121">Linux</span><span class="sxs-lookup"><span data-stu-id="c3628-121">Linux</span></span> | <span data-ttu-id="c3628-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="c3628-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="c3628-123">3.0-buster, 3.0</span><span class="sxs-lookup"><span data-stu-id="c3628-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="c3628-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="c3628-124">Debian 10</span></span> | <span data-ttu-id="c3628-125">İşletim sistemi varyantı belirtilmemişse varsayılan görüntü.</span><span class="sxs-lookup"><span data-stu-id="c3628-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="c3628-126">3.0-alp in</span><span class="sxs-lookup"><span data-stu-id="c3628-126">3.0-alpine</span></span> | <span data-ttu-id="c3628-127">Alp 3.9</span><span class="sxs-lookup"><span data-stu-id="c3628-127">Alpine 3.9</span></span> | <span data-ttu-id="c3628-128">Alp temel görüntüleri Debian veya Ubuntu olanlardan çok daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="c3628-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="c3628-129">3.0-disko</span><span class="sxs-lookup"><span data-stu-id="c3628-129">3.0-disco</span></span> | <span data-ttu-id="c3628-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="c3628-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="c3628-131">3.0-biyonik</span><span class="sxs-lookup"><span data-stu-id="c3628-131">3.0-bionic</span></span> | <span data-ttu-id="c3628-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c3628-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="c3628-133">Alp taban görüntü debian ve Ubuntu görüntüleri için 200 MB ile karşılaştırıldığında, yaklaşık 100 MB.</span><span class="sxs-lookup"><span data-stu-id="c3628-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="c3628-134">Alpine'nin paket yönetiminde bazı yazılım paketleri veya kitaplıklar kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="c3628-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="c3628-135">Hangi görüntüyü kullanacağından emin değilseniz, varsayılan Debian'ı seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c3628-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3628-136">Yapı ve çalışma süresi için Linux'un aynı varyantını kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c3628-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="c3628-137">Bir varyantüzerinde oluşturulmuş ve yayımlanmış uygulamalar başka bir türde çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c3628-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="c3628-138">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3628-138">Create a Docker image</span></span>

<span data-ttu-id="c3628-139">Docker görüntüsü *Dockerdosyası*tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c3628-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="c3628-140">Bu, uygulamayı oluşturmak ve uygulamayı oluşturmak veya çalıştırmak için gereken bağımlılıkları yüklemek için gereken tüm komutları içeren bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c3628-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="c3628-141">Aşağıdaki örnek, ASP.NET Core 3.0 uygulaması için en basit Dockerfile'ı gösterir:</span><span class="sxs-lookup"><span data-stu-id="c3628-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="c3628-142">Dockerfile iki bölümden oluşur: `sdk` ilk oluşturmak ve uygulama yayınlamak için temel görüntü kullanır; `aspnet` ikincisi, tabandan bir çalışma zamanı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3628-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="c3628-143">Bunun nedeni, `sdk` görüntünün çalışma zamanı görüntüsü için yaklaşık 200 MB ile karşılaştırıldığında 900 MB civarında olması ve içeriğinin çoğunun çalışma zamanında gereksiz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c3628-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="c3628-144">Yapı adımları</span><span class="sxs-lookup"><span data-stu-id="c3628-144">The build steps</span></span>

| <span data-ttu-id="c3628-145">Adım</span><span class="sxs-lookup"><span data-stu-id="c3628-145">Step</span></span> | <span data-ttu-id="c3628-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3628-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c3628-147">Temel görüntüyü bildirir ve `builder` diğer adı atar.</span><span class="sxs-lookup"><span data-stu-id="c3628-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="c3628-148">Dizini `/src` oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c3628-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="c3628-149">Ana bilgisayardaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c3628-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="c3628-150">Harici paketleri geri yükler (ASP.NET Core 3.0 çerçevesi SDK ile önceden yüklenir).</span><span class="sxs-lookup"><span data-stu-id="c3628-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="c3628-151">Sürüm oluşturma yı oluşturur ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="c3628-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="c3628-152">Bayrağın `--runtime` gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c3628-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="c3628-153">Çalışma zamanı görüntü adımları</span><span class="sxs-lookup"><span data-stu-id="c3628-153">The runtime image steps</span></span>

| <span data-ttu-id="c3628-154">Adım</span><span class="sxs-lookup"><span data-stu-id="c3628-154">Step</span></span> | <span data-ttu-id="c3628-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3628-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c3628-156">Yeni bir temel görüntü bildirir.</span><span class="sxs-lookup"><span data-stu-id="c3628-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="c3628-157">Dizini `/app` oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c3628-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="c3628-158">Yayınlanan uygulamayı önceki resimden, ilk `builder` `FROM` satırdaki diğer adı kullanarak kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c3628-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="c3628-159">Kapsayıcı başladığında çalışacak komutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c3628-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="c3628-160">Çalışma `dotnet` zamanı görüntüsündeki komut yalnızca DLL dosyalarını çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="c3628-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="c3628-161">Docker'da HTTPS</span><span class="sxs-lookup"><span data-stu-id="c3628-161">HTTPS in Docker</span></span>

<span data-ttu-id="c3628-162">Docker için Microsoft temel `ASPNETCORE_URLS` görüntüleri, `http://+:80`ortam değişkenini ,kestrel'in bu bağlantı noktasında HTTPS olmadan çalıştığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c3628-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="c3628-163">ÖZEL bir sertifikayla HTTPS kullanıyorsanız [(Kendi barındırılan gRPC uygulamalarında](self-hosted.md)açıklandığı gibi), bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3628-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="c3628-164">Dockerfile'Nizin çalışma zamanı görüntü oluşturma bölümünde ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3628-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="c3628-165">.dockerignore dosyası</span><span class="sxs-lookup"><span data-stu-id="c3628-165">The .dockerignore file</span></span>

<span data-ttu-id="c3628-166">Belirli `.gitignore` dosyaları ve dizinleri kaynak denetiminden `.dockerignore` dışlayan dosyalar gibi, dosya da yapı sırasında görüntüye kopyalanmasını engellemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3628-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="c3628-167">Bu yalnızca zaman kopyalama dan tasarruf sağlar, ama aynı zamanda `obj` pc'nizden dizin görüntü içine kopyalanmış olan kaynaklanan bazı hataları önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3628-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="c3628-168">En azından dosyanız için `bin` ve `obj` dosyanıza giriş eklemeniz `.dockerignore` gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3628-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="c3628-169">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3628-169">Build the image</span></span>

<span data-ttu-id="c3628-170">Tek bir uygulama ile bir çözüm için, ve böylece tek bir Dockerfile, temel dizine Dockerfile koymak en basit.</span><span class="sxs-lookup"><span data-stu-id="c3628-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="c3628-171">Başka bir deyişle, `.sln` dosyayla aynı dizine koyun.</span><span class="sxs-lookup"><span data-stu-id="c3628-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="c3628-172">Bu durumda, görüntüyü oluşturmak için Dockerfile'ı içeren dizinden aşağıdaki `docker build` komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3628-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="c3628-173">Kafa karıştırıcı `--tag` adlandırılmış bayrak `-t`(kısaltılabilir) belirtilmişse gerçek etiketi de dahil olmak üzere görüntünün tüm adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3628-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="c3628-174">Sonunda `.` yapının çalıştırılan bağlamı belirtir; Dockerfile'deki `COPY` komutların geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="c3628-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="c3628-175">Tek bir çözüm içinde birden çok uygulamanız varsa, her uygulama için Dockerfile'ı dosyanın yanında kendi klasöründe `.csproj` tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3628-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="c3628-176">Çözümün ve tüm `docker build` projelerin görüntüye kopyalandığından emin olmak için komutu yine de temel dizinden çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3628-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="c3628-177">`--file` (veya) `-f`bayrağını kullanarak geçerli dizinin altında bir Dockerdosyası belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3628-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="c3628-178">Görüntüyü makinenizdeki bir kapta çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c3628-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="c3628-179">Resmi yerel Docker örneğinde çalıştırmak için `docker run` komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3628-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="c3628-180">Bayrak, `-ti` geçerli terminalinizi konteynerterminaline bağlar ve etkileşimli modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3628-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="c3628-181">Yayımlar `-p 5000:80` (bağlantılar) port 80 yerel barındırma ağ arabiriminde bağlantı noktası 5000 için kapsayıcı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c3628-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="c3628-182">Görüntüyü kayıt defterine itme</span><span class="sxs-lookup"><span data-stu-id="c3628-182">Push the image to a registry</span></span>

<span data-ttu-id="c3628-183">Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için onu Docker kayıt defterine itin.</span><span class="sxs-lookup"><span data-stu-id="c3628-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="c3628-184">Dahili ağların docker kayıt defteri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3628-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="c3628-185">Bu [docker kendi `registry` görüntü](https://docs.docker.com/registry/deploying/) (Docker kayıt bir Docker konteyner çalışır) çalışan kadar basit olabilir, ancak çeşitli daha kapsamlı çözümler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c3628-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="c3628-186">Dış paylaşım ve bulut kullanımı için [Azure Kapsayıcı Kayıt Defteri](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c3628-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="c3628-187">Docker Hub'a gitmek için, kullanıcı veya kuruluş adınız ile görüntü adını öneleyin.</span><span class="sxs-lookup"><span data-stu-id="c3628-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="c3628-188">Özel bir kayıt defterine itmek için, resim adını kayıt sahibi adı ve kuruluş adı ile önek.</span><span class="sxs-lookup"><span data-stu-id="c3628-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="c3628-189">Görüntü bir kayıt defterinde olduktan sonra, tek tek Docker ana bilgisayarlarına veya Kubernetes gibi bir konteyner düzenleme motoruna dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3628-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c3628-190">[Önceki](self-hosted.md)
>[Sonraki](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="c3628-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
