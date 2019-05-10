---
title: 'Nasıl yapılır: Özel ToolStripRenderer Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: ec74528ecb3d2ca1fca78c3a81e71a0093843b4d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651652"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Nasıl yapılır: Özel ToolStripRenderer Uygulama
Görünümünü özelleştirebileceğiniz bir <xref:System.Windows.Forms.ToolStrip> türetildiği bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer>. Bu size sağlanan görünümü farklı bir görünüm oluşturmak için esneklik <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve <xref:System.Windows.Forms.ToolStripSystemRenderer> sınıfları.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, özel bir uygulama gösterilmektedir <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu örnekte, `GridStrip` kutucukları bir görüntü oluşturmak için bir tablo düzeni taşımak kullanıcı izin veren bir kayan kutucuk Bulmacanın denetimi uygular. Özel bir <xref:System.Windows.Forms.ToolStrip> denetim düzenler, <xref:System.Windows.Forms.ToolStripButton> bir kılavuz düzeni denetimleri. Düzen, bir Sürükle ve bırak işlemi kullanarak bitişik bir kutucuk kullanıcı kaydırabilirsiniz boş bir hücreye içerir. Kullanıcı taşıyabilirsiniz kutucukları vurgulanır.  
  
 `GridStripRenderer` Sınıfı özelleştirir üç yönlerini `GridStrip` denetimin görünümü:  
  
- `GridStrip` Kenarlık  
  
- <xref:System.Windows.Forms.ToolStripButton> Kenarlık  
  
- <xref:System.Windows.Forms.ToolStripButton> Görüntü  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
