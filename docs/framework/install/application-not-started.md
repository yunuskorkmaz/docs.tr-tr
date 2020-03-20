---
title: Sorun giderme 'Bu uygulama başlatılamadı'
description: "'Bu uygulama başlatılamadı' iletişim kutusunu görürseniz ne yapmanız gerektiğini öğrenin."
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965912"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>'Bu uygulama başlatılamadı' hata iletisi hata giderme

.NET Framework için geliştirilen uygulamalar genellikle .NET Framework'ün belirli bir sürümünün sisteminize yüklenmesini gerektirir. Bazı durumlarda, yüklü bir sürümü veya .NET Framework mevcut beklenen sürümü olmadan bir uygulama çalıştırmayı deneyebilirsiniz. Bu genellikle aşağıdaki gibi bir hata iletişim kutusu üretir:

![Bu uygulama başlatılamadı](media/application-not-started/app-could-not-be-started.png)

Bu genellikle aşağıdaki koşullardan birini gösterir:

- Sisteminizdeki bir .NET Framework yüklemesi bozuldu.

- Uygulamanızın gerektirdiği .NET Framework sürümü algılanamaz.

Başvurunuzu çalıştırabilmeniz için bu sorunu gidermek için aşağıdakileri yapın:

1. .NET [Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135)indirin. İndirme tamamlandığında araç otomatik olarak çalışır.

1. .NET Framework Repair Tool aşağıdaki şekilde gösterilenler gibi ek bir eylem önerirse, **İleri'yi**seçin.

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-recommended-changes.png)

1. .NET Framework Repair Tools, değişikliklerin tamamolduğunu belirtmek için aşağıdaki şekilde gösterilen bir iletişim kutusu görüntüler. Uygulamanızı yeniden çalıştırmayı denerken iletişim kutusunu açık bırakın. Bu, .NET Framework Repair Tool bozuk bir .NET Framework yüklemesini tanımlayıp düzeltmişse başarılı olmalıdır.

   ![Önerilen değişiklikler](media/application-not-started/repair-tool-changes-complete.png)

1. Uygulamanız başarılı bir şekilde **çalışıyorsa, Bitiş** düğmesini seçin. Aksi **takdirde, İleri** düğmesini seçin.

1. **Sonraki** düğmesini seçtiyseniz, .NET Framework Repair Tool aşağıdaki gibi bir iletişim kutusu görüntüler. Tanı lama bilgilerini Microsoft'a göndermek için **Bitiş** düğmesini seçin.

   ![Sorunu çözemiyor](media/application-not-started/repair-tool-no-resolution.png)

1. Uygulamayı hala çalıştıramıyorsanız, aşağıdaki tabloda gösterildiği gibi .NET Framework'ün Windows sürümünüz tarafından desteklenen en son sürümünü yükleyin.

   |Windows sürümü|.NET Framework kurulumu|
   |---|---|
   |Windows 10 Yıldönümü Güncelleştirmesi ve sonraki sürümler|[.NET Framework 4.8 Çalışma Zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Kasım Güncelleştirmesi|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4.8 Çalışma Zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Framework 4.8 Çalışma Zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4.8, Windows 10 Mayıs 2019 Güncelleştirmesi'nde önceden yüklenmiştir.

1. Uygulamayı başlatmayı dene.

1. Bazı durumlarda, .NET Framework 3.5'i yüklemenizi isteyen aşağıdaki gibi bir iletişim kutusu görebilirsiniz. .NET Framework 3.5'i yüklemek için **bu özelliği karşıdan yükleyin ve yükleyin** ve uygulamayı yeniden başlatın.

   ![Sorunu çözemiyor](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çerçeve Sistem Gereksinimleri](../get-started/system-requirements.md)
- [.NET Framework kurulum kılavuzu](index.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md)
