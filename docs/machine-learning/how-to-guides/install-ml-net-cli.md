---
title: komut-line arabirimi (CLI) aracıML.NET nasıl yüklenir?
description: ML.NET komut satırı arabirimi (CLI) aracını nasıl yükleyip yükseltecek, düşürecek ve kaldırabilirsiniz öğrenin.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848645"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>komut-line arabirimi (CLI) aracıML.NET nasıl yüklenir?

CLI(komut satırı arabirimi) ML.NET Windows, Mac veya Linux'a nasıl yükleyin.

CLI ML.NET, otomatik makine öğrenimi (AutoML) ve eğitim veri seti kullanarak kaliteli ML.NET modeller ve kaynak kodu oluşturur.

> [!NOTE]
> Bu konu, şu anda Önizleme'de olan cli ve ML.NET AutoML'ML.NET anlamına gelir ve malzeme değişebilir.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Çekirdek 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)

Oluşturulan C# kod projelerini Visual Studio ile `F5` tuşa `dotnet run` basarak veya (.NET Core CLI) ile çalıştırabilirsiniz.

Not: [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) komutu `dotnet tool` çalışmıyorsa, Windows'tan oturum açın ve yeniden oturum açın.

## <a name="install"></a>Yükleme

cli ML.NET diğer dotnet Global Tool gibi yüklenir. .NET `dotnet tool install` Core CLI komutunu kullanırsınız.

Aşağıdaki örnekte, varsayılan NuGet akış konumunda cli ML.NET nasıl yüklenir:

```dotnetcli
dotnet tool install -g mlnet
```

Araç yüklenemezse (diğer bir zamanda varsayılan NuGet akışında kullanılamıyorsa), hata iletileri görüntülenir. Beklediğiniz özet akışlarının kontrol edilebilmektedir.

Yükleme başarılı olursa, aracı aramak için kullanılan komutu ve aşağıdaki örneğe benzer şekilde yüklenen sürümü gösteren bir ileti görüntülenir:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Yüklemenin başarılı olduğunu aşağıdaki komutu yazarak onaylayabilirsiniz:

```console
mlnet
```

'Otomatik tren' komutu gibi mlnet aracı için kullanılabilir komutlar için yardım görmelisiniz.

## <a name="install-a-specific-release-version"></a>Belirli bir sürüm sürümünü yükleme

Bir ön sürüm sürümünü veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, aşağıdaki biçimi kullanarak [çerçeveyi](../../standard/frameworks.md) belirtebilirsiniz:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Paketin düzgün yüklenip yüklenmediğinizi aşağıdaki komutu yazarak da kontrol edebilirsiniz:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>CLI paketini kaldırın

Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>CLI paketini güncelleştirin

Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>CLI önerilerini ayarlama (sekme tabanlı otomatik tamamlama)

cli ML.NET dayandığı `System.CommandLine`için, sekme tamamlanması için yerleşik desteği vardır.

Sekme otomatik tamamlamanın nasıl çalıştığına bir örnek aşağıdaki animasyonda gösterilmiştir:

![image](./media/cli-tab-completion.gif)

'Sekme tabanlı otomatik tamamlama' (parametre önerileri) *Windows PowerShell* ve *macOS/Linux bash* üzerinde çalışır ancak *Windows CMD*üzerinde çalışmaz.

Etkinleştirmek için, geçerli önizleme sürümünde, son kullanıcının kabuk başına bir kez birkaç adım atması gerekir, aşağıda özetlenmiştir. Bu işlem tamamlandıktan sonra, cli ML.NET `System.CommandLine` gibi tüm uygulamalar için çalışacaktır.

Tamamlanmasını sağlamak istediğiniz makinede iki şey yapmanız gerekir.

1. Aşağıdaki `dotnet-suggest` komutu çalıştırarak genel aracı yükleyin:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Kabuk profilinize uygun şim komut dosyasını ekleyin. Bir kabuk profil dosyası oluşturmanız gerekebilir. Şim komut dosyası, tamamlanma isteklerini `dotnet-suggest` kabuğunuzdan uygun `System.CommandLine`tabanlı uygulamaya temsilci olarak sunan araca iletir.

    - Bash için, `~/.bash_profile` [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini ekleyin.

    - PowerShell için, PowerShell profilinize [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini ekleyin. Konsolunuzda aşağıdaki komutu çalıştırarak PowerShell profilinize beklenen yolu bulabilirsiniz:

    ```console
    echo $profile
    ```

(Diğer kabuklar [için](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) bir [sorun](https://github.com/dotnet/System.CommandLine/issues)arayın veya açın.)

## <a name="installation-directory"></a>Kurulum dizini

CLI ML.NET varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konumlar, SDK ilk çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle burada yüklenilen Global Araçlar doğrudan çağrılabilir.

Not: Genel Araçlar kullanıcıya özeldir, makine geneli değildir. Kullanıcıya özel olmak, makinenin tüm kullanıcıları tarafından kullanılabilen bir Global Tool yükleyemeyeceğiniz anlamına gelir. Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.

Genel Araçlar belirli bir dizine de yüklenebilir. Belirli bir dizine yüklendiğinde, kullanıcı, bu dizini yola ekleyerek, komutu belirtilen dizini çağırarak veya aracı belirtilen dizinin içinden arayarak komutun kullanılabilir olduğundan emin olmalıdır.
Bu durumda, .NET Core CLI bu konumu OTOMATIK olarak PATH ortamı değişkenine eklemez.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI genel bakış](../automate-training-with-cli.md)
- [Öğretici: cli ML.NET ile duyguları analiz edin](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI otomatik tren komutu başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)
