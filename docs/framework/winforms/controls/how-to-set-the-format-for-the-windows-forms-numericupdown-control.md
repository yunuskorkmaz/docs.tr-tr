---
title: NumericUpDown denetiminin biçimini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742179"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama
Değerlerin Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminde nasıl görüntüleneceğini yapılandırabilirsiniz. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliği, ondalık ayırıcıdan sonra kaç sayının görüneceğini belirler; Varsayılan değer 0 ' dır. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliği, her üç ondalık basamak arasına bir ayırıcının eklenip eklenmeyeceğini belirler; Varsayılan değer `false`. <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliği `true`olarak ayarlandıysa, denetim değeri onlu biçim yerine onaltılık olarak görüntüleyebilir. Varsayılan değer `false`.  
  
### <a name="to-format-the-numeric-value"></a>Sayısal değeri biçimlendirmek için  
  
- <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliğini bir tamsayı olarak ayarlayıp <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliğini `true` veya `false`olarak ayarlayarak ondalık değeri görüntüleyin.  
  
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
  
- <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliğini `true`olarak ayarlayarak onaltılık bir değer görüntüleyin.  
  
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
    > Değer formda onaltılı olarak görüntülense bile, <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği üzerinde gerçekleştirdiğiniz tüm testler, onun ondalık değerini test eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown Denetimi](numericupdown-control-windows-forms.md)
- [NumericUpDown Denetimine Genel Bakış](numericupdown-control-overview-windows-forms.md)
