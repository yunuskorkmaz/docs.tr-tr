---
title: DataGridView denetiminin ölçeklendirilmesi için en iyi uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744128"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler

<xref:System.Windows.Forms.DataGridView> denetimi, en fazla ölçeklenebilirlik sağlamak için tasarlanmıştır. Büyük miktarlarda veri görmeniz gerekiyorsa, büyük miktarlarda bellek tüketmeden veya Kullanıcı arabirimi (UI) yanıt verme süresini düşürmemek için bu konuda açıklanan yönergeleri izlemelisiniz. Bu konuda aşağıdaki sorunlar ele alınmaktadır:

- Hücre stillerini verimli bir şekilde kullanma

- Kısayol menülerini verimli bir şekilde kullanma

- Otomatik yeniden boyutlandırmayı verimli kullanma

- Seçili hücreleri, satırları ve sütun koleksiyonlarını verimli bir şekilde kullanma

- Paylaşılan satırları kullanma

- Satırların paylaşılmayan hale gelmesini önlemek

Özel performans gereksinimleriniz varsa, sanal modu uygulayabilir ve kendi veri yönetimi işlemlerinizi sağlayabilirsiniz. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki veri görüntüleme modları](data-display-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.

## <a name="using-cell-styles-efficiently"></a>Hücre stillerini verimli bir şekilde kullanma

Her bir hücre, satır ve sütun kendi stil bilgisine sahip olabilir. Stil bilgileri <xref:System.Windows.Forms.DataGridViewCellStyle> nesnelerinde depolanır. Birçok bireysel <xref:System.Windows.Forms.DataGridView> öğesi için hücre stili nesneleri oluşturmak, özellikle büyük miktarda verilerle çalışırken verimsiz olabilir. Performans etkisini önlemek için aşağıdaki yönergeleri kullanın:

- Bağımsız <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewRow> nesneleri için hücre stili özellikleri ayarlamaktan kaçının. Bu, <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği tarafından belirtilen satır nesnesini içerir. Satır şablonundan kopyalanan her yeni satır, şablonun hücre stili nesnesinin kendi kopyasını alır. En yüksek ölçeklenebilirlik için <xref:System.Windows.Forms.DataGridView> düzeyinde hücre stili özelliklerini ayarlayın. Örneğin, <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini ayarlayın.

- Bazı hücreler varsayılan biçimlendirme dışında biçimlendirme gerektiriyorsa, hücre, satır veya sütun grupları üzerinde aynı <xref:System.Windows.Forms.DataGridViewCellStyle> örneğini kullanın. Tek tek hücrelerde, satırlarda ve sütunlarda <xref:System.Windows.Forms.DataGridViewCellStyle> türündeki özellikleri doğrudan ayarlamaktan kaçının. Hücre stili paylaşımı örneği için bkz. [nasıl yapılır: Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Ayrıca, <xref:System.Windows.Forms.DataGridView.CellFormatting> olay işleyicisini işleyerek hücre stillerini ayrı olarak ayarlarken bir performans cezasına da kaçınabilirsiniz. Bir örnek için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Bir hücrenin stilini belirlerken, <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> özelliğini kullanın. <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğine erişmek, özelliği zaten kullanılmıyorsa, <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının yeni bir örneğini oluşturur. Ayrıca, bazı stiller satır, sütun veya denetimden devralınmışsa, bu nesne hücrenin tüm stil bilgilerini içermeyebilir. Hücre stili devralma hakkında daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.

## <a name="using-shortcut-menus-efficiently"></a>Kısayol menülerini verimli bir şekilde kullanma

Her bir hücre, satır ve sütun kendi kısayol menüsüne sahip olabilir. <xref:System.Windows.Forms.DataGridView> denetimindeki kısayol menüleri <xref:System.Windows.Forms.ContextMenuStrip> denetimleriyle temsil edilir. Hücre stili nesnelerinde olduğu gibi, birçok ayrı <xref:System.Windows.Forms.DataGridView> öğesi için kısayol menülerinin oluşturulması performansı olumsuz etkiler. Bu ceza olmaması için aşağıdaki yönergeleri kullanın:

- Tek tek hücreler ve satırlar için kısayol menüleri oluşturmaktan kaçının. Bu, denetime yeni satırlar eklendiğinde, onun kısayol menüsüyle birlikte klonlanan satır şablonunu içerir. En yüksek ölçeklenebilirlik için, denetimin tamamı için tek bir kısayol menüsü belirtmek üzere yalnızca denetimin <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliğini kullanın.

- Birden çok satır veya hücre için birden çok kısayol menüsü gerekiyorsa, <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> veya <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> olaylarını işleyin. Bu olaylar, kısayol menü nesnelerini kendi başınıza yönetmenize imkan tanıyarak performansı ayarlamanıza olanak sağlar.

## <a name="using-automatic-resizing-efficiently"></a>Otomatik yeniden boyutlandırmayı verimli kullanma

Hücre içeriğinin tamamının kırpma olmadan gösterilmesi için, satırlar, sütunlar ve üst bilgiler hücre içeriği değiştikçe otomatik olarak yeniden boyutlandırılabilir. Boyutlandırma modlarını değiştirme, satırları, sütunları ve başlıkları da yeniden boyutlandırabilir. Doğru boyutu anlamak için, <xref:System.Windows.Forms.DataGridView> denetimi, gereken her hücrenin değerini incelemektir. Büyük veri kümeleriyle çalışırken, bu analiz otomatik yeniden boyutlandırma gerçekleştiğinde denetimin performansını olumsuz yönde etkileyebilir. Performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:

- Büyük bir satır kümesiyle <xref:System.Windows.Forms.DataGridView> denetiminde otomatik boyutlandırmayı kullanmaktan kaçının. Otomatik boyutlandırma kullanırsanız, yalnızca görüntülenmiş satırlara göre yeniden boyutlandırın. Yalnızca, sanal moddaki yalnızca görüntülenmiş satırları kullanın.

  - Satırlar ve sütunlar için <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>ve <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> Numaralandırmaların `DisplayedCells` veya `DisplayedCellsExceptHeaders` alanını kullanın.

  - Satır üst bilgileri için <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> numaralandırmanın <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> veya <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> alanını kullanın.

- Maksimum ölçeklenebilirlik için otomatik boyutlandırmayı devre dışı bırakın ve programlı yeniden boyutlandırmayı kullanın.

Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)bölümüne bakın.

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Seçili hücreleri, satırları ve sütun koleksiyonlarını verimli bir şekilde kullanma

<xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonu, büyük seçimlerde verimli bir şekilde gerçekleştirmez. Tipik bir <xref:System.Windows.Forms.DataGridView> denetimindeki hücrelerden çok daha az satır olduğundan ve satırlardan çok daha az sütun olduğundan, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonları daha az bir ölçüde verimsiz olabilir. Bu koleksiyonlarla çalışırken performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:

- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonun içeriğine erişmeden önce <xref:System.Windows.Forms.DataGridView> tüm hücrelerin seçili olup olmadığını anlamak için <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yönteminin dönüş değerini denetleyin. Ancak, bu yöntemin satırların paylaşılmayan hale gelmesine neden olabileceğini unutmayın. Daha fazla bilgi için sonraki bölüme bakın.

- Seçilen hücrelerin sayısını öğrenmek için <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> <xref:System.Collections.ICollection.Count%2A> özelliğini kullanmaktan kaçının. Bunun yerine <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> yöntemini kullanın ve <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> değerini geçirin. Benzer şekilde, seçilen satır ve sütun koleksiyonlarına erişmek yerine seçili öğelerin sayısını öğrenmek için <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> yöntemlerini kullanın.

- Hücre tabanlı seçim modlarından kaçının. Bunun yerine, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>olarak ayarlayın.

## <a name="using-shared-rows"></a>Paylaşılan satırları kullanma

Paylaşılan satırlar aracılığıyla <xref:System.Windows.Forms.DataGridView> denetiminde verimli bellek kullanımı elde edilir. Satırlar, <xref:System.Windows.Forms.DataGridViewRow> sınıfının örneklerini paylaşarak, görünümü ve davranışları hakkında çok daha fazla bilgi sağlayacaktır.

Satır örneklerinin paylaşılması belleği kaydetirken, satırlar kolayca paylaşılmayan hale gelebilir. Örneğin, bir Kullanıcı bir hücreyle doğrudan etkileşime geçtiğinde, kendi satırı paylaşılmayan hale gelir. Bu, önlenemez olduğu için, bu konudaki yönergeler yalnızca çok büyük miktarlarda verilerle çalışırken ve yalnızca kullanıcılar, programınızın her çalıştırılışında verilerin görece küçük bir bölümüyle etkileşime gireceğinden faydalıdır.

Herhangi bir hücreden değer içeriyorsa, bir satır ilişkisiz <xref:System.Windows.Forms.DataGridView> denetiminde paylaşılamaz. <xref:System.Windows.Forms.DataGridView> denetimi bir dış veri kaynağına bağlandığında veya sanal modu uyguladığınızda ve kendi veri kaynağınızı sağladığınızda, hücre değerleri hücre nesneleri yerine denetimin dışında saklanır ve satırların paylaşılması sağlanır.

Satır nesnesi yalnızca, tüm hücrelerinin durumu satır durumundan ve hücreleri içeren sütunların durumlarına göre belirlenebilir ise paylaşılabilir. Bir hücrenin durumunu, satır ve sütun durumundan daha fazla çıkarsanmayacak şekilde değiştirirseniz, satır paylaşılamaz.

Örneğin, bir satır aşağıdaki durumların hiçbirinde paylaşılamaz:

- Satır seçili bir sütunda olmayan tek bir seçili hücre içeriyor.

- Satır, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> veya <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> özellikleri ayarlanmış bir hücre içeriyor.

- Satır, <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> özelliği ayarlanmış bir <xref:System.Windows.Forms.DataGridViewComboBoxCell> içeriyor.

Sınırlı mod veya sanal modda, <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ve <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> olaylarını işleyerek tek tek hücreler için araç Ipuçları ve kısayol menüleri sağlayabilirsiniz.

<xref:System.Windows.Forms.DataGridView> denetim, <xref:System.Windows.Forms.DataGridViewRowCollection>satır her eklendiğinde paylaşılan satırları otomatik olarak kullanmayı deneyecektir. Satırların paylaşıldığından emin olmak için aşağıdaki yönergeleri kullanın:

- <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yönteminin `Add(Object[])` aşırı yüklemesini ve <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonunun <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yönteminin `Insert(Object[])` aşırı yüklemesini çağırmaktan kaçının. Bu aşırı yüklemeler, paylaşılmayan satırları otomatik olarak oluşturur.

- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliğinde belirtilen satırın aşağıdaki durumlarda paylaşıldığından emin olun:

  - `Add()` veya <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yönteminin `Add(Int32)` aşırı yüklerini veya <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> koleksiyonunun <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> yönteminin `Insert(Int32,Int32)` aşırı yüklemesini çağırırken.

  - <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> özelliğinin değeri artırıldığında.

  - <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> özelliği ayarlanırken.

- <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> koleksiyonunun <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>ve <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> yöntemleri çağrılırken `indexSource` parametresi tarafından belirtilen satırın paylaşılabilmesi için emin olun.

- <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yönteminin `Add(DataGridViewRow)` aşırı yüklemesi, <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> yöntemi, <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yönteminin `Insert(Int32,DataGridViewRow)` aşırı yüklemesi ve <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> koleksiyonunun <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> yöntemi çağrılırken, belirtilen satır veya satırların paylaşılabilmesi için emin olun.

Bir satırın paylaşılıp paylaşılmadığını anlamak için, satır nesnesini almak için <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> yöntemini kullanın ve ardından nesnenin <xref:System.Windows.Forms.DataGridViewBand.Index%2A> özelliğini kontrol edin. Paylaşılan satırlarda her zaman – 1 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> Özellik değeri vardır.

## <a name="preventing-rows-from-becoming-unshared"></a>Satırların paylaşılmayan hale gelmesini önlemek

Paylaşılan satırlar kod veya kullanıcı eyleminin sonucu olarak paylaşılmayan hale gelebilir. Bir performans etkisini önlemek için, satırların paylaşılmayan hale gelmesine neden olmaması gerekir. Uygulama geliştirme sırasında, satırların ne zaman paylaşılmayan hale geldiğini öğrenmek için <xref:System.Windows.Forms.DataGridView.RowUnshared> olayını işleyebilirsiniz. Bu, satır paylaşma sorunlarını ayıkladığında yararlı olur.

Satırların paylaşılmayan hale gelmesini engellemek için aşağıdaki yönergeleri kullanın:

- <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunun dizinini oluşturmaktan kaçının veya bir `foreach` döngüsü ile yineleme yapın. Genellikle satırlara doğrudan erişmeniz gerekmez. satırlarda çalışan <xref:System.Windows.Forms.DataGridView> Yöntemler satır örnekleri yerine satır dizini bağımsız değişkenlerini alır. Ayrıca, satır ile ilgili olaylar için işleyiciler, satırları paylaşılmayan hale gelmesine neden olmadan satırları işlemek için kullanabileceğiniz satır özelliklerine sahip olay bağımsız değişkeni nesneleri alır.

- Bir satır nesnesine erişmeniz gerekiyorsa <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> yöntemini kullanın ve satırın gerçek dizinini geçirin. Ancak, bu yöntem aracılığıyla alınan bir paylaşılan satır nesnesini değiştirmenin, bu nesneyi paylaşan tüm satırları değiştirecek olduğunu unutmayın. Yeni kayıtlar için satır diğer satırlarla paylaşılmaz, bu nedenle başka bir satırı değiştirdiğinizde bu işlem etkilenmez. Ayrıca, paylaşılan bir satırla temsil edilen farklı satırlarda kısayol menülerinin farklı olabileceğini unutmayın. Paylaşılan bir satır örneğinden doğru kısayol menüsünü almak için <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> yöntemini kullanın ve satırın gerçek dizinini geçirin. Bunun yerine paylaşılan satırın <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> özelliğine eriştiğinizde,-1 ' in paylaşılan satır dizinini kullanır ve doğru kısayol menüsünü almacaktır.

- <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> koleksiyonunun dizinini oluşturmaktan kaçının. Bir hücreye doğrudan erişmek, üst satırının paylaşılmayan olmasına ve yeni bir <xref:System.Windows.Forms.DataGridViewRow>örnekmasına neden olur. Hücreyle ilişkili olaylara yönelik işleyiciler, satır özelliklerine sahip olay bağımsız değişkeni nesnelerini, satırların paylaşılmayan hale gelmesine neden olmadan hücreleri işlemek için kullanabileceğiniz hücre özellikleriyle alırlar. <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> özelliğini, hücreye doğrudan erişmeden geçerli hücrenin satır ve sütun dizinlerini almak için de kullanabilirsiniz.

- Hücre tabanlı seçim modlarından kaçının. Bu modlar, satırların paylaşılmayan hale gelmesine neden olur. Bunun yerine, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>olarak ayarlayın.

- <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> olaylarını işlemez. Bu olaylar, satırların paylaşılmayan hale gelmesine neden olur. Ayrıca, bu olayları oluşturan <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> yöntemlerini çağırmayın.

- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> Özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>olduğunda <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> koleksiyonuna erişmeyin. Bu, tüm seçili satırların paylaşılmayan hale gelmesine neden olur.

- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> yöntemini çağırmayın. Bu yöntem, satırların paylaşılmayan hale gelmesine neden olabilir.

- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> Özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>olduğunda <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> yöntemini çağırmayın. Bu, tüm satırların paylaşılmayan hale gelmesine neden olur.

- Sütunundaki ilgili özellik `true`olarak ayarlandığında, bir hücrenin <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> veya <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> özelliğini `false` olarak ayarlamayın. Bu, tüm satırların paylaşılmayan hale gelmesine neden olur.

- <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> özelliğine erişmeyin. Bu, tüm satırların paylaşılmayan hale gelmesine neden olur.

- <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini çağırmayın. Özel bir karşılaştırıcı ile sıralama tüm satırların paylaşılmayan hale gelmesine neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)
