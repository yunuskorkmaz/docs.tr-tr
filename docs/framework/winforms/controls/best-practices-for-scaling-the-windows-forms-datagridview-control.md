---
title: Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 895dd132c070157355c28a935e43240f2750159e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57706423"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler
<xref:System.Windows.Forms.DataGridView> Denetimi en fazla ölçekleme sağlamak için tasarlanmıştır. Büyük miktarlarda veri görüntülemek gerekiyorsa, büyük miktarlarda bellek tüketen veya kullanıcı arabirimi (UI) yanıt verme hızını önemli önlemek için bu konuda açıklanan yönergeleri izlemelisiniz. Bu konuda aşağıdaki sorunlar ele alınmıştır:  
  
-   Hücre stilleri verimli şekilde kullanma  
  
-   Kısayol menüleri verimli şekilde kullanma  
  
-   Otomatik boyutlandırma verimli bir şekilde kullanma  
  
-   Seçili hücreler, satırlar ve sütunlarla koleksiyonları verimli şekilde kullanma  
  
-   Paylaşılan satırlar kullanma  
  
-   Paylaşımı kaldırılabilir hale satırları önleme  
  
 Özel performans gereksinimleriniz varsa, sanal modu uygulama ve kendi veri yönetimi işlemleri sağlar. Daha fazla bilgi için [Windows Forms DataGridView denetiminde veri görüntüleme modları](data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Hücre stilleri verimli şekilde kullanma  
 Kendi stil bilgilerini, her bir hücre, satır ve sütun olabilir. Stil bilgilerini depolanan <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri. Hücre birçok kişiye ait stili nesneleri oluşturma <xref:System.Windows.Forms.DataGridView> özellikle büyük miktarlarda veri ile çalışırken öğeleri verimsiz olabilir. Performansı etkilemelerini önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Tek tek hücre stil özelliklerini ayarlamaktan kaçının <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewRow> nesneleri. Bu tarafından belirtilen satır nesneyi içeren <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği. Satır şablondan klonlanmış her yeni satır şablonun hücre stil nesnesinin kendine ait kopyasını alır. En yüksek ölçeklenebilirlik için hücre stil özelliklerini ayarlama <xref:System.Windows.Forms.DataGridView> düzeyi. Örneğin, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği.  
  
-   Bazı hücreler varsayılan biçimlendirme dışında biçimlendirme gerektiriyorsa, aynı kullanın <xref:System.Windows.Forms.DataGridViewCellStyle> hücre, satır veya sütun grupları arasında örneği. Doğrudan türünün özelliklerini ayarlamaktan kaçının <xref:System.Windows.Forms.DataGridViewCellStyle> tek tek hücreler, satırlar ve sütunlarla üzerinde. Hücre stili paylaşımı ilişkin bir örnek için bkz [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Bir performans cezası hücre stilleri ayrı olarak işleyerek ayarlarken kaçınabilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> olay işleyicisi. Bir örnek için bkz [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Bir hücrenin stili belirlerken kullanın <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği. Erişim <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği, yeni bir örneğini oluşturur <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği zaten kullanımda değilse sınıfı. Ayrıca, bazı stilleri satır, sütun veya denetim devralınırsa, bu nesne hücre için tam stil bilgileri içermeyebilir. Hücre stili devralma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimindeki hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Kısayol menüleri verimli şekilde kullanma  
 Her bir hücre, satır ve sütun kısayol menüsünü olabilir. Kısayol menülerinde <xref:System.Windows.Forms.DataGridView> denetimi tarafından temsil edilir <xref:System.Windows.Forms.ContextMenuStrip> kontrol eder. Yalnızca nesnelerle hücre stili gibi çok sayıda kullanıcı için kısayol menüleri oluşturma <xref:System.Windows.Forms.DataGridView> öğeleri performansı olumsuz etkileyecektir. Bu cezasını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Tek tek hücrelere ve satır için kısayol menüleri oluşturmaktan kaçının. Bu denetim için yeni satır eklendiğinde yanı sıra, kısayol menüsünü kopyalanan satır şablonunu içerir. En yüksek ölçeklenebilirlik için yalnızca denetimin kullanın <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> eksiksiz bir denetim için tek bir kısayol menüsü belirtmek için özellik.  
  
-   Birden çok satır veya hücre birden çok kısayol menüleri gerekiyorsa, tanıtıcı <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> veya <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> olayları. Bu olaylar kısayol menüsünde nesneleri yönetmenize olanak sağlayan kendiniz performansını ayarlama etmenize imkan sağlar.  
  
## <a name="using-automatic-resizing-efficiently"></a>Otomatik boyutlandırma verimli bir şekilde kullanma  
 Böylece tüm hücre içeriğini kırpma olmadan görüntülenir satırlar, sütunlar ve üst bilgileri hücre içerik değiştikçe otomatik olarak boyutlandırılabilir. Boyutlandırma modlarını değiştirmek, ayrıca satırları, sütunları ve üst bilgileri boyutlandırabilirsiniz. Doğru boyutta belirlemek için <xref:System.Windows.Forms.DataGridView> denetimini barındırmak gereken her bir hücre değerini inceleyin. Otomatik yeniden boyutlandırma oluştuğunda büyük veri kümeleriyle çalışırken, bu analiz denetim performansını olumsuz yönde etkileyebilir. Performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Üzerinde otomatik boyutlandırma kullanmaktan kaçının bir <xref:System.Windows.Forms.DataGridView> büyük bir satır kümesi denetimi. Otomatik boyutlandırma, yalnızca görüntülenen satırları temel alarak boyutlandırma kullanıyorsanız. Yalnızca görüntülenen satır de sanal modu kullanın.  
  
    -   Satırları ve sütunları için kullanmak `DisplayedCells` veya `DisplayedCellsExceptHeaders` alanını <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, ve <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> numaralandırma.  
  
    -   Satır üst bilgileri için kullanmak <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> veya <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> alanını <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> sabit listesi.  
  
-   En yüksek ölçeklenebilirlik için otomatik boyutlandırmayı kapatın ve yeniden boyutlandırma programlı kullanın.  
  
 Daha fazla bilgi için [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Seçili hücre, satır ve sütunları koleksiyonları verimli şekilde kullanma  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Koleksiyon büyük seçimleri verimli bir şekilde gerçekleştirmez. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonları da olabilir verimsiz, ancak daha düşük bir düzeyde için tipik bir hücre birçok daha az satır olduğundan <xref:System.Windows.Forms.DataGridView> denetimi ve satırdan çok daha az sütun. Bu koleksiyonlar ile çalışırken, performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Belirlemek için olup olmadığını tüm hücreleri <xref:System.Windows.Forms.DataGridView> içeriğine erişmek için önce seçilen <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonu, dönüş değeri denetleyin <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemi. Ancak, bu yöntem paylaşılmayan olacak satırları neden olabileceğini unutmayın. Daha fazla bilgi için sonraki bölüme bakın.  
  
-   Kullanmaktan kaçının <xref:System.Collections.ICollection.Count%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> seçilen hücre sayısını belirlemek için. Bunun yerine, <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> yöntemi ve geçişinde <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> değeri. Benzer şekilde, kullanmak <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> seçilen satır ve sütun koleksiyonlar erişmek yerine seçilen öğelerin sayısını belirlemek için yöntemleri.  
  
-   Hücre tabanlı seçim modları kaçının. Bunun yerine, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Kullanılarak paylaşılan satırlar  
 Verimli bellek kullanımı gerçekleştirilir <xref:System.Windows.Forms.DataGridView> denetim aracılığıyla paylaşılan satırlar. Satır kadar bilgileri paylaşabilir, Görünüm ve davranışlarını hakkında mümkün olduğunca örneklerini paylaşarak <xref:System.Windows.Forms.DataGridViewRow> sınıfı.  
  
 Satır örnekleri paylaşımı bellek kaydeder, ancak satır kolayca paylaşılmayan olabilir. Örneğin, bir kullanıcı bir hücreye ile doğrudan etkileşim her satırına paylaşılmayan haline gelir. Bu kaçınılmaz sağladığından, çok büyük miktarda veriyle çalışırken ve kullanıcıların verileri görece küçük bir kısmıyla programınız her çalıştırdığınızda yalnızca yararlanacak bu konudaki yönergeleri daha kullanışlıdır.  
  
 Bir satır paylaşılan bir bağlantısız içinde <xref:System.Windows.Forms.DataGridView> hücrelerinden birini değerler içeriyorsa, denetim. Zaman <xref:System.Windows.Forms.DataGridView> denetimin bir dış veri kaynağına bağlı veya sanal modu uygulama ve kendi veri kaynağı, hücre değerlerinin hücre nesne satırları paylaşılmasına izin vererek, denetimin dışında kalan yerine depolanır.  
  
 Satır nesnesi, yalnızca tüm hücreleri durumunu durumu satır ve hücre içeren sütunları durumlarını belirlenemezse paylaşılabilir. Böylece artık, satır ve sütun durumundan çıkarılabildiği hücre durumunu değiştirirseniz satır paylaşılamaz.  
  
 Örneğin, bir satır aşağıdaki durumlarda hiçbirinde paylaşılamaz:  
  
-   Seçili sütundaki değil tek bir seçili hücrenin satır içerir.  
  
-   Satır içeren bir hücreye içerir, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> veya <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> özellikleri kümesi.  
  
-   Satır içeren bir <xref:System.Windows.Forms.DataGridViewComboBoxCell> ile kendi <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> özellik kümesi.  
  
 Bağlı mod veya sanal modu, araç ipuçları ve kısayol menüleri için tek tek hücrelere işleyerek sağlayabilir <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ve <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> olayları.  
  
 <xref:System.Windows.Forms.DataGridView> Denetim satırlar eklenen her paylaşılan satırlar kullanmak otomatik olarak deneyecek <xref:System.Windows.Forms.DataGridViewRowCollection>. Satırları paylaşılır emin olmak için aşağıdaki yönergeleri kullanın:  
  
-   Çağırmaktan kaçınmanız `Add(Object[])` aşırı yükünü <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi ve `Insert(Object[])` aşırı yükünü <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu. Bu aşırı yüklemeler, otomatik olarak paylaşılmayan satırları oluşturun.  
  
-   Belirtilen satır olduğundan emin olun <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliği aşağıdaki durumlarda paylaşılabilir:  
  
    -   Çağrılırken `Add()` veya `Add(Int32)` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi veya `Insert(Int32,Int32)` aşırı yükünü <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu.  
  
    -   Zaman değerini artırmayı <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> özelliği.  
  
    -   Ayarlarken <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> özelliği.  
  
-   Tarafından belirtilen satır olduğundan emin olun `indexSource` çağırırken parametre paylaşılabilir <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, ve <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> yöntemlerinin <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu.  
  
-   Çağrılırken belirtilen satır veya satır paylaşılabilir mutlaka `Add(DataGridViewRow)` aşırı yükünü <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> yöntemi `Insert(Int32,DataGridViewRow)` aşırı yükünü <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi ve <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> yöntemi<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>koleksiyonu.  
  
 Bir satır paylaştırılmış olup olmadığını belirlemek için <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> satır nesnesini almak ve sonra nesnenin denetleyin yöntemi <xref:System.Windows.Forms.DataGridViewBand.Index%2A> özelliği. Paylaşılan satırlar her zaman sahip bir <xref:System.Windows.Forms.DataGridViewBand.Index%2A> – 1 özellik değeri.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Paylaşımı kaldırılabilir hale satırları önleme  
 Paylaşılan satırlar, kod veya kullanıcı eylemi sonucunda paylaşılmayan olabilir. Performansı etkilemelerini önlemek için paylaşılmayan olacak satırları neden kaçınmanız gerekir. Uygulama geliştirme sırasında işleyebilirsiniz <xref:System.Windows.Forms.DataGridView.RowUnshared> satırları paylaşılmayan duruma ne zaman belirlemek için olay. Bu, satır paylaşma sorunlarda hata ayıklaması kullanışlıdır.  
  
 Satırları paylaşımı kaldırılabilir haline gelmesini önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Dizin oluşturma önlemek <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu veya onunla üzerinden yineleme bir `foreach` döngü. Genellikle doğrudan satırlarına erişmesi gerekmez. <xref:System.Windows.Forms.DataGridView> satırlarda çalışan yöntemleri satır örnekleri yerine satır dizini bağımsız değişkenleri alır. Ayrıca, satır ile ilgili olayları için işleyiciler olay bağımsız değişkeni nesneleri paylaşılmayan vermemesine neden olmadan satırları yönlendirme için kullanabileceğiniz satır özellikleri alır.  
  
-   Bir satırda nesneye erişmek ihtiyacınız varsa <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> yöntemi ve sıranın gerçek dizin geçirin. Ancak, bu yöntem kullanılarak alınan bir paylaşılan satır nesnesini değiştirme bu nesne paylaşan tüm satırları değiştireceğini unutmayın. Yeni kayıtlar için satır herhangi bir satır değiştirdiğinizde, etkilenecek değil diğer satırlar ile ancak paylaşılmıyor. Ayrıca, paylaşılan bir satır tarafından temsil edilen farklı satırlar farklı kısayol menüleri olabileceğini unutmayın. Paylaşılan satır örneğinden doğru kısayol menüsünü almak için kullanın <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> yöntemi ve sıranın gerçek dizin geçirin. Paylaşılan sıranın erişim <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> özelliği bunun yerine, -1 paylaşılan satır dizinini kullanır ve doğru kısayol menüsünü almaz.  
  
-   Dizin oluşturma önlemek <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> koleksiyonu. Bir hücre erişim, doğrudan kendi üst satır, yeni bir örnekleme, paylaşılmayan olacak neden olacak <xref:System.Windows.Forms.DataGridViewRow>. Hücre ile ilgili olayları için işleyiciler hücreler, satırlar paylaşılmayan olacak neden olmadan yönetmek için kullanabileceğiniz bir hücre özellikleri ile olay bağımsız değişkeni nesnelerini alır. Ayrıca <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> doğrudan hücre erişmeden geçerli hücre, satır ve sütun dizinleri almak için özellik.  
  
-   Hücre tabanlı seçim modları kaçının. Bu modlardan paylaşılmayan olacak satırları neden. Bunun yerine, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
-   İşlememek <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> olayları. Bu olayları paylaşılmayan olacak satırları neden. Ayrıca, çağırmayın <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> bu olay yöntemleri.  
  
-   Erişim sağlanır <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> koleksiyonu olduğunda <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Bu, tüm seçili satırları paylaşılmayan olacak neden olur.  
  
-   Çağırmayın <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> yöntemi. Bu yöntem paylaşılmayan olacak satırları neden olabilir.  
  
-   Çağırmayın <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> yöntemi zaman <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Bu, tüm satırların paylaşılmayan duruma neden olur.  
  
-   Ayarlı değil <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> veya <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> bir hücreye özelliği `false` kendi sütununda karşılık gelen özelliği ayarlandığında `true`. Bu, tüm satırların paylaşılmayan duruma neden olur.  
  
-   Erişim sağlanır <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> özelliği. Bu, tüm satırların paylaşılmayan duruma neden olur.  
  
-   Çağırmayın `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi. Özel bir karşılaştırıcı ile sıralama, tüm satırların paylaşılmayan duruma neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)
