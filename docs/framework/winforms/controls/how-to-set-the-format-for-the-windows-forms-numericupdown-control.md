---
title: "Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama"
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
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 001cc32aa9e1f31695f3b349480b6dd5154b31a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama
Windows Forms'ta değerlerin nasıl görüntüleneceğini yapılandırabilirsiniz <xref:System.Windows.Forms.NumericUpDown> denetim. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği, kaç tane numaraları görünür ondalık ayırıcıdan sonra belirler; varsayılan değer 0'dır. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Özelliği, her üç ondalık basamak arasında bir ayırıcı eklenip eklenmeyeceğini belirler; varsayılan `false`. Denetim değerleri ondalık biçiminde yerine onaltılık görüntüleyebilirsiniz <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliği ayarlanmış `true`; varsayılan `false`.  
  
### <a name="to-format-the-numeric-value"></a>Sayısal değer biçimlendirmek için  
  
-   Ayarlayarak ondalık bir değeri görüntülemek <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliği bir tamsayı ve ayarı için <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliğine `true` veya `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     veya  
  
-   Bir onaltılık değer ayarlayarak görüntüler <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliğine `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  Değeri, onaltılık olarak form üzerinde görüntülenir olsa bile, tüm testler gerçekleştirdiğiniz <xref:System.Windows.Forms.NumericUpDown.Value%2A> özellik ondalık değerini test.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown denetimi](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [NumericUpDown denetimine genel bakış](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
