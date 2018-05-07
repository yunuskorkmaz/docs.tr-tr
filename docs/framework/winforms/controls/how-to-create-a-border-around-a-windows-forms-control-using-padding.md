---
title: 'Nasıl yapılır: Doldurmayı kullanarak Windows Forms Denetiminin Çevresinde Kenarlık Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: 7866b78afd768fa99ceacfdee13c086a9ac00e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Nasıl yapılır: Doldurmayı kullanarak Windows Forms Denetiminin Çevresinde Kenarlık Oluşturma
Aşağıdaki kod örneğinde kenarlık oluşturma veya geçici anahat gösteren bir <xref:System.Windows.Forms.RichTextBox> denetim. Örnek değerini ayarlar bir <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Padding> özelliğini 5 ve ayarlar <xref:System.Windows.Forms.Control.Dock%2A> bir alt özelliği <xref:System.Windows.Forms.RichTextBox> denetimini <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> , <xref:System.Windows.Forms.Panel> Denetim ayarlanmış <xref:System.Drawing.Color.Blue%2A>, mavi kenarlık oluşturur <xref:System.Windows.Forms.RichTextBox> denetim.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Padding>  
 [Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
