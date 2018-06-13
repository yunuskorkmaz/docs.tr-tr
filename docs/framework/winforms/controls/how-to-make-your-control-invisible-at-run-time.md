---
title: 'Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: 51e804c7f01b55ed7504837042b6c32bf47d9405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532418"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma
Ne zaman çalışma zamanında görünmez bir kullanıcı denetimi oluşturmak isteyebilirsiniz zamanlar vardır. Örneğin, bir uyarı saati bir denetim ne zaman uyarı sizi uyarabilir dışında görünmez olabilir. Bu ayar kolayca gerçekleştirilir <xref:System.Windows.Forms.Control.Visible%2A> özelliği. Varsa <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`, denetiminizi normal olarak görünür. Varsa `false`, denetiminizi gizlenir. Denetim kodu görünmez sırasında hala çalışabilir rağmen kullanıcı arabirimi aracılığıyla denetimi ile etkileşim mümkün olmaz. Kullanıcı girişi (örneğin, fare tıklamaları) hala yanıt görünmeyen bir denetim oluşturmak istiyorsanız, saydam bir denetim oluşturmanız gerekir. Daha fazla bilgi için bkz: [denetiminize saydam arka plan vermiş](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Çalışma zamanında denetiminizi görünmez yapmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliğine `false`.  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
