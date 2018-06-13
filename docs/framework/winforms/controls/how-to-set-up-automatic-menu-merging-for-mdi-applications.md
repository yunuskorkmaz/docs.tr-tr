---
title: 'Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533467"
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
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
