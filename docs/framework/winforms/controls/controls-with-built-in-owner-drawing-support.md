---
title: "Yerleşik Sahip Çizimi Destekli Denetimler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd297dcc11005d6b6d47bb9ce3853a757046e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Yerleşik Sahip Çizimi Destekli Denetimler
Sahip çizimi olarak da bilinen özel çizim olduğundan, Windows Forms içinde belirli denetimleri görsel görünümünü değiştirmek için bir tekniktir.  
  
> [!NOTE]
>  Bu konudaki "Denetim" word herhangi birinden türetilen sınıflar anlamına kullanılacak <xref:System.Windows.Forms.Control> veya <xref:System.ComponentModel.Component>.  
  
 Genellikle, Windows boyama otomatik olarak özellik ayarları gibi kullanarak işler <xref:System.Windows.Forms.Control.BackColor%2A> denetiminin görünümünü belirlemek için. Sahip çizimi ile özelliklerini kullanarak kullanılabilir olmayan öğeler görünümünü değiştirme boyama işleminin alın. Örneğin, birçok denetimler görüntülenen metnin rengini ayarlamanıza olanak sağlar, ancak tek bir rengi sınırlı olur. Sahip çizimi metnin bir bölümünü siyah ve kırmızı bölümünde görüntülemek gibi şeyler olanak tanır.  
  
 Uygulamada, grafik bir form üzerinde çizim sahip çizimi benzer. Örneğin, grafik yöntemlerini işleyici formun için kullanabileceğinizi <xref:System.Windows.Forms.Control.Paint> benzetmek için olay bir `ListBox` denetimi, ancak sahip olabilir tüm kullanıcı etkileşimi işlemek için kendi kod yazmak. Çizim sahibi olan denetim içeriğini çizmek için kodunuzu kullanır, ancak Aksi takdirde tüm iç yeteneklerini korur. Her öğe, denetimi çizmek için veya diğer yönlerini her öğe için varsayılan görünümünü kullanırken her öğe bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Sahip çizimi Windows Forms denetimleri  
 Sahip çizimi destekleyen denetimleri gerçekleştirmek için genellikle bir özellik ayarlama ve bir veya daha fazla olayları işlemek.  
  
 Çoğu denetim çizim Bu destek sahip bir `OwnerDraw` veya `DrawMode` denetimi çizim ilgili olay veya kendisi boyar olduğunda olayları oluşturup oluşturmayacağını belirten özellik.  
  
 Olmayan denetimleri bir `OwnerDraw` veya `DrawMode` özelliği `DataGridView` otomatik olarak gerçekleşir çizim olayları sağlar, Denetim ve `ToolStrip` kendi olan bir dış işleme sınıfı kullanılarak çizilip denetimi Çizim ilgili olaylar.  
  
 Olayları çizim birçok farklı türdeki vardır, ancak bir denetim içindeki tek bir öğe çizmek için tipik bir çizim olayı oluşur. Olay işleyicisini alır bir `EventArgs` çizilen öğeyle ilgili bilgiler içeren ve kullandığınız araçlara nesne çizmek için kullanabilirsiniz. Örneğin, bu nesne öğesi'nin dizin numarasını kendi üst koleksiyonundaki genellikle içeren bir <xref:System.Drawing.Rectangle> belirten öğesi'nin sınırları, görüntülemek ve bir <xref:System.Drawing.Graphics> boyama yöntemleri çağırmak için nesne. Bazı olaylar için `EventArgs` nesnesi öğesi ve varsayılan olarak, arka plan veya odak dikdörtgeni gibi bazı yönlerini öğesi boyamak için çağırabilirsiniz yöntemleri hakkında ek bilgi sağlar.  
  
 Sahip tarafından çizilmiş özelleştirmelerinizi içeren yeniden kullanılabilir bir denetim oluşturmak için sahip çizimi destekleyen bir denetim sınıfından türetilen yeni bir sınıf oluşturun. Çizim olayları işleme yerine çizimi kodunuzu geçersiz kılma işlemleri için uygun dahil `On` *EventName* yöntemini veya yöntemlerini Yeni sınıfta. Taban sınıfı çağrı emin olun `On` *EventName* yöntemini veya yöntemlerini bu durumda böylece kullanıcılar denetiminizin çizimi olayları işlemek ve ek özelleştirme sağlar.  
  
 .NET Framework'ün tüm sürümlerinde aşağıdaki Windows Forms denetimleri destek sahip çizimi:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem>(tarafından kullanılan <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Sahip çizimi yalnızca aşağıdaki denetimleri Destek [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Sahip çizimi ve bu yeni aşağıdaki denetimleri Destek [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Aşağıdaki bölümlerde her bu denetimleri için ek ayrıntılar sağlanmaktadır.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox ve ComboBox denetimleri  
 <xref:System.Windows.Forms.ListBox> Ve <xref:System.Windows.Forms.ComboBox> denetimleri ya da tüm bir boyut veya farklı boyutlarda denetiminde ayrı öğeleri Çiz olanak tanır.  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Forms.CheckedListBox> denetim türetilir <xref:System.Windows.Forms.ListBox> denetimi, bunu desteklemiyor sahip çizimi.  
  
 Her bir öğe aynı boyutta çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ve işlemek `DrawItem` olay.  
  
 Farklı bir boyut kullanarak her bir öğeyi çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve her ikisi de işlemek `MeasureItem` ve `DrawItem` olaylar. `MeasureItem` Olayı sağlar, önce bir öğenin boyutunu belirtmek `DrawItem` olayı, o öğe için oluşur.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem bileşeni  
 <xref:System.Windows.Forms.MenuItem> Bileşen bir tek menü öğesini temsil eden bir <xref:System.Windows.Forms.MainMenu> veya <xref:System.Windows.Forms.ContextMenu> bileşeni.  
  
 Çizmek için bir <xref:System.Windows.Forms.MenuItem>ayarlayın, `OwnerDraw` özelliğine `true` ve işlemek kendi `DrawItem` olay. Menü öğesi önce boyutunu özelleştirmek için `DrawItem` olayı oluşur, tanıtıcı öğesi'nin `MeasureItem` olay.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl Denetimi  
 <xref:System.Windows.Forms.TabControl> Denetim tek tek sekmeler denetiminde Çiz olanak sağlar. Sahip çizimi yalnızca sekmeler etkiler; <xref:System.Windows.Forms.TabPage> içeriği etkilenmez.  
  
 Her sekme çizmek için bir <xref:System.Windows.Forms.TabControl>ayarlayın `DrawMode` özelliğine <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ve işlemek `DrawItem` olay. Sekme denetimi görünür olduğunda bu olay her sekme için bir kez oluşur.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip Bileşeni  
 <xref:System.Windows.Forms.ToolTip> Bileşen görüntülendiğinde tüm araç ipucu Çiz olanak sağlar.  
  
 Çizmek için bir <xref:System.Windows.Forms.ToolTip>ayarlayın, `OwnerDraw` özelliğine `true` ve işlemek kendi `Draw` olay. Boyutunu özelleştirmek için <xref:System.Windows.Forms.ToolTip> önce `Draw` olayı oluşur, işleme `Popup` olay ve kümesi <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olay işleyicisi özelliği.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView Denetimi  
 <xref:System.Windows.Forms.ListView> Denetimi tek tek öğe, alt öğeler ve sütun üst bilgileri denetiminde çizmek sağlar.  
  
 Sahip çizimi, denetimi etkinleştirmek için ayarlanmış `OwnerDraw` özelliğine `true`.  
  
 Her öğe, denetimi çizmek için tanıtıcı `DrawItem` olay.  
  
 Her alt veya sütun üstbilgisini denetiminde çizmek için zaman <xref:System.Windows.Forms.ListView.View%2A> özelliği ayarlanmış <xref:System.Windows.Forms.View.Details>, tanıtıcı `DrawSubItem` ve `DrawColumnHeader` olaylar.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView Denetimi  
 <xref:System.Windows.Forms.TreeView> Denetim tek düğümler denetiminde Çiz olanak sağlar.  
  
 Yalnızca her düğümünde görüntülenen metin çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ve işlemek `DrawNode` metnini çizmek için olay.  
  
 Her düğümün tüm öğeleri çizmek için ayarlanmış `DrawMode` özelliğine <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> ve işlemek `DrawNode` ihtiyacınız metni, simgeleri denetlemek kutuları, artı ve eksi işaretlerine, gibi ve düğümlerini bağlayan çizgilerin hangi öğeleri çizmek için olay.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView Denetimi  
 <xref:System.Windows.Forms.DataGridView> Denetim tek tek hücre ve satırları denetiminde Çiz olanak sağlar.  
  
 Tek tek hücreleri çizmek için tanıtıcı `CellPainting` olay.  
  
 Tek tek satır veya satır öğeleri çizmek için aşağıdakilerden birini veya her ikisini de işlemek `RowPrePaint` ve `RowPostPaint` olaylar. `RowPrePaint` Olay, bir satır hücrelerde boyanır önce gerçekleşir ve `RowPostPaint` olay hücreleri boyanır sonra oluşur. Her iki olayları işlemek ve `CellPainting` satır arka plan, tek tek hücreler ve satır ön plan ayrı olarak boyamak için olay veya burada gereksinim ve satır diğer öğeler için varsayılan görüntü kullanmak belirli özelleştirmelere sağlayabilir.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip Denetimi  
 <xref:System.Windows.Forms.ToolStrip>ve türetilen denetimler herhangi bir değişiklik görünümlerini, özelleştirmenize olanak sağlar.  
  
 Özel işleme için sağlamak için <xref:System.Windows.Forms.ToolStrip> denetimler, ayarlayın `Renderer` özelliği bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, veya <xref:System.Windows.Forms.ToolStripContentPanel> için bir `ToolStripRenderer` nesne ve bir veya daha fazla tarafından sağlanan birçok çizim olay işleme `ToolStripRenderer` sınıfı. Alternatif olarak, kümesinin bir `Renderer` kendi sınıfının bir örneği özelliğine türetilen `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, veya <xref:System.Windows.Forms.ToolStripSystemRenderer> uygulayan veya belirli geçersiz kılmaları `On` *EventName* yöntemleri.  
  
 Kod örnekleri dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
