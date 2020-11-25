---
title: Self-Signed sertifikalarına genel bakış oluşturma
description: .NET Core ve ASP.NET Core projelerine yönelik işlevselliği ve otomatik olarak imzalanan sertifikaları kullanmak için diğer seçenekleri ekleyen Microsoft DotNet dev-CERT aracına genel bakış.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 15bbe3997ca34b503074595fa027bc6dfff1c0a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761422"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="ba258-103">.NET CLı ile otomatik olarak imzalanan sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba258-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="ba258-104">Otomatik olarak imzalanan sertifikalar kullanılırken geliştirme ve test senaryolarında bunları oluşturmanın ve kullanmanın farklı yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="ba258-104">When using self-signed certificates, there's different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="ba258-105">Bu kılavuzda, ile otomatik olarak imzalanan sertifikaları `dotnet dev-certs` ve ve gibi diğer seçenekleri kullanarak kapsayabileceksiniz `PowerShell` `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="ba258-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="ba258-106">Daha sonra, bir kapsayıcıda barındırılan [ASP.NET Core uygulaması](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) gibi bir örnek kullanarak sertifikanın yükleneceğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba258-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba258-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ba258-107">Prerequisites</span></span>

<span data-ttu-id="ba258-108">Örnekte, ya da kullanabilirsiniz `.netcore 3.1` `.net 5` .</span><span class="sxs-lookup"><span data-stu-id="ba258-108">In the sample, you can utilize either `.netcore 3.1` or `.net 5`.</span></span>

