---
title: Self-Signed sertifikalarına genel bakış oluşturma
description: .NET Core ve ASP.NET Core projelerine yönelik işlevselliği ve otomatik olarak imzalanan sertifikaları kullanmak için diğer seçenekleri ekleyen Microsoft DotNet dev-CERT aracına genel bakış.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: d1675abb7d584b72d981f9db739e02269abe662c
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189147"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="46ea0-103">.NET CLı ile otomatik olarak imzalanan sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="46ea0-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="46ea0-104">Otomatik olarak imzalanan sertifikalar kullanılırken geliştirme ve test senaryolarında bunları oluşturmanın ve kullanmanın farklı yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="46ea0-104">When using self-signed certificates, there are different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="46ea0-105">Bu kılavuzda, ile otomatik olarak imzalanan sertifikaları `dotnet dev-certs` ve ve gibi diğer seçenekleri kullanarak kapsayabileceksiniz `PowerShell` `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="46ea0-106">Daha sonra, bir kapsayıcıda barındırılan [ASP.NET Core uygulaması](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) gibi bir örnek kullanarak sertifikanın yükleneceğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46ea0-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="46ea0-107">Prerequisites</span></span>

<span data-ttu-id="46ea0-108">Örnekte, .NET Core 3,1 veya .NET 5 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-108">In the sample, you can utilize either .NET Core 3.1 or .NET 5.</span></span>

<span data-ttu-id="46ea0-109">İçin `dotnet dev-certs` , uygun .NET sürümünün yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="46ea0-109">For `dotnet dev-certs`, be sure to have the appropriate version of .NET installed:</span></span>

* [<span data-ttu-id="46ea0-110">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="46ea0-110">Install .NET on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="46ea0-111">Linux 'ta .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="46ea0-111">Install .NET on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="46ea0-112">MacOS 'ta .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="46ea0-112">Install .NET on macOS</span></span>](../install/macos.md)

<span data-ttu-id="46ea0-113">Bu örnek, [Docker Istemcisinin](https://www.docker.com/products/docker) [Docker 17,06](https://docs.docker.com/release-notes/docker-ce) veya sonraki bir sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="46ea0-114">Örnek uygulamayı hazırlama</span><span class="sxs-lookup"><span data-stu-id="46ea0-114">Prepare sample app</span></span>

<span data-ttu-id="46ea0-115">Test için kullanmak istediğiniz çalışma zamanına bağlı olarak, [.NET Core 3,1](#net-core-31-sample-app) veya [.NET 5](#net-5-sample-app)gibi örnek uygulamayı hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing, either [.NET Core 3.1](#net-core-31-sample-app) or [.NET 5](#net-5-sample-app).</span></span>

<span data-ttu-id="46ea0-116">Bu kılavuzda, [örnek bir uygulama](https://hub.docker.com/_/microsoft-dotnet-samples) kullanacaksınız ve uygun yerlerde değişiklik yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="46ea0-116">For this guide, you'll use a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="net-core-31-sample-app"></a><span data-ttu-id="46ea0-117">.NET Core 3,1 örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="46ea0-117">.NET Core 3.1 sample app</span></span>

<span data-ttu-id="46ea0-118">Örnek uygulamayı alma.</span><span class="sxs-lookup"><span data-stu-id="46ea0-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="46ea0-119">Depoya yerel olarak gidin ve çalışma alanını bir düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="46ea0-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="46ea0-120">Dağıtımı *kırpmak* için DotNet Publish parametrelerini kullanmak ISTIYORSANıZ, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="46ea0-121">Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="46ea0-122">Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="46ea0-123">' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="46ea0-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="46ea0-124">Çalışma zamanının .NET Core 3,1 ' e işaret ettiğini doğrulamak için Dockerfile 'ı değiştirin:</span><span class="sxs-lookup"><span data-stu-id="46ea0-124">Modify the Dockerfile to make sure the runtime points to .NET Core 3.1:</span></span>

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet-core
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

<span data-ttu-id="46ea0-125">Örnek uygulamaya işaret ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="46ea0-126">Test için kapsayıcıyı yerel olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a><span data-ttu-id="46ea0-127">.NET 5 örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="46ea0-127">.NET 5 sample app</span></span>

<span data-ttu-id="46ea0-128">Bu kılavuzda, [örnek aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) .NET 5 için denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .NET 5.</span></span>

<span data-ttu-id="46ea0-129">Örnek uygulama [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) 'ın .NET 5 kullandığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) is using .NET 5.</span></span>

<span data-ttu-id="46ea0-130">Ana bilgisayar işletim sistemine bağlı olarak, ASP.NET çalışma zamanının güncellenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-130">Depending on the host OS, the ASP.NET runtime may need to be updated.</span></span> <span data-ttu-id="46ea0-131">Örneğin, `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` Dockerfile içinde olarak değiştirme, uygun Windows çalışma zamanını hedeflemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="46ea0-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="46ea0-132">Örneğin, Windows 'da sertifikaların test edilmesine yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="46ea0-132">For example, this will help with testing the certificates on Windows:</span></span>

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore -r win-x64

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app -r win-x64 --self-contained false --no-restore

# final stage/image
# Uses the 2009 release; 2004, 1909, and 1809 are other choices
FROM mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["aspnetapp"]

```

