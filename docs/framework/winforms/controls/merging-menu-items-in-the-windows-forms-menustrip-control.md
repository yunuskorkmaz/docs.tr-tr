---
title: MenuStrip denetiminde menü öğelerini birleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739045"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Windows Forms MenuStrip Denetiminde Menü Öğelerini Birleştirme
Birden çok belgeli arabirim (MDI) uygulamanız varsa, alt formdan menü öğelerini veya tüm menüleri üst formun menülerine birleştirebilirsiniz.  
  
 Bu konu başlığı altında, bir MDI uygulamasındaki menü öğeleriyle birleştirme ile ilişkili temel kavramlar açıklanmaktadır.  
  
## <a name="general-concepts"></a>Genel Kavramlar  
 Yordam birleştirme, hem hedef hem de kaynak denetimi içerir:  
  
- Hedef, menü öğelerini birleştirdiğiniz ana veya MDI üst formundaki <xref:System.Windows.Forms.MenuStrip> denetimidir.  
  
- Kaynak, hedef menüdeki birleştirmek istediğiniz menü öğelerini içeren MDI alt formundaki <xref:System.Windows.Forms.MenuStrip> denetimidir.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği, açılan listesini geçerli MDI üst formunun MDI alt öğelerinin başlıklarıyla dolduramayacağınız menü öğesini tanımlar. Örneğin, genellikle **pencere** menüsünde açık olan MDI alt öğelerini listeleyin.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> özelliği, bir MDI alt formundaki <xref:System.Windows.Forms.MenuStrip> hangi menü öğelerinin gireceğini belirler.  
  
 Menü öğelerini el ile veya otomatik olarak birleştirebilirsiniz. Menü öğeleri her iki yöntem için de aynı şekilde birleştirilir, ancak birleştirme, bu konunun ilerleyen kısımlarında "El Ile birleştirme" ve "otomatik birleştirme" bölümlerinde anlatıldığı şekilde farklı şekilde etkinleştirilir. Hem el ile hem de otomatik birleştirme işleminde, her birleştirme eylemi bir sonraki birleştirme eylemini etkiler.  
  
 <xref:System.Windows.Forms.MenuStrip> birleştirme, menü öğelerini, <xref:System.Windows.Forms.MainMenu>olduğu gibi, kopyalamak yerine bir <xref:System.Windows.Forms.ToolStrip> diğerine taşıdıkça.  
  
## <a name="mergeaction-values"></a>MergeAction değerleri  
 <xref:System.Windows.Forms.MergeAction> özelliğini kullanarak kaynak <xref:System.Windows.Forms.MenuStrip> menü öğelerinde birleştirme eylemini ayarlarsınız.  
  
 Aşağıdaki tabloda, kullanılabilir birleştirme eylemlerinin anlamı ve tipik kullanımı açıklanmaktadır.  
  
|MergeAction değeri|Açıklama|Genel kullanım|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|Varsayılanını Kaynak öğeyi hedef öğenin koleksiyonunun sonuna ekler.|Programın bir kısmı etkinleştirildiğinde menünün sonuna menü öğeleri ekleme.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Kaynak öğeyi, kaynak öğede ayarlanan <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> özelliği tarafından belirtilen konumdaki hedef öğenin koleksiyonuna ekler.|Programın bir kısmı etkinleştirildiğinde menü öğelerini ortasına veya menünün başlangıcına ekleme.<br /><br /> <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri her iki menü öğesi için de aynıysa, bu değerler ters sırada eklenir. Özgün siparişi korumak için uygun şekilde <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> ayarlayın.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Bir metin eşleşmesi bulur veya metin eşleşmesi bulunmazsa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri kullanır ve ardından eşleşen hedef menü öğesini kaynak menü öğesiyle değiştirir.|Hedef menü öğesini, farklı bir şeyi yapan aynı ada sahip bir kaynak menü öğesiyle değiştirme.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Bir metin eşleşmesi bulur veya metin eşleşmesi bulunmazsa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri kullanır ve sonra tüm açılan öğeleri kaynaktan hedefe ekler.|Menü öğelerini bir alt menüye ekleyen veya ekleyen veya alt menüden menü öğelerini kaldıran bir menü yapısı oluşturma. Örneğin, bir MDI alt öğesinden bir menü öğesini ana <xref:System.Windows.Forms.MenuStrip>farklı **Kaydet** menüsüne ekleyebilirsiniz.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly>, herhangi bir eylemde bulunmadan menü yapısında gezinmenizi sağlar. Sonraki öğeleri değerlendirmek için bir yol sağlar.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Metin eşleşmesi bulur veya metin eşleşmesi bulunmazsa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> değeri kullanır ve sonra öğeyi hedeften kaldırır.|Hedef <xref:System.Windows.Forms.MenuStrip>bir menü öğesi kaldırılıyor.|  
  
## <a name="manual-merging"></a>El ile birleştirme  
 Yalnızca <xref:System.Windows.Forms.MenuStrip> denetimleri otomatik birleştirmeye katılır. <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> denetimleri gibi diğer denetimlerin öğelerini birleştirmek için, kodunuzda gereken <xref:System.Windows.Forms.ToolStripManager.Merge%2A> ve <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> yöntemleri çağırarak bunları el ile birleştirmeniz gerekir.  
  
## <a name="automatic-merging"></a>Otomatik birleştirme  
 Kaynak formu etkinleştirerek MDI uygulamaları için otomatik birleştirme kullanabilirsiniz. MDI uygulamasında bir <xref:System.Windows.Forms.MenuStrip> kullanmak için, kaynak <xref:System.Windows.Forms.MenuStrip> üzerinde gerçekleştirilen birleştirme eylemlerinin hedef <xref:System.Windows.Forms.MenuStrip>yansıtılmasını sağlamak üzere <xref:System.Windows.Forms.Form.MainMenuStrip%2A> özelliğini hedef <xref:System.Windows.Forms.MenuStrip> olarak ayarlayın.  
  
 MDI kaynağında <xref:System.Windows.Forms.MenuStrip> etkinleştirerek otomatik birleştirmeyi tetikleyebilirsiniz. Etkinleştirme sonrasında, kaynak <xref:System.Windows.Forms.MenuStrip> MDI hedefi ile birleştirilir. Yeni bir form etkin hale geldiğinde, birleştirme son formdan geri döndürülür ve yeni formda tetiklenir. <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> özelliğini her bir <xref:System.Windows.Forms.ToolStripItem>gerektiği şekilde ayarlayarak ve her bir <xref:System.Windows.Forms.MenuStrip><xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> özelliğini ayarlayarak bu davranışı kontrol edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
- [Nasıl yapılır: MenuStrip ile MDI Pencere Listesi Oluşturma](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
