---
title: ML.NET komut satırı arabirimi (CLı) aracını yüklemek
description: ML.NET komut satırı arabirimi (CLı) aracını yükleme, yükseltme, düşürme ve kaldırma hakkında bilgi edinin.
ms.date: 06/08/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 13203246411deadf3ab13a5eba0d2c8e6e9027c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602277"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>ML.NET komut satırı arabirimi (CLı) aracını yüklemek

Windows, Mac veya Linux 'a ML.NET CLı (komut satırı arabirimi) yüklemeyi öğrenin.

ML.NET CLı, otomatik makine öğrenimi (Otomatikml) ve bir eğitim veri kümesini kullanarak iyi kalitede ML.NET modelleri ve kaynak kodu oluşturur.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)

- Seçim [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)

Oluşturulan C# kod projelerini Visual Studio ile veya tuşuna basarak `F5` `dotnet run` (.NET Core CLI) çalıştırabilirsiniz.

Not: .NET Core SDK yükledikten sonra `dotnet tool` komut çalışmaz, Windows oturumunu kapatın ve yeniden oturum açın.

## <a name="install"></a>Yükleme

ML.NET CLı, diğer DotNet genel aracı gibi yüklenir. `dotnet tool install`.NET Core CLI komutunu kullanın.

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

' Sınıflandırma ' komutu gibi mlnet aracının kullanılabilir komutları için yardım görmeniz gerekir.

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

ML.NET CLı tabanlı olduğundan `System.CommandLine` , sekme tamamlama için yerleşik desteğe sahiptir.

Aşağıdaki animasyonda sekme otomatik tamamlama 'nın nasıl çalıştığına bir örnek gösterilmektedir:

![image](./media/cli-tab-completion.gif)

' Sekme tabanlı otomatik tamamlama ' (parametre önerileri) *Windows PowerShell* ve *MacOS/Linux Bash* üzerinde çalışır, ancak *Windows cmd*'de çalışmaz.

Bu ayarı etkinleştirmek için, geçerli önizleme sürümünde son kullanıcının aşağıda belirtilen her kabuk için birkaç adım olması gerekir. Bu işlem tamamlandıktan sonra, ML.NET CLı gibi kullanılarak yazılan tüm uygulamalar için tamamlama işlemleri çalışacaktır `System.CommandLine` .

Tamamlamayı etkinleştirmek istediğiniz makinede iki şey yapmanız gerekir.

1. `dotnet-suggest`Aşağıdaki komutu çalıştırarak genel aracı 'nı yüklersiniz:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Kabuk profilinize uygun dolgu betiğini ekleyin. Bir kabuk profili dosyası oluşturmanız gerekebilir. Dolgu betiği, kabuğunuzun tamamlanma isteklerini `dotnet-suggest` , uygun tabanlı uygulamaya temsilci olan bir araca iletir `System.CommandLine` .

    - Bash için [DotNet-öner-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini ' ye ekleyin `~/.bash_profile` .

    - PowerShell için, [DotNet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini PowerShell profilinize ekleyin. Konsolunda aşağıdaki komutu çalıştırarak, PowerShell profilinize beklenen yolu bulabilirsiniz:

    ```console
    echo $profile
    ```

(Diğer kabuklar için bir [sorun](https://github.com/dotnet/System.CommandLine/issues) [bulun](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açın.)

## <a name="installation-directory"></a>Yükleme dizini

ML.NET CLı varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.

Not: genel araçlar, makineye genel değil, kullanıcıya özeldir. Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir. Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçlar, belirli bir dizine de yüklenebilir. Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.
Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı genel bakış](../automate-training-with-cli.md)
- [Öğretici: ML.NET CLı ile yaklaşımı çözümleme](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLı otomatik eğitme komut başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
