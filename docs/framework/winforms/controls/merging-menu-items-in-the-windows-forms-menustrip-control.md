---
title: Windows Forms MenuStrip Denetiminde Menü Öğelerini Birleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: dbe1c0325499e7b925d504fc80f9034f9e387475
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231571"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Windows Forms MenuStrip Denetiminde Menü Öğelerini Birleştirme
Çok Belgeli Arabirim (MDI) uygulaması varsa, üst formun menülerle menü öğeleri veya alt formun tamamını menülerden birleştirebilirsiniz.  
  
 Bu konu, bir MDI uygulamasında menü öğelerini birleştirme ile ilgili temel kavramları açıklar.  
  
## <a name="general-concepts"></a>Genel Kavramlar  
 Hem hedef hem de kaynak denetimi birleştirme yordamları içerir:  
  
-   Hedef <xref:System.Windows.Forms.MenuStrip> içine, birleştirme menü öğeleri ana veya MDI üst formu denetimi.  
  
-   Kaynak <xref:System.Windows.Forms.MenuStrip> hedef menüye birleştirmek istediğiniz menü öğeleri içeren MDI alt formu denetimi.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Geçerli MDI başlıkları ile doldurmak, aşağı açılan liste formun MDI üst menü öğesi özelliği tanımlar. Genellikle, üzerinde şu anda açık olan bir MDI alt öğe listesinde **penceresi** menüsü.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Özelliği, menü öğeleri geldiğini tanımlayan bir <xref:System.Windows.Forms.MenuStrip> MDI alt formu üzerinde.  
  
 Menü öğelerini el ile veya otomatik olarak birleştirebilirsiniz. Her iki yöntem de aynı şekilde menü öğelerini birleştirme, ancak birleştirme işlemi bu konunun ilerleyen bölümlerindeki "El ile birleştirme" ve "Otomatik birleştirme" bölümlerde açıklandığı gibi farklı şekilde etkinleştirilir. Otomatik ve el ile birleştirme her birleştirme eylemini sonraki birleştirme eylemi etkiler.  
  
 <xref:System.Windows.Forms.MenuStrip> Birleştirme taşır menü öğelerinin birinden <xref:System.Windows.Forms.ToolStrip> başka bir durum olduğu gibi bunları kopyalama yerine <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>MergeAction değerleri  
 Kaynak menü öğelerini birleştirme eylemini ayarlamak <xref:System.Windows.Forms.MenuStrip> kullanarak <xref:System.Windows.Forms.MergeAction> özelliği.  
  
 Aşağıdaki tabloda kullanılabilir birleştirme eylemleri seçeneğidir; yani ve tipik kullanımını açıklar.  
  
|MergeAction değeri|Açıklama|Genel kullanım|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Varsayılan) Kaynak öğe hedef öğenin koleksiyonun sonuna ekler.|Programın bir kısmını etkinleştirildiğinde menü sonuna menü öğeleri ekleme.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Kaynak öğesi tarafından belirtilen konumda hedef öğenin koleksiyonuna ekler <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> kaynak öğede ayarlanan özelliği.|Programın bir kısmını etkinleştirildiğinde, Orta veya başlangıç menüsünün menü öğeleri ekleme.<br /><br /> Varsa değerini <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> aynı olan iki menü öğeleri için ters sırada eklenir. Ayarlama <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> uygun şekilde özgün sırasını korumak için.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulunursa ve daha sonra kaynak Menü öğesiyle eşleşen hedef menü öğesini değiştirir.|Hedef menü öğesi kaynağı farklı bir şey yapan aynı ada sahip Menü öğesiyle değiştirin.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulunursa ve ardından tüm açılan öğelerin kaynaktan hedef ekler.|Menüsü yapısı oluşturma ekler veya içinde bir alt menüye menü öğeleri ekler veya bir menüden menü öğeleri kaldırır. Örneğin, bir menü öğesi bir MDI alt bir ana ekleyebileceğiniz <xref:System.Windows.Forms.MenuStrip> **Kaydet** menüsü.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> herhangi bir işlem yapmadan menüsü yapısı gitmenizi sağlar. Sonraki öğeleri değerlendirmek için bir yol sunar.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Bir metin eşleşme bulur veya kullanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri metin eşleşme bulunursa ve ardından hedef öğeyi kaldırır.|Bir menü öğesi hedeften kaldırma <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>El ile birleştirme  
 Yalnızca <xref:System.Windows.Forms.MenuStrip> denetimleri katılmak otomatik birleştirme. Diğer denetimlerin öğeleri gibi birleştirmek için <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> denetimleri birleştirmeniz gerekir bunları el ile çağrı yaparak <xref:System.Windows.Forms.ToolStripManager.Merge%2A> ve <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> kodunuzda gerekli olarak yöntemler.  
  
## <a name="automatic-merging"></a>Otomatik birleştirme  
 Otomatik MDI uygulamaları için birleştirme kaynağı formun etkinleştirerek kullanabilirsiniz. Kullanılacak bir <xref:System.Windows.Forms.MenuStrip> bir MDI uygulamasında ayarlamak <xref:System.Windows.Forms.Form.MainMenuStrip%2A> hedef özelliğini <xref:System.Windows.Forms.MenuStrip> böylece kaynak üzerinde gerçekleştirilen eylemler birleştirme <xref:System.Windows.Forms.MenuStrip> hedef yansıtılır <xref:System.Windows.Forms.MenuStrip>.  
  
 Otomatik birleştirme etkinleştirerek tetikleyebilirsiniz <xref:System.Windows.Forms.MenuStrip> MDI kaynak. Etkinleştirme kaynağını bağlı <xref:System.Windows.Forms.MenuStrip> MDI hedef birleştirilir. Yeni bir form etkin olduğunda, birleştirme son formda geri ve yeni bir form üzerinde tetiklenen. Ayarlayarak bu davranışı denetleyebilirsiniz <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> her gerektiğinde özelliği <xref:System.Windows.Forms.ToolStripItem>, ayarlayarak <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> her özellik <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
- [Nasıl yapılır: MenuStrip ile MDI Pencere Listesi Oluşturma](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
