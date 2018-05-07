---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 699d20e6afb2335336b3652be5907f0dd72299fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="a-startup-form-has-not-been-specified"></a>Başlangıç formu belirtilmedi
Uygulamanın kullandığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıf ancak başlangıç formu belirtmiyor.  
  
 Bu durum ortaya çıkabilir **etkinleştir uygulama çerçevesi** Proje Tasarımcısı'nda onay kutusu seçili ancak **başlangıç formu** belirtilmedi. Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Uygulama için bir başlangıç nesnesi belirtin.  
  
     Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
2.  Geçersiz kılma <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlamak için yöntemin <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> başlangıç formu özelliğine.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>  
 [Visual Basic Uygulama Modeline Genel Bakış](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
