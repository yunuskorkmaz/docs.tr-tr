---
title: (Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: 3fd46a6e8aad61d2f8ce5a230c856470f913d0bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551780"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>(Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma
Power Packs denetimlerine başvuruda bir uygulama dağıtmak istiyorsanız (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, veya <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), denetimler hedef bilgisayarda yüklü olmalıdır.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Power Packs denetimleri bir önkoşul olarak yükleme  
 Uygulama başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir. Önkoşul bileşenlerini yükleme işlemi olarak bilinir *önyükleme*.  
  
 Visual Studio geliştirme bilgisayarınızda yüklüyken Power paketleri önyükleyici paketi Visual Studio önyükleyicisi dizinine eklenir. Bu paket sonra önkoşulları ya da eklemek için yordamları izleyerek geldiğinde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.  
  
 Varsayılan olarak, yükleme paketi ile aynı konumdan önyüklendi bileşenleri dağıtılır. Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerden dağıtmayı tercih edebilirsiniz.  
  
> [!NOTE]
>  Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarında yönetici veya benzer kullanıcı izinlerine gerekebilir. İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi ne olursa olsun uygulamayı yüklemek için yönetici izinleri gerekir. Uygulama yüklendikten sonra kullanıcı uygulamayı yönetici izinleri olmadan çalıştırabilirsiniz.  
  
 Yükleme sırasında kullanıcıların hedef bilgisayarda mevcut değillerse Power Packs denetimlerine yüklemek için istenir.  
  
 Önyükleme için bir alternatif, Power Packs denetimleri bir elektronik yazılım dağıtım sistemi gibi Microsoft Systems Management Server'ı kullanarak önceden dağıtabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)
- [Visual Basic Power Packs denetimleri](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
