---
title: 'Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: a4b6e3bbc0750ba69607b5c0f96bdbb542aea1be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529404"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma
Taşımak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> dışı bir <xref:System.Windows.Forms.ToolStripContainer> forma.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Bir ToolStrip forma ToolStripContainer dışına taşımak için  
  
1.  Seçin <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Kes <xref:System.Windows.Forms.ToolStrip> göre CTRL + X basarak veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** bağlam menüsünden.  
  
3.  Formu seçin.  
  
4.  Yapıştırma <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşlarına veya tercih **Yapıştır** gelen **Düzenle** menüsü.  
  
5.  Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
