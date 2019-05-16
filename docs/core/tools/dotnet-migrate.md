---
title: DotNet komut geçirme
description: Dotnet geçirme komutu, bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 05/25/2018
ms.openlocfilehash: 861cd2cb982c6f41baf00a2cbd7e04b26816af76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631946"
---
# <a name="dotnet-migrate"></a>DotNet geçirme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet migrate` -Önizleme 2 .NET Core projesi bir .NET Core SDK'sı 1.0 projesine geçirir.

## <a name="synopsis"></a>Synopsis

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet migrate` Komutu geçerli bir önizleme 2 geçirir *project.json*-geçerli bir .NET Core SDK'sı 1.0 projeye dayalı *csproj* proje.

Kök proje ve kök projesini içeren tüm proje başvuruları, varsayılan olarak, komut geçirir. Kullanarak bu davranışı devre dışı `--skip-project-references` zamanında seçeneği.

Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:

* Tek bir projeye belirterek *project.json* geçirmek için dosya.
* Tüm belirtilen dizinlerin *global.json* dosya yolunu geçirerek *global.json* dosya.
* A *solution.sln* geçirildikten burada çözümde başvurulan proje dosyası.
* Belirtilen dizini yinelemeli olarak tüm alt üzerinde.

`dotnet migrate` Komut tutar geçirilen *project.json* içindeki dosya bir `backup` dizin yoksa, oluşturduğu dizin. Kullanarak bu davranışı geçersiz `--skip-backup` seçeneği.

Varsayılan olarak, geçiş işlemi için standart çıktı (STDOUT) geçiş işleminin durumunu çıkarır. Kullanırsanız `--report-file <REPORT_FILE>` seçeneği, çıkışı bir dosyaya kaydedilir belirtin.

`dotnet migrate` Komutu, yalnızca geçerli Önizleme 2 destekler *project.json*-tabanlı projelerine. Bunu DNX veya Preview 1'e geçirmek için kullanamazsınız, yani *project.json*-tabanlı projelerine MSBuild/csproj projelerine doğrudan. Önce el ile projeyi Önizleme 2'ye geçirmek gereken *project.json*-tabanlı proje ve ardından `dotnet migrate` projeyi geçirmek için komutu.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Aşağıdakilerden birine yolu:

* bir *project.json* geçirmek için dosya.
* bir *global.json* dosya: Belirtilen klasörleri *global.json* geçirilir.
* bir *solution.sln* dosya: çözümde başvurulan projeler geçirilir.
* geçiş için bir dizin: yinelemeli olarak arar *project.json* belirtilen dizinin içinde geçirmek için dosyaları.

Varsayılan olarak hiçbir şey belirtilmezse, geçerli dizin.

## <a name="options"></a>Seçenekler

`--format-report-file-json <REPORT_FILE>`

Geçiş raporu dosyasını kullanıcı yerine JSON iletileri olarak çıktı.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-r|--report-file <REPORT_FILE>`

Bir dosyaya konsol ek olarak geçiş raporu çıktı.

`-s|--skip-project-references [Debug|Release]`

Proje geçiş Atla başvuruyor. Varsayılan olarak, proje başvurularına geçirilen yinelemeli olarak olur.

`--skip-backup`

Taşıma atla *project.json*, *global.json*, ve  *\*.xproj* için bir `backup` başarılı geçişten sonra dizin.

`-t|--template-file <TEMPLATE_FILE>`

Geçiş için kullanılacak şablonu csproj dosyasını. Varsayılan olarak, aynı şablonu bırakılan `dotnet new console` kullanılır.

`-v|--sdk-package-version <VERSION>`

Geçirilen uygulamada başvurulan sdk Paket sürümü. Varsayılan SDK sürümüdür `dotnet new`.

`-x|--xproj-file <FILE>`

Kullanılacak xproj dosyanın yolu. Proje dizininde birden fazla xproj olduğunda gereklidir.

## <a name="examples"></a>Örnekler

Bir projede geçerli dizin ve tüm proje ve proje bağımlılıklarını Geçir:

`dotnet migrate`

Geçiş tüm projeleri *global.json* dosyası içerir:

`dotnet migrate path/to/global.json`

Yalnızca geçerli proje ve proje proje (P2P) bağımlılık geçirin. Ayrıca, belirli bir SDK'sı sürümünü kullanın:

`dotnet migrate -s -v 1.0.0-preview4`
