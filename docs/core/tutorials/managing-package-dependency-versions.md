---
title: .NET Core 1.0 için paket bağımlılığı sürümlerini yönetme
description: .NET Core kitaplıkları ve uygulamaları için paket bağımlılık sürüm yönetimi hakkında bilgi edinin.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168617"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>.NET Core 1.0 için paket bağımlılığı sürümlerini yönetme

Bu makale, .NET Core kitaplıkları ve uygulamaları için paket sürümleri hakkında bilmeniz gerekenler kapsar.

## <a name="glossary"></a>Sözlük

**Düzeltme** -bağımlılıkları düzeltme kullanmakta olduğunuz NuGet üzerinde .NET Core 1.0 için yayımlanan paket aynı "ailesi" anlamına gelir.

**Metapackage** -NuGet paketlerini kümesini temsil eden bir NuGet paketi.

**Kırpma** -bir metapackage, bağımlı değildir paketlerini kaldırma işlemi.  NuGet paketi yazarları için ilgili bir sorun budur.  Bkz: [azaltma Paket bağımlılıklarını project.json ile](../deploying/reducing-dependencies.md) daha fazla bilgi için. 

## <a name="fix-your-dependencies-to-net-core-10"></a>.NET Core 1.0 için bağımlılıklarınızı düzeltme

Güvenilir bir şekilde paketlerini geri yükleyip güvenilir kod yazma için bağımlılıklarınızı yanı sıra .NET Core 1.0 sevkiyat paketleri sürümlerine düzeltmek önemlidir.  Başka bir deyişle, her paketi, hiçbir ek niteleyicileri tek bir sürüm gerekir.

**1.0 sabit paketleri örnekleri**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**1.0 düzeltilmez paketleri örnekleri**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Bu neden önemlidir?

Bağımlılıklarınızı hangi gemileri birlikte .NET Core 1.0 için düzeltme varsa, bu paketleri tüm birlikte çalışacağından emin ediyoruz. Bu şekilde sabit olmayan paketler kullanırsanız, böyle bir garanti yoktur.

### <a name="scenarios"></a>Senaryolar

Tüm paketleri ve bunların sürümlerini .NET Core 1.0 ile yayımlanan büyük bir listesi olmasa da, kodunuzun belirli senaryolarda düşerse içinden aramak sahip.

**Yalnızca bağlı olan** `NETStandard.Library` **?**

Bu nedenle, düzeltmeniz durumunda, `NETStandard.Library` paket sürümüne `1.6`.  Bu seçkin metapackage olduğu için paket kapanış ayrıca 1.0 sabit.

**Yalnızca bağlı olan** `Microsoft.NETCore.App` **?**

Bu nedenle, düzeltmeniz durumunda, `Microsoft.NETCore.App` paket sürümüne `1.0.0`.  Bu seçkin metapackage olduğu için paket kapanış ayrıca 1.0 sabit.

**İşiniz [kırpmayı](../deploying/reducing-dependencies.md) ,** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackage bağımlılıkları?**

Bu durumda, 1.0 ile başlamanız metapackage düzeltildiğini emin olmanız gerekir.  Kırpma sonra bağlı tek paketler de 1.0 için sabittir.

**Paketleri dışında bağlı olduğunuz** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **meta paketler?**

Bu durumda, diğer bağımlılıklarınızı 1.0 için düzeltme gerekir.  Doğru paket sürümlerini görmek ve yapı numaralarını bu makalenin sonunda.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Bir bölme dize kullanma hakkında bir not (\*), sürüm oluşturma

Bir bölme kullandığı sürüm oluşturma düzeni benimseyen (\*) dizesi: `"System.Collections":"4.0.11-*"`.

**Bunu**.  Bir bölme dize kullanarak farklı derlemelerden bazıları daha .NET Core 1.0 boyunca olabilir paketleri geri neden olabilir.  Bu, ardından uyumsuz olan bazı paketlerde neden olabilir.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Paketler ve sürüm numaraları Metapackage tarafından düzenlenmiştir

[Tüm .NET Standard paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Tüm çalışma zamanı paketlerini ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Tüm .NET Core uygulama paketlerini ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
