---
title: Windows 10, 8,1, 8 ' de .NET Framework 3,5 'yi yükler
description: 3,5 .NET Framework Windows 10, Windows 8.1 ve Windows 8 ' e nasıl yükleyeceğinizi öğrenin.
ms.date: 07/16/2018
ms.openlocfilehash: 208016e22eed324a3996552284072c6ad29637a5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716387"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme

Windows 10, Windows 8.1 ve Windows 8 ' de uygulama çalıştırmak için .NET Framework 3,5 gerekebilir. Bu yönergeleri önceki Windows sürümleri için de kullanabilirsiniz.

## <a name="install-the-net-framework-35-on-demand"></a>Isteğe bağlı .NET Framework 3,5 'yi yükler

.NET Framework 3,5 gerektiren bir uygulamayı çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusunu görebilirsiniz. .NET Framework 3,5 ' i etkinleştirmek için **Bu özelliği yüklensin** ' i seçin. Bu seçenek, Internet bağlantısı gerektirir.

![.NET Framework yükleme iletişim kutusunun ekran görüntüsü.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Bu açılan pencereyi neden alıyorum?

.NET Framework, Microsoft tarafından oluşturulur ve uygulamaları çalıştırmak için bir ortam sağlar. Kullanılabilir farklı sürümler vardır. Birçok şirket, .NET Framework kullanarak çalıştırmak için uygulamalarını geliştirir ve bu uygulamalar belirli bir sürümü hedefler. Bu açılan pencereyi görürseniz, .NET Framework sürüm 3,5 gerektiren bir uygulamayı çalıştırmaya çalışıyorsunuz, ancak sisteminizde bu sürüm yüklü değil.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Denetim Masası 'nda .NET Framework 3,5 ' i etkinleştirin

Windows Denetim Masası aracılığıyla .NET Framework 3,5 ' i etkinleştirebilirsiniz. Bu seçenek, Internet bağlantısı gerektirir.

1. Windows tuşu logosunun Windows tuşu ![ekran görüntüsüne basın.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) klavyenizde "Windows özellikleri" yazın ve ENTER tuşuna basın. **Windows özelliklerini aç veya kapat** iletişim kutusu görüntülenir.

2. **.NET Framework 3,5 (.net 2,0 ve 3,0 içerir)** onay kutusunu Işaretleyin, **Tamam**' ı seçin ve istenirse bilgisayarınızı yeniden başlatın.

   ![Denetim Masası ile .NET yüklemesini gösteren ekran görüntüsü.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Bu işlevselliğe ihtiyaç duyan bir geliştirici veya sunucu yöneticisi değilseniz **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF)** için alt öğeleri seçmeniz gerekmez.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>.NET Framework 3,5 yüklemesinde sorun giderme

Yükleme sırasında, bu sorunları nasıl çözebileceği hakkında bilgi için, 0x800f0906, 0x800f0907, 0x800F081F veya 0x800F0922 hatasıyla karşılaşabilirsiniz. Bu durumda, bu sorunların nasıl çözümleneceğini görmek için [.NET Framework 3,5 yükleme hatası: 0x800f0906, 0x800f0907 veya 0x800F081F](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) makalesine başvurabilirsiniz.

Yükleme sorununuzu hala çözemezseniz veya Internet bağlantınız yoksa, Windows Yükleme medyanızı kullanarak yüklemeyi deneyebilirsiniz. Daha fazla bilgi için bkz. [Dağıtım Görüntüsü Bakımı ve yönetimi (DISM) kullanarak .NET Framework 3,5 dağıtma](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Yükleme medyanız yoksa, bkz. [Windows için yükleme medyası oluşturma](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> .NET Framework 3,5 ' i yükleme kaynağı olarak Windows Update bağlı değilseniz, aynı karşılık gelen Windows işletim sistemi sürümündeki kaynakları kesinlikle kullandığınızdan emin olmanız gerekir. Aynı Windows sürümüne karşılık gelen bir kaynak yolu kullanılması, eşleşmeyen bir .NET Framework 3,5 sürümünün yüklenmesini engellemez. Ancak bu, sistemin desteklenmeyen ve serviceable durumunda olmasına neden olur.
