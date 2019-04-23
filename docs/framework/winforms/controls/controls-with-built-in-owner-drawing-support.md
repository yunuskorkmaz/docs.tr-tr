---
title: Yerleşik Sahip Çizimi Destekli Denetimler
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: 1807170b2f5df2333ec3b271a11f9b929c1e7993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087189"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Yerleşik Sahip Çizimi Destekli Denetimler
Sahip çizim olarak da bilinen özel çizim olduğundan, Windows Forms içinde belirli denetimlerin görünümünü değiştirmek için kullanılan bir tekniktir.  
  
> [!NOTE]
>  Öğesinden türetilen sınıfları birlikte kullanıldığı senaryolar için bu konudaki "control" sözcüğü kullanılan <xref:System.Windows.Forms.Control> veya <xref:System.ComponentModel.Component>.  
  
 Genellikle, Windows boyama otomatik olarak özellik ayarları gibi kullanarak işler <xref:System.Windows.Forms.Control.BackColor%2A> denetiminin görünümünü belirlemek için. Sahip çizim özelliklerini kullanarak mevcut olmayan öğeleri görünümünü değiştirme boyama işleminin yararlanın. Örneğin, çoğu denetim görüntülenen metnin rengini ayarlamanıza olanak tanıyan, ancak tek bir renge sınırlıdır. Sahip çizim, metnin bir bölümünü siyah ve kırmızı bir bölümü görüntüleme gibi işlemler yapmanıza olanak sağlar.  
  
 Uygulamada, sahip çizim grafik bir form üzerinde çizim benzerdir. Örneğin, grafik yöntemlerini işleyici formun için kullanabileceğinizi <xref:System.Windows.Forms.Control.Paint> benzetmek için olay bir `ListBox` denetimidir, ancak sahip tüm kullanıcı etkileşimi işlemek için kendi kodunuzu yazma. Sahip çizim denetimi içeriğini çizmek için kodunuzu kullanır ancak Aksi takdirde tüm iç özellikleri korur. Her öğesi denetiminde çizin veya diğer yönleri her öğe için varsayılan görünümünü kullanırken her öğe bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Sahip çizim Windows Forms denetimleri  
 Sahip çizim destekleyen denetimleri gerçekleştirmek için genellikle bir özellik kümesi ve bir veya daha fazla olayları işlemek.  
  
 Çoğu denetim çizme, destek sahip bir `OwnerDraw` veya `DrawMode` denetimi, çizim ilgili olay veya olay kendisini boyar oluşturup oluşturmayacağını belirten özellik.  
  
 Sahip olmayan denetimleri bir `OwnerDraw` veya `DrawMode` özelliği `DataGridView` otomatik olarak gerçekleşen çizim olayları sağlayan bir denetimi ve `ToolStrip` kendi bir dış işleme sınıfı kullanılarak çizilir denetimi Çizim ile ilgili olayları.  
  
 Olayları çizim birçok farklı türdeki vardır, ancak tek bir öğe içinde bir denetim çizmek için tipik bir çizim olayı oluşur. Olay işleyicisini alır bir `EventArgs` çizilen öğe hakkında bilgiler içerir ve kullandığınız araçlara nesne çizmek için kullanabilirsiniz. Örneğin, bu nesnenin üst koleksiyon içindeki öğenin dizin numarasını genellikle içerir bir <xref:System.Drawing.Rectangle> belirten öğenin sınırları görüntülemek ve <xref:System.Drawing.Graphics> Boya yöntemleri çağırmak için nesne. Bazı olaylar için `EventArgs` nesne öğesi ve varsayılan olarak arka plan ya da bir odak dikdörtgeni gibi bazı yönlerini öğesi boyamak için çağırabileceğiniz yöntemler hakkında ek bilgi sağlar.  
  
 Sahip tarafından çizilmiş özelleştirmelerinizi içeren yeniden kullanılabilir bir denetim oluşturmak için sahip çizim destekleyen bir denetim sınıfından türeyen yeni bir sınıf oluşturun. Çizim olayları işleme yerine sahip çizimi kodunuzu geçersiz kılmalar için uygun dahil `On` *EventName* yöntemi veya yeni yöntemler. Temel sınıfı çağırın emin `On` *EventName* yöntemini veya yöntemlerini bu durumda kullanıcı denetiminizin sahip çizimi olayları işlemek ve ek özelleştirme sağlayın.  
  
 Tüm .NET Framework sürümlerinde çizim aşağıdaki Windows Forms denetimleri destek sahibi:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (tarafından kullanılan <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Sahip çizim yalnızca aşağıdaki denetimleri desteği [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Sahip çizim ve yeni olan aşağıdaki denetimleri desteği [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Aşağıdaki bölümlerde her bu denetimleri için ek ayrıntılar sağlayın.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox ve ComboBox denetimleri  
 <xref:System.Windows.Forms.ListBox> Ve <xref:System.Windows.Forms.ComboBox> denetimlerini bir boyutu da şirket içinde veya farklı boyutlarda denetimindeki öğeyi çizmek etkinleştirin.  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Forms.CheckedListBox> denetim türetilen <xref:System.Windows.Forms.ListBox> denetimi, bunu desteklemiyor sahip çizimi.  
  
 Her bir öğe aynı boyutta çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ve işleme `DrawItem` olay.  
  
 Başka bir boyutu kullanarak her bir öğeyi çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve her ikisini birden işlemek `MeasureItem` ve `DrawItem` olayları. `MeasureItem` Olayı sağlar, önce bir öğenin boyutunu belirtmek `DrawItem` olayı, o öğe için oluşur.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Nasıl yapılır: Bir ComboBox denetiminde değişken boyutlu metin oluşturma](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem bileşeni  
 <xref:System.Windows.Forms.MenuItem> Bileşenini temsil eder, bir tek menü öğesi bir <xref:System.Windows.Forms.MainMenu> veya <xref:System.Windows.Forms.ContextMenu> bileşeni.  
  
 Çizmek için bir <xref:System.Windows.Forms.MenuItem>ayarlayın, `OwnerDraw` özelliğini `true` ve işlemek, `DrawItem` olay. Önce menü öğesinin boyutunu özelleştirmek için `DrawItem` bir olay oluşursa, öğenin işlemek `MeasureItem` olay.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl Denetimi  
 <xref:System.Windows.Forms.TabControl> Denetim ayrı sekmeler denetimi çizmek sağlar. Sahip çizim yalnızca sekmeler etkiler; <xref:System.Windows.Forms.TabPage> içeriği etkilenmez.  
  
 Her sekme çizim için bir <xref:System.Windows.Forms.TabControl>ayarlayın `DrawMode` özelliğini <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ve işleme `DrawItem` olay. Sekme denetimi görünür olduğunda bu olay her sekme için bir kez gerçekleşir.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip Bileşeni  
 <xref:System.Windows.Forms.ToolTip> Bileşeni tüm araç ipucu görüntülendiğinde çizmek etkinleştirir.  
  
 Çizmek için bir <xref:System.Windows.Forms.ToolTip>ayarlayın, `OwnerDraw` özelliğini `true` ve işlemek, `Draw` olay. Boyutunu özelleştirmek için <xref:System.Windows.Forms.ToolTip> önce `Draw` olay geçildikten tanıtıcı `Popup` olay ve kümesi <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olay işleyicisi özelliği.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView Denetimi  
 <xref:System.Windows.Forms.ListView> , Tek tek öğeleri, alt öğeler ve sütun üst bilgilerini denetimi çizmek denetim olanağı sağlar.  
  
 Sahip çizim denetiminde etkinleştirmek için `OwnerDraw` özelliğini `true`.  
  
 Her öğesi denetiminde çizmek için tanıtıcı `DrawItem` olay.  
  
 Her alt veya sütun başlığı denetimi çizmek için zaman <xref:System.Windows.Forms.ListView.View%2A> özelliği <xref:System.Windows.Forms.View.Details>, tanıtıcı `DrawSubItem` ve `DrawColumnHeader` olayları.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView Denetimi  
 <xref:System.Windows.Forms.TreeView> , Tek tek düğümlere denetimi çizmek denetim olanağı sağlar.  
  
 Yalnızca her bir düğümünde görüntülenen metni çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ve işleme `DrawNode` metnini çizmek için olay.  
  
 Her düğümün tüm öğelerini çizmek için ayarlanmış `DrawMode` özelliğini <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> ve işleme `DrawNode` ihtiyacınız kutuları, artı ve eksi işaretlerine, metni, simgeler denetlemek gibi ve düğümlerini bağlayan satırları hangi öğelerini çizmek için olay.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView Denetimi  
 <xref:System.Windows.Forms.DataGridView> Denetimi denetiminde ayrı hücrelere ve satırları çizmek sağlar.  
  
 Tek tek hücrelere çizmek için tanıtıcı `CellPainting` olay.  
  
 Tek bir satır veya satır öğelerini çizmek için birini veya ikisini birden işlemek `RowPrePaint` ve `RowPostPaint` olayları. `RowPrePaint` Olayı, bir satır hücrelerde boyanır önce oluşur ve `RowPostPaint` olay hücreleri boyanır sonra oluşur. Her iki olayları işleyebilir ve `CellPainting` satır arka plan, tek tek hücrelere ve satır ön plan ayrı olarak boyamak için olay veya burada ihtiyacınız ve varsayılan görüntüyü satırın diğer öğeleri kullanmak belirli özelleştirmeleri sağlayabilir.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip Denetimi  
 <xref:System.Windows.Forms.ToolStrip> ve türetilen denetimler görünümlerini herhangi bir özelliği özelleştirmenize olanak sağlar.  
  
 Özel işleme sağlamak için <xref:System.Windows.Forms.ToolStrip> denetimleri ayarlayın `Renderer` özelliği bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, veya <xref:System.Windows.Forms.ToolStripContentPanel> için bir `ToolStripRenderer` nesnesi ve bir veya daha çok sayıda çizim olaylarının tarafından sağlanan işleme `ToolStripRenderer` sınıfı. Alternatif olarak ayarlanmış bir `Renderer` kendi sınıfının bir örneğini özelliğini türetilen `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, veya <xref:System.Windows.Forms.ToolStripSystemRenderer> uygulayan veya özel geçersiz kılar `On` *EventName* yöntemleri.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu Oluşturma ve](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Nasıl yapılır: Bir ToolStrip denetimini özel olarak çizme](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
