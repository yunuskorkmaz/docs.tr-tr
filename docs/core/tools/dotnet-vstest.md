---
title: DotNet vstest command - .NET Core CLI
description: Dotnet vstest komutu bir proje ve tüm bağımlılıkları oluşturur.
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: e11b193ff7a8c639078c5cf279b7fbbeab553c92
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-vstest"></a>DotNet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet-vstest` -Belirtilen dosyalarından testleri çalıştırır.

## <a name="synopsis"></a>Özet

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>Açıklama

`dotnet-vstest` Komutu çalıştırır `VSTest.Console` çalıştırmak için komut satırı uygulaması birim otomatik ve kodlanmış UI uygulama testleri.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Belirtilen derlemelerden testleri çalıştırın. Birden çok test derleme adlarının boşlukla ayırın.

## <a name="options"></a>Seçenekler

`--Settings|/Settings:<Settings File>`

Testleri çalıştırırken kullanılacak ayarları.

`--Tests|/Tests:<Test Names>`

Sağlanan değerlerle eşleşen adlarıyla testleri çalıştırın. Birden çok değeri virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Belirli bir yol özel test bağdaştırıcılarından test çalışması (varsa) kullanın.

`--Platform|/Platform:<Platform type>`

Hedef platform mimarisi test yürütmesi için kullanılır. Geçerli değerler `x86`, `x64`, ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Hedef .NET Framework sürümü test yürütmesi için kullanılır. Geçerli değerler örnekleri `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`vb. Desteklenen diğer değerler `Framework35`, `Framework40`, `Framework45`, ve `FrameworkCore10`.

`--Parallel|/Parallel`

Testler paralel olarak yürütün. Varsayılan olarak, tüm kullanılabilir çekirdekler makinede kullanılabilir. Açık bir çekirdek sayısı ayarlar dosyasıyla ayarlayın.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verilen ifade eşleşen testleri çalıştırın. `<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, işleci biri burada `=`, `!=`, veya `~`.  İşleç `~` 'içeren' anlamsallarını sahiptir ve gibi dize özellikleri için geçerlidir `DisplayName`. Parantez `()` alt ifadeleri gruplamak için kullanılır.

`-?|--Help|/?|/Help`

Komutu için kısa bir Yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için Günlükçü belirtin.  

* Team Foundation Server için test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Sonuçları bir Visual Studio Test sonuçları dosyası (TRX) için oturum açmak için kullandığınız `trx` Günlükçü sağlayıcısı. Bu anahtarı bir dosya olarak test sonuçlarını oluşturur. günlük dosyası adı verilen ile dizin. Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulan sağlanan değil.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Listeleri verilen test kapsayıcısı testlerden buldu.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Ayrıntılı günlükleri test Platform sağlar. Günlükleri sağlanan dosyasına yazılır.

`args`

Bağdaştırıcıya geçirmek için ek bağımsız değişkenlerini belirtir. Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`, burada `<n>` bağımsız değişkeni adı ve `<v>` bağımsız değişken değeri. Birden çok bağımsız değişkenleri ayırmak için boşluk kullanın.

## <a name="examples"></a>Örnekler

Testleri çalıştırmak `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Testleri çalıştırmak `mytestproject.dll`, özel adda özel klasör verme:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Testleri çalıştırmak `mytestproject.dll` ve `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Çalıştırma `TestMethod1` testler:

`dotnet vstest /Tests:TestMethod1`

Çalıştırma `TestMethod1` ve `TestMethod2` testleri:

`dotnet vstest /Tests:TestMethod1,TestMethod2`

