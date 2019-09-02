---
title: .NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve mevcut .NET Framework kodunu .NET Core 'a bağlamak için nasıl kullanabileceğinizi öğrenin
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 71e390881d4e9c7836622abeed49c0ea2e5f7526
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202556"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>.NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın

Mevcut kodun .NET Core 'a taşıma sırasında bulunan en yaygın sorunlardan bazıları yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır. *Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET Core uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.

Bu paket, API kümesini önemli ölçüde artıran ve neredeyse hiçbir değişiklik yapılmaksızın mevcut kodu derlenen [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) mantıksal bir uzantısıdır. Ancak .NET Standard taahhüdünü korumak için ("tüm .NET uygulamalarının sağladığı API kümesidir"), bu, kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma gibi tüm platformlarda çalışmadığınız teknolojileri içermemektedir GetVersionEx.

*Windows Uyumluluk paketi* .NET Standard en üstünde bulunur ve yalnızca Windows olan teknolojiler için erişim sağlar. .NET Core 'a geçmek isteyen ancak ilk adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için özellikle faydalıdır. Bu senaryoda, yalnızca Windows teknolojilerini kullanamayacak, sıfır mimari avantajları olan yalnızca bir geçiş değildir.

## <a name="package-contents"></a>Paket içeriği

*Windows Uyumluluk Paketi* , [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet paketi aracılığıyla sağlanır ve .NET Core veya .NET Standard hedefleyen projelerden başvurulabilir.

Aşağıdaki teknoloji alanlarından yalnızca Windows 'un yanı sıra platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:

* Kod Sayfaları
* CodeDom
* Yapılandırma
* Dizin Hizmetleri
* İnizde
* ODBC
* İzinler
* Bağlantı Noktaları
* Windows Access Control listeleri (ACL)
* Windows Communication Foundation (WCF)
* Windows şifrelemesi
* Windows olay günlüğü
* Windows Yönetim Araçları (WMI)
* Windows performans sayaçları
* Windows Kayıt Defteri
* Windows Çalışma Zamanı önbelleğe alma
* Windows Hizmetleri

Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Kullanmaya başlayın

1. Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.

2. Mevcut kodu .NET Core 'a veya .NET Standard taşıma sırasında [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)NuGet paketini yüklemek.

3. Windows üzerinde kalmak isterseniz, hazırsınız demektir.

4. Linux veya macOS 'ta .NET Core uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, platformlar arası çalışmayan API 'lerin kullanımını bulmak için [API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) ' ni kullanın.

5. Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Tanıtım için [Windows Uyumluluk Paketi 'Nin Channel 9 videosunu](https://channel9.msdn.com/Events/Connect/2017/T123)inceleyin.
