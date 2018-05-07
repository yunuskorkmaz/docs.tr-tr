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
ms.openlocfilehash: acf5967c015d61a0cc148e5cb509a5a7ded2152c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Nasıl yapılır: Özel ToolStripRenderer Uygulama
Görünümünü özelleştirebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> türeyen bir sınıf uygulayarak denetim <xref:System.Windows.Forms.ToolStripRenderer>. Bu size sağlanan görünümü farklı bir görünüm oluşturmak için esneklik <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve <xref:System.Windows.Forms.ToolStripSystemRenderer> sınıfları.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, özel bir uygulamak gösterilmiştir <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu örnekte, `GridStrip` denetimi bir görüntü oluşturmak için bir tablo düzeni döşeme taşımak kullanıcı izin veren bir kayan kutucuğu Bulmacanın uygular. Özel bir <xref:System.Windows.Forms.ToolStrip> denetim düzenler kendi <xref:System.Windows.Forms.ToolStripButton> bir kılavuz düzeni denetimlerinde. Düzen içine bir Sürükle ve bırak işlemi kullanarak bitişik bir kutucuğu kullanıcı kaydırabilirsiniz boş bir hücre içerir. Kullanıcı taşıyabilirsiniz döşeme vurgulanır.  
  
 `GridStripRenderer` Sınıfı özelleştirir üç yönlerini `GridStrip` denetiminin görünüşünü:  
  
-   `GridStrip` Kenarlık  
  
-   <xref:System.Windows.Forms.ToolStripButton> Kenarlık  
  
-   <xref:System.Windows.Forms.ToolStripButton> Görüntü  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
