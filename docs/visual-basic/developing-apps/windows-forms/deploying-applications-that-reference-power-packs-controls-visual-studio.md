---
title: (Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d73c7111c3d89cadcad317c9a67e5f483da7125
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>(Visual Studio) Power Packs denetimlerine başvuruda bulunan uygulamaları dağıtma
Power Packs denetimlerine başvuruda bulunan bir uygulamayı dağıtmak istiyorsanız (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, veya <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), denetimler hedef bilgisayarda yüklü olmalıdır.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Power Packs denetimlerine bir önkoşul olarak yükleme  
 Bir uygulamayı başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir. Önkoşul bileşenlerini yükleme işlemi olarak bilinen *önyükleme*.  
  
 Visual Studio geliştirme bilgisayarınızda yüklü olduğunda Power Packs önyükleyici paketi Visual Studio önyükleyici dizinine eklenir. Bu paket sonra da önkoşulları ekleme yordamlarına izlediğinizde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.  
  
 Varsayılan olarak, yükleme paketi aynı konumda önyükleme bileşenleri dağıtılır. Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerini dağıtmayı seçebilirsiniz.  
  
> [!NOTE]
>  Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarda yönetici veya benzer kullanıcı izinlerine gerekebilir. İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi bağımsız olarak uygulamayı yüklemek için yönetici izinleri gerekir. Uygulama yüklendikten sonra kullanıcı uygulamayı yönetim izinleri olmadan çalıştırabilirsiniz.  
  
 Yükleme sırasında bunlar hedef bilgisayarda mevcut değilse Power Packs denetimlerine yüklemek için kullanıcılara sorulur.  
  
 Önyükleme alternatif olarak, Power Packs denetimlerine Microsoft Systems Management Server gibi bir elektronik yazılım dağıtım sistemi kullanarak önceden dağıtabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Visual Basic Power Packs denetimleri](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
