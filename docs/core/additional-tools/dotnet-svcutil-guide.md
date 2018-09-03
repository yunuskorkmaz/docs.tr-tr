---
title: Microsoft WCF dotnet svcutil aracı
description: .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için WCF svcutil aracına benzer işlevsellik ekleyen Microsoft WCF svcutil dotnet araç genel bakış.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484127"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Microsoft WCF dotnet svcutil aracı

Windows Communication Foundation (WCF) **dotnet svcutil** araçtır bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve istemci proxy yöntemleri içeren bir WCF sınıfı oluşturur bir .NET Core CLI aracı, web hizmet işlemleri erişim.

Benzer şekilde [ **Service Model meta verilerini - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .NET Framework projeleri için araç **dotnet svcutil** bir web hizmeti başvurusu oluşturmak için bir komut satırı aracı .NET Core ve .NET Standard projelerine uyumludur.

**Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio, Visual Studio ile ilk sevk edilen hizmet sağlayıcısı bağlı 2017 v15.5. **Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Önkoşullar

* [.NET core SDK'sı](https://www.microsoft.com/net/download) v1.0.4 veya sonraki sürümler
* Sık kullandığınız kod düzenleyici

## <a name="getting-started"></a>Başlarken

Aşağıdaki örnek bir .NET Core konsol projesi için bir web hizmeti başvurusu eklemek ve hizmeti çağırmak için gereken adımlarda size yol gösterir. Adlı bir .NET Core konsol uygulaması oluşturacaksınız _HelloSvcutil_ ve aşağıdaki sözleşme uygulayan bir web hizmeti için bir başvuru ekler:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Bu örnekte, web hizmeti, şu adresten barındırılması varsayılacak: `http://contoso.com/SayHello.svc`

Bir Windows, macOS veya Linux komut penceresinde aşağıdaki adımları gerçekleştirin:

1. Adlı bir dizin oluşturmak _HelloSvcutil_ projeniz için ve aşağıdaki örnekte olduğu gibi geçerli dizin yapın:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Bu dizin kullanarak azure'da yeni bir C# konsol projesi oluşturma [ `dotnet new` ](../tools/dotnet-new.md) komutuyla şu şekilde:

```console
dotnet new console
```

3. Açık `HelloSvcutil.csproj` proje dosyası düzenleyicinizde, düzenleme `Project` öğesi ve ekleme [ `dotnet-svcutil` NuGet paketini](https://nuget.org/packages/dotnet-svcutil) CLI aracı başvuru olarak, aşağıdaki kodu kullanarak:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. Geri yükleme _dotnet svcutil_ kullanarak paket [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:

```console
dotnet restore
```

5. Çalıştırma _dotnet_ ile _svcutil_ gibi web hizmeti başvurusu dosyası oluşturmak için komutu:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
Oluşturulan dosyası olarak kaydedilen _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ aracı gerekli proxy kodu tarafından uygun WCF paketleri paket başvuruları projeye de ekler.

6. Kullanarak WCF paketleri geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutuyla şu şekilde:

```console
dotnet restore
```

7. Açık `Program.cs` dosya Düzenleyicisi'nde, Düzen `Main()` yöntemi ve web hizmetini çağırmak için aşağıdaki kodla değiştirin otomatik olarak oluşturulan kodu:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Kullanarak uygulama çalıştırma [ `dotnet run` ](../tools/dotnet-run.md) komutuyla şu şekilde:

```console
dotnet run
```
Aşağıdaki çıktıyı görmeniz gerekir: "Dotnet svcutil Merhaba!"

Ayrıntılı bir açıklaması için `dotnet-svcutil` aracı parametreleri, help parametresini aşağıdaki şekilde geçirme aracı Çağır:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Sonraki adımlar

### <a name="feedback--questions"></a>Geri bildirim ve sorular

Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Sürüm notları

* Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.

### <a name="information"></a>Bilgiler

* [DotNet svcutil NuGet paketi](https://nuget.org/packages/dotnet-svcutil)
