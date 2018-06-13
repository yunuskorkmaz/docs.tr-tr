---
title: 'Nasıl yapılır: Windows Forms NumericUpDown Denetimi ile Sayı Değerleri Ayarlama ve Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: e214f556224577c3029b2b742784e58932d792f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535567"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetimi ile Sayı Değerleri Ayarlama ve Döndürme
Windows Forms sayısal değerini <xref:System.Windows.Forms.NumericUpDown> denetim belirlenir kendi <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği. Herhangi bir özellik olarak olduğu denetimin değeri için koşullu testleri yazabilirsiniz. Bir kez <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği ayarlanmışsa, doğrudan bu işlemleri gerçekleştirmek için kod yazarak ayarlayabilir veya çağırabilirsiniz <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemleri.  
  
### <a name="to-set-the-numeric-value"></a>Sayısal değer ayarlamak için  
  
1.  Bir değer atadığınız <xref:System.Windows.Forms.NumericUpDown.Value%2A> kodunda ya da özellikleri penceresinde özelliği.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     -veya-  
  
2.  Çağrı <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> veya <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> artırmak veya değer belirtilen miktar azaltmak için yöntemi <xref:System.Windows.Forms.NumericUpDown.Increment%2A> özelliği.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Sayısal değer döndürmek için  
  
-   Erişim <xref:System.Windows.Forms.NumericUpDown.Value%2A> kodda özelliği.  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.NumericUpDown>  
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>  
 [NumericUpDown Denetimi](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [NumericUpDown Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
