---
title: 'Nasıl yapılır: Çalışma zamanında denetiminizi görünmez yapma'
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
ms.openlocfilehash: 52ea2336bac1ec483cb86e24114090a1b3725038
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708983"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Nasıl yapılır: Çalışma zamanında denetiminizi görünmez yapma
Çalışma zamanında görünmez olan bir kullanıcı denetimi oluşturmak isteyebilirsiniz zamanlar vardır. Örneğin, bir uyarı saati bir denetim ne zaman uyarı sizi uyarabilir dışında görünmez olabilir. Bu ayarlayarak kolayca gerçekleştirilir <xref:System.Windows.Forms.Control.Visible%2A> özelliği. Varsa <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`, Denetim normal olarak görünür. Varsa `false`, denetiminizin gizlenir. Denetiminiz kodunda görünmez hala çalışabilir ancak kullanıcı arabirimi aracılığıyla denetimi ile etkileşim kurmak mümkün olmayacaktır. Kullanıcı girişi (örneğin, fare tıklamaları) hala yanıt veren görünmeyen bir denetim oluşturmak istiyorsanız, saydam bir denetimi oluşturmanız gerekir. Daha fazla bilgi için [denetiminiz saydam bir arka plan verme](how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>İçin çalışma zamanında denetiminizi görünmez yapma  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliğini `false`.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Control.Visible%2A>
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Nasıl yapılır: Denetiminize saydam arka plan verme](how-to-give-your-control-a-transparent-background.md)
