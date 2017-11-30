---
title: "Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6f0dcfd24414ef868a1a5414af4fcde1b9a14ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma
Örnek metin özel çizim gösterir bir <xref:System.Windows.Forms.ComboBox> denetim. Bir öğe belirli bir ölçütü karşıladığında büyük yazı tipiyle çizilmiş ve kırmızı açık.  
  
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
  
-   A <xref:System.Windows.Forms.ComboBox> adlı Denetim `ListBox1` üç öğelerle <xref:System.Windows.Forms.ComboBox.Items%2A> özelliği. Bu örnekte, üç öğe adlı `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Özelliği `ComboBox1` ayarlanmalıdır <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Bu teknik da geçerlidir <xref:System.Windows.Forms.ListBox> denetim — yerine, bir <xref:System.Windows.Forms.ListBox> için <xref:System.Windows.Forms.ComboBox>.  
  
-   Başvurular <xref:System.Windows.Forms?displayProperty=nameWithType> ve <xref:System.Drawing?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [Yerleşik sahip çizimi destekli denetimler](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [ListBox denetimi](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [ComboBox denetimi](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
