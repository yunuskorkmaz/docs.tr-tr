---
title: Kod la .NET Core bağlantı noktası için Windows Uyumluluk Paketini kullanma
description: Windows Uyumluluk Paketi ve varolan .NET Framework kodunu .NET Core'a bağlantı noktasına getirmek için nasıl kullanabileceğiniz hakkında bilgi edinin.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228630"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Kod la .NET Core bağlantı noktası için Windows Uyumluluk Paketini kullanma

Varolan kodu .NET Core'a taşıma yaparken bulunan en yaygın sorunlardan bazıları, yalnızca .NET Framework'de bulunan API'lere ve teknolojilere bağımlılıktır. *Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu nedenle .NET Core uygulamaları ve .NET Standart kitaplıkları oluşturmak çok daha kolaydır.

Uyumluluk [paketi,.NET Standart 2.0'ın](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) API kümesini önemli ölçüde artıran mantıksal bir uzantısıdır. Varolan kod, neredeyse hiçbir değişiklik olmadan derlenmiştir. "Tüm .NET uygulamalarının sağladığı API kümesi" sözünü tutmak için ,.NET Standardı kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayan API'ler gibi tüm platformlarda çalışamayacak teknolojileri içermez. Windows Uyumluluk Paketi .NET Standard'ın üstünde yer alan ve yalnızca Windows'a özel teknolojilere erişim sağlar. Özellikle .NET Core'a geçmek isteyen ancak en azından ilk adım olarak Windows'da kalmayı planlayan müşteriler için kullanışlıdır. Bu senaryoda, yalnızca Windows teknolojilerini kullanabilmek geçiş engelini ortadan kaldırır.

## <a name="package-contents"></a>Paket içeriği

Windows Uyumluluk Paketi [Microsoft.Windows.Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) üzerinden sağlanır ve .NET Core veya .NET Standard'ı hedefleyen projelerden başvurulabilir.

Yalnızca Windows'a özel ve aşağıdaki teknoloji alanlarından çapraz platform API'leri de dahil olmak üzere yaklaşık 20.000 API sağlar:

- Kod Sayfaları
- Codedom
- Yapılandırma
- Dizin Hizmetleri
- Çizim
- ODBC
- İzinler
- Bağlantı Noktaları
- Windows Erişim Denetim Listeleri (ACL)
- Windows Communication Foundation (WCF)
- Windows Şifreleme
- Windows EventLog
- Windows Yönetim Araçları (WMI)
- Windows Performans Sayaçları
- Windows Kayıt Defteri
- Windows Runtime Önbelleğe Alma
- Windows Hizmetleri

Daha fazla bilgi için [uyumluluk paketinin belirtimine](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md)bakın.

## <a name="get-started"></a>Kullanmaya başlayın

1. Taşımadan önce, [Taşıma işlemine](index.md)bir göz attıktan emin olun.

2. Varolan kodu .NET Core veya .NET Standard'a taşımayaparken, [Microsoft.Windows.Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükleyin.

   Windows'da kalmak istiyorsanız, tamamen hazırsınız.

3. Linux veya macOS'ta .NET Core uygulamasını veya .NET Standart kitaplığını çalıştırmak istiyorsanız, çapraz platformda çalışmayan API'lerin kullanımını bulmak için [API Analyzer'ı](../../standard/analyzers/api-analyzer.md) kullanın.

4. Bu API'lerin kullanımlarını kaldırın, platform ötesi alternatiflerle değiştirin veya aşağıdaki gibi bir platform denetimi kullanarak onları korur:

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

Bir demo için, [Windows Uyumluluk Paketi'nin Kanal 9 videosuna](https://channel9.msdn.com/Events/Connect/2017/T123)göz atın.
