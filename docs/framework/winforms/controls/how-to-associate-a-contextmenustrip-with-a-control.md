---
title: "Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 7776a5e5ed6e650aad82f7863a7fa1748006b3bc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421235"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme
Denetimleri ve kısayol menüleri oluşturduktan sonra kullanıcı denetimi tıklattığında verilen kısayol menüsünü görüntülemek için aşağıdaki yordamları kullanın. Bu yordamlar ilişkilendirmek bir <xref:System.Windows.Forms.ContextMenuStrip> ve bir Windows formu ile bir <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Contextmenustrip'ni bir Windows formu ile ilişkilendirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliğini ilişkili adı <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Contextmenustrip'ni bir ToolStrip denetimi ile ilişkilendirmek için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliğini ilişkili adı <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir Windows formu oluşturur ve bir <xref:System.Windows.Forms.ToolStrip>ve farklı bir ilişkilendirir <xref:System.Windows.Forms.ContextMenuStrip> denetimi ile bunların her biri.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Nasıl yapılır: Bir ContextMenuStrip'e Menü Öğeleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [ContextMenuStrip Denetimi](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
