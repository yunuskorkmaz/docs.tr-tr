---
title: PrintForm bileşeni (Visual Basic) başvuruda bulunan uygulamaları dağıtma
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f49a5ef8dd4e36c9ab055ca01dc25ed05b083349
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>PrintForm bileşeni (Visual Basic) başvuruda bulunan uygulamaları dağıtma
Başvuruda bulunan bir uygulamayı dağıtmak istiyorsanız, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen, bileşen hedef bilgisayarda yüklü olmalıdır.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>PrintForm bir önkoşul olarak yükleme  
 Bir uygulamayı başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir. Önkoşul bileşenlerini yükleme işlemi olarak bilinen *önyükleme*.  
  
 Zaman <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni geliştirme bilgisayarınızda yüklü, Microsoft Visual Basic Power Packs önyükleyici paketi Visual Studio önyükleyici dizinine eklenir. Bu paket sonra da önkoşulları ekleme yordamlarına izlediğinizde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.  
  
 Varsayılan olarak, yükleme paketi aynı konumda önyükleme bileşenleri dağıtılır. Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerini dağıtmayı seçebilirsiniz.  
  
> [!NOTE]
>  Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarda yönetici veya benzer kullanıcı izinlerine gerekebilir. İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi bağımsız olarak uygulamayı yüklemek için yönetici izinleri gerekir. Uygulama yüklendikten sonra kullanıcı uygulamayı yönetim izinleri olmadan çalıştırabilirsiniz.  
  
 Yükleme sırasında kullanıcıların yüklemeniz istenir <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> hedef bilgisayarda mevcut değilse bileşeni.  
  
 Önyükleme alternatif olarak, önceden dağıtabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Microsoft Systems Management Server gibi bir elektronik yazılım dağıtım sistemi kullanarak bileşen.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [PrintForm Bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)
