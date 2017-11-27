---
title: "Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)
Ayarladığınızda <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliği bir <xref:System.Windows.Forms.ToolStrip> denetimini `true`, denetimin kapsayıcısının uçtan uca doldurur ve öğenin kapsayıcısına göre yeniden boyutlandırır olduğunda yeniden boyutlandırır. Bu yapılandırmada, öğeyi denetiminde gibi uzatmak yararlı bir <xref:System.Windows.Forms.ToolStripTextBox>, kullanılabilir alanı dolduracak şekilde ve denetimi yeniden boyutlandırır yeniden boyutlandırmak için. Görünüm ve davranış Microsoft® Internet Explorer Adres çubuğuna benzer elde etmek istiyorsanız bu uzatma Örneğin, yararlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde türetilmiş bir sınıf sağlar <xref:System.Windows.Forms.ToolStripTextBox> adlı `ToolStripSpringTextBox`. Bu sınıf geçersiz kılmaları <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> üst kullanılabilir genişliğini hesaplamak için yöntem <xref:System.Windows.Forms.ToolStrip> diğer tüm öğeleri birleşik genişliğini çıkarılmasıyla denetim. Bu kod örneği de sağlayan bir <xref:System.Windows.Forms.Form> sınıfı ve bir `Program` yeni davranışı göstermek için sınıf.  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [ToolStrip denetim mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Nasıl yapılır: bir StatusStrip içinde Spring özelliğini etkileşimli olarak kullanma](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
