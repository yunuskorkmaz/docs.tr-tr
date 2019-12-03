---
title: WCF geliştiricileri için Docker-gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
ms.date: 09/02/2019
ms.openlocfilehash: d23dc46526183b459c36f11bae4def8b1c9b9410
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711295"
---
# <a name="create-docker-images"></a><span data-ttu-id="192c8-103">Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="192c8-103">Create Docker images</span></span>

<span data-ttu-id="192c8-104">Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="192c8-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="192c8-105">ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="192c8-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="192c8-106">ASP.NET Core uygulamalar için Microsoft temel görüntüleri</span><span class="sxs-lookup"><span data-stu-id="192c8-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="192c8-107">Microsoft, .NET Core uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="192c8-108">ASP.NET Core 3,0 görüntüsü oluşturmak için iki temel görüntü kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="192c8-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span> 

- <span data-ttu-id="192c8-109">Uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="192c8-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="192c8-110">Dağıtım için bir çalışma zamanı görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="192c8-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="192c8-111">Görüntü</span><span class="sxs-lookup"><span data-stu-id="192c8-111">Image</span></span> | <span data-ttu-id="192c8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="192c8-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="192c8-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="192c8-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="192c8-114">`docker build`ile uygulama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="192c8-114">For building applications with `docker build`.</span></span> <span data-ttu-id="192c8-115">Üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="192c8-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="192c8-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="192c8-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="192c8-117">Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="192c8-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="192c8-118">Üretim için.</span><span class="sxs-lookup"><span data-stu-id="192c8-118">For production.</span></span> |

<span data-ttu-id="192c8-119">Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="192c8-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="192c8-120">Resim etiketi (ler)</span><span class="sxs-lookup"><span data-stu-id="192c8-120">Image tag(s)</span></span> | <span data-ttu-id="192c8-121">Linux</span><span class="sxs-lookup"><span data-stu-id="192c8-121">Linux</span></span> | <span data-ttu-id="192c8-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="192c8-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="192c8-123">3,0-Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="192c8-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="192c8-124">De, 10</span><span class="sxs-lookup"><span data-stu-id="192c8-124">Debian 10</span></span> | <span data-ttu-id="192c8-125">Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü.</span><span class="sxs-lookup"><span data-stu-id="192c8-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="192c8-126">3,0-alçam</span><span class="sxs-lookup"><span data-stu-id="192c8-126">3.0-alpine</span></span> | <span data-ttu-id="192c8-127">Alçam 3,9</span><span class="sxs-lookup"><span data-stu-id="192c8-127">Alpine 3.9</span></span> | <span data-ttu-id="192c8-128">Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="192c8-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="192c8-129">3,0-disco</span><span class="sxs-lookup"><span data-stu-id="192c8-129">3.0-disco</span></span> | <span data-ttu-id="192c8-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="192c8-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="192c8-131">3,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="192c8-131">3.0-bionic</span></span> | <span data-ttu-id="192c8-132">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="192c8-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="192c8-133">Alp temel görüntüsü 100 MB boyutunda, de, ve Ubuntu görüntüleri için 200 MB ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="192c8-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="192c8-134">Bazı yazılım paketleri veya kitaplıkları alp 'nin paket yönetiminde bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="192c8-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="192c8-135">Hangi görüntünün kullanılacağı konusunda emin değilseniz, muhtemelen varsayılan deni seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="192c8-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="192c8-136">Derleme ve çalışma zamanı için aynı Linux türevini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="192c8-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="192c8-137">Bir çeşit üzerinde oluşturulan ve yayımlanan uygulamalar, başka bir değişkenle çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="192c8-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="192c8-138">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="192c8-138">Create a Docker image</span></span>

<span data-ttu-id="192c8-139">Docker görüntüsü bir *Dockerfile*tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="192c8-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="192c8-140">Bu, uygulamayı oluşturmak için gereken tüm komutları içeren bir metin dosyasıdır ve uygulamayı oluşturmak ya da çalıştırmak için gerekli tüm bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="192c8-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="192c8-141">Aşağıdaki örnekte, bir ASP.NET Core 3,0 uygulaması için en basit Dockerfile gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="192c8-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="192c8-142">Dockerfile iki bölümden oluşur: ilki, uygulamayı derlemek ve yayımlamak için `sdk` temel görüntüsünü kullanır; İkincisi `aspnet` temel öğesinden bir çalışma zamanı görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="192c8-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="192c8-143">Bunun nedeni, `sdk` görüntüsünün 900 MB 'lik bir yerdir ve çalışma zamanı görüntüsü için 200 MB 'nin etrafında ve bu içeriğin çoğu çalışma zamanında gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="192c8-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="192c8-144">Derleme adımları</span><span class="sxs-lookup"><span data-stu-id="192c8-144">The build steps</span></span>

| <span data-ttu-id="192c8-145">Adım</span><span class="sxs-lookup"><span data-stu-id="192c8-145">Step</span></span> | <span data-ttu-id="192c8-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="192c8-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="192c8-147">Temel görüntüyü bildirir ve `builder` diğer adı atar.</span><span class="sxs-lookup"><span data-stu-id="192c8-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="192c8-148">`/src` dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="192c8-149">Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="192c8-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="192c8-150">Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler.</span><span class="sxs-lookup"><span data-stu-id="192c8-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="192c8-151">Bir yayın derlemesi oluşturur ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="192c8-152">`--runtime` bayrağının gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="192c8-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="192c8-153">Çalışma zamanı görüntüsü adımları</span><span class="sxs-lookup"><span data-stu-id="192c8-153">The runtime image steps</span></span>

