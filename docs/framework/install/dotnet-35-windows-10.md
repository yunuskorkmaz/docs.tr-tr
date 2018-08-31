---
title: Windows 10, Windows 8.1 ve Windows 8 üzerinde .NET Framework 3.5 yükleme
description: Windows 10, Windows 8.1 ve Windows 8 üzerinde .NET Framework 3.5 yüklemeyi öğrenin.
author: rlander
ms.author: mairaw
ms.date: 07/16/2018
ms.openlocfilehash: 7b3b7ca5709008260ea284602a3ed8d2b288c410
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257526"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Windows 10, Windows 8.1 ve Windows 8 üzerinde .NET Framework 3.5 yükleme

Windows 10, Windows 8.1 ve Windows 8 üzerinde bir uygulamayı çalıştırmak için .NET Framework 3.5 gerekir. Önceki Windows sürümleri için bu yönergeleri de kullanabilirsiniz.

## <a name="install-the-net-framework-35-on-demand"></a>İsteğe bağlı olarak .NET Framework 3.5 yükleme

.NET Framework 3.5 gerektiren bir uygulama çalıştırmayı denerseniz, aşağıdaki yapılandırma iletişim kutusu görebilirsiniz. Seçin **bu özelliği yükleyebilmek** .NET Framework 3.5 etkinleştirme. Bu seçenek, Internet bağlantısı gerektirir.

![.NET framework yükleme iletişim kutusu](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Neden bu açılır alıyorum?

.NET Framework, Microsoft tarafından oluşturulur ve uygulamaları çalıştırmak için bir ortam sağlar. Farklı sürümler bulunur. Birçok şirket .NET Framework kullanılarak çalıştırılacak uygulamalarını geliştirme ve bu uygulamaların belirli bir sürümü hedeflemesini. Bu açılır pencere görürsünüz, .NET Framework sürüm 3.5 gerektiren bir uygulamayı çalıştırmak çalışıyorsunuz, ancak bu sürüm, sisteminizde yüklü değil.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Denetim Masası'nda .NET Framework 3.5 etkinleştirme

.NET Framework 3.5 Windows Denetim Masası'ndan etkinleştirebilirsiniz. Bu seçenek, Internet bağlantısı gerektirir.

1. Windows Windows tuşuna basın ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) klavyenizde "Windows özellikleri" yazın ve Enter tuşuna basın. **Kapatma Windows özelliklerini aç veya Kapat** iletişim kutusu görüntülenir.

2. Seçin **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusunu seçin **Tamam**ve istenirse, bilgisayarınızı yeniden başlatın.

   ![.NET ile Denetim Masası'nı yükleme](./media/dotnet-control-panel.png)

   Alt öğeler için seçmeniz gerekmez **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF) HTTP olmayan etkinleştirme** bir geliştiriciyseniz sürece veya Bu işlevselliği gerektiren Sunucu Yöneticisi.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>.NET Framework 3.5 yükleme sorunlarını giderme

0x800f0906, 0x800f0907, 0x800f081f veya 0x800F0922 başvurun ve bu durumda, hata, yükleme sırasında karşılaşabileceğiniz [.NET Framework 3.5 yükleme hatası: 0x800f0906, 0x800f0907 veya 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) bunları çözmek için sorun.

Yükleme sorununuzu hala çözümlenemiyor veya bir Internet bağlantınız yoksa, onu, Windows yükleme ortamını kullanarak yüklemeyi deneyebilirsiniz. Daha fazla bilgi için [Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) kullanarak .NET Framework 3.5 dağıtma](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Yükleme medyasını yoksa bkz [yükleme medyası oluşturmak için Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Windows Update'te .NET Framework 3.5 yüklemek için kaynak olarak bağlı değil, aynı karşılık gelen Windows işletim sistemi sürümünü kaynaklarından tamamen kullanılacak emin olmanız gerekir. Aynı Windows sürümüne karşılık gelmiyor bir kaynak yolu kullanarak eşleşmeyen bir .NET Framework 3.5 sürümünü yüklenmesini engellemez. Ancak, bu desteklenmeyen ve unserviceable durumda olması için sistem neden olur.
