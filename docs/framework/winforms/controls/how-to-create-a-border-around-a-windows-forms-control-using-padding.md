---
title: Doldurma kullanarak denetim etrafında kenarlık oluşturma
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
ms.openlocfilehash: 114186ab5784cf892cb01e9fe2648ce22cecc4b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742192"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Nasıl yapılır: Doldurmayı kullanarak Windows Forms Denetiminin Çevresinde Kenarlık Oluşturma
Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.RichTextBox> denetimi etrafında kenarlık veya anahat oluşturmayı gösterir. Örnek, bir <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Padding> özelliğinin değerini 5 olarak ayarlar ve alt <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlar. <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.RichTextBox> denetiminin etrafında mavi bir kenarlık oluşturan <xref:System.Drawing.Color.Blue%2A>olarak ayarlanmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Padding>
- [Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma](margin-and-padding-in-windows-forms-controls.md)
