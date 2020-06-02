---
title: DotNet geçiş komutu
description: DotNet Migrate komutu bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 02/14/2020
ms.openlocfilehash: 2e7f9ae5a1d11c54280d914b04df761f0d5aff99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284098"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK

## <a name="name"></a>Name

`dotnet migrate`-Preview 2 .NET Core projesini .NET Core SDK stilinde bir projeye geçirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a>Description

Bu komut kullanım dışıdır. `dotnet migrate`Komut artık .NET Core 3,0 SDK ile başlayarak kullanılamaz. Yalnızca bir Preview 2 .NET Core projesini, desteklenmeyen bir 1. x .NET Core projesine geçirebilirler.

Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği tüm proje başvurularını geçirir. Çalışma zamanında seçeneği kullanılarak bu davranış devre dışı bırakılır `--skip-project-references` .

Aşağıdaki varlıklarda geçiş yapılabilir:

* Geçirilecek *Project. JSON* dosyasını belirterek tek bir proje.
* Global. *json dosyasında bir* yolu geçirerek *Global. JSON* dosyasında belirtilen tüm dizinler.
* Çözümde başvurulan projeleri geçirirken *çözüm. sln* dosyası.
* Verilen dizinin tüm alt dizinlerinde özyinelemeli olarak.

`dotnet migrate`Komut, geçirilen *Project. JSON* dosyasını Dizin `backup` yoksa oluşturduğu bir dizin içinde tutar. Bu davranış seçeneği kullanılarak geçersiz kılınır `--skip-backup` .

Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) verir. `--report-file <REPORT_FILE>`Seçeneğini kullanırsanız, çıkış dosyaya kaydedilir.

`dotnet migrate`Komutu yalnızca geçerli Preview 2 *Project. JSON*tabanlı projeleri destekler. Bu, DNX veya Preview 1 *Project. JSON*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirebileceğiniz anlamına gelir. Önce projeyi bir Preview 2 *Project. JSON*tabanlı projeye el ile geçirmeniz ve ardından `dotnet migrate` projeyi geçirmek için komutunu kullanmanız gerekir.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Aşağıdakilerden birinin yolu:

* geçirilecek bir *Project. JSON* dosyası.
* *Global. JSON* dosyası: *Global. JSON* içinde belirtilen klasörler geçirilir.
* bir *çözüm. sln* dosyası: çözümde başvurulan projeler geçirilir.
* geçirilecek Dizin: özyinelemeli olarak *Project. JSON* dosyalarını belirtilen dizin içinde geçirilecek şekilde arar.

Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.

## <a name="options"></a>Seçenekler

`--format-report-file-json <REPORT_FILE>`

Geçiş raporu dosyasını kullanıcı iletileri yerine JSON olarak çıkar.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-r|--report-file <REPORT_FILE>`

Konsola ek olarak çıkış geçiş raporu.

`-s|--skip-project-references [Debug|Release]`

Proje başvurularını geçirmeyi atlayın. Varsayılan olarak, proje başvuruları yinelemeli olarak geçirilir.

`--skip-backup`

Başarılı geçişten sonra *Project. JSON*, *Global. JSON*ve * \* . xproj* ' ı bir dizine taşımayı atlayın `backup` .

`-t|--template-file <TEMPLATE_FILE>`

Geçiş için kullanılacak şablon csproj dosyası. Varsayılan olarak, tarafından bırakılan ile aynı şablon `dotnet new console` kullanılır.

`-v|--sdk-package-version <VERSION>`

Geçirilen uygulamada başvurulan SDK paketinin sürümü. Varsayılan, ' deki SDK sürümüdür `dotnet new` .

`-x|--xproj-file <FILE>`

Kullanılacak xproj dosyasının yolu. Proje dizininde birden fazla xproj olduğunda gereklidir.

## <a name="examples"></a>Örnekler

Geçerli dizindeki bir projeyi ve projenin tüm proje bağımlılıklarını geçirin:

`dotnet migrate`

*Global. JSON* dosyasının içerdiği tüm projeleri geçirin:

`dotnet migrate path/to/global.json`

Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıkları yoktur. Ayrıca, belirli bir SDK sürümünü kullanın:

`dotnet migrate -s -v 1.0.0-preview4`
