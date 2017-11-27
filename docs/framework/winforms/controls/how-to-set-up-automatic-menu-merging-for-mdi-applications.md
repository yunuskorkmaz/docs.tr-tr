---
title: "Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e99aed38ed6c3af3424c264631f0eaf27e46af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama
Otomatik bir Çoklu belge arabirimi (MDI) uygulaması birleştirmeyi ayarlamak için aşağıdaki yordamı temel adımları sunar <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Otomatik menü birleştirmeyi ayarlama için  
  
1.  MDI üst formu ayarlayarak oluşturma kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`.  
  
2.  Ekleme bir <xref:System.Windows.Forms.MenuStrip> ayarı MDI için kendi <xref:System.Windows.Forms.Form.MainMenuStrip%2A> özelliğini <xref:System.Windows.Forms.MenuStrip>.  
  
3.  MDI alt formu oluşturma ve ayarlama kendi <xref:System.Windows.Forms.Form.MdiParent%2A> üst formun adını özelliğine.  
  
4.  Ekleme bir <xref:System.Windows.Forms.MenuStrip> MDI alt formu.  
  
5.  Alt formunda <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `false`.  
  
6.  Alt formun için menü öğeleri ekleme <xref:System.Windows.Forms.MenuStrip> üst form birleştirmek istediğiniz <xref:System.Windows.Forms.MenuStrip> alt formu zaman etkinleştirilir.  
  
7.  Kullanım <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> özelliği menüsünde alt form öğelerini <xref:System.Windows.Forms.MenuStrip> üst forma nasıl birleştirecek denetlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip denetimine genel bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
