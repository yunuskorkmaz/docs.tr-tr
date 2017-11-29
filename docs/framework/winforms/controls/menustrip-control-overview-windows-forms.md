---
title: "MenuStrip Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06cd4e812f4acf546dad577a2e1ddc571281ebe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip Denetimine Genel Bakış (Windows Forms)
Menüleri, ortak bir tema göre gruplandırılmış komutları tutarak kullanıcılarınıza işlevselliği kullanıma sunar.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetim bu Visual Studio ve .NET Framework sürümü için yenidir. Denetimi ile Microsoft Office içinde bulunanlar gibi menüleri kolayca oluşturabilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> Birden çok belge arabirimi (MDI) ve menü birleştirme, araç ipuçları ve taşma denetimi destekler. Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüler ve ayırıcı çubukları ekleyerek kullanılabilirlik ve, menüler okunabilirliğini geliştirebilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.MainMenu> kontrol; ancak, <xref:System.Windows.Forms.MainMenu> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip denetimi kullanmanın yolları  
 Kullanım <xref:System.Windows.Forms.MenuStrip> denetimini:  
  
-   Metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutlarını erişme alternatif modları gibi arabirimi ve yerleşim özellikleri destekleyen yaygın olarak kullanılan menüleri gelişmiş kullanıcı, kolayca özelleştirilmiş oluşturun.  
  
-   Genel Görünümü ve davranışı işletim sisteminin destekler.  
  
-   Tüm kapsayıcıları ve içerilen öğelerin için tutarlı bir şekilde olayları işlemek, diğer denetimler için olayları işlemek aynı şekilde.  
  
 Aşağıdaki tabloda bazı özellikle önemli özelliklerini gösterir <xref:System.Windows.Forms.MenuStrip> ve sınıfları ilişkili.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Alır veya ayarlar <xref:System.Windows.Forms.ToolStripMenuItem> MDI alt formları listesini görüntülemek için kullanılır.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Alır veya ayarlar alt menüler MDI uygulamaları üst menülerde nasıl birleştirilir.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Alır veya MDI uygulamalarında menü içinde birleştirilmiş bir öğenin konumunu ayarlar.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Alır veya formun MDI alt formları için bir kapsayıcı olup olmadığını belirten bir değer ayarlar.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Araç ipuçları için gösterilip gösterilmeyeceğini belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.MenuStrip> taşması işlevselliği destekler.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Alır veya ayarlar ile ilişkili kısayol tuşları <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Alır veya ayarlar kısayol, anahtarları olup olmadığını belirten bir değer ile ilişkili <xref:System.Windows.Forms.ToolStripMenuItem> yanında görüntülenen <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Aşağıdaki tabloda önemli gösterilmektedir <xref:System.Windows.Forms.MenuStrip> Yahoo! companion sınıfları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Görüntülenen seçilebilir bir seçeneği temsil eden bir <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Bir kısayol menüsü temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Kullanıcının kullanıcı tıklattığında görüntülenen bir listeden tek bir öğe seçmesini sağlar bir denetimi temsil eden bir <xref:System.Windows.Forms.ToolStripDropDownButton> ya da daha üst düzey menü öğesi.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Türetilen denetimler için temel işlevleri sağlar <xref:System.Windows.Forms.ToolStripItem> tıklatıldığında açılan öğeleri görüntüleyin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
