---
title: 'Nasıl yapılır: ToolStrip denetimi dışında hareket etmek için SEKME tuşunu etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: e1d7917d7e12ba286e7ddf4e95a68769852a17f7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704342"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Nasıl yapılır: ToolStrip denetimi dışında hareket etmek için SEKME tuşunu etkinleştirme
/ Taşımak için SEKME tuşuna basın kullanıcının etkinleştirmek için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> sonraki denetime sekme sırası.  
  
 <xref:System.Windows.Forms.ToolStrip> SEKME tuşunu ve ok tuşları öğeleri içinde ilk basarak kabul <xref:System.Windows.Forms.ToolStrip>. Kullanıcı ikinci kez TAB tuşuna bastığında, kullanıcının sonraki denetime sekme sırasının alır.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Sonraki denetime bir ToolStrip dışına taşımak için SEKME tuşuna basın kullanıcının etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.TabStop%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
