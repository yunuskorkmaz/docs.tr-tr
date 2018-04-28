---
title: Windows Uyumluluk Paketi kullanılarak .NET çekirdek - bağlantı noktası oluşturma
description: Windows Uyumluluk Paketi hakkında bilgi edinmek ve nasıl, kullanabilir, .NET Core için var olan .NET Framework koda bağlantı noktası
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 4ef7d9c847d48ae7bbb2d553b1c05cb90a1c5a7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-windows-compatibility-pack"></a>Windows Uyumluluk Paketi kullanma

.NET Core, var olan kodu bağlantı noktası oluşturma, geliştiriciler yüz en yaygın sorunları API'leri ve yalnızca .NET Framework mevcut teknolojiler üzerinde bağımlı biridir. *Windows Uyumluluk Paketi* .NET standart kitaplıkları yanı sıra .NET Core uygulamalar oluşturmak için var olan kodu daha uygun hale bu teknolojilerin birçoğu sağlamanın hakkında sağlamaktır.

Bu mantıksal bir pakettir [.NET standart 2.0 uzantısı](../whats-new/index.md#api-changes-and-library-support) önemli ölçüde artırır API kümesi ve var olan kodu derlendiğinden emin neredeyse hiçbir değişikliğe. Ancak .NET Standard promise tutmak için ("tüm .NET uygulamalarını API kümesi olmasından"), bu kayıt defteri gibi tüm platformlarda Windows Yönetim Araçları (WMI) çalışamaz teknolojileri eklemediniz veya yansıma yayma API'ler.

*Windows Uyumluluk Paketi* .NET standart üstünde bulunur ve Windows yalnızca teknolojileri erişim sağlar. .NET Core ancak Windows bir ilk adım olarak kalmak için plan taşımak istediğiniz müşteriler için özellikle yararlı olur. Bu senaryoda, yalnızca Windows teknolojileri kullanan yazdıramama yalnızca geçiş hurdle sıfır mimari avantajları sahip olur.

## <a name="package-contents"></a>Paket içeriğini

*Windows Uyumluluk Paketi* NuGet paketi üzerinden sağlanan [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) ve .NET Core veya .NET standart hedefleme projelerden başvurulabilir.

20. 000'hakkında bilgi sağlayan aşağıdaki teknoloji alanlarına yalnızca Windows hem de platformlar arası API'lerden dahil olmak üzere API:

* Kod Sayfaları
* CodeDom
* Yapılandırma
* Dizin Hizmetleri
* Çizim
* ODBC
* İzinler
* Bağlantı noktaları
* Windows erişim denetim listeleri (ACL)
* Windows Communication Foundation (WCF)
* Windows şifrelemesi
* Windows olay günlüğü
* Windows Yönetim Araçları (WMI)
* Windows performans sayaçları
* Windows Kayıt Defteri
* Windows çalışma zamanı önbelleğe alma
* Windows Hizmetleri

Daha fazla bilgi için bkz: [uyumluluk paketinin belirtim](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Kullanmaya başlayın

1. Bağlantı noktası oluşturma önce bir göz atalım emin olun [bağlantı noktası oluşturma işlemi](index.md).

2. .NET Core veya .NET standart varolan kod bağlantı noktası oluşturma, NuGet paket yüklemesi [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Windows üzerinde kalmasını istiyorsanız, başlamaya hazırsınız.

4. .NET Core uygulama veya .NET standart kitaplığı, Linux veya macOS çalıştırmak istiyorsanız, kullanmak [API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) platformlar arası çalışmaz API'leri kullanımını bulunamıyor.

5. Bu API kullanımları kaldırma, platformlar arası seçenekleri ile değiştirin ya da bunları gibi bir platform denetimi kullanarak koruma:

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

Gösteri için kullanıma [Windows uyumluluk paketinin Channel 9 video](https://channel9.msdn.com/Events/Connect/2017/T123).

