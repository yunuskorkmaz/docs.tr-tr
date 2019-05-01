---
title: 'Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 9106a69ea9f28442da6e3270f7cf5abb9374b62d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913665"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma
Taşımak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> dışı bir <xref:System.Windows.Forms.ToolStripContainer> forma.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Bir ToolStrip forma ToolStripContainer dışına taşımak için  
  
1. Seçin <xref:System.Windows.Forms.ToolStrip>.  
  
2. Kes <xref:System.Windows.Forms.ToolStrip> göre CTRL + X basarak veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** bağlam menüsünden.  
  
3. Formu seçin.  
  
4. Yapıştırma <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşlarına veya tercih **Yapıştır** gelen **Düzenle** menüsü.  
  
5. Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
