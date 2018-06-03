---
title: Microsoft WCF dotnet svcutil aracı
description: .NET Core ve ASP.NET Core projeleri, .NET Framework projeleri için WCF svcutil aracı benzer için işlevsellik ekler Microsoft WCF dotnet svcutil aracı genel bakış.
author: mlacouture
ms.author: jralexander
ms.date: 05/31/2018
ms.openlocfilehash: 1ef428059ff5d02ecf88d6c56875b712e3707caa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728762"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Microsoft WCF dotnet svcutil aracı

Windows Communication Foundation (WCF) **dotnet svcutil** aracı, bir ağ konumu üzerinde bir web hizmetinden veya WSDL dosya meta verileri alır ve istemci proxy yöntemleri içeren bir WCF sınıf oluşturur bir araçtır .NET Core CLI, web hizmeti işlemleri erişin.

Benzer şekilde [ **hizmet Model meta verilerini - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe) .NET Framework projeleri için araç **dotnet svcutil** bir web hizmeti başvuru oluşturmak için bir komut satırı aracıdır .NET Core ve .NET standart projeleri ile uyumludur.

**Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web hizmeti başvuru** ](wcf-web-service-reference-guide) Visual Studio, Visual Studio ile ilk sevk hizmet sağlayıcısı bağlı 2017 v15.5. **Dotnet svcutil** aracı .NET Core CLI aracı olarak, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform eklentisidir.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvuruları ekleme, güvenliği tehlikeye atabilir. 

## <a name="prerequisites"></a>Önkoşullar

* [.NET core SDK](https://www.microsoft.com/net/download) v1.0.4 veya sonraki sürümler
* Sık kullanılan Kod Düzenleyicisi

## <a name="getting-started"></a>Başlarken

Aşağıdaki örnek bir web hizmeti başvuru .NET Core konsol projesi ekleyin ve hizmetini çağırmak için gereken adımlarda size yol gösterir. Adlı bir .NET Core konsol uygulaması oluşturacak _HelloSvcutil_ aşağıdaki sözleşme uygulayan bir web hizmetine başvuru ekler:
```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```
Bu örnekte, web hizmeti şu adresten barındırılması olduğu kabul edilir: _http://myhost/SayHello.svc_

Gelen bir `Windows`, `macOS`, veya `Linux` komut penceresinde aşağıdaki adımları gerçekleştirin:

1. Adlı bir dizin oluşturun _HelloSvcutil_ projeniz için ve aşağıdaki örnekteki gibi geçerli dizininiz yapın:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Bu dizin kullanarak yeni bir C# konsol projesi oluşturun. [ `dotnet new` ](../tools/dotnet-new.md) gibi komut:

```console
dotnet new console
```

3. Açık `HelloSvcutil.csproj` proje dosyası düzenleyicinizde, düzenleme `Project` öğesi ekleyin [ `dotnet-svcutil` NuGet paketi](https://nuget.org/packages/dotnet-svcutil) CLI aracı başvuru olarak, aşağıdaki kodu kullanarak:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. Geri yükleme _dotnet svcutil_ kullanarak paketini [ `dotnet restore` ](../tools/dotnet-restore.md) gibi komut:

```console
dotnet restore
```

5. Çalıştırma _dotnet_ ile _svcutil_ komut aşağıdaki gibi web hizmeti referans dosyasını oluşturmak için:

```console
dotnet svcutil http://myhost/SayHello.svc
```
Oluşturulan dosyası olarak kaydedilir _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ aracı ayrıca ekler uygun WCF paketlerini gerekli proxy kodla paket referanslarını projeye.

6. WCF paketlerini kullanarak geri [ `dotnet restore` ](../tools/dotnet-restore.md) gibi komut:

```console
dotnet restore
```

7. Açık `Program.cs` dosya düzenleyicinizde, Düzen `Main()` yöntemi ve web hizmetini çağırmak için aşağıdaki kodla değiştirin otomatik olarak oluşturulan kodu:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Kullanarak uygulamayı çalıştırma [ `dotnet run` ](../tools/dotnet-run.md) gibi komut:

```console
dotnet run
```
Şu çıktı görmeniz gerekir: "Merhaba dotnet svcutil!"

Ayrıntılı bir açıklaması için `dotnet-svcutil` aracı parametreleri, Yardım parametresi şu şekilde geçirme aracı Çağır:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Sonraki adımlar

### <a name="feedback--questions"></a>Geri bildirim & sorular
Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Herhangi bir varolan sorular veya sorunlar gözden geçirebilirsiniz [WCF bağlantıların github'da adresindeki](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Sürüm notları
* Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere. 

### <a name="information"></a>Bilgiler
* [DotNet svcutil NuGet paketi](https://nuget.org/packages/dotnet-svcutil)
