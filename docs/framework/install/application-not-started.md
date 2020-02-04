---
title: "' Bu uygulama başlatılamadı ' sorunlarını giderme"
description: "' Bu uygulama başlatılamadı ' iletişim kutusu görürseniz yapılacaklar hakkında bilgi edinin."
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965912"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>' Bu uygulama başlatılamadı ' hata iletisiyle ilgili sorun giderme

.NET Framework için geliştirilen uygulamalar genellikle sisteminize belirli bir .NET Framework sürümünün yüklenmesini gerektirir. Bazı durumlarda, yüklü bir sürüm veya .NET Framework beklenen sürümü olmadan bir uygulamayı çalıştırmayı deneyebilirsiniz. Bu genellikle aşağıdaki gibi bir hata iletişim kutusu üretir:

![Bu uygulama başlatılamadı](media/application-not-started/app-could-not-be-started.png)

Bu genellikle aşağıdaki koşullardan birini belirtir:

- Sisteminizdeki bir .NET Framework yüklemesi bozuk hale geldi.

- Uygulamanız için gereken .NET Framework sürümü algılanamıyor.

Uygulamanızı çalıştırabilmeniz için bu sorunu gidermek üzere şunları yapın:

1. [.NET Framework onarım aracını indirin (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135). Yükleme tamamlandığında araç otomatik olarak çalışır.

1. .NET Framework onarım aracı aşağıdaki şekilde gösterilen ek işlemleri önerirse, **İleri**' yi seçin.

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-recommended-changes.png)

1. .NET Framework onarım araçları, değişikliklerin tamamlandığını göstermek için aşağıdaki şekilde gösterilen bir iletişim kutusu görüntüler. Uygulamanızı yeniden çalıştırmayı deneirken iletişim kutusunu açık bırakın. .NET Framework Onarım Aracı bozuk bir .NET Framework yüklemesi tanımlamışsa ve düzeltiyorsa bu başarılı olmalıdır.

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-changes-complete.png)

1. Uygulamanız başarıyla çalışırsa, **son** düğmesini seçin. Aksi takdirde, **İleri** düğmesini seçin.

1. **İleri** düğmesini seçtiyseniz, .NET Framework onarım aracı aşağıdaki gibi bir iletişim kutusu görüntüler. Tanılama bilgilerini Microsoft 'a göndermek için **son** düğmesini seçin.

   ![Sorun çözümlenemiyor](media/application-not-started/repair-tool-no-resolution.png)

1. Uygulamayı hala çalıştıramıyorum, aşağıdaki tabloda gösterildiği gibi, Windows sürümünüz tarafından desteklenen .NET Framework en son sürümünü yükleyebilirsiniz.

   |Windows sürümü|.NET Framework yükleme|
   |---|---|
   |Windows 10 yıldönümü güncelleştirmesi ve sonraki sürümleri|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Kasım güncelleştirmesi|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4,8, Windows 10 Mayıs 2019 güncelleştirme ' ye önceden yüklenmiştir.

1. Uygulamayı başlatmayı deneyin.

1. Bazı durumlarda, aşağıdaki gibi bir iletişim kutusu görebilirsiniz. Bu, 3,5 .NET Framework yüklemenizi ister. 3,5 .NET Framework yüklemek için **Bu özelliği indir ve yükle** ' yi seçip uygulamayı yeniden başlatın.

   ![Sorun çözümlenemiyor](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework sistem gereksinimleri](../get-started/system-requirements.md)
- [.NET Framework Yükleme Kılavuzu](index.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md)
