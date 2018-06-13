---
title: .NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme
description: .NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yüklemek öğrenin.
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.openlocfilehash: 226449b8ee7c9360e6bfdc5bfa5dfeb59f19bd2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387422"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme

Windows 10, Windows 8.1 ve Windows 8 uygulama çalıştırmak için .NET Framework 3.5 gerekebilir. Önceki Windows sürümleri için bu yönergeleri de kullanabilirsiniz.

## <a name="install-the-net-framework-35-on-demand"></a>İsteğe bağlı olarak .NET Framework 3.5 yükleyin

.NET Framework 3.5 gerektiren bir uygulama çalıştırmayı denerseniz aşağıdaki yapılandırma iletişim kutusu görebilirsiniz. Seçin **bu özelliği yüklemek** .NET Framework 3.5 etkinleştirmek için. Bu seçenek, bir Internet bağlantısı gerektirir.

![.NET framework yükleme iletişim kutusu](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Neden bu açılır alıyorum?

.NET Framework Microsoft tarafından oluşturulan ve uygulamaları çalıştırmak için bir ortam sağlar. Farklı sürümlerinde kullanılabilir. Birçok şirket .NET Framework kullanılarak çalıştırmak için uygulamalarını geliştirmek ve belirli bir sürümü bu uygulamaları hedefleyebilirsiniz. Bu açılır pencere görürseniz, .NET Framework sürüm 3.5 gerektiren bir uygulamayı çalıştırmak çalıştığınız, ancak bu sürümü, sisteminizde yüklü değil.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Denetim Masası'ndaki .NET Framework 3.5 etkinleştir

.NET Framework 3.5 Windows Denetim Masası'ndan etkinleştirebilirsiniz. Bu seçenek, bir Internet bağlantısı gerektirir.

1. Windows Windows tuşuna ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) klavyenizde "Windows özellikleri" yazın ve Enter tuşuna basın. **Kapatma Windows özelliklerini aç veya Kapat** iletişim kutusu görüntülenir.

2. Seçin **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu, select **Tamam**ve istenirse, bilgisayarınızı yeniden başlatın.

   ![.NET ile Denetim Masası'nı yükleme](./media/dotnet-control-panel.png)

   Alt öğeler için seçmeniz gerekmez **Windows Communication Foundation (WCF) HTTP etkinleştirmesi** ve **Windows Communication Foundation (WCF) HTTP olmayan etkinleştirme** geliştiriciyseniz sürece veya Bu işlevselliği gerektiren Sunucu Yöneticisi.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>.NET Framework 3.5 yükleme sorunlarını giderme

Yükleme sırasında hata 0x800f0906, 0x800f0907, 0x800f081f veya 0x800F0922 bakın; bu durumda, karşılaşabileceğiniz [.NET Framework 3.5 yükleme hatası: 0x800f0906, 0x800f0907 veya 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) bunları gidermek nasıl görmek için sorunları.

Yükleme sorununuzu hala çözümlenemiyor veya bir Internet bağlantısı yoksa, Windows yükleme medyasını kullanarak yüklemeyi deneyebilirsiniz. Daha fazla bilgi için bkz: [Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) kullanarak .NET Framework 3.5 dağıtmak](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Yükleme medyasının yoksa bkz [yükleme medyasını oluşturmak için Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).
