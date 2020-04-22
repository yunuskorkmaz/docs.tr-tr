---
title: WCF svcutil aracına genel bakış
description: .NET Framework projeleri için WCF svcutil aracına benzer şekilde .NET Core ve ASP.NET Core projeleri için işlevsellik ekleyen Microsoft WCF dotnet-svcutil aracına genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 1f500c9355112183a135c2b639807c7cd62fbbfc
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021259"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>.NET Core için WCF dotnet-svcutil aracı

Windows Communication Foundation (WCF) **dotnet-svcutil** aracı, ağ konumundaki bir web hizmetinden veya WSDL dosyasındaki meta verileri alan ve web hizmeti işlemlerine erişen istemci proxy yöntemleri içeren bir WCF sınıfı oluşturan bir .NET aracıdır.

.NET Framework projeleri için [**svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı olan Service Model Metadata'ya benzer şekilde, **dotnet-svcutil** ,NET Core ve .NET Standard projeleri ile uyumlu bir web hizmeti başvurusu oluşturmak için bir komut satırı aracıdır.

**Dotnet-svcutil** aracı, Visual Studio 2017 sürüm 15.5 ile ilk olarak gönderilen [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio bağlantılı servis sağlayıcısına alternatif bir seçenektir. **Dotnet-svcutil** aracı bir .NET aracı olarak, Linux, macOS ve Windows'da çapraz platform da kullanılabilir.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan gelen hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan referans eklemek güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Ön koşullar

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler
- En sevdiğiniz kod düzenleyicisi

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler
- En sevdiğiniz kod düzenleyicisi

---

## <a name="getting-started"></a>Başlarken

Aşağıdaki örnek, bir .NET Core web projesine bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımları size iletir. *HelloSvcutil* adında bir .NET Core web uygulaması oluşturacak ve aşağıdaki sözleşmeyi uygulayan bir web hizmetine başvuru ekleyeceğiz:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Bu örnekiçin, web hizmetinin aşağıdaki adreste barındırılan olacağını varsayalım:`http://contoso.com/SayHello.svc`

Windows, macOS veya Linux komut penceresinden aşağıdaki adımları gerçekleştirin:

1. Projeniz için _HelloSvcutil_ adında bir dizin oluşturun ve aşağıdaki örnekte olduğu gibi geçerli dizininiz olsun:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Aşağıdaki komutu [`dotnet new`](../tools/dotnet-new.md) kullanarak bu dizinde yeni bir C# web projesi oluşturun:

    ```dotnetcli
    dotnet new web
    ```

3. [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak yükleyin: <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Proje `HelloSvcutil.csproj` dosyasını düzenleyicinizde açın, `Project` öğeyi düzenlemeyi ve [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) aşağıdaki kodu kullanarak CLI araç başvurusu olarak ekleyin:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Sonra aşağıdaki komutu kullanarak _dotnet-svcutil_ paketini geri yükleyin: [`dotnet restore`](../tools/dotnet-restore.md)

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Web hizmeti başvuru dosyasını oluşturmak için _dotnet-svcutil_ komutunu aşağıdaki gibi çalıştırın:

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Oluşturulan dosya _HelloSvcutil/ServiceReference/Reference.cs_olarak kaydedilir. _Dotnet-svcutil_ aracı, proxy kodunun gerektirdiği uygun WCF paketlerini de paket referansolarak projeye ekler.

## <a name="using-the-service-reference"></a>Hizmet Başvuruyu Kullanma

1. Aşağıdaki komutu kullanarak [`dotnet restore`](../tools/dotnet-restore.md) WCF paketlerini geri yükleyin:

    ```dotnetcli
    dotnet restore
    ```

2. Kullanmak istediğiniz istemci sınıfının ve işlemin adını bulun. `Reference.cs`hizmetteki işlemleri çağırmak için `System.ServiceModel.ClientBase`kullanılabilecek yöntemlerle devralan bir sınıf içerir. Bu örnekte, _SayHello_ hizmetinin _Merhaba_ işlemini aramak istiyorsunuz. `ServiceReference.SayHelloClient`istemci sınıfın adıdır ve işlemi çağırmak `HelloAsync` için kullanılabilecek bir yöntem vardır.

3. Düzenleyicinizdeki `Startup.cs` dosyayı açın ve en üstteki hizmet başvuru ad alanı için bir kullanım deyimi ekleyin:

    ```csharp
    using ServiceReference;
    ```

4. Web hizmetini `Configure` çağırmak için yöntemi edin. Bunu, istemci nesnesinden devralan sınıfın bir `ClientBase` örneğini oluşturarak ve yöntemi istemci nesnesi üzerinde çağırarak yaparsınız:

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
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

5. Aşağıdaki komutu [`dotnet run`](../tools/dotnet-run.md) kullanarak uygulamayı çalıştırın:

    ```dotnetcli
    dotnet run
    ```

6. Konsolda listelenen URL'ye (örneğin, `http://localhost:5000`web tarayıcınızda) gidin.

Aşağıdaki çıktıyı görmelisiniz: "Merhaba dotnet-svcutil!"

`dotnet-svcutil` Takım parametrelerinin ayrıntılı bir açıklaması için, yardım parametresini aşağıdaki gibi geçen aracı çağırın:
# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Geri bildirim & sorular

Herhangi bir sorunuz veya geri bildiriminiz varsa, [GitHub'da bir sorun açın.](https://github.com/dotnet/wcf/issues/new) Ayrıca [GitHub'daki WCF repo'sunda](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)varolan tüm soruları veya sorunları inceleyebilirsiniz.

## <a name="release-notes"></a>Sürüm notları

- Bilinen sorunlar da dahil olmak üzere güncelleştirilmiş sürüm bilgileri için [Yayın notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) bakın.

## <a name="information"></a>Bilgi

- [dotnet-svcutil NuGet Paketi](https://nuget.org/packages/dotnet-svcutil)
