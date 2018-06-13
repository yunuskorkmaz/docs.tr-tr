---
title: 'Nasıl yapılır: Bir ToolStrip Denetimi Dışında Hareket Etmek için SEKME tuşunu etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: 0af6c4c308ac1988b5f1babd80897afd5bf6a4d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531221"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Nasıl yapılır: Bir ToolStrip Denetimi Dışında Hareket Etmek için SEKME tuşunu etkinleştirme
İşyeri dışında taşımak için SEKME tuşuna basın kullanıcıya etkinleştirmek için aşağıdaki yordamı kullanın bir <xref:System.Windows.Forms.ToolStrip> sekme sırasında bir sonraki denetime.  
  
 <xref:System.Windows.Forms.ToolStrip> İçin SEKME tuşunu ve ok tuşları select öğeleri ilk tuşuna kabul <xref:System.Windows.Forms.ToolStrip>. Kullanıcı ikinci kez SEKME tuşuna bastığında, kullanıcının bir sonraki denetime sekme sırasını alır.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Kullanıcının bir sonraki denetime dışında bir ToolStrip taşımak için SEKME tuşuna etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.TabStop%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
