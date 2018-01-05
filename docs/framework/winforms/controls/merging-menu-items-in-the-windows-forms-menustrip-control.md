---
title: "Windows Forms MenuStrip Denetiminde Menü Öğelerini Birleştirme"
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
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd54855f7ee618915fea4fcb8f465cc8c1a68164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Windows Forms MenuStrip Denetiminde Menü Öğelerini Birleştirme
Bir Çoklu belge arabirimi (MDI) uygulaması varsa, üst formu menüleri menü öğeleri veya alt formun tüm menülerden birleştirebilirsiniz.  
  
 Bu konuda bir MDI uygulamada menü öğelerini birleştirme ile ilişkili temel kavramlarını açıklar.  
  
## <a name="general-concepts"></a>Genel kavramlar  
 Hem hedef hem de kaynak denetimi birleştirme yordamları içerir:  
  
-   Hedef <xref:System.Windows.Forms.MenuStrip> içine, birleştirme menü öğeleri ana veya MDI üst form denetimi.  
  
-   Kaynak <xref:System.Windows.Forms.MenuStrip> hedef menüsüne birleştirmek istediğiniz menü öğeleri içeren MDI alt form denetimi.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Özelliği geçerli MDI başlıkları ile doldurmak, aşağı açılan liste formun MDI üst menü öğesi tanımlar. Genellikle Örneğin, şu anda açık MDI alt öğe listesi **penceresi** menüsü.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Özelliği, menü öğeleri alınması tanımlayan bir <xref:System.Windows.Forms.MenuStrip> MDI alt formu üzerinde.  
  
 Menü öğelerini el ile veya otomatik olarak birleştirebilirsiniz. Her iki yöntem için aynı şekilde menü öğelerini birleştirme, ancak birleştirme bu konunun devamındaki "El ile birleştirme" ve "Otomatik birleştirme" bölümlerde açıklandığı gibi farklı şekilde etkinleştirilir. Otomatik ve el ile birleştirme her birleştirme eylemini İleri birleştirme eylemini etkiler.  
  
 <xref:System.Windows.Forms.MenuStrip>Birleştirme taşır menü öğeleri birinden <xref:System.Windows.Forms.ToolStrip> başka bir durum haliyle yerine bunları kopyalama <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>MergeAction değerleri  
 Kaynak menü öğelerini birleştirme eylemini ayarlayın <xref:System.Windows.Forms.MenuStrip> kullanarak <xref:System.Windows.Forms.MergeAction> özelliği.  
  
 Aşağıdaki tabloda kullanılabilir birleştirme eylemleri seçeneğidir; yani ve tipik kullanımını açıklar.  
  
|MergeAction değeri|Açıklama|Genel kullanım|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Varsayılan) Kaynak öğe hedef öğesi'nin koleksiyonun sonuna ekler.|Program bir bölümü etkinleştirildiğinde menü öğeleri menü sonuna ekleniyor.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Kaynak öğesi tarafından belirtilen konumda hedef öğesi'nin koleksiyonuna ekler <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> kaynak öğede ayarlanan özelliği.|Program bir bölümü etkinleştirildiğinde, Orta veya menü başlangıcını menü öğeleri ekleme.<br /><br /> Varsa değerini <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> aynı olan iki menü öğeleri için bunlar ters sırada eklenir. Ayarlama <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> uygun şekilde özgün sırasını korumak için.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulundu ve kaynak menü öğesi ile eşleşen hedef menü öğesi yerini alır.|Bir hedef menü öğesini farklı bir şey yapan aynı ada bir kaynak menü öğesi değiştiriliyor.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulundu ve ardından tüm açılan öğeleri kaynaktan hedefe ekler.|Menü yapısı oluşturmaya ekler veya bir alt menü öğelerini ekler veya bir menüden menü öğeleri kaldırır. Örneğin, bir menü öğesi bir MDI alt bir ana ekleyebileceğiniz <xref:System.Windows.Forms.MenuStrip> **Kaydet** menüsü.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly>herhangi bir eylemde bulunmadan menü yapısında gezinmeniz olanak tanır. Sonraki öğeleri değerlendirmek için bir yol sağlar.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulundu ve ardından hedef öğeyi kaldırır.|Menü öğesi hedef kaldırma <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>El ile birleştirme  
 Yalnızca <xref:System.Windows.Forms.MenuStrip> denetimleri katılmak otomatik birleştirme. Diğer denetimlerin öğeleri gibi birleştirmek için <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> denetimleri, gerekir birleştirme bunları el ile çağırarak <xref:System.Windows.Forms.ToolStripManager.Merge%2A> ve <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> gerektiği gibi kodunuzda yöntemleri.  
  
## <a name="automatic-merging"></a>Otomatik birleştirme  
 Otomatik MDI uygulamaları için birleştirme kaynak formun etkinleştirerek kullanabilirsiniz. Kullanmak için bir <xref:System.Windows.Forms.MenuStrip> bir MDI uygulamada ayarlanan <xref:System.Windows.Forms.Form.MainMenuStrip%2A> hedef özelliğine <xref:System.Windows.Forms.MenuStrip> kaynak üzerinde gerçekleştirilen eylemler birleştirme böylece <xref:System.Windows.Forms.MenuStrip> hedef yansıtılır <xref:System.Windows.Forms.MenuStrip>.  
  
 Otomatik etkinleştirerek birleştirme tetikleyebilir <xref:System.Windows.Forms.MenuStrip> MDI kaynağı. Etkinleştirme, kaynak üzerinde <xref:System.Windows.Forms.MenuStrip> MDI hedef birleştirilir. Yeni bir form etkin olduğunda, birleştirme son formdaki döndürüldü ve yeni formdaki tetiklendi. Bu davranış ayarlayarak denetleyebilirsiniz <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> her gerektiğinde özelliği <xref:System.Windows.Forms.ToolStripItem>, ayarlayarak <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> her özellik <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip Denetimi](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Nasıl yapılır: MenuStrip ile MDI Pencere Listesi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
