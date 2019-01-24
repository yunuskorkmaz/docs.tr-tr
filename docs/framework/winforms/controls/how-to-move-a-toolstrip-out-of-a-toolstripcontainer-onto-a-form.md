---
title: 'Nasıl yapılır: Bir ToolStrip forma ToolStripContainer taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 4e5c621b9738ce6b5f259425e63a2369556c4ded
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597727"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Nasıl yapılır: Bir ToolStrip forma ToolStripContainer taşıma
Taşımak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> dışı bir <xref:System.Windows.Forms.ToolStripContainer> forma.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Bir ToolStrip forma ToolStripContainer dışına taşımak için  
  
1.  Seçin <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Kes <xref:System.Windows.Forms.ToolStrip> göre CTRL + X basarak veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** bağlam menüsünden.  
  
3.  Formu seçin.  
  
4.  Yapıştırma <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşlarına veya tercih **Yapıştır** gelen **Düzenle** menüsü.  
  
5.  Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
