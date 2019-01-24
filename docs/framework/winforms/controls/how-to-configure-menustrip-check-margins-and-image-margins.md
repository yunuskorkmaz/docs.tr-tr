---
title: 'Nasıl yapılır: Yapılandırma MenuStrip denetim kenar boşluklarını ve görüntü kenar boşluklarını'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
ms.openlocfilehash: 49c228fef387a7c2a18cf8cecd5081e7b5519ab3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530781"
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a>Nasıl yapılır: Yapılandırma MenuStrip denetim kenar boşluklarını ve görüntü kenar boşluklarını
Özelleştirebileceğiniz bir <xref:System.Windows.Forms.MenuStrip> ayarlayarak <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> ve <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> çeşitli birleşimlerini özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ayarlayın ve özelleştirmek gösterilmiştir <xref:System.Windows.Forms.ContextMenuStrip> kenar boşluklarını ve görüntü kenar boşluklarını denetleyin. Yordam için aynı olan bir <xref:System.Windows.Forms.ContextMenuStrip> veya <xref:System.Windows.Forms.MenuStrip>.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
- [Nasıl yapılır: Kenar boşluklarını ve görüntü kenar boşluklarını ContextMenuStrip denetimlerinde denetim etkinleştir](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
