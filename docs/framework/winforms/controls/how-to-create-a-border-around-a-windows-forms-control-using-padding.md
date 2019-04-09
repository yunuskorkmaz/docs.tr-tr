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
ms.openlocfilehash: e3bbf43dbe45e675df172a6c3e1db16a3ba9caa8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124035"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Nasıl yapılır: Doldurmayı kullanarak Windows Forms Denetiminin Çevresinde Kenarlık Oluşturma
Aşağıdaki kod örneği, kenarlık oluşturma veya geçici olarak ana hatlarıyla gösterilmiştir bir <xref:System.Windows.Forms.RichTextBox> denetimi. Örnek ayarlar bir <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Padding> 5 ve kümeleri için özellik <xref:System.Windows.Forms.Control.Dock%2A> bir alt özellik <xref:System.Windows.Forms.RichTextBox> denetimi <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> , <xref:System.Windows.Forms.Panel> Denetim ayarı <xref:System.Drawing.Color.Blue%2A>, etrafında mavi bir kenarlık oluşturan <xref:System.Windows.Forms.RichTextBox> denetimi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Padding>
- [Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma](margin-and-padding-in-windows-forms-controls.md)
