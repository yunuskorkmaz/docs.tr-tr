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
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930187"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Yerleşik Sahip Çizimi Destekli Denetimler
Özel çizim olarak da bilinen Windows Forms sahip çizimi, belirli denetimlerin görsel görünümünü değiştirmek için bir tekniktir.  
  
> [!NOTE]
> Bu konudaki "Control" sözcüğü ya <xref:System.Windows.Forms.Control> <xref:System.ComponentModel.Component>da ' den türetilen sınıfların anlamı için kullanılır.  
  
 Genellikle, Windows, bir denetimin görünüşünü belirleme gibi özellik ayarlarını <xref:System.Windows.Forms.Control.BackColor%2A> kullanarak boyamayı otomatik olarak gerçekleştirir. Sahip çizimi ile boyama işlemini gerçekleştirerek, özellikler kullanılarak kullanılamayan görünüm öğelerini değiştirmiş olursunuz. Örneğin, birçok denetim görüntülenen metnin rengini ayarlamanıza izin verir, ancak tek bir renkle sınırlı olursunuz. Sahip çizimi, metnin bir kısmını siyah ve kırmızı renkte görüntüleme gibi işlemleri yapmanızı sağlar.  
  
 Uygulamada, sahip çizimi, grafikleri bir biçimde çizmekle benzerdir. Örneğin, bir <xref:System.Windows.Forms.Control.Paint> `ListBox` denetime öykünmek için formun olayına yönelik bir işleyicide grafik yöntemlerini kullanabilirsiniz, ancak tüm kullanıcı etkileşimini işlemek için kendi kodunuzu yazmanız gerekir. Sahip çizimi ile denetim, kendi içeriğini çizmek için kodunuzu kullanır, aksi halde tüm iç özelliklerini korur. Her bir öğenin diğer yönleri için varsayılan görünümü kullanırken, denetimdeki her öğeyi çizmek veya her öğenin bazı yönlerini özelleştirmek için grafik yöntemlerini kullanabilirsiniz.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Windows Forms Denetimlerinde sahip çizimi  
 Kendisini destekleyen denetimlerde sahip çizimi gerçekleştirmek için, genellikle bir özellik ayarlarsınız ve bir veya daha fazla olayı idare edersiniz.  
  
 Sahip çizimi destekleyen çoğu denetim, denetimin, `OwnerDraw` kendisini `DrawMode` boyayan çizimle ilgili olay veya olaylarını yapıp oluşturmayacağını belirten bir veya özelliğine sahiptir.  
  
 Veya `OwnerDraw` `DataGridView` `ToolStrip` özelliğine sahip olmayan denetimler, otomatik olarak oluşan çizim olayları ve kendi kendine sahip bir dış işleme sınıfı kullanılarak çizilen denetim gibi bir denetimi içermez. `DrawMode` çizimlerle ilgili olaylar.  
  
 Birçok farklı çizim olayı türü vardır, ancak denetim içinde tek bir öğe çizmek için tipik bir çizim olayı oluşur. Olay işleyicisi, çizmekte `EventArgs` olan öğe ve araç çizmek için kullanabileceğiniz araçlar hakkında bilgi içeren bir nesnesi alır. Örneğin, bu nesne genellikle öğenin kendi üst koleksiyonundaki dizin numarasını, <xref:System.Drawing.Rectangle> öğenin görüntü sınırlarını <xref:System.Drawing.Graphics> ve Paint yöntemlerini çağırmak için bir nesneyi içerir. Bu `EventArgs` nesne, bazı olaylar için, arka plan veya odak dikdörtgeni gibi, varsayılan olarak öğenin bazı yönlerini boyamak için çağırabilmeniz gereken öğe ve yöntemler hakkında ek bilgiler sağlar.  
  
 Sahip tarafından çizilmiş özelleştirmeleri içeren yeniden kullanılabilir bir denetim oluşturmak için, sahip çizimi destekleyen bir denetim sınıfından türetilen yeni bir sınıf oluşturun. Çizim olaylarını işlemek yerine, yeni sınıftaki uygun `On` *EventName* yöntemi veya yöntemleri için sahip çizim kodunuzu geçersiz kılmalara ekleyin. Denetiminizin kullanıcılarının sahip çizim olaylarını işleyebilmesi ve `On`ek özelleştirme sağlaması için bu durumda temel sınıf *EventName* metodunu veya yöntemlerini çağırdığınızdan emin olun.  
  
 Aşağıdaki Windows Forms denetimleri, tüm .NET Framework sürümlerindeki sahip çizimini destekler:  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(ve <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu>tarafından kullanılır)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Aşağıdaki denetimler yalnızca .NET Framework 2,0 ' de sahip çizimi destekler:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Aşağıdaki denetimler sahip çizimi destekler ve .NET Framework 2,0 ' de yenidir:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 Aşağıdaki bölümlerde bu denetimlerin her biri için ek ayrıntılar sağlanmaktadır.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox ve ComboBox denetimleri  
 <xref:System.Windows.Forms.ListBox> Ve<xref:System.Windows.Forms.ComboBox> denetimleri, tek bir boyutta ya da değişen boyutlarda denetimdeki tek tek öğeleri çizmenizi sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.CheckedListBox> Denetim <xref:System.Windows.Forms.ListBox> denetimden türetilse de, sahip çizimi desteklemez.  
  
 Her öğeyi aynı boyutta çizmek için `DrawMode` özelliği olarak <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> ayarlayın ve `DrawItem` olayı işleyin.  
  
 Her bir öğeyi farklı bir boyut kullanarak çizmek `DrawMode` için, özelliğini `MeasureItem` ve olaylarını <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> ve `DrawItem` işlemek için öğesini olarak ayarlayın. Olay, bu öğe için `DrawItem` olay gerçekleşmeden önce bir öğenin boyutunu belirtmenize olanak sağlar. `MeasureItem`  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Nasıl yapılır: ComboBox denetiminde değişken boyutlu metin oluşturma](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem bileşeni  
 Bileşen bir <xref:System.Windows.Forms.MainMenu> veya<xref:System.Windows.Forms.ContextMenu> bileşenindeki tek bir menü öğesini temsil eder. <xref:System.Windows.Forms.MenuItem>  
  
 Bir <xref:System.Windows.Forms.MenuItem>çizmek için, `OwnerDraw` `true`özelliğiniolarak ayarlayın ve olayınıişleyin.`DrawItem` `DrawItem` Olay gerçekleşmeden önce menü öğesinin boyutunu özelleştirmek için, `MeasureItem` öğenin olayını işleyin.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl Denetimi  
 <xref:System.Windows.Forms.TabControl> Denetim, denetimde ayrı sekmeler çizmenizi sağlar. Sahip çizimi yalnızca sekmeleri etkiler; <xref:System.Windows.Forms.TabPage> içerik etkilenmez.  
  
 İçindeki her bir <xref:System.Windows.Forms.TabControl>sekmeyi çizmek için, `DrawMode` `DrawItem` özelliğini olarak <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> ayarlayın ve olayı işleyin. Bu olay, her sekme için yalnızca sekme denetimde görünür olduğunda gerçekleşir.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip Bileşeni  
 <xref:System.Windows.Forms.ToolTip> Bileşeni, görüntülendiğinde araç ipucunun tamamını çizmenizi sağlar.  
  
 Bir <xref:System.Windows.Forms.ToolTip>çizmek için, `OwnerDraw` `true`özelliğiniolarak ayarlayın ve olayınıişleyin.`Draw` Olay gerçekleşmeden <xref:System.Windows.Forms.ToolTip>önceöğesinin boyutunu özelleştirmek için <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> olayıişleyinveolayişleyicisindekiözelliğiayarlayın.`Popup` `Draw`  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView Denetimi  
 <xref:System.Windows.Forms.ListView> Denetim, denetimdeki öğeleri, alt öğeleri ve sütun üstbilgilerini tek tek çizmenizi sağlar.  
  
 Denetimde sahip çizimi etkinleştirmek için `OwnerDraw` özelliğini olarak `true`ayarlayın.  
  
 Denetimdeki her öğeyi çizmek için `DrawItem` olayı işleyin.  
  
 <xref:System.Windows.Forms.ListView.View%2A> Özelliği olarak <xref:System.Windows.Forms.View.Details>ayarlandığında, denetimde her alt öğe veya sütun üstbilgisini çizmek için `DrawSubItem` ve `DrawColumnHeader` olaylarını işleyin.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView Denetimi  
 <xref:System.Windows.Forms.TreeView> Denetim, denetimde tek tek düğümler çizmenizi sağlar.  
  
 Yalnızca her düğümde görüntülenecek metni çizmek için, `DrawMode` özelliğini olarak <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> ayarlayın ve metni çizmek için `DrawNode` olayı işleyin.  
  
 Her bir düğümün tüm öğelerini çizmek için, `DrawMode` <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> özelliği olarak ayarlayın ve istediğiniz öğeleri ( `DrawNode` metin, simgeler, onay kutuları, artı eksi işaretleri ve düğümleri bağlayan çizgiler) çizmek için olayı işleyin.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView Denetimi  
 <xref:System.Windows.Forms.DataGridView> Denetim, denetimde tek tek hücreler ve satırlar çizmenizi sağlar.  
  
 Ayrı hücreler çizmek için `CellPainting` olayı işleyin.  
  
 Tek tek satırları veya satır öğelerini çizmek için `RowPrePaint` ve `RowPostPaint` olaylarını bir veya her ikisini de işleyin. Olay, bir satırdaki hücreler boyanmadan önce oluşur `RowPostPaint` ve bu olay, hücreler boyandıktan sonra gerçekleşir. `RowPrePaint` Satır arka planı, tek tek hücreler `CellPainting` ve satır ön planını ayrı olarak boyamak için hem olayları hem de olayı işleyebilirsiniz veya ihtiyacınız olan özel özelleştirmeler sağlayabilir ve bu, satırın diğer öğeleri için varsayılan ekranı kullanır.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki satırların görünümünü özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip Denetimi  
 <xref:System.Windows.Forms.ToolStrip>ve türetilmiş denetimler, görünüşlerinin herhangi bir yönünü özelleştirmenizi sağlar.  
  
 Denetimler için <xref:System.Windows.Forms.ToolStrip> özel işleme sağlamak üzere, bir <xref:System.Windows.Forms.ToolStripManager> <xref:System.Windows.Forms.ToolStrip> `Renderer` <xref:System.Windows.Forms.ToolStripPanel>,, veya <xref:System.Windows.Forms.ToolStripContentPanel> 'ibirnesnesineayarlayınvebirveyadahafazlaçizimolayınınsağladığı`ToolStripRenderer` `ToolStripRenderer` sınıf. Alternatif olarak, bir `Renderer` özelliği `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>ya <xref:System.Windows.Forms.ToolStripSystemRenderer> da belirli `On`bir *EventName* yöntemini uygulayan veya geçersiz kılan kendi sınıfınızın bir örneğine ayarlayın.  
  
 Kod örnekleri de dahil olmak üzere daha fazla bilgi için aşağıdaki konulara bakın:  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Nasıl yapılır: Windows Forms ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Nasıl yapılır: ToolStrip denetimi özel çizimi](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
