---
title: Bağlantı noktası kodu için Windows Uyumluluk Paketi 'ni kullanma
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve bunu kullanarak .NET 5 ve .NET Core 3,1 ' ye mevcut .NET Framework kodu bağlantı noktası oluşturabilirsiniz.
author: terrajobst
ms.date: 03/04/2021
ms.openlocfilehash: c90cc960cd9ff3707877afc023f95e0e03716aab
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604820"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-5"></a>.NET 5 + için Windows Uyumluluk Paketi ' ni kullanarak bağlantı noktası kodu

.NET Framework mevcut kodu .NET 'e taşırken bulunan en yaygın sorunlardan bazıları, yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır. *Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.

Uyumluluk Paketi, API kümesini önemli ölçüde artıran [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) bir mantıksal uzantısıdır. Mevcut kod, neredeyse hiçbir değişiklik ile derlenir. "Tüm .NET uygulamalarının sağladığı API 'Ler kümesi" taahhüdünü sürdürmek için .NET Standard, kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma API 'Leri gibi tüm platformlarda çalışmayan teknolojiler içermez. Windows Uyumluluk Paketi .NET Standard en üstünde bulunur ve yalnızca bu Windows teknolojilerine erişim sağlar. Özellikle .NET 'e geçmek isteyen ancak en azından ilk bir adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için yararlıdır. Bu senaryoda, yalnızca Windows teknolojilerini kullanabilirsiniz geçiş ' i ortadan kaldırır.

## <a name="package-contents"></a>Paket içeriği

Windows Uyumluluk Paketi, [Microsoft. Windows. Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) aracılığıyla sağlanır ve .net veya .NET Standard hedef olan projelerden başvurulabilirler.

Aşağıdaki teknoloji alanlarından yalnızca Windows ve platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:

- Kod Sayfaları
- CodeDom
- Yapılandırma
- Dizin Hizmetleri
- Çizim
- ODBC
- İzinler
- Bağlantı noktaları
- Windows Access Control listeleri (ACL)
- Windows Communication Foundation (WCF)
- Windows şifrelemesi
- Windows olay günlüğü
- Windows Yönetim Araçları (WMI)
- Windows performans sayaçları
- Windows Kayıt Defteri
- Windows Çalışma Zamanı önbelleğe alma
- Windows Hizmetleri

Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).

## <a name="get-started"></a>başlarken

1. Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.

2. Mevcut kodu .NET veya .NET Standard taşırken, [Microsoft. Windows. Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükler.

   Windows üzerinde kalmak isterseniz, hazırsınız demektir.

3. Linux veya macOS 'ta .NET uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, [API Analyzer](../../standard/analyzers/api-analyzer.md) ' ı kullanarak platformlar arası çalışmayan API 'lerin kullanımını bulun.

4. Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:

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

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework .NET 'a taşıma hakkında genel bakış](index.md)
- [ASP.NET Core geçişe ASP.NET](/aspnet/core/migration/proper-to-2x)
- [.NET Framework WPF uygulamalarını .NET 'e geçirme](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework Windows Forms uygulamalarını .NET 'a geçirme](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [.NET için bağlantı noktası .NET Framework kitaplıkları](libraries.md)