<span data-ttu-id="46ea0-133">Linux 'ta sertifikaları test etmemiz durumunda mevcut Dockerfile 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="46ea0-134">' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="46ea0-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="46ea0-135">`dotnet publish`Dağıtımı *kırpmak* için parametreleri kullanmak istiyorsanız, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-135">If you want to use `dotnet publish` parameters to *trim* the deployment, make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="46ea0-136">Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="46ea0-137">Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="46ea0-138">Örnek uygulamaya işaret ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="46ea0-139">Test için kapsayıcıyı yerel olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="46ea0-140">Otomatik olarak imzalanan sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="46ea0-140">Create a self-signed certificate</span></span>

<span data-ttu-id="46ea0-141">Kendinden imzalı bir sertifika oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46ea0-141">You can create a self-signed certificate:</span></span>

- [<span data-ttu-id="46ea0-142">DotNet dev-CERT ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-142">With dotnet dev-certs</span></span>](#with-dotnet-dev-certs)
- [<span data-ttu-id="46ea0-143">PowerShell ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-143">With PowerShell</span></span>](#with-powershell)
- [<span data-ttu-id="46ea0-144">OpenSSL ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-144">With OpenSSL</span></span>](#with-openssl)

### <a name="with-dotnet-dev-certs"></a><span data-ttu-id="46ea0-145">DotNet dev-CERT ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-145">With dotnet dev-certs</span></span>

<span data-ttu-id="46ea0-146">`dotnet dev-certs`Otomatik olarak imzalanan sertifikalarla çalışmak için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-146">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="46ea0-147">Bu örnek bir PowerShell konsolu kullanır.</span><span class="sxs-lookup"><span data-stu-id="46ea0-147">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="46ea0-148">Bu durumda, sertifika adı *aspnetapp*. pfx proje derleme adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-148">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="46ea0-149">`crypticpassword` , kendi seçtiğiniz bir parola için bir bağımsız olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46ea0-149">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="46ea0-150">Konsol "geçerli bir HTTPS sertifikası zaten var." ise, deponuzda bir güvenilen sertifika zaten var.</span><span class="sxs-lookup"><span data-stu-id="46ea0-150">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="46ea0-151">Bu, MMC konsolu kullanılarak aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-151">It can be exported using MMC Console.</span></span>

<span data-ttu-id="46ea0-152">Sertifika için uygulama gizli dizilerini yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="46ea0-152">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="46ea0-153">Note: parolanın, sertifika için kullanılan parolayla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-153">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="46ea0-154">Kapsayıcı görüntüsünü HTTPS için yapılandırılan ASP.NET Core çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="46ea0-154">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="46ea0-155">Uygulama başladıktan sonra Web tarayıcınızda sayfasına gidin `https://localhost:8001` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-155">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="46ea0-156">Temizleme</span><span class="sxs-lookup"><span data-stu-id="46ea0-156">Clean up</span></span>

<span data-ttu-id="46ea0-157">Gizlilikler ve sertifikalar kullanımda değilse, bunları temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-157">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a><span data-ttu-id="46ea0-158">PowerShell ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-158">With PowerShell</span></span>

<span data-ttu-id="46ea0-159">Otomatik olarak imzalanan sertifikalar oluşturmak için PowerShell 'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-159">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="46ea0-160">[PKI istemcisi](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) , kendinden imzalı bir sertifika oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-160">The [PKI Client](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="46ea0-161">Sertifika oluşturulacaktır, ancak test amaçları doğrultusunda bir tarayıcıda test için bir sertifika deposuna yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-161">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="46ea0-162">Bu noktada, sertifikaların bir [MMC ek bileşeninden](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-162">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="46ea0-163">Örnek kapsayıcıyı Linux (WSL) için Windows alt sisteminde çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46ea0-163">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="46ea0-164">Birim bağlama ile dosya yolunun konağa göre farklı işlenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="46ea0-164">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="46ea0-165">Örneğin, WSL 'de */c/CERT* ' yi */mnt/c/CERT* ile değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-165">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="46ea0-166">Daha önce Windows için oluşturulmuş kapsayıcıyı kullanıyorsanız, Çalıştır komutu aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="46ea0-166">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="46ea0-167">Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-167">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="46ea0-168">Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-168">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="46ea0-169">Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-169">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="46ea0-170">Temizleme</span><span class="sxs-lookup"><span data-stu-id="46ea0-170">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a><span data-ttu-id="46ea0-171">OpenSSL ile</span><span class="sxs-lookup"><span data-stu-id="46ea0-171">With OpenSSL</span></span>

<span data-ttu-id="46ea0-172">Otomatik olarak imzalanan sertifikalar oluşturmak için [OpenSSL](https://www.openssl.org/) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46ea0-172">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="46ea0-173">Bu örnek, ile WSL/Ubuntu ve Bash kabuğunu kullanır `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-173">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="46ea0-174">Bu, bir. CRT ve bir. anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46ea0-174">This will generate a .crt and a .key.</span></span>

```bash
PARENT="contoso.com"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 365 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = www.${PARENT}"; \
  echo "DNS.2 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```

<span data-ttu-id="46ea0-175">. Pfx almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="46ea0-175">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="46ea0-176">. Aspnetcore 3,1 örneği, `.pfx` ve parolasını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="46ea0-176">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="46ea0-177">`.net 5`Çalışma zamanından Itibaren Kestrel, ayrıca `.crt` ped kodlu dosyaları da alabilir `.key` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-177">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="46ea0-178">Ana bilgisayar işletim sistemine bağlı olarak, sertifikanın güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-178">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="46ea0-179">Bir Linux konağında, ' güvenme ' sertifikası farklıdır ve bu sertifikaya bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="46ea0-179">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="46ea0-180">Bu kılavuzun amaçları doğrultusunda, PowerShell kullanarak Windows 'da bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="46ea0-180">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="46ea0-181">.NET Core 3,1 için, WSL 'de şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="46ea0-181">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="46ea0-182">.NET 5 ' den başlayarak, Kestrel `.crt` ve pek kodlu `.key` dosyaları alabilir.</span><span class="sxs-lookup"><span data-stu-id="46ea0-182">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="46ea0-183">.NET 5 için aşağıdaki komutla örneği çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46ea0-183">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="46ea0-184">WSL 'de, birim bağlama yolunun yapılandırmaya bağlı olarak değişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="46ea0-184">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="46ea0-185">Windows 'ta .NET Core 3,1 için aşağıdaki komutu çalıştırın `Powershell` :</span><span class="sxs-lookup"><span data-stu-id="46ea0-185">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="46ea0-186">Windows 'da .NET 5 için PowerShell 'de aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="46ea0-186">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="46ea0-187">Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.</span><span class="sxs-lookup"><span data-stu-id="46ea0-187">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="46ea0-188">Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-188">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="46ea0-189">Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="46ea0-189">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="46ea0-190">Temizleme</span><span class="sxs-lookup"><span data-stu-id="46ea0-190">Clean up</span></span>

<span data-ttu-id="46ea0-191">Testi tamamladıktan sonra otomatik olarak imzalanan sertifikaları temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46ea0-191">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
