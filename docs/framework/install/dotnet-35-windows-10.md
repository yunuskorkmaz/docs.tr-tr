---
title: Windows 10, 8.1, 8'e .NET Framework 3.5'i yükleyin
description: .NET Framework 3.5'i Windows 10, Windows 8.1 ve Windows 8'e nasıl yükleyin öğrenin.
ms.date: 07/16/2018
ms.openlocfilehash: cfe21c0821b8f3223301dcc802533e1aaf024a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965951"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme

Windows 10, Windows 8.1 ve Windows 8'de bir uygulamayı çalıştırmak için .NET Framework 3.5'e ihtiyacınız olabilir. Bu yönergeleri önceki Windows sürümleri için de kullanabilirsiniz.

## <a name="download-the-offline-installer"></a>Çevrimdışı yükleyiciyi indirin

.NET Framework 3.5 SP1 çevrimdışı yükleyici [.NET Framework 3.5 SP1 İndirme sayfasında](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) mevcuttur ve Windows 10'dan önce Windows sürümleri için kullanılabilir.

## <a name="install-the-net-framework-35-on-demand"></a>.NET Framework 3.5'i İsteğe Bağlı Olarak Yükleyin

.NET Framework 3.5 gerektiren bir uygulamayı çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusunu görebilirsiniz. .NET Framework 3.5'i etkinleştirmek için **bu özelliği yükle'yi** seçin. Bu seçenek internet bağlantısı gerektirir.

![.NET Framework yükleme iletişim kutusunun ekran görüntüsü.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Neden bu açılır pencereyi ben alıyorum?

.NET Framework Microsoft tarafından oluşturulur ve uygulamaları çalıştırmak için bir ortam sağlar. Farklı sürümleri mevcuttur. Birçok şirket .NET Framework'u kullanarak çalışacak şekilde uygulamalarını geliştirir ve bu uygulamalar belirli bir sürümü hedeflemektedir. Bu açılır pencereyi görürseniz, .NET Framework sürüm 3.5 gerektiren bir uygulamayı çalıştırmaya çalışıyorsunuz, ancak bu sürüm sisteminizde yüklü değil.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Kontrol Panelinde .NET Framework 3.5'i etkinleştirme

.NET Framework 3.5'i Windows Denetim Masası aracılığıyla etkinleştirebilirsiniz. Bu seçenek internet bağlantısı gerektirir.

1. Windows tuşu ![logosunun Windows tuşu Ekran Görüntüsü'ne basın.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) klavyenizde "Windows Özellikleri" yazın ve Enter tuşuna basın. **Windows özelliklerini aç veya kapat** iletişim kutusu görüntülenir.

2. **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusunu seçin, **Tamam'ı**seçin ve istenirse bilgisayarınızı yeniden başlatın.

   ![.NET'in kontrol paneli ile yüklenmesini gösteren ekran görüntüsü.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Bu işlevselliğe ihtiyaç duyan bir geliştirici veya sunucu yöneticisi değilseniz, **Windows Communication Foundation (WCF) HTTP Etkinleştirme** ve **Windows İletişim Vakfı (WCF) Non-HTTP Etkinleştirme** için alt öğeleri seçmeniz gerekmez.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>.NET Framework 3.5 yükleme sorunlarını giderme

Kurulum sırasında, hata 0x800f0906, 0x800f0907, 0x800f081f veya 0x800F0922, bu durumda bakın [.NET Framework 3.5 kurulum hatası bakın: 0x800f0907 veya 0x800f0907 veya 0x800f08f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) bu sorunları çözmek için nasıl görmek için görebilirsiniz.

Yükleme sorununuzu hala çözemediyseniz veya Internet bağlantınız yoksa, Windows yükleme ortamınızı kullanarak yüklemeyi deneyebilirsiniz. Daha fazla bilgi için Dağıtım [Görüntü Servis ve Yönetimi (DISM) kullanarak .NET Framework 3.5'e](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism)bakın. Yükleme ortamınız yoksa, [windows için yükleme ortamı oluştur'a](https://support.microsoft.com/help/15088/windows-create-installation-media)bakın.

> [!WARNING]
> .NET Framework 3.5'i yüklemek için kaynak olarak Windows Update'e güvenmiyorsanız, aynı ilgili Windows işletim sistemi sürümündeki kaynakları kesinlikle kullandığınızdan emin olmalısınız. Windows'un aynı sürümüne karşılık gelen bir kaynak yolu kullanmak,.NET Framework 3.5'in eşleşmeyen bir sürümünün yüklenmesini engellemez. Ancak, bu sistemin desteklenmeyen ve hizmet verilemez bir durumda olmasını neden olur.
