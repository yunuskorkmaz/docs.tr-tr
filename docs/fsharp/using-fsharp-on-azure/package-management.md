---
title: 'Azure için paket Yönetimi F # ile kullanma'
description: 'F # Azure bağımlılıkları yönetmek için paket veya Nuget kullanma'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da6938c6ee29292571f4269c68a9148c13738422
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a>F # Azure bağımlılıklar için paket Yönetimi

Bir paket Yöneticisi'ni kullandığınızda Azure geliştirme için paketleri alma kolaydır. İki seçenek olan [Paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Paket kullanma

Kullanıyorsanız, [Paket](https://fsprojects.github.io/Paket/) bağımlılık Yöneticisi olarak, kullandığınız `paket.exe` aracı Azure bağımlılıkları ekleyin. Örneğin:

    > paket add nuget WindowsAzure.Storage

Veya kullanıyorsanız, [Mono](https://www.mono-project.com/) platformlar arası .NET geliştirme için:

    > mono paket.exe add nuget WindowsAzure.Storage

Bu ekler `WindowsAzure.Storage` , geçerli dizin içinde projesi için Paket bağımlılıklarını kümesine değiştirme `paket.dependencies` dosya ve paketini indirin. Bağımlılıklarını daha önce ayarlamış veya bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan bir proje üzerinde çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıkları yükler:

    > paket install

Veya Mono geliştirme için:

    > mono paket.exe install

Bu gibi en son sürümü için tüm paket bağımlılıklarını güncelleştirebilirsiniz:

    > paket update

Veya Mono geliştirme için:

    > mono paket.exe update

## <a name="using-nuget"></a>Nuget kullanma

Kullanıyorsanız, [NuGet](https://www.nuget.org/) bağımlılık Yöneticisi olarak, kullandığınız `nuget.exe` aracı Azure bağımlılıkları ekleyin. Örneğin:

    > nuget install WindowsAzure.Storage -ExcludeVersion

Veya Mono geliştirme için:

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

Bu ekler `WindowsAzure.Storage` projesi geçerli dizinde ve indirme paketi için Paket bağımlılıklarını, dizi. Bağımlılıklarını daha önce ayarlamış veya bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan bir proje üzerinde çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıkları yükler:

    > nuget restore 

Veya Mono geliştirme için:

    > mono nuget.exe restore

Bu gibi en son sürümü için tüm paket bağımlılıklarını güncelleştirebilirsiniz:

    > nuget update

Veya Mono geliştirme için:

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>Başvurulan Derlemeler

Kullanarak paketlerinde derlemeleri başvuruda bulunmanız paketlerinizi F # komut dosyanıza kullanmak için bir `#r` yönergesi. Örneğin:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

Gördüğünüz gibi DLL ve paket adı ile aynı tam olarak olmayabilir tam DLL adı göreli yolunu belirtmeniz gerekir. Yolun framework sürümü ve büyük olasılıkla bir paket sürüm numarasını içerir. Tüm yüklü derlemelerin bulmak için aşağıdakine benzer bir Windows komut satırında kullanabilirsiniz:

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

Veya bir UNIX Kabuğu'nda bir şey şöyle:

    > find packages/WindowsAzure.Storage -name "*.dll"

Bu yüklenmiş derlemeleri yollar sağlar. Buradan, framework sürümünüz için doğru yolu seçebilirsiniz.
