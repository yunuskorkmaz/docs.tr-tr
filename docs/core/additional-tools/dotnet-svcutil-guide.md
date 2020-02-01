---
title: WCF Svcutil aracına genel bakış
description: .NET Framework projelerine yönelik WCF Svcutil aracına benzer şekilde .NET Core ve ASP.NET Core projelerine yönelik işlevler ekleyen Microsoft WCF DotNet-Svcutil aracına genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920944"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>.NET Core için WCF DotNet-Svcutil aracı

Windows Communication Foundation (WCF) **DotNet-Svcutil** Aracı, bir ağ konumundaki veya bir wsdl dosyasındaki bir Web hizmetinden meta verileri alan ve Web hizmeti işlemlerine erişen istemci proxy yöntemlerini IÇEREN bir WCF sınıfı oluşturan bir .net aracıdır.

.NET Framework projelerine yönelik [**hizmet modeli meta verileri-Svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracına benzer şekilde **DotNet-Svcutil** , .NET Core ve .NET Standard projeleriyle uyumlu bir Web hizmeti başvurusu oluşturmaya yönelik bir komut satırı aracıdır.

**DotNet-Svcutil** Aracı, Ilk olarak visual Studio 2017 sürüm 15,5 ile birlikte gelen [**WCF Web hizmeti başvurusu**](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısına alternatif bir seçenektir. .NET aracı olarak **DotNet-Svcutil** Aracı, Linux, MacOS ve Windows üzerinde platformlar arası kullanıma sunulmuştur.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Prerequisites

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[DotNet-Svcutil 2. x](#tab/dotnetsvcutil2x)

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri
- En sevdiğiniz kod düzenleyiciniz

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet-Svcutil 1. x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri
- En sevdiğiniz kod düzenleyiciniz

---

## <a name="getting-started"></a>Başlarken

Aşağıdaki örnek, bir .NET Core Web projesine Web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir. *Merhaba Svcutil* adlı bir .NET Core Web uygulaması oluşturacak ve aşağıdaki sözleşmeyi uygulayan bir Web hizmetine başvuru ekleyeceğiz:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Bu örnekte, Web hizmetinin şu adreste barındırıldığını varsayalım: `http://contoso.com/SayHello.svc`

Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları uygulayın:

1. Projeniz için _Hellosvcutil_ adlı bir dizin oluşturun ve aşağıdaki örnekte olduğu gibi geçerli dizininiz yapın:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Aşağıdaki şekilde C# [`dotnet new`](../tools/dotnet-new.md) komutunu kullanarak bu dizinde yeni bir Web projesi oluşturun:

    ```dotnetcli
    dotnet new web
    ```

3. [`dotnet-svcutil` NuGet PAKETINI](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak yükler:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[DotNet-Svcutil 2. x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet-Svcutil 1. x](#tab/dotnetsvcutil1x)
    `HelloSvcutil.csproj` proje dosyasını Düzenleyicinizde açın, `Project` öğesini düzenleyin ve aşağıdaki kodu kullanarak bir CLı araç başvurusu olarak [`dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) ekleyin:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Daha sonra [`dotnet restore`](../tools/dotnet-restore.md) komutunu kullanarak _DotNet-Svcutil_ paketini aşağıdaki gibi geri yükleyin:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Web hizmeti başvuru dosyasını aşağıdaki gibi oluşturmak için _DotNet-Svcutil_ komutunu çalıştırın:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[DotNet-Svcutil 2. x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet-Svcutil 1. x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Oluşturulan dosya _Merhaba Svcutil/ServiceReference/Reference. cs_olarak kaydedilir. _DotNet-Svcutil_ aracı Ayrıca, proxy kodunun paket başvuruları olarak gerekli olan uygun WCF paketlerini projeye ekler.

## <a name="using-the-service-reference"></a>Hizmet başvurusunu kullanma

1. [`dotnet restore`](../tools/dotnet-restore.md) komutunu kullanarak WCF paketlerini aşağıdaki şekilde geri yükleyin:

    ```dotnetcli
    dotnet restore
    ```

2. Kullanmak istediğiniz istemci sınıfının ve işlemin adını bulun. `Reference.cs`, hizmet üzerindeki işlemleri çağırmak için kullanılabilecek yöntemler ile `System.ServiceModel.ClientBase`devralan bir sınıf içerir. Bu örnekte, _SayHello_ hizmetinin _Hello_ işlemini çağırmak istiyorsunuz. `ServiceReference.SayHelloClient`, istemci sınıfının adıdır ve işlemi çağırmak için kullanılabilecek `HelloAsync` adlı bir yöntemi vardır.

3. `Startup.cs` dosyasını Düzenleyicinizde açın ve en üstteki hizmet başvurusu ad alanı için bir using ifadesini ekleyin:

    ```csharp
    using ServiceReference;
    ```

4. Web hizmetini çağırmak için `Configure` yöntemini düzenleyin. Bunu, `ClientBase` devralan ve istemci nesnesinde yöntemi çağıran sınıfının bir örneğini oluşturarak yapabilirsiniz:

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. [`dotnet run`](../tools/dotnet-run.md) komutunu kullanarak uygulamayı aşağıdaki şekilde çalıştırın:

    ```dotnetcli
    dotnet run
    ```

6. Web tarayıcınızda konsolunda listelenen URL 'ye gidin (örneğin, `http://localhost:5000`).

Şu çıktıyı görmeniz gerekir: "Hello DotNet-Svcutil!"

`dotnet-svcutil` aracı parametrelerinin ayrıntılı bir açıklaması için, yardım parametresini aşağıdaki gibi geçirerek aracı çağırın:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[DotNet-Svcutil 2. x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet-Svcutil 1. x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Geri bildirim & soruları

Sorularınız veya geri bildiriminiz varsa [GitHub ' da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Ayrıca, [GitHub 'DAKI WCF](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)deposundaki mevcut soruları veya sorunları da inceleyebilirsiniz.

## <a name="release-notes"></a>Sürüm notları

- Bilinen sorunlar da dahil olmak üzere, güncelleştirilmiş sürüm bilgileri için [sürüm notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) bakın.

## <a name="information"></a>Bilgisi

- [DotNet-Svcutil NuGet paketi](https://nuget.org/packages/dotnet-svcutil)
