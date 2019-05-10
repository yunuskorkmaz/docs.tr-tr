---
title: ML.NET komut satırı arabirimi (CLI) aracı yükleme
description: Genel bakış ve ML.NET komut satırı arabirimi (CLI) aracı yükleme.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066237"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>ML.NET komut satırı arabirimi (CLI) aracı yükleme

ML.NET CLI (komut satırı arabirimi) kaliteli ML.NET modelleri ve sağladığınız eğitim veri kümeleri üzerinde tabanlı kaynak kodu oluşturmak için bir komut istemi üzerinde (Windows, Mac veya Linux) çalıştırabilirsiniz. bir araçtır.

> [!NOTE]
> ML.NET CLI ve ML.NET AutoML şu anda önizlemede olan bu konuda ifade eder ve malzeme değişiklik gösterebilir.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET core SDK'sını 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)

Çalıştırabilir ya da oluşturulan C# kod projelerini Visual Studio F5 veya ile `dotnet run` (.NET Core CLI).

Not: Yükledikten sonra eğer [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` çalışmıyor komutu, Windows oturumunuzu kapatıp tekrar açın.

## <a name="install"></a>Yükleme

ML.NET CLI herhangi diğer dotnet gibi genel aracı yüklenir. Kullandığınız `dotnet tool install` .NET Core CLI komutu. 

Aşağıdaki örnek, NuGet Özet akışı konumu varsayılan olarak ML.NET CLI'yı yükleme gösterilmektedir:

```console
> dotnet tool install -g mlnet
```

(Diğer bir deyişle, NuGet akışı varsayılan olarak kullanılabilir değilse) araç yüklenemiyor, hata iletileri görüntülenir. Beklediğiniz akışları denetlendiği denetleyin.

Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:

```console
> mlnet
```

'Otomatik train' komutu gibi mlnet aracı için kullanılabilir komutlar için Yardım görmeniz gerekir.

## <a name="install-a-specific-release-version"></a>Belirli bir sürümünü yükleyin

Yayın öncesi bir sürümü ya da aracının belirli bir sürümü yüklemeye çalışıyorsanız, sürüm numarası şu biçimi kullanarak belirtebilirsiniz:

```console
> dotnet tool install -g <package-name> --version <version-number>
```

Aşağıdaki komutu yazarak paketi düzgün şekilde yüklendiğinden de göz atabilirsiniz:

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>CLI paketini Kaldır

Paket yerel makinenizden kaldırmak için aşağıdaki komutu yazın:

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>CLI paketini güncelleştirmek

Güncelleştirme paketi, yerel makinenizde aşağıdaki komutu yazın:

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>CLI önerileri (sekme tabanlı otomatik tamamlama) ayarlama

ML.NET CLI dayalı olduğundan `System.CommandLine`, onu sekme tamamlama için yerleşik destek içerir.

Aşağıdaki animasyonda sekme otomatik tamamlama nasıl çalıştığına ilişkin bir örnek gösterilir:

![görüntü](./media/cli-tab-completion.gif)

'Sekmesinde tabanlı Otomatik Tamamlama' (parametre önerileri) çalışır *Windows PowerShell* ve *macOS/Linux bash* ancak işe yaramaz *Windows CMD*.

Geçerli Önizleme sürümünde, etkinleştirmek için son kullanıcı başına bir kez aşağıda özetlenen Kabuk birkaç adım gerekir. Bunu yaptıktan sonra tamamlamaları kullanılarak yazılmış tüm uygulamalar için çalışır `System.CommandLine` ML.NET CLI gibi.

Tamamlama etkinleştirmek için istediğiniz makinede iki işlem gerçekleştirmesi gerekir.

1. Yükleme `dotnet-suggest` aşağıdaki komutu çalıştırarak genel aracı:

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. Uygun dolgu komut kabuğu profilinize ekleyin. Bir kabuk profili dosyası oluşturmanız gerekebilir. Dolgu betik için kabuğundan tamamlama isteği iletir `dotnet-suggest` uygun temsilciler aracı `System.CommandLine`-uygulama tabanlı.

    * Bash için içeriğini Ekle [dotnet Öner shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) için `~/.bash_profile`.

    * PowerShell için içeriğini Ekle [dotnet Öner shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) PowerShell profiliniz için. Konsolunuzda aşağıdaki komutu çalıştırarak PowerShell profiliniz için beklenen yoldan bulabilirsiniz:

    ```console
    > echo $profile
    ``` 

(Diğer Kabukları için [Ara](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açık bir [sorunu](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Yükleme dizini

ML.NET CLI, varsayılan dizini veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

SDK'yı ilk kez çalıştırdığınızda, genel araçları yüklü doğrudan çağrılabilir için bu konumları kullanıcının yoluna eklenir.

Not: Genel araçları kullanıcıya özel, genel makine yok. Kullanıcıya özel olan, makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz anlamına gelir. Aracı yalnızca, aracının yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçları Ayrıca belirli bir dizindeki yüklenebilir. Belirli bir dizindeki yüklendiğinde, kullanıcı komutu kullanılabilir yolunda belirtilen dizinle komutunu çağırarak bu dizine ekleyerek emin olmanız gerekir veya belirtilen dizin içinde aracından çağırma.
Bu durumda, .NET Core CLI bu konum otomatik olarak PATH ortam değişkenine eklemez.

## <a name="see-also"></a>Ayrıca bkz.

- ['Başlangıç ML.NET CLI aracı ile' öğretici](../tutorials/mlnet-cli.md)
- [Otomatik olarak ML.NET CLI aracını kullanarak modelleri eğitme](../automate-training-with-cli.md)
- [ML.NET CLI otomatik train komut Başvuru Kılavuzu](../reference/ml-net-cli-reference.md) 
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)
