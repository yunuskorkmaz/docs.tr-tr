---
title: "' Bu uygulama başlatılamadı ' sorunlarını giderme"
description: "' Bu uygulama başlatılamadı ' iletişim kutusu görürseniz yapılacaklar hakkında bilgi edinin."
ms.date: 09/05/2019
ms.openlocfilehash: 92055bf40500eba4f7c892d11af12d8e675ddd5d
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605249"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>' Bu uygulama başlatılamadı ' hata iletisiyle ilgili sorun giderme

.NET Framework için geliştirilen uygulamalar genellikle sisteminize belirli bir .NET Framework sürümünün yüklenmesini gerektirir. Bazı durumlarda, yüklü bir sürüm ya da beklenen .NET Framework sürümü olmadan bir uygulamayı çalıştırmayı deneyebilirsiniz. Bu genellikle aşağıdaki gibi bir hata iletişim kutusu üretir:

![Bu uygulama başlatılamadı](media/application-not-started/app-could-not-be-started.png)

Bu hata genellikle aşağıdaki koşullardan birini gösterir:

- Sisteminizdeki bir .NET Framework yüklemesi bozuk hale geldi.

- Uygulamanız için gereken .NET Framework sürümü algılanamıyor.

Uygulamanızı çalıştırabilmeniz için bu sorunu gidermek üzere şunları yapın:

1. [.NET Framework onarım aracını indirin (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). Yükleme tamamlandığında araç otomatik olarak çalışır.

1. .NET Framework onarım aracı aşağıdaki şekilde gösterilen ek işlemleri önerirse, **İleri**' yi seçin.

   ![Onarım Aracı önerilen değişiklikler](media/application-not-started/repair-tool-recommended-changes.png)

1. .NET Framework onarım araçları, değişikliklerin tamamlandığını göstermek için aşağıdaki şekilde gösterilen bir iletişim kutusu görüntüler. Uygulamanızı yeniden çalıştırmayı deneirken iletişim kutusunu açık bırakın. .NET Framework Onarım Aracı bozuk bir .NET Framework yüklemesi tanımlamışsa ve düzeltiyorsa bu başarılı olmalıdır.

   ![Araç değişikliklerini onarma Tamam](media/application-not-started/repair-tool-changes-complete.png)

1. Uygulamanız başarıyla çalışırsa, **son** düğmesini seçin. Aksi takdirde, **İleri** düğmesini seçin.

1. **İleri** düğmesini seçtiyseniz, .NET Framework onarım aracı aşağıdaki gibi bir iletişim kutusu görüntüler. Tanılama bilgilerini Microsoft 'a göndermek için **son** düğmesini seçin.

   ![Sorun çözümlenemiyor](media/application-not-started/repair-tool-no-resolution.png)

1. Uygulamayı hala çalıştıramıyorum, aşağıdaki tabloda gösterildiği gibi, Windows sürümünüz tarafından desteklenen .NET Framework en son sürümünü yükleyebilirsiniz.

   |Windows sürümü|.NET Framework yükleme|
   |---|---|
   |Windows 10 yıldönümü güncelleştirmesi ve sonraki sürümleri|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Kasım güncelleştirmesi|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Framework 4,8 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4,8, Windows 10 Mayıs 2019 güncelleştirme ' ye önceden yüklenmiştir.

1. Uygulamayı başlatmayı deneyin.

1. Bazı durumlarda, aşağıdaki gibi bir iletişim kutusu görebilirsiniz. .NET Framework 3,5 yüklemenizi ister. .NET Framework 3,5 yüklemek için **Bu özelliği indir ve yükle** ' yi seçip uygulamayı yeniden başlatın.

   ![.NET Framework 3,5 ' i yüklemek için önerilen Windows özellikleri iletişim kutusu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework sistem gereksinimleri](../get-started/system-requirements.md)
- [.NET Framework Yükleme Kılavuzu](index.md)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md)
