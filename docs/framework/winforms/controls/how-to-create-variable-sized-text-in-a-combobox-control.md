---
title: 'Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 9155893b3d47707e0e55ee33e30d7998654f9e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085616"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma
Bu örnek özel çizim metin gösterir bir <xref:System.Windows.Forms.ComboBox> denetimi. Bir öğenin belirli bir ölçütü karşıladığında bir büyük yazı tipiyle çizilmiş ve kırmızı açık.  
  
## <a name="example"></a>Örnek  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows formu.  
  
-   A <xref:System.Windows.Forms.ComboBox> adlı Denetim `ListBox1` üç öğelerle <xref:System.Windows.Forms.ComboBox.Items%2A> özelliği. Bu örnekte, üç öğeye adlandırılır `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Özelliği `ComboBox1` ayarlanmalıdır <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Bu teknik de geçerlidir <xref:System.Windows.Forms.ListBox> denetim — yerini alabilecek bir <xref:System.Windows.Forms.ListBox> için <xref:System.Windows.Forms.ComboBox>.  
  
-   Başvurular <xref:System.Windows.Forms?displayProperty=nameWithType> ve <xref:System.Drawing?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Yerleşik Sahip Çizimi Destekli Denetimler](controls-with-built-in-owner-drawing-support.md)
- [ListBox Denetimi](listbox-control-windows-forms.md)
- [ComboBox Denetimi](combobox-control-windows-forms.md)