| <span data-ttu-id="192c8-154">Adım</span><span class="sxs-lookup"><span data-stu-id="192c8-154">Step</span></span> | <span data-ttu-id="192c8-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="192c8-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="192c8-156">Yeni bir temel görüntü bildirir.</span><span class="sxs-lookup"><span data-stu-id="192c8-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="192c8-157">`/app` dizinini oluşturur ve geçerli çalışma dizini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="192c8-158">İlk `FROM` satırından `builder` diğer adını kullanarak yayımlanmış uygulamayı önceki görüntüden kopyalar.</span><span class="sxs-lookup"><span data-stu-id="192c8-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="192c8-159">Kapsayıcı başladığında çalıştırılacak komutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="192c8-160">Çalışma zamanı görüntüsündeki `dotnet` komutu yalnızca DLL dosyalarını çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="192c8-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="192c8-161">Docker 'da HTTPS</span><span class="sxs-lookup"><span data-stu-id="192c8-161">HTTPS in Docker</span></span>

<span data-ttu-id="192c8-162">Docker için Microsoft temel görüntüleri, Kestrel Bu bağlantı noktasında HTTPS olmadan çalıştığı anlamına gelen `ASPNETCORE_URLS` ortam değişkenini `http://+:80`olarak ayarladı.</span><span class="sxs-lookup"><span data-stu-id="192c8-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="192c8-163">HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [Şirket içinde barındırılan gRPC uygulamalarında](self-hosted.md)açıklandığı gibi), bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="192c8-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="192c8-164">Dockerfile 'ın çalışma zamanı görüntüsü oluşturma bölümünde ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="192c8-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="192c8-165">. Dockerıgnore dosyası</span><span class="sxs-lookup"><span data-stu-id="192c8-165">The .dockerignore file</span></span>

<span data-ttu-id="192c8-166">Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutulan dosyaları `.gitignore` benzer şekilde, `.dockerignore` dosyası, derleme sırasında dosya ve dizinlerin görüntüye kopyalanmasını hariç tutmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="192c8-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="192c8-167">Bu, yalnızca kopyalama zamandan tasarruf etmez, ancak BILGISAYARıNıZDAKI `obj` dizininin görüntüye kopyalanmasından kaynaklanan bazı hatalardan da kaçınabilir.</span><span class="sxs-lookup"><span data-stu-id="192c8-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="192c8-168">En azından, `.dockerignore` dosyanıza `bin` ve `obj` için girdi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="192c8-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="192c8-169">Görüntüyü oluşturma</span><span class="sxs-lookup"><span data-stu-id="192c8-169">Build the image</span></span>

<span data-ttu-id="192c8-170">Tek bir uygulama ve bu nedenle tek bir Dockerfile içeren bir çözüm için, Dockerfile 'ı temel dizine koymak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="192c8-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="192c8-171">Diğer bir deyişle, `.sln` dosyası ile aynı dizine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="192c8-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="192c8-172">Bu durumda, görüntüyü oluşturmak için Dockerfile dosyasını içeren dizinden aşağıdaki `docker build` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="192c8-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="192c8-173">`--tag` bayrağını (`-t`kısaltabilen), belirtilen gerçek etiket dahil olmak üzere görüntünün tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="192c8-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="192c8-174">Sonundaki `.`, yapı çalıştırılacağı bağlamı belirtir; Dockerfile içindeki `COPY` komutları için geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="192c8-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="192c8-175">Tek bir çözümde birden çok uygulamanız varsa, her bir uygulama için Dockerfile dosyasını `.csproj` dosyasının yanına kendi klasöründe tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="192c8-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="192c8-176">Çözümün ve tüm projelerin görüntüye kopyalandığından emin olmak için temel dizinden `docker build` komutunu yine de çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="192c8-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="192c8-177">`--file` (veya `-f`) bayrağını kullanarak geçerli dizinin altında bir Dockerfile belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="192c8-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="192c8-178">Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="192c8-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="192c8-179">Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="192c8-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="192c8-180">`-ti` bayrağı geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="192c8-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="192c8-181">`-p 5000:80`, kapsayıcıda bağlantı noktası 80 ' i localhost ağ arabirimindeki bağlantı noktası 80 ' e yayınlar.</span><span class="sxs-lookup"><span data-stu-id="192c8-181">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="192c8-182">Görüntüyü bir kayıt defterine gönderme</span><span class="sxs-lookup"><span data-stu-id="192c8-182">Push the image to a registry</span></span>

<span data-ttu-id="192c8-183">Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için bir Docker kayıt defterine gönderin.</span><span class="sxs-lookup"><span data-stu-id="192c8-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="192c8-184">İç ağların bir Docker kayıt defteri sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="192c8-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="192c8-185">Bu, [Docker 'ın kendi `registry` görüntüsünü](https://docs.docker.com/registry/deploying/) (Docker kayıt defteri bir Docker kapsayıcısında çalıştırılır) çalıştırmak kadar basit olabilir, ancak daha kapsamlı çeşitli çözümler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="192c8-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="192c8-186">Dış paylaşım ve bulut kullanımı için [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="192c8-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="192c8-187">Docker Hub 'ına göndermek için, görüntü adını Kullanıcı veya kuruluş adınızla ön eke koyun.</span><span class="sxs-lookup"><span data-stu-id="192c8-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="192c8-188">Özel bir kayıt defterine göndermek için, görüntü adını kayıt defteri ana bilgisayar adı ve kuruluş adı ile önek olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="192c8-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="192c8-189">Görüntü bir kayıt defterinden olduktan sonra, tek tek Docker konaklarına veya Kubernetes gibi bir kapsayıcı düzenleme altyapısına dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="192c8-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="192c8-190">[Önceki](self-hosted.md)
>[İleri](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="192c8-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
