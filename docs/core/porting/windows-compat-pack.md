---
title: .NET Core kod bağlantı noktası için Windows Uyumluluk Paketi kullanma
description: Windows Uyumluluk Paketi hakkında bilgi edinmek ve nasıl, kullanabilir, bağlantı noktası var olan .NET Framework kodu .NET Core için
author: terrajobst
ms.date: 11/13/2017
ms.custom: seodec18
ms.openlocfilehash: 0a409c953ce38ed4c2959adaf4de9d3730ce37f4
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169943"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>.NET Core kod bağlantı noktası için Windows Uyumluluk Paketi kullanma

.NET Core için mevcut kodu taşıyorsanız, bulunan en yaygın sorunlardan bazılarını, API ve .NET Framework yalnızca bulunur teknolojilerini bağımlılıklardır. *Windows Uyumluluk Paketi* .NET Core uygulamaları ve .NET standart kitaplıkları oluşturmak çok daha kolay olacak şekilde bu teknolojilerin birçoğu sağlar.

Bu mantıksal bir pakettir [.NET Standard 2.0 uzantısı](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) önemli ölçüde artar API kümesi ve varolan kodu derlendiğinden emin neredeyse değişikliğe. Ancak .NET Standard'ın promise tutulabilmesi için ("tüm .NET uygulamalarında sağlayan API kümesi sağlıyor"), bu kayıt defteri gibi tüm platformlarda Windows Yönetim Araçları (WMI) çalışamaz teknolojileri eklemediğiniz veya yansıma yayma API'ler.

*Windows Uyumluluk Paketi* .NET Standard en üstünde yer alan ve Windows sadece teknolojileri erişim sağlar. .NET Core ancak bir ilk adım Windows kalabilmek için plan taşımak istediğiniz müşteriler özellikle yararlıdır. Bu senaryoda yalnızca Windows teknolojileri kullanacak şekilde boyutlandırılmamışsa, yalnızca bir geçiş hurdle sıfır mimari avantajlarla olur.

## <a name="package-contents"></a>Paket içeriği

*Windows Uyumluluk Paketi* NuGet paketi sağlanan [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) ve .NET Core veya .NET Standard hedefleyen projeleri başvurulabilir.

Yaklaşık 20. 000 sağladığı API'leri, yalnızca Windows yanı platformlar arası API'lerinden aşağıdaki teknoloji alanları dahil olmak üzere:

* Kod Sayfaları
* CodeDom
* Yapılandırma
* Dizin Hizmetleri
* Çizim
* ODBC
* İzinler
* Bağlantı Noktaları
* Windows erişim denetim listeleri (ACL)
* Windows Communication Foundation (WCF)
* Windows şifreleme
* Windows olay günlüğü
* Windows Yönetim Araçları (WMI)
* Windows performans sayaçları
* Windows Kayıt Defteri
* Windows çalışma zamanı önbelleğe alma
* Windows Hizmetleri

Daha fazla bilgi için [uyumluluk paketinin belirtim](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Kullanmaya başlayın

1. Taşıma önce göz atın emin olun [taşıma işlemi](index.md).

2. .NET Core veya .NET Standard için mevcut kodu taşıyorsanız, NuGet paketini yüklemek [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Windows üzerinde kalmak istiyorsanız, başlamaya hazırsınız.

4. Linux veya Macos'ta .NET Core uygulaması veya .NET Standard kitaplığı çalıştırmak istediğiniz kullanırsanız [API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) platformlar arası çalışmaz API kullanım bulunamadı.

5. Bu API kullanımları Kaldır, bunları platformlar arası alternatif ile değiştirin veya gibi bir platform denetimi kullanarak bunları koruma:

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

Bir tanıtım için kullanıma [Windows Uyumluluk Paketi Channel 9 video](https://channel9.msdn.com/Events/Connect/2017/T123).

