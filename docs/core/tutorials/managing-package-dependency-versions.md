---
title: ".NET Core 1.0 paket bağımlılık sürümlerini yönetme"
description: ".NET Core kitaplıkları ve uygulamalar için paket bağımlılık sürüm yönetimi hakkında bilgi edinin."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.openlocfilehash: b0d4082d020da782b334a5b3999905f7de744e64
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2017
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>.NET Core 1.0 paket bağımlılık sürümlerini yönetme

Bu makalede, .NET Core kitaplıkları ve uygulamalar için paket sürümleri hakkında bilmeniz gerekenleri yer almaktadır.

## <a name="glossary"></a>Sözlük

**Düzeltme** -bağımlılıkları düzelttikten kullanmakta olduğunuz NuGet üzerinde .NET Core 1.0 için yayımlanan paket aynı "ailesi" anlamına gelir.

**Metapackage** -NuGet paket kümesini temsil eden bir NuGet paketi.

**Kırpma** -metapackage, bağımlı değildir paketlerini kaldırma eylemi.  Bu NuGet paketi yazarları için ilgili bir şeydir.  Bkz: [paket bağımlılıklarıyla küçültme project.json](../deploying/reducing-dependencies.md) daha fazla bilgi için. 

## <a name="fix-your-dependencies-to-net-core-10"></a>Bağımlılıklarınız .NET Core 1.0 için düzeltme

Güvenilir bir şekilde paketleri geri yükleyin ve güvenilir kod yazma için bağımlılıklarınızı .NET Core 1.0 sevkiyat paketleri sürümlerine düzeltmek önemlidir.  Başka bir deyişle, her paketi hiçbir ek niteleyicileri ile tek bir sürümü gerekir.

**1.0 sabit paketleri örnekleri**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**1.0 düzeltilmez paketleri örnekleri**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Bu neden önemli?

.NET Core 1.0 yanı sıra hangi gelir, bağımlılıkları düzeltin, bu paketleri tüm birlikte çalışacağını garanti ediyoruz. Bu şekilde sabit olmayan paketleri kullanıyorsanız, bu tür bir garantisi yoktur.

### <a name="scenarios"></a>Senaryolar

Tüm paketler ve .NET Core 1.0 ile yayımlanan sürümlerine büyük listesini olsa da, kodunuzu belirli senaryolarda düşerse üzerinden aramak olmayabilir.

**Yalnızca bağlı olan** `NETStandard.Library` **?**

Bu nedenle, düzeltmelidir varsa, `NETStandard.Library` paketi sürümüne `1.6`.  Bu seçkin metapackage olduğundan, paket kapatma 1.0 de düzeltilmiştir.

**Yalnızca bağlı olan** `Microsoft.NETCore.App` **?**

Bu nedenle, düzeltmelidir varsa, `Microsoft.NETCore.App` paketi sürümüne `1.0.0`.  Bu seçkin metapackage olduğundan, paket kapatma 1.0 de düzeltilmiştir.

**Olduğunuz [kırpma](../deploying/reducing-dependencies.md) ,** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackage bağımlılıkları?**

Bu durumda, ile başlamanız metapackage 1.0 düzeltildiğini emin olmalısınız.  Kırpma sonra bağımlı tek paketler 1.0 de düzeltilmiştir.

**Paketleri dışında bağlı olduğunuz** `NETStandard.Library` **veya** `Microsoft.NETCore.App` **metapackages?**

Öyleyse, başka bir bağımlılık 1.0 için çözmeniz gerekir.  Ve yapı numaralarını bu makalenin sonunda doğru paket sürümlerini bakın.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Splat dizesi kullanarak bir not (\*), sürüm oluşturma

Bir splat kullanan bir sürüm desen benimseyen (\*) dize şuna benzer: `"System.Collections":"4.0.11-*"`.

**Bunu**.  Splat dizesi kullanılarak farklı yapılandırmalardan bazıları .NET Core 1. 0 ' daha fazla boyunca olabilir paketleri geri neden olabilir.  Bu, ardından uyumsuz olan bazı paketler neden olabilir.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Paketler ve sürüm numaraları Metapackage tarafından düzenlenmiştir

[Tüm .NET standart paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Tüm çalışma zamanı paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Tüm .NET Core uygulama paketleri ve bunların sürümlerini 1.0 listesi](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
