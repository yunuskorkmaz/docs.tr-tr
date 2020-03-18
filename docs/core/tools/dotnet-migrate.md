---
title: dotnet geçiş komutu
description: Dotnet geçir komutu bir projeyi ve tüm bağımlılıklarını geçirmektedir.
ms.date: 02/14/2020
ms.openlocfilehash: 6148048c469c43320cc4459352fd2fb62f101740
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503703"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK

## <a name="name"></a>Adı

`dotnet migrate`- Önizleme 2 .NET Core projesini .NET Core SDK tarzı bir projeye geçirin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Açıklama

Bu komut küçümsüyor. Komut `dotnet migrate` artık .NET Core 3.0 SDK ile başlayarak kullanılamaz. Yalnızca Önizleme 2 .NET Core projesini destek dışı olan 1.x .NET Core projesine geçirebilirsiniz.

Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği proje başvurularını geçirmektedir. Bu davranış, çalışma `--skip-project-references` zamanında seçeneği kullanılarak devre dışı bırakılır.

Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:

* Tek bir proje *project.json* dosyasını belirterek geçirin.
* Global.json dosyasında belirtilen tüm dizinler *global.json* dosyasına giden bir yoldan geçerek. *global.json*
* Çözümde başvurulan projeleri geçirdiği bir *solution.sln* dosyası.
* Verilen dizinin tüm alt dizilişlerinde özyinelemeli olarak.

Komut, `dotnet migrate` geçirilen *project.json* dosyasını `backup` dizin yoksa oluşturduğu bir dizinin içinde tutar. Bu davranış `--skip-backup` seçeneği kullanılarak geçersiz kılındı.

Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) çıkarır. `--report-file <REPORT_FILE>` Seçeneği kullanırsanız, çıktı belirtin dosyaya kaydedilir.

Komut `dotnet migrate` yalnızca geçerli Preview 2 *project.json*tabanlı projeleri destekler. Bu, DNX veya Preview 1 *project.json*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirmek için kullanamayacağınız anlamına gelir. Önce projeyi önizleme 2 *project.json*tabanlı projeye el ile geçirmeniz `dotnet migrate` ve ardından projeyi geçirmek için komutu kullanmanız gerekir.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Aşağıdakilerden birine giden yol:

* bir *project.json* dosyası geçiş için.
* global.json dosyası: *global.json'da* belirtilen klasörler geçirilir. *global.json*
* *solution.sln* dosyası: çözümde başvurulan projeler geçirilir.
* geçirilen bir dizin: belirtilen dizinin içinde geçiş yapmak için *project.json* dosyalarını özyinelemeli olarak arar.

Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizini alır.

## <a name="options"></a>Seçenekler

`--format-report-file-json <REPORT_FILE>`

Kullanıcı iletileri yerine JSON olarak çıktı geçiş raporu dosyası.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-r|--report-file <REPORT_FILE>`

Konsola ek olarak bir dosyaya geçiş raporu çıktı.

`-s|--skip-project-references [Debug|Release]`

Geçiş proje başvurularını atlayın. Varsayılan olarak, proje başvuruları özyinelemeli olarak geçirilir.

`--skip-backup`

Başarılı *geçişten sonra project.json,* *global.json*ve `backup` * \*.xproj'u* bir dizine taşıyın.

`-t|--template-file <TEMPLATE_FILE>`

Geçiş için kullanılacak csproj dosyasını şablonleyin. Varsayılan olarak, bırakılan `dotnet new console` şablonla aynı şablon kullanılır.

`-v|--sdk-package-version <VERSION>`

Geçirilen uygulamada başvurulan sdk paketinin sürümü. Varsayılan sdk `dotnet new`sürümü.

`-x|--xproj-file <FILE>`

Xproj dosyasına giden yol. Bir proje dizininde birden fazla xproj olduğunda gereklidir.

## <a name="examples"></a>Örnekler

Bir projeyi geçerli dizinde ve projeden projeye tüm bağımlılıklarında geçirin:

`dotnet migrate`

*global.json* dosyasının içerdiği tüm projeleri geçirin:

`dotnet migrate path/to/global.json`

Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıklar yapmayın. Ayrıca, belirli bir SDK sürümünü kullanın:

`dotnet migrate -s -v 1.0.0-preview4`
