---
title: Azure için ile F# paket yönetimi kullanma
description: Azure bağımlılıklarını yönetmek F# için paket veya NuGet kullanma
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214219"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# Azure Bağımlılıkları için Paket Yönetimi

Paket Yöneticisi kullandığınızda Azure geliştirme için paketleri almak kolaydır. İki seçenek, [paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/)' dir.

## <a name="using-paket"></a>Paket kullanımı

Bağımlılık yöneticiniz olarak [paket](https://fsprojects.github.io/Paket/) kullanıyorsanız, Azure bağımlılıklarını eklemek için `paket.exe` aracını kullanabilirsiniz. Örneğin:

```console
> paket add nuget WindowsAzure.Storage
```

Veya, platformlar arası .NET geliştirme için [mono](https://www.mono-project.com/) kullanıyorsanız:

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

Bu, geçerli `WindowsAzure.Storage` dizindeki proje için paket bağımlılıkları kümesine eklenir, `paket.dependencies` dosyayı değiştirebilir ve paketi indirebilir. Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:

```console
> paket install
```

Ya da, mono geliştirme için:

```console
> mono paket.exe install
```

Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:

```console
> paket update
```

Ya da, mono geliştirme için:

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>NuGet kullanma

Bağımlılık yöneticiniz olarak [NuGet](https://www.nuget.org/) kullanıyorsanız, `nuget.exe` aracı kullanarak Azure bağımlılıklarını ekleyebilirsiniz. Örneğin:

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

Ya da, mono geliştirme için:

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

Bu, geçerli `WindowsAzure.Storage` dizindeki proje için paket bağımlılıkları kümesine ekler ve paketi indirir. Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:

```console
> nuget restore
```

Ya da, mono geliştirme için:

```console
> mono nuget.exe restore
```

Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:

```console
> nuget update
```

Ya da, mono geliştirme için:

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>Başvurulan Derlemeler

F# Komut betiğinizdeki paketleri kullanabilmeniz için, bir `#r` yönergesi kullanarak paketlere dahil olan derlemelere başvurmanız gerekir. Örneğin:

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

Gördüğünüz gibi, DLL için göreli yolu ve tam DLL adını belirtmeniz gerekir. Bu, paket adıyla tam olarak aynı olmayabilir. Yol, çerçeve sürümü ve muhtemelen paket sürüm numarası içerecektir. Yüklü tüm derlemeleri bulmak için bir Windows komut satırında şuna benzer bir şey kullanabilirsiniz:

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Ya da bir UNIX kabuğunda şuna benzer:

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

Bu, size yüklü derlemelerin yollarını verecektir. Buradan, çerçeve sürümünüz için doğru yolu seçebilirsiniz.
