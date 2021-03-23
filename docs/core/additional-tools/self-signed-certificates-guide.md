---
title: Self-Signed sertifikalarına genel bakış oluşturma
description: .NET Core ve ASP.NET Core projelerine yönelik işlevselliği ve otomatik olarak imzalanan sertifikaları kullanmak için diğer seçenekleri ekleyen Microsoft DotNet dev-CERT aracına genel bakış.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 738af3fc091e415399a53015a40748ad6116a2b4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873022"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a>.NET CLı ile otomatik olarak imzalanan sertifikalar oluşturma

Otomatik olarak imzalanan sertifikalar kullanılırken geliştirme ve test senaryolarında bunları oluşturmanın ve kullanmanın farklı yolları vardır.  Bu kılavuzda, ile otomatik olarak imzalanan sertifikaları `dotnet dev-certs` ve ve gibi diğer seçenekleri kullanarak kapsayabileceksiniz `PowerShell` `OpenSSL` .

Daha sonra, bir kapsayıcıda barındırılan [ASP.NET Core uygulaması](https://github.com/dotnet/dotnet-docker/blob/main/samples/run-aspnetcore-https-development.md) gibi bir örnek kullanarak sertifikanın yükleneceğini doğrulayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Örnekte, .NET Core 3,1 veya .NET 5 ' i kullanabilirsiniz.

İçin `dotnet dev-certs` , uygun .NET sürümünün yüklü olduğundan emin olun:

* [Windows 'a .NET yükler](../install/windows.md)
* [Linux 'ta .NET 'i yükler](../install/linux.md)
* [MacOS 'ta .NET 'i yükler](../install/macos.md)

Bu örnek, [Docker Istemcisinin](https://www.docker.com/products/docker) [Docker 17,06](https://docs.docker.com/release-notes/docker-ce) veya sonraki bir sürümünü gerektirir.

## <a name="prepare-sample-app"></a>Örnek uygulamayı hazırlama

Test için kullanmak istediğiniz çalışma zamanına bağlı olarak, [.NET Core 3,1](#net-core-31-sample-app) veya [.NET 5](#net-5-sample-app)gibi örnek uygulamayı hazırlamanız gerekir.

Bu kılavuzda, [örnek bir uygulama](https://hub.docker.com/_/microsoft-dotnet-samples) kullanacaksınız ve uygun yerlerde değişiklik yapacaksınız.

### <a name="net-core-31-sample-app"></a>.NET Core 3,1 örnek uygulama

Örnek uygulamayı alma.

```console
git clone https://github.com/dotnet/dotnet-docker/
```

Depoya yerel olarak gidin ve çalışma alanını bir düzenleyicide açın.

> [!NOTE]
> Dağıtımı *kırpmak* için DotNet Publish parametrelerini kullanmak ISTIYORSANıZ, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.
Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin. Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.

' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

Çalışma zamanının .NET Core 3,1 ' e işaret ettiğini doğrulamak için Dockerfile 'ı değiştirin:

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

Örnek uygulamaya işaret ettiğinizden emin olun.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Test için kapsayıcıyı yerel olarak oluşturun.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a>.NET 5 örnek uygulama

Bu kılavuzda, [örnek aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) .NET 5 için denetlenmelidir.

Örnek uygulama [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/Dockerfile) 'ın .NET 5 kullandığını denetleyin.

Ana bilgisayar işletim sistemine bağlı olarak, ASP.NET çalışma zamanının güncellenmesi gerekebilir. Örneğin, `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` Dockerfile içinde olarak değiştirme, uygun Windows çalışma zamanını hedeflemeye yardımcı olur.

Örneğin, Windows 'da sertifikaların test edilmesine yardımcı olur:

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

Linux 'ta sertifikaları test etmemiz durumunda mevcut Dockerfile 'ı kullanabilirsiniz.

' Nin `aspnetapp.csproj` uygun hedef Framework 'ü içerdiğinden emin olun:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> `dotnet publish`Dağıtımı *kırpmak* için parametreleri kullanmak istiyorsanız, SSL sertifikalarını desteklemek için uygun bağımlılıkların eklendiğinden emin olun.
Uygun derlemelerin kapsayıcıya eklendiğinden emin olmak için [DotNet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj) 'i güncelleştirin. Başvuru için,. csproj dosyasını, kendi içinde olan dağıtımlar için kırpma kullanılırken [SSL sertifikalarını destekleyecek](../deploying/trim-self-contained.md#support-for-ssl-certificates) şekilde güncelleştirmeyi denetleyin.

Örnek uygulamaya işaret ettiğinizden emin olun.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Test için kapsayıcıyı yerel olarak oluşturun.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a>Otomatik olarak imzalanan sertifika oluşturma

Kendinden imzalı bir sertifika oluşturabilirsiniz:

- [DotNet dev-CERT ile](#with-dotnet-dev-certs)
- [PowerShell ile](#with-powershell)
- [OpenSSL ile](#with-openssl)

### <a name="with-dotnet-dev-certs"></a>DotNet dev-CERT ile

`dotnet dev-certs`Otomatik olarak imzalanan sertifikalarla çalışmak için ' i kullanabilirsiniz. Bu örnek bir PowerShell konsolu kullanır.

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> Bu durumda, sertifika adı *aspnetapp*. pfx proje derleme adıyla eşleşmelidir. `crypticpassword` , kendi seçtiğiniz bir parola için bir bağımsız olarak kullanılır. Konsol "geçerli bir HTTPS sertifikası zaten var." ise, deponuzda bir güvenilen sertifika zaten var. Bu, MMC konsolu kullanılarak aktarılabilir.

Sertifika için uygulama gizli dizilerini yapılandırın:

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> Note: parolanın, sertifika için kullanılan parolayla eşleşmesi gerekir.

Kapsayıcı görüntüsünü HTTPS için yapılandırılan ASP.NET Core çalıştırın:

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

Uygulama başladıktan sonra Web tarayıcınızda sayfasına gidin `https://localhost:8001` .

#### <a name="clean-up"></a>Temizleme

Gizlilikler ve sertifikalar kullanımda değilse, bunları temizlediğinizden emin olun.

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a>PowerShell ile

Otomatik olarak imzalanan sertifikalar oluşturmak için PowerShell 'i kullanabilirsiniz. [PKI istemcisi](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) , kendinden imzalı bir sertifika oluşturmak için kullanılabilir.

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

Sertifika oluşturulacaktır, ancak test amaçları doğrultusunda bir tarayıcıda test için bir sertifika deposuna yerleştirilmelidir.

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

Bu noktada, sertifikaların bir [MMC ek bileşeninden](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)görüntülenebilir olması gerekir.

Örnek kapsayıcıyı Linux (WSL) için Windows alt sisteminde çalıştırabilirsiniz:

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> Birim bağlama ile dosya yolunun konağa göre farklı işlenebileceğini unutmayın.  Örneğin, WSL 'de */c/CERT* ' yi */mnt/c/CERT* ile değiştirebilir.

Daha önce Windows için oluşturulmuş kapsayıcıyı kullanıyorsanız, Çalıştır komutu aşağıdaki gibi görünür:

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.

Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun. Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .

#### <a name="clean-up"></a>Temizleme

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a>OpenSSL ile

Otomatik olarak imzalanan sertifikalar oluşturmak için [OpenSSL](https://www.openssl.org/) kullanabilirsiniz. Bu örnek, ile WSL/Ubuntu ve Bash kabuğunu kullanır `OpenSSL` .

Bu, bir. CRT ve bir. anahtarı oluşturur.

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

. Pfx almak için aşağıdaki komutu kullanın:

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> . Aspnetcore 3,1 örneği, `.pfx` ve parolasını kullanacaktır. `.net 5`Çalışma zamanından Itibaren Kestrel, ayrıca `.crt` ped kodlu dosyaları da alabilir `.key` .

Ana bilgisayar işletim sistemine bağlı olarak, sertifikanın güvenilir olması gerekir. Bir Linux konağında, ' güvenme ' sertifikası farklıdır ve bu sertifikaya bağımlıdır.

Bu kılavuzun amaçları doğrultusunda, PowerShell kullanarak Windows 'da bir örnek aşağıda verilmiştir:

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

.NET Core 3,1 için, WSL 'de şu komutu çalıştırın:

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

.NET 5 ' den başlayarak, Kestrel `.crt` ve pek kodlu `.key` dosyaları alabilir. .NET 5 için aşağıdaki komutla örneği çalıştırabilirsiniz:

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> WSL 'de, birim bağlama yolunun yapılandırmaya bağlı olarak değişebileceğini unutmayın.

Windows 'ta .NET Core 3,1 için aşağıdaki komutu çalıştırın `Powershell` :

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Windows 'da .NET 5 için PowerShell 'de aşağıdaki komutu çalıştırın:

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

Uygulama kurulduktan sonra tarayıcıda contoso.com:8001 adresine gidin.

Konak girdilerinin `contoso.com` uygun IP adresinde (örneğin, 127.0.0.1) yanıt verecek şekilde güncelleştirildiğinden emin olun. Sertifika tanınmazsa, kapsayıcınıza yüklenmiş sertifikaya da konakta güvenildiğinden ve için uygun SAN/DNS girişleri olduğundan emin olun `contoso.com` .

#### <a name="clean-up"></a>Temizleme

Testi tamamladıktan sonra otomatik olarak imzalanan sertifikaları temizlediğinizden emin olun.

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
