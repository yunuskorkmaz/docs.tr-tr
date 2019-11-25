---
title: ML.NET komut satırı arabirimi (CLı) aracını yüklemek
description: ML.NET komut satırı arabirimi (CLı) aracının genel bakış ve yükleme.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: feeb4832b5bbd39f28ac2c6f6caa40d60b4f3aa9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977078"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>ML.NET komut satırı arabirimi (CLı) aracını yüklemek

ML.NET CLı (komut satırı arabirimi), sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabileceğiniz bir araçtır.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- Seçim [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)

Oluşturulan C# kod projelerini Visual Studio F5 ile veya `dotnet run` (.NET Core CLI) ile çalıştırabilirsiniz.

Not: [.NET Core 2,2 SDK 'yı](https://dotnet.microsoft.com/download/dotnet-core/2.2) yükledikten sonra `dotnet tool` komutu çalışmıyor, Windows oturumunu kapatıp tekrar oturum açın.

## <a name="install"></a>Yükleme

ML.NET CLı, diğer DotNet genel aracı gibi yüklenir. `dotnet tool install` .NET Core CLI komutunu kullanın.

Aşağıdaki örnek, ML.NET CLı 'nın varsayılan NuGet akış konumuna nasıl yükleneceğini göstermektedir:

```dotnetcli
dotnet tool install -g mlnet
```

Araç yüklenemezse (yani, varsayılan NuGet akışında yoksa) hata iletileri görüntülenir. Beklediğiniz akışların denetlendiğinden emin olun.

Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:

```console
mlnet
```

' Auto-eğitme ' komutu gibi mlnet aracının kullanılabilir komutları için yardım görmeniz gerekir.

## <a name="install-a-specific-release-version"></a>Belirli bir yayın sürümünü yükler

Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, [çerçeveyi](../../standard/frameworks.md) aşağıdaki biçimi kullanarak belirtebilirsiniz:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Ayrıca, aşağıdaki komutu yazarak paketin düzgün yüklenip yüklenmediğini da denetleyebilirsiniz:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>CLı paketini kaldırma

Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>CLı paketini güncelleştirme

Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>CLı önerilerini ayarlama (sekme tabanlı otomatik tamamlama)

ML.NET CLı `System.CommandLine`tabanlı olduğundan, sekme tamamlama için yerleşik desteğe sahiptir.

Aşağıdaki animasyonda sekme otomatik tamamlama 'nın nasıl çalıştığına bir örnek gösterilmektedir:

![görüntü](./media/cli-tab-completion.gif)

' Sekme tabanlı otomatik tamamlama ' (parametre önerileri) *Windows PowerShell* ve *MacOS/Linux Bash* üzerinde çalışır, ancak *Windows cmd*'de çalışmaz.

Bu ayarı etkinleştirmek için, geçerli önizleme sürümünde son kullanıcının aşağıda belirtilen her kabuk için birkaç adım olması gerekir. Bu işlem tamamlandıktan sonra, ML.NET CLı gibi `System.CommandLine` kullanılarak yazılmış tüm uygulamalar için tamamlama işlemleri çalışacaktır.

Tamamlamayı etkinleştirmek istediğiniz makinede iki şey yapmanız gerekir.

1. Aşağıdaki komutu çalıştırarak `dotnet-suggest` genel aracını yüklersiniz:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Kabuk profilinize uygun dolgu betiğini ekleyin. Bir kabuk profili dosyası oluşturmanız gerekebilir. Dolgu betiği, kabuğınızdan tamamlama isteklerini, uygun `System.CommandLine`tabanlı uygulamaya temsilci olan `dotnet-suggest` aracına iletmez.

    - Bash için [DotNet-öner-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini `~/.bash_profile`' ye ekleyin.

    - PowerShell için, [DotNet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini PowerShell profilinize ekleyin. Konsolunda aşağıdaki komutu çalıştırarak, PowerShell profilinize beklenen yolu bulabilirsiniz:

    ```console
    echo $profile
    ```

(Diğer kabuklar için bir [sorun](https://github.com/dotnet/System.CommandLine/issues) [bulun](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açın.)

## <a name="installation-directory"></a>Yükleme dizini

ML.NET CLı varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| ATAYAMADı          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.

Not: genel araçlar, makineye genel değil, kullanıcıya özeldir. Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir. Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçlar, belirli bir dizine de yüklenebilir. Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.
Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.

## <a name="see-also"></a>Ayrıca bkz.

- [' ML.NET CLı aracıyla çalışmaya başlama ' öğreticisi](../tutorials/mlnet-cli.md)
- [ML.NET CLı aracı ile modelleri otomatik olarak eğitme](../automate-training-with-cli.md)
- [ML.NET CLı otomatik eğitme komut başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