<span data-ttu-id="ba258-109">İçin `dotnet dev-certs` uygun sürüme sahip olduğunuzdan emin olun `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="ba258-109">For `dotnet dev-certs`, be sure to have the appropriate version of `dotnet` installed:</span></span>

* [<span data-ttu-id="ba258-110">Windows 'a DotNet 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="ba258-110">Install dotnet on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="ba258-111">Linux 'ta DotNet 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="ba258-111">Install dotnet on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="ba258-112">MacOS 'ta DotNet 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="ba258-112">Install dotnet on macOS</span></span>](../install/macos.md)

<span data-ttu-id="ba258-113">Bu örnek, [Docker Istemcisinin](https://www.docker.com/products/docker) [Docker 17,06](https://docs.docker.com/release-notes/docker-ce) veya sonraki bir sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ba258-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="ba258-114">Örnek uygulamayı hazırlama</span><span class="sxs-lookup"><span data-stu-id="ba258-114">Prepare sample app</span></span>

<span data-ttu-id="ba258-115">Test için kullanmak istediğiniz çalışma zamanına bağlı olarak örnek uygulamayı hazırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba258-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing.</span></span>

<span data-ttu-id="ba258-116">Bu kılavuzda, [örnek bir uygulama](https://hub.docker.com/_/microsoft-dotnet-samples) kullanacaksınız ve uygun yerlerde değişiklik yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="ba258-116">For this guide, you'll be using a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="prepare-net-core-31-sample-app"></a><span data-ttu-id="ba258-117">.NET Core 3,1 örnek uygulamasını hazırlayın</span><span class="sxs-lookup"><span data-stu-id="ba258-117">Prepare .NET Core 3.1 sample app</span></span>

<span data-ttu-id="ba258-118">Örnek uygulamayı alma.</span><span class="sxs-lookup"><span data-stu-id="ba258-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="ba258-119">Depoya yerel olarak gidin ve çalışma alanını bir düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="ba258-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="ba258-120">Dağıtımı *kırpmak* için DotNet Publish parametrelerini kullanmak ISTIYORSANıZ, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="ba258-121">Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba258-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="ba258-122">Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ba258-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="ba258-123">' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="ba258-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ba258-124">Çalışma zamanının. netcore 3,1 ' ye işaret ettiğini doğrulamak için Dockerfile 'ı değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ba258-124">Modify the Dockerfile to make sure the runtime points to .netcore 3.1:</span></span>

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

<span data-ttu-id="ba258-125">Örnek uygulamaya işaret ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="ba258-126">Test için kapsayıcıyı yerel olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba258-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="prepare-net-5-sample-app"></a><span data-ttu-id="ba258-127">.NET 5 örnek uygulamasını hazırlama</span><span class="sxs-lookup"><span data-stu-id="ba258-127">Prepare .NET 5 sample app</span></span>

<span data-ttu-id="ba258-128">Bu kılavuzda, [örnek aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) .NET 5 için denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba258-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .net 5.</span></span>

<span data-ttu-id="ba258-129">Örnek uygulama [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) 'ın .NET 5 kullandığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ba258-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) is using .net 5.</span></span>

<span data-ttu-id="ba258-130">Konak işletim sistemine bağlı olarak, ASPNET çalışma zamanının güncellenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ba258-130">Depending on the host os, the aspnet runtime may need to be updated.</span></span> <span data-ttu-id="ba258-131">Örneğin, `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` Dockerfile içinde olarak değiştirme, uygun Windows çalışma zamanını hedeflemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ba258-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="ba258-132">Örneğin, Windows 'da sertifikaların test edilmesine yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="ba258-132">For example, this will help with testing the certificates on Windows:</span></span>

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

<span data-ttu-id="ba258-133">Linux 'ta sertifikaları test etmemiz durumunda mevcut Dockerfile 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba258-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="ba258-134">' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="ba258-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="ba258-135">Dağıtımı *kırpmak* için DotNet Publish parametrelerini kullanmak ISTIYORSANıZ, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-135">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="ba258-136">Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba258-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="ba258-137">Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ba258-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="ba258-138">Örnek uygulamaya işaret ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="ba258-139">Test için kapsayıcıyı yerel olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba258-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate-with-dotnet-dev-certs"></a><span data-ttu-id="ba258-140">DotNet dev-CERT ile kendinden imzalı bir sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba258-140">Create a self-signed certificate with dotnet dev-certs</span></span>

<span data-ttu-id="ba258-141">`dotnet dev-certs`Otomatik olarak imzalanan sertifikalarla çalışmak için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba258-141">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="ba258-142">Bu örnek bir PowerShell konsolu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba258-142">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="ba258-143">Bu durumda, sertifika adı *aspnetapp*. pfx proje derleme adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba258-143">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="ba258-144">`crypticpassword` , kendi seçtiğiniz bir parola için bir bağımsız olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba258-144">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="ba258-145">Konsol "geçerli bir HTTPS sertifikası zaten var." ise, deponuzda bir güvenilen sertifika zaten var.</span><span class="sxs-lookup"><span data-stu-id="ba258-145">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="ba258-146">Bu, MMC konsolu kullanılarak aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba258-146">It can be exported using MMC Console.</span></span>

<span data-ttu-id="ba258-147">Sertifika için uygulama gizli dizilerini yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="ba258-147">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="ba258-148">Note: parolanın, sertifika için kullanılan parolayla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba258-148">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="ba258-149">Kapsayıcı görüntüsünü HTTPS için yapılandırılan ASP.NET Core çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ba258-149">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="ba258-150">Uygulama başladıktan sonra Web tarayıcınızda sayfasına gidin `https://localhost:8001` .</span><span class="sxs-lookup"><span data-stu-id="ba258-150">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

### <a name="clean-up"></a><span data-ttu-id="ba258-151">Temizleme</span><span class="sxs-lookup"><span data-stu-id="ba258-151">Clean up</span></span>

<span data-ttu-id="ba258-152">Gizlilikler ve sertifikalar kullanımda değilse, bunları temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-152">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

## <a name="create-a-self-signed-certificate-with-powershell"></a><span data-ttu-id="ba258-153">PowerShell ile otomatik olarak imzalanan sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba258-153">Create a self-signed certificate with PowerShell</span></span>

