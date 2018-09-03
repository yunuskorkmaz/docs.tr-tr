---
title: 'Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 10799ad4db103fb50a25e600418fb8b5003c24ea
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486062"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma
Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> kendi sınıfından türetilen yazarak bir profesyonel görünümünü ve davranışını (Görünüm) denetimleri <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.  
  
 Visual Studio'da bu özellik için kapsamlı desteği yoktur.  
  
 Bkz: [izlenecek yol: profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStrip> taklit eden bir bileşik denetim oluşturmak için denetimleri **Gezinti bölmesinde** Microsoft Outlook® tarafından sağlanan.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [izlenecek yol: bir profesyonel stilde ToolStrip denetimi oluşturma](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
