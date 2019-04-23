---
title: 'Nasıl yapılır: Bir Uygulama için ToolStrip Oluşturucusunu Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 857d5ea3771b098d4edcbd7b24f1e6feaf3ec2cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083082"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Nasıl yapılır: Bir Uygulama için ToolStrip Oluşturucusunu Ayarlama
Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> denetimleri tek tek veya tüm <xref:System.Windows.Forms.ToolStrip> denetimleri, uygulamanızda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için özel Oluşturucu seçmeli olarak uygulamak gösterilmiştir bir <xref:System.Windows.Forms.ToolStrip> denetimi ve bir <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
 Bu kod örneği kullanmak için derlemek ve uygulamayı çalıştırın ve ardından gelen özel Perforator kapsamını seçin <xref:System.Windows.Forms.ComboBox> denetimi. Tıklayın **Uygula** Oluşturucu ayarlamak için.  
  
 Özel menü öğesi işleme görmek için seçin <xref:System.Windows.Forms.MenuStrip> seçeneğini <xref:System.Windows.Forms.ComboBox> tıklayın, Denetim **Uygula**ve ardından açın **dosya** menü öğesi.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Ayarlama <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu tümüne uygulamak için özellik <xref:System.Windows.Forms.ToolStrip> denetimleri, uygulamanızda.  
  
 Ayarlama <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu için bireysel uygulamak için özellik <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
