---
title: DotNet command - .NET Core CLI geçirme
description: Dotnet geçirmek komutu bir proje ve tüm bağımlılıkları geçirir.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 67a845f7604dededd00746fa6b74a320b3e134fa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697111"
---
# <a name="dotnet-migrate"></a>DotNet geçirme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet migrate` -Önizleme 2 .NET Core proje .NET Core SDK 1.0 projeye taşır.

## <a name="synopsis"></a>Özet

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet migrate` Komutu geçerli bir önizleme 2 geçirir *project.json*-geçerli bir .NET Core SDK 1.0 projesine temel *csproj* projesi.

Varsayılan olarak, kök proje ve kök projeyi içeren tüm proje başvuruları komutu geçirir. Bu davranış kullanarak devre dışı `--skip-project-references` çalışma zamanında seçeneği.

Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:

* Belirterek tek bir proje *project.json* geçirmek için dosya.
* Tüm belirtilen dizinlerin *global.json* dosya yolunu geçirerek *global.json* dosya.
* A *solution.sln* geçirildikten burada çözümde başvurulan projeleri dosya.
* Belirtilen dizin yinelemeli olarak tüm Altdizinler üzerinde.

`dotnet migrate` Komutu tutar geçirilen *project.json* içindeki dosya bir `backup` dizin yoksa, onu oluşturan dizin. Kullanılarak bu davranışı geçersiz `--skip-backup` seçeneği.

Varsayılan olarak, geçiş işlemi için standart çıkış (STDOUT) geçiş işleminin durumunu çıkarır. Kullanırsanız `--report-file <REPORT_FILE>` seçeneği, çıktı dosyasına kaydedilir belirtin.

`dotnet migrate` Komutu yalnızca geçerli Önizleme 2 destekler *project.json*-tabanlı projelerine. Bunu DNX veya Preview 1 geçirmek için kullanamazsınız, yani *project.json*-tabanlı projelerine MSBuild/csproj projelerine doğrudan. İlk proje Önizleme 2'ye el ile geçiş yapmanız *project.json*-tabanlı proje ve ardından `dotnet migrate` proje geçirmek için komutu.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Yolu şunlardan biri:

* bir *project.json* geçirmek için dosya.
* bir *global.json* dosya: Belirtilen klasörleri *global.json* geçirilir.
* bir *solution.sln* dosya: çözümde başvurulan projeleri geçirilir.
* geçirmek için bir dizin: özyinelemeli olarak arar *project.json* dosyaları içinde belirtilen dizin geçirmek için.

Varsayılan olarak hiçbir şey belirtilmişse, geçerli dizin.

## <a name="options"></a>Seçenekler

`--format-report-file-json <REPORT_FILE>`

Geçiş rapor çıktı dosyası kullanıcı yerine JSON iletileri olarak.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-r|--report-file <REPORT_FILE>`

Çıktı geçiş rapor Konsolu ek olarak bir dosya için.

`-s|--skip-project-references [Debug|Release]`

Proje geçirme Atla başvurur. Varsayılan olarak, proje başvuruları geçirilen yinelemeli olarak gelir.

`--skip-backup`

Taşıma atla *project.json*, *global.json*, ve  *\*artık.xproj* için bir `backup` başarılı geçişten sonra dizin.

`-t|--template-file <TEMPLATE_FILE>`

Geçiş için kullanılacak şablonu csproj dosyası. Varsayılan olarak, bir aynı şablonu bırakılan `dotnet new console` kullanılır.

`-v|--sdk-package-version <VERSION>`

Geçirilen uygulamada başvurulan sdk paketi sürümü. Varsayılan SDK'ın sürümüdür `dotnet new`.

`-x|--xproj-file <FILE>`

Kullanılacak xproj dosya yolu. Proje dizininde birden fazla xproj olduğunda gereklidir.

## <a name="examples"></a>Örnekler

Geçerli dizinde ve tüm proje proje bağımlılıkları projede Geçir:

`dotnet migrate`

Geçiş tüm projeleri *global.json* dosya içerir:

`dotnet migrate path/to/global.json`

Yalnızca geçerli proje ve proje proje (P2P) bağımlılık geçirin. Ayrıca, belirli bir SDK sürümü kullanın:

`dotnet migrate -s -v 1.0.0-preview4`