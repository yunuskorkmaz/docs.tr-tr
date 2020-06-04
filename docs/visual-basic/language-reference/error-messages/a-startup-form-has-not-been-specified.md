---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409913"
---
# <a name="a-startup-form-has-not-been-specified"></a>Başlangıç formu belirtilmedi

Uygulama sınıfı kullanır, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ancak başlangıç formunu belirtmez.  
  
 Bu durum proje tasarımcısında **uygulama çerçevesini etkinleştir** onay kutusu işaretliyse, ancak **başlangıç formu** belirtilmediğinde ortaya çıkabilir. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Uygulama için bir başlangıç nesnesi belirtin.  
  
     Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>Özelliği başlangıç formu olarak ayarlamak için yöntemini geçersiz kılın <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visual Basic Uygulama Modeline Genel Bakış](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
