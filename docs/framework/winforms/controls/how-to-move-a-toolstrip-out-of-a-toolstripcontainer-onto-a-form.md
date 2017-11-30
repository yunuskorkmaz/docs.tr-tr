---
title: "Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02d1e4b105329f3d346168123debbbf73e17b9eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma
Taşımak için aşağıdaki yordamı kullanın bir <xref:System.Windows.Forms.ToolStrip> dışında bir <xref:System.Windows.Forms.ToolStripContainer> forma.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Forma ToolStripContainer dışında bir ToolStrip taşımak için  
  
1.  Seçin <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Kesme <xref:System.Windows.Forms.ToolStrip> göre CTRL + X tuşlarına veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** ve bağlam menüsünden.  
  
3.  Formu seçin.  
  
4.  Yapıştır <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşuna basarak veya seçin **Yapıştır** gelen **Düzenle** menüsü.  
  
5.  Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStrip denetimine genel bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
