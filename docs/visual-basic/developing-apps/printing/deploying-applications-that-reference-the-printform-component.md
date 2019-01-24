---
title: (Visual Basic) printform denetimlerine başvuruda bulunan uygulamaları dağıtma
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 78d332c88b45fa9b1204d9d5352a6027409254e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562433"
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>(Visual Basic) printform denetimlerine başvuruda bulunan uygulamaları dağıtma
Başvuran bir uygulama dağıtmak istiyorsanız <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen, bileşen, hedef bilgisayarda yüklü olması gerekir.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>PrintForm bir önkoşul olarak yükleme  
 Uygulama başarıyla dağıtmak için uygulama tarafından başvurulan tüm bileşenleri dağıtmanız gerekir. Önkoşul bileşenlerini yükleme işlemi olarak bilinir *önyükleme*.  
  
 Zaman <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen geliştirme bilgisayarınızda yüklü, Microsoft Visual Basic Power Packs önyükleyici paketi Visual Studio önyükleyicisi dizinine eklenir. Bu paket sonra önkoşulları ya da eklemek için yordamları izleyerek geldiğinde kullanılabilir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] veya Windows Installer dağıtımı.  
  
 Varsayılan olarak, yükleme paketi ile aynı konumdan önyüklendi bileşenleri dağıtılır. Alternatif olarak, kullanıcılar bunları gerektiği şekilde yükleyebileceğiniz bir URL veya dosya paylaşımı konumu bileşenlerden dağıtmayı tercih edebilirsiniz.  
  
> [!NOTE]
>  Önyükleme bileşenlerini yüklemek için kullanıcının bilgisayarında yönetici veya benzer kullanıcı izinlerine gerekebilir. İçin [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yani kullanıcı uygulama tarafından belirtilen güvenlik düzeyi ne olursa olsun uygulamayı yüklemek için yönetici izinleri gerekir. Uygulama yüklendikten sonra kullanıcı uygulamayı yönetici izinleri olmadan çalıştırabilirsiniz.  
  
 Yüklemek için yükleme sırasında kullanıcılara sorulur <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> hedef bilgisayarda mevcut değilse bileşeni.  
  
 Önyükleme için bir alternatif, önceden dağıtabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bir elektronik yazılım dağıtım sistemi gibi Microsoft Systems Management Server'ı kullanarak bileşeni.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)
- [PrintForm Bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)
