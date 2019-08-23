---
title: 'Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949157"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama
Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminde değerlerin nasıl görüntüleneceğini yapılandırabilirsiniz. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği, ondalık ayırıcıdan sonra kaç sayının görüneceğini belirler; varsayılan değer 0 ' dır. Özelliği, her üç ondalık basamak arasına bir ayırıcının eklenip eklenmeyeceğini belirler; varsayılan değer `false`. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Özelliği `false`olarak `true`ayarlandıysa, denetim değeri ondalık biçimi yerine onaltılı olarak görüntülenebilir; varsayılan değer.  
  
### <a name="to-format-the-numeric-value"></a>Sayısal değeri biçimlendirmek için  
  
- <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği bir tamsayı olarak ayarlayıp veya <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> `true` `false`olarak ayarlayarak ondalık değeri görüntüleyin.  
  
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
  
     -veya-  
  
- <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Özelliğini olarak`true`ayarlayarak onaltılık bir değer görüntüleyin.  
  
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
    > Değer formda onaltılı olarak gösterilse bile, <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği üzerinde gerçekleştirdiğiniz tüm testler, ondalık değerini test eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown Denetimi](numericupdown-control-windows-forms.md)
- [NumericUpDown Denetimine Genel Bakış](numericupdown-control-overview-windows-forms.md)
