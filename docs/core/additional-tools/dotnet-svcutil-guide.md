---
title: WCF svcutil aracına genel bakış
description: .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için WCF svcutil aracına benzer işlevsellik ekleyen Microsoft WCF svcutil dotnet araç genel bakış.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: b5dfb84f19c3748daa303c828cbe881f1582eb76
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612829"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>.NET Core için WCF dotnet svcutil aracı

Windows Communication Foundation (WCF) **dotnet svcutil** araçtır bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve istemci proxy yöntemleri içeren bir WCF sınıfı oluşturur bir .NET Core CLI aracı, web hizmet işlemleri erişim.

Benzer şekilde [ **Service Model meta verilerini - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .NET Framework projeleri için araç **dotnet svcutil** bir web hizmeti başvurusu oluşturmak için bir komut satırı aracı .NET Core ve .NET Standard projelerine uyumludur.

**Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio, Visual Studio ile ilk sevk edilen hizmet sağlayıcısı bağlı 2017 v15.5. **Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Önkoşullar

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)
* [.NET core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler
* Sık kullandığınız kod düzenleyici

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
* [.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler
* Sık kullandığınız kod düzenleyici

---

## <a name="getting-started"></a>Başlarken

Aşağıdaki örnek bir .NET Core web projesi için bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir. Adlı bir .NET Core web uygulaması oluşturacaksınız _HelloSvcutil_ aşağıdaki sözleşme uygulayan bir web hizmeti için bir başvuru ekleyin:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Bu örnekte, web hizmeti şu adresten barındırılacak varsayalım: `http://contoso.com/SayHello.svc`

Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları gerçekleştirin:

1. Adlı bir dizin oluşturmak _HelloSvcutil_ projeniz için ve aşağıdaki örnekte olduğu gibi geçerli dizin yapın:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Yeni bir C# directory kullanarak web projesi [ `dotnet new` ](../tools/dotnet-new.md) komutuyla şu şekilde:

```console
dotnet new web
```

3. Yükleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı olarak:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet tool install --global dotnet-svcutil
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
Açık `HelloSvcutil.csproj` proje dosyası düzenleyicinizde, düzenleme `Project` öğesi ve ekleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı başvuru olarak, aşağıdaki kodu kullanarak:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

Daha sonra geri _dotnet svcutil_ kullanarak paket [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:

```console
dotnet restore
```

---

4. Çalıştırma _dotnet svcutil_ gibi web hizmeti başvurusu dosyası oluşturmak için komutu:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil http://contoso.com/SayHello.svc
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```console
dotnet svcutil http://contoso.com/SayHello.svc
```

---

Oluşturulan dosyası olarak kaydedilen _HelloSvcutil/ServiceReference/Reference.cs_. _Dotnet svcutil_ aracı gerekli proxy kodu tarafından uygun WCF paketleri paket başvuruları projeye de ekler.

## <a name="using-the-service-reference"></a>Hizmet başvurusunu kullanma

1. Kullanarak WCF paketleri geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:

```console
dotnet restore
```

2. İstemci adı, sınıf ve kullanmak istediğiniz işlemi bulun. `Reference.cs` devralan bir sınıfın içereceği `System.ServiceModel.ClientBase`, hizmetteki işlemleri çağırmak için kullanılan yöntemleri. Bu örnekte, aramak istediğiniz _SayHello_ hizmetin _Hello_ işlemi. `ServiceReference.SayHelloClient` İstemci sınıf adıdır ve sahip bir yöntemi çağıran `HelloAsync` işlemi çağırmak için kullanılabilir.

3. Açık `Startup.cs` Düzenleyicisi'nde dosya ve kullanarak bir ekleme üst hizmet başvurusu isim uzayı için:

```csharp
using ServiceReference;
```

 4. Düzen `Configure` web hizmetini çağırmak için yöntem. Devralınan sınıfının bir örneğini oluşturarak bunu `ClientBase` ve istemci nesneye yöntemi çağırma:

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

5. Kullanarak uygulama çalıştırma [ `dotnet run` ](../tools/dotnet-run.md) komutuyla şu şekilde:

```console
dotnet run
```

6. Konsolda listelenen URL'ye gidin (örneğin, `http://localhost:5000`) web tarayıcınızda.

Aşağıdaki çıktıyı görmeniz gerekir: "Hello dotnet-svcutil!"

Ayrıntılı bir açıklaması için `dotnet-svcutil` aracı parametreleri, help parametresini aşağıdaki şekilde geçirme aracı Çağır:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Geri bildirim ve sorular

Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Sürüm notları

* Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.

## <a name="information"></a>Bilgiler

* [DotNet svcutil NuGet paketi](https://nuget.org/packages/dotnet-svcutil)
