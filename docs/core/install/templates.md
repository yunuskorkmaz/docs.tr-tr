---
title: SDK şablonlarını yükleyip yönetme-.NET Core
description: .NET Core şablonlarının Windows, Linux ve macOS 'a nasıl yükleneceğini öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324487"
---
# <a name="manage-net-project-and-item-templates"></a>.NET projesi ve öğe şablonlarını yönetme

.NET Core, kullanıcıların NuGet, NuGet paket dosyası veya dosya sistemi dizininden şablon yüklemesine veya kaldırmasına olanak tanıyan bir şablon sistemi sağlar. Bu makalede, .NET Core şablonlarının .NET Core SDK CLı aracılığıyla nasıl yönetileceği açıklanır.

Şablon oluşturma hakkında daha fazla bilgi için bkz. [öğretici: şablon oluşturma](../tutorials/cli-templates-create-item-template.md).

## <a name="install-template"></a>Şablonu yükler

Şablonlar [dotnet new](../tools/dotnet-new.md) , parametresiyle SDK komutu aracılığıyla yüklenir `-i` . Bir şablonun NuGet paket tanımlayıcısını ya da şablon dosyalarını içeren bir klasörü sağlayabilirsiniz.

### <a name="nuget-hosted-package"></a>NuGet barındırılan paketi

.NET CLı şablonları, geniş dağıtım için [NuGet](https://www.nuget.org/) 'e yüklenir. Şablonlar, özel bir akıştan da yüklenebilir. Bir şablonu bir NuGet akışına yüklemek yerine, [Yerel NuGet paketi](#local-nuget-package) bölümünde açıklandığı gibi *nupkg* şablon dosyaları dağıtılabilir ve el ile yüklenebilir.

NuGet akışlarını yapılandırma hakkında daha fazla bilgi için bkz [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) ..

Varsayılan NuGet akışından bir şablon paketi yüklemek için şu `dotnet new -i {package-id}` komutu kullanın:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

Varsayılan NuGet akışından belirli bir sürüme sahip bir şablon paketi yüklemek için şu `dotnet new -i {package-id}::{version}` komutu kullanın:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a>Yerel NuGet paketi

Bir şablon paketi oluşturulduğunda, bir *nupkg* dosyası oluşturulur. Şablonlar içeren bir *nupkg* dosyanız varsa, şu `dotnet new -i {path-to-package}` komutla yükleyebilirsiniz:

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a>Klasör

Bir *nupkg* dosyasından şablon yüklemeye alternatif olarak, bir klasörden şablonları doğrudan komutuyla da yükleyebilirsiniz `dotnet new -i {folder-path}` . Belirtilen klasör, bulunan herhangi bir şablon için şablon paketi tanımlayıcısı olarak değerlendirilir. Belirtilen klasör hiyerarşisinde bulunan tüm şablon yüklendi.

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

`{folder-path}`Komutta belirtilen, bulunan tüm şablonlar için şablon paketi tanımlayıcısı olur. [Liste şablonları](#list-templates) bölümünde belirtildiği gibi, komutuyla yüklenmiş şablonların bir listesini alabilirsiniz `dotnet new -u` . Bu örnekte, şablon paketi tanımlayıcısı, yüklemesi için kullanılan klasör olarak gösterilir:

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a>Şablonu kaldır

Şablonlar, [dotnet new](../tools/dotnet-new.md) parametresiyle SDK komutu aracılığıyla kaldırılır `-u` . Bir şablonun NuGet paket tanımlayıcısını ya da şablon dosyalarını içeren bir klasörü sağlayabilirsiniz.

### <a name="nuget-package"></a>NuGet paketi

NuGet şablon paketi yüklendikten sonra, bir NuGet akışından veya *nupkg* dosyasından, NuGet paket tanımlayıcısına başvurarak uygulamayı kaldırabilirsiniz.

Bir şablon paketini kaldırmak için şu komutu kullanın `dotnet new -u {package-id}` :

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a>Klasör

Şablonlar bir [klasör yolu](#folder)aracılığıyla yüklendiğinde, klasör yolu şablon paketi tanımlayıcısı olur.

Bir şablon paketini kaldırmak için şu komutu kullanın `dotnet new -u {package-folder-path}` :

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a>Liste şablonları

Standart kaldırma komutunu bir paket tanımlayıcısı olmadan kullanarak, yüklü şablonların bir listesini, her şablonu kaldırmak için olan komutla birlikte görebilirsiniz.

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a>Diğer SDK 'lardan şablon yükler

SDK 'nın her bir sürümünü sırayla yüklediyseniz, örneğin SDK 2,0 ' i ve SDK 2,1 ' yi yüklediyseniz ve bu nedenle, SDK 'nın şablonlarının her birini yüklemiş olursunuz. Bununla birlikte, 3,1 gibi daha sonraki bir SDK sürümüyle başlatırsanız, SDK 3,1 sürümü SDK 2,1 ve SDK 3,1 olduğunda yalnızca [LTS (uzun süreli destek) yayınları](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) için şablonlar dahil edilmiştir. Başka bir sürüm için şablonlar dahil değildir.

.NET Core şablonları NuGet üzerinde bulunur ve bunları diğer tüm şablonlar gibi yükleyebilirsiniz. Daha fazla bilgi için bkz. [NuGet barındırılan paketini yükler](#nuget-hosted-package).

| SDK              | NuGet paket tanımlayıcısı                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| .NET Core 2.1    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| .NET Core 2.2    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| .NET Core 3.0    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| .NET Core 3,1    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| ASP.NET Core 2,1 | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| ASP.NET Core 2,2 | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| ASP.NET Core 3,0 | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| ASP.NET Core 3,1 | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

Örneğin .NET Core SDK, .NET Core 2,1 ve .NET Core 3,1 ' i hedefleyen bir konsol uygulaması için şablonlar içerir. .NET Core 3,0 ' i hedeflemek istediyseniz, 3,0 şablonlarını yüklemeniz gerekir.

01. .NET Core 3,0 ' i hedefleyen bir uygulama oluşturmayı deneyin.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Bir hata iletisi görürseniz, şablonları yüklemeniz gerekir.

    > Giriş ile eşleşen yüklü bir şablon bulunamadı, bu, çevrimiçi olarak aranıyor...

01. .NET Core 3,0 proje şablonlarını yükler.

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. Uygulamayı ikinci kez oluşturmayı deneyin.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Projenin oluşturulduğunu belirten bir ileti görmeniz gerekir.

    > "Konsol uygulaması" şablonu başarıyla oluşturuldu.
    >
    > Oluşturma sonrası eylemler işleniyor... Path-to-Project-File. csproj üzerinde ' dotnet restore ' çalıştırılıyor... Geri yüklenecek projeler belirleniyor... Path-to-Project-File. csproj için 1,05 sn 'de geri yükleme tamamlandı.
    >
    > Geri yükleme başarılı.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: öğe şablonu oluşturma](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
