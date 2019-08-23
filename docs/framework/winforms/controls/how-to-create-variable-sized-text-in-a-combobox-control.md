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
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914744"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma
Bu örnek, bir <xref:System.Windows.Forms.ComboBox> denetimdeki metnin özel çizimini gösterir. Bir öğe belirli bir ölçütü karşıladığında, daha büyük bir yazı tipiyle çizilir ve kırmızı renkte olur.  
  
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
 Bu örnek şunları gerektirir:  
  
- Bir Windows formu.  
  
- Özelliğindeki üç öğeyle `ListBox1` <xref:System.Windows.Forms.ComboBox> adlıbirdenetim<xref:System.Windows.Forms.ComboBox.Items%2A> . Bu örnekte, üç öğe adlandırılır `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Özelliği`ComboBox1` olarak ayarlanmalıdır<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    > Bu teknik Ayrıca <xref:System.Windows.Forms.ListBox> denetim için de geçerlidir — için <xref:System.Windows.Forms.ComboBox>bir <xref:System.Windows.Forms.ListBox> kullanabilirsiniz.  
  
- <xref:System.Windows.Forms?displayProperty=nameWithType> Ve<xref:System.Drawing?displayProperty=nameWithType> ad alanlarına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Yerleşik Sahip Çizimi Destekli Denetimler](controls-with-built-in-owner-drawing-support.md)
- [ListBox Denetimi](listbox-control-windows-forms.md)
- [ComboBox Denetimi](combobox-control-windows-forms.md)