<span data-ttu-id="ba258-154">Otomatik olarak imzalanan sertifikalar oluşturmak için PowerShell 'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba258-154">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="ba258-155">[PKI istemcisi](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) , kendinden imzalı bir sertifika oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba258-155">The [PKI Client](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="ba258-156">Sertifika oluşturulacaktır, ancak test amaçları doğrultusunda bir tarayıcıda test için bir sertifika deposuna yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba258-156">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="ba258-157">Bu noktada, sertifikaların bir [MMC ek bileşeninden](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba258-157">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="ba258-158">Örnek kapsayıcıyı Linux (WSL) için Windows alt sisteminde çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba258-158">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="ba258-159">Birim bağlama ile dosya yolunun konağa göre farklı işlenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba258-159">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="ba258-160">Örneğin, WSL 'de */c/CERT* ' yi */mnt/c/CERT* ile değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ba258-160">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="ba258-161">Daha önce Windows için oluşturulmuş kapsayıcıyı kullanıyorsanız, Çalıştır komutu aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="ba258-161">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="ba258-162">Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.</span><span class="sxs-lookup"><span data-stu-id="ba258-162">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="ba258-163">Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-163">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="ba258-164">Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="ba258-164">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="ba258-165">Temizleme</span><span class="sxs-lookup"><span data-stu-id="ba258-165">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

## <a name="create-a-self-signed-certificate-with-openssl"></a><span data-ttu-id="ba258-166">OpenSSL ile otomatik olarak imzalanan sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba258-166">Create a self-signed certificate with OpenSSL</span></span>

<span data-ttu-id="ba258-167">Otomatik olarak imzalanan sertifikalar oluşturmak için [OpenSSL](https://www.openssl.org/) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba258-167">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="ba258-168">Bu örnek, ile WSL/Ubuntu ve Bash kabuğunu kullanır `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="ba258-168">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="ba258-169">Bu, bir. CRT ve bir. anahtarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba258-169">This will generate a .crt and a .key.</span></span>

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

<span data-ttu-id="ba258-170">. Pfx almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ba258-170">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="ba258-171">. Aspnetcore 3,1 örneği, `.pfx` ve parolasını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="ba258-171">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="ba258-172">`.net 5`Çalışma zamanından Itibaren Kestrel, ayrıca `.crt` ped kodlu dosyaları da alabilir `.key` .</span><span class="sxs-lookup"><span data-stu-id="ba258-172">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="ba258-173">Ana bilgisayar işletim sistemine bağlı olarak, sertifikanın güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba258-173">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="ba258-174">Bir Linux konağında, ' güvenme ' sertifikası farklıdır ve bu sertifikaya bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba258-174">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="ba258-175">Bu kılavuzun amaçları doğrultusunda, PowerShell kullanarak Windows 'da bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ba258-175">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="ba258-176">.NET Core 3,1 için, WSL 'de şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ba258-176">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="ba258-177">.NET 5 ' den başlayarak, Kestrel `.crt` ve pek kodlu `.key` dosyaları alabilir.</span><span class="sxs-lookup"><span data-stu-id="ba258-177">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="ba258-178">.NET 5 için aşağıdaki komutla örneği çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba258-178">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="ba258-179">WSL 'de, birim bağlama yolunun yapılandırmaya bağlı olarak değişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba258-179">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="ba258-180">Windows 'ta .NET Core 3,1 için aşağıdaki komutu çalıştırın `Powershell` :</span><span class="sxs-lookup"><span data-stu-id="ba258-180">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="ba258-181">Windows 'da .NET 5 için PowerShell 'de aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ba258-181">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="ba258-182">Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.</span><span class="sxs-lookup"><span data-stu-id="ba258-182">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="ba258-183">Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-183">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="ba258-184">Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="ba258-184">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="ba258-185">Temizleme</span><span class="sxs-lookup"><span data-stu-id="ba258-185">Clean up</span></span>

<span data-ttu-id="ba258-186">Testi tamamladıktan sonra otomatik olarak imzalanan sertifikaları temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba258-186">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
