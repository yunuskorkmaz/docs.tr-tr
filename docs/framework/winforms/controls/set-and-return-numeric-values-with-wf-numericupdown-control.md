---
title: NumericUpDown denetimiyle sayısal değerleri ayarlama ve döndürme
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
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743028"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Nasıl yapılır: Windows Forms NumericUpDown Denetimi ile Sayı Değerleri Ayarlama ve Döndürme
Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminin sayısal değeri <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine göre belirlenir. Denetimin değeri için diğer tüm özellikler gibi koşullu testler yazabilirsiniz. <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği ayarlandıktan sonra, bu işlemi gerçekleştirmek için kod yazarak doğrudan ayarlayabilir veya <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemlerini çağırabilirsiniz.  
  
### <a name="to-set-the-numeric-value"></a>Sayısal değeri ayarlamak için  
  
1. Koddaki <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine veya Özellikler penceresi bir değer atayın.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     veya  
  
2. Değeri <xref:System.Windows.Forms.NumericUpDown.Increment%2A> özelliğinde belirtilen miktara göre artırmak veya azaltmak için <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> veya <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemini çağırın.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Sayısal değeri döndürmek için  
  
- Koddaki <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine erişin.  
  
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
