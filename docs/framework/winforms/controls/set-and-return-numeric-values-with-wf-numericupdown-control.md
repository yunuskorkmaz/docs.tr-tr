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
ms.openlocfilehash: 3da2c7b057732e9b2db5e048dec037e4e9910c0a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625741"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetimi ile Sayı Değerleri Ayarlama ve Döndürme
Windows Forms sayısal değerini <xref:System.Windows.Forms.NumericUpDown> denetimi tarafından belirlenir, <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği. Herhangi bir özellik olarak ile yalnızca koşullu testler için denetimin değerini yazabilirsiniz. Bir kez <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği, doğrudan bu işlemleri gerçekleştirmek için kod yazarak bunu ayarlayabilirsiniz veya çağırabilirsiniz <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemleri.  
  
### <a name="to-set-the-numeric-value"></a>Sayısal değer ayarlamak için  
  
1. Bir değer atayın <xref:System.Windows.Forms.NumericUpDown.Value%2A> kodda veya Özellikler penceresinde özelliği.  
  
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
  
2. Çağrı <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> veya <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> artırmak veya değer belirtilen miktara göre azaltmak için yöntemi <xref:System.Windows.Forms.NumericUpDown.Increment%2A> özelliği.  
  
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
  
- Erişim <xref:System.Windows.Forms.NumericUpDown.Value%2A> kod özelliği.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [NumericUpDown Denetimi](numericupdown-control-windows-forms.md)
- [NumericUpDown Denetimine Genel Bakış](numericupdown-control-overview-windows-forms.md)
