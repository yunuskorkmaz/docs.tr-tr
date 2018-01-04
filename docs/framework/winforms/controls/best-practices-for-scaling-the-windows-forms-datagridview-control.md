---
title: "Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd629bd38e08c8d6909ee4ad771f17b1554fc80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler
<xref:System.Windows.Forms.DataGridView> Denetimi en fazla ölçeklenebilirlik sağlamak için tasarlanmıştır. Büyük miktarda veri görüntülemek gerekiyorsa, büyük miktarlarda bellek tüketerek veya kullanıcı arabirimi (UI) yanıtlama düşürmesini önlemek için bu konuda açıklanan yönergeleri izlemelisiniz. Bu konuda aşağıdaki konular açıklanmaktadır:  
  
-   Hücre stilleri verimli şekilde kullanma  
  
-   Kısayol menüleri verimli şekilde kullanma  
  
-   Otomatik boyutlandırma verimli bir şekilde kullanma  
  
-   Seçili hücre, satır ve sütunları koleksiyonlar verimli şekilde kullanma  
  
-   Paylaşılan satırlar kullanma  
  
-   Paylaşımı kaldırılabilir olma satırları önleme  
  
 Özel performans gereksinimlerine varsa, sanal modu uygulama ve kendi veri yönetimi işlemlerini sağlar. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde veri görüntüleme modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Hücre stilleri verimli şekilde kullanma  
 Her bir hücre, satır ve sütun kendi stil bilgilerini olabilir. Stil bilgilerini depolanır <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri. Hücre stili nesneleri için birçok kişi oluşturma <xref:System.Windows.Forms.DataGridView> özellikle büyük miktarlarda veri çalışırken öğeleri verimsiz, olabilir. Bir performans etkisi önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Kişi için hücre stili özelliklerini ayarlamaktan kaçının <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewRow> nesneleri. Bu tarafından belirtilen satır nesnesi içerir <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği. Satır şablondan klonlanmış her yeni satır şablonun hücre stil nesnesinin kendine ait kopyasını alır. En yüksek ölçeklenebilirlik için hücre stil özelliklerini ayarlama <xref:System.Windows.Forms.DataGridView> düzeyi. Örneğin, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği.  
  
-   Bazı hücreler varsayılan biçimlendirme dışında biçimlendirme gerektiriyorsa, aynı kullanmak <xref:System.Windows.Forms.DataGridViewCellStyle> hücre, satır veya sütun grupları arasında örneği. Doğrudan türünün özelliklerini ayarlamaktan kaçının <xref:System.Windows.Forms.DataGridViewCellStyle> tek tek hücrelerini, satırları ve sütunları üzerinde. Hücre stili paylaşımı örneği için bkz: [nasıl yapılır: ayarlama varsayılan hücre stilleri Windows Forms DataGridView denetimi için](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Bir performans cezası hücre stilleri ayrı ayrı işleyerek ayarlarken önleyebilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> olay işleyicisi. Bir örnek için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Bir hücrenin stili belirlerken kullanmak <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> özelliği yerine <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> özelliği. Erişme <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği yeni bir örneğini oluşturur <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği olmayan zaten kullanılıyorsa sınıfı. Ayrıca, bu nesnenin bazı stilleri satır, sütun veya denetim devralınırsa, hücre için tam stil bilgilerini içermeyebilir. Hücre stili devralma hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Kısayol menüleri verimli şekilde kullanma  
 Her bir hücre, satır ve sütun kendi kısayol menüsünü olabilir. Kısayol menüleri <xref:System.Windows.Forms.DataGridView> denetim temsil ettiği <xref:System.Windows.Forms.ContextMenuStrip> kontrol eder. Yalnızca nesnelerle hücre stili gibi çok sayıda kullanıcı için kısayol menüleri oluşturma <xref:System.Windows.Forms.DataGridView> öğeleri performansı olumsuz etkileyecektir. Bu cezasını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Kısayol menüleri tek tek hücre ve satırları oluşturmamaya özen gösterin. Bu yeni satırlar için denetim eklendiğinde yanı sıra kısayol menüsünü klonlanmış satır şablonunu içerir. En yüksek ölçeklenebilirlik için yalnızca denetimin kullanın <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliği tüm denetim tek kısayol menüsünü belirtin.  
  
-   Birden çok satır veya hücre birden çok kısayol menüleri gerektiriyorsa, işleme <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> veya <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> olaylar. Bu olayların kısayol menüsü nesneleri yönetmenize olanak sağlayan kendiniz performansı ayarlamak olanak sağlar.  
  
## <a name="using-automatic-resizing-efficiently"></a>Otomatik boyutlandırma verimli bir şekilde kullanma  
 Böylece hücreleri tüm içeriğini kırpma olmadan görüntülenir satırlar, sütunlar ve üst bilgileri otomatik olarak hücre içerik değiştikçe yeniden boyutlandırılabilir. Boyutlandırma modlarını değiştirme satırlar, sütunlar ve üstbilgileri yeniden boyutlandırabilirsiniz. Doğru boyutunu belirlemek için <xref:System.Windows.Forms.DataGridView> denetimini uyum gereken her bir hücre değerini inceleyin. Otomatik boyutlandırma oluştuğunda büyük veri kümeleri ile çalışırken, bu çözümleme denetim performansını olumsuz yönde etkileyebilir. Performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Otomatik boyutlandırma üzerinde kullanmaktan kaçının bir <xref:System.Windows.Forms.DataGridView> büyük bir satır kümesi denetimi. Otomatik boyutlandırma, yalnızca görüntülenen satırları temel alarak yeniden boyutlandırma kullanıyorsanız. Yalnızca görüntülenen satırları de sanal modunda kullanın.  
  
    -   Satırları ve sütunları için kullanmak `DisplayedCells` veya `DisplayedCellsExceptHeaders` alanını <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, ve <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> numaralandırmalar.  
  
    -   Satır başlıklarının kullanmak <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> veya <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> alanını <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> numaralandırması.  
  
-   En yüksek ölçeklenebilirlik için otomatik boyutlandırmayı kapatın ve yeniden boyutlandırma programlı kullanın.  
  
 Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Seçili hücre, satır ve sütunları koleksiyonları verimli şekilde kullanma  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Koleksiyonu büyük seçimlerinde verimli bir şekilde gerçekleştirmez. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonları da verimsiz olmasına neden olabilir, ancak daha düşük bir derecede tipik bir hücre sayısından daha az satır sayısını olduğundan <xref:System.Windows.Forms.DataGridView> denetimi ve çok daha az sütun satırdan. Bu koleksiyonlar ile çalışırken, performans cezalarını önlemek için aşağıdaki yönergeleri kullanın:  
  
-   Belirlemek için olup olmadığını tüm hücreleri <xref:System.Windows.Forms.DataGridView> içeriğine erişmek önce seçili <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonu, dönüş değerini denetlemek <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemi. Ancak, bu yöntem paylaşılmayan olmasını satırları neden olabileceğini unutmayın. Daha fazla bilgi için sonraki bölüme bakın.  
  
-   Kullanmaktan kaçının <xref:System.Collections.ICollection.Count%2A> özelliği <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> seçili hücre sayısını belirlemek için. Bunun yerine, kullanın <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> yöntemi ve geçişinde <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> değeri. Benzer şekilde, kullanın <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> seçilen satır ve sütun koleksiyonlar erişme yerine seçilen öğelerin sayısını belirlemek için yöntem.  
  
-   Hücre tabanlı seçim modları kaçının. Bunun yerine, ayarlamak <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Paylaşılan satırlar kullanma  
 Verimli bellek kullanımı gerçekleştirilir <xref:System.Windows.Forms.DataGridView> denetimi aracılığıyla paylaşılan satırlar. Satır paylaşır, Görünüm ve davranış hakkında kadar bilgi mümkün olduğunca örneklerini paylaşarak <xref:System.Windows.Forms.DataGridViewRow> sınıfı.  
  
 Satır örnekleri paylaşımı bellekten tasarruf sırada satırları kolayca paylaşılmayan olabilir. Örneğin, bir kullanıcı bir hücreye ile doğrudan etkileşim olduğunda, kendi satır paylaşılmayan olur. Bu kaçınılmaz olduğundan, yalnızca çok büyük miktarda veri çalışırken ve yalnızca kullanıcıların veri görece küçük bir bölümünü programınızı her çalıştırıldığında etkileşime gireceğini olduğunda bu konudaki yönergeleri daha kullanışlıdır.  
  
 Bir satır paylaşılan bir ilişkisiz içinde <xref:System.Windows.Forms.DataGridView> hücrelerinden birini değerler içeriyorsa, denetim. Zaman <xref:System.Windows.Forms.DataGridView> denetim için dış veri kaynağına bağlı veya sanal modu uygulama ve kendi veri kaynağı sağlamak, hücre değerlerini satırları paylaşılmasına izin vererek, hücre nesne yerine denetimi dışında kalan depolanır.  
  
 Satır nesnesi, yalnızca tüm hücreleri durumunu satır durumunu ve hücreler içeren sütunlar durumlarını belirlediyseniz, paylaşılabilir. Böylece, artık satır ve sütun durumundan anlaşılan bir hücre durumunu değiştirirseniz, satır paylaşılamaz.  
  
 Örneğin, bir satır aşağıdaki durumların herhangi birinde paylaşılamaz:  
  
-   Seçili sütundaki değil tek bir seçili hücre satır içerir.  
  
-   Bir hücrenin satır içerir, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> veya <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> özelliklerini ayarla.  
  
-   Satır içeren bir <xref:System.Windows.Forms.DataGridViewComboBoxCell> ile kendi <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> özellik kümesi.  
  
 İlişkili modunda veya sanal modunda araç ipuçları ve kısayol menüleri tek tek hücresini işleyerek sağlayabilir <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ve <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> olaylar.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi her satır için eklendiklerinde paylaşılan satırlar kullanmak otomatik olarak başlatacak <xref:System.Windows.Forms.DataGridViewRowCollection>. Satır paylaşılır emin olmak için aşağıdaki kılavuzları kullanın:  
  
-   Arama kaçının `Add(Object[])` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi ve `Insert(Object[])` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu. Bu aşırı paylaşılmayan satırları otomatik olarak oluşturun.  
  
-   Belirtilen satır olduğundan emin olun <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliği aşağıdaki durumlarda paylaşılabilir:  
  
    -   Çağrılırken `Add()` veya `Add(Int32)` , overloads <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi veya `Insert(Int32,Int32)` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu.  
  
    -   Değerini artırmayı zaman <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> özelliği.  
  
    -   Ayarlarken <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> özelliği.  
  
-   Belirtilen satır olduğundan emin olun `indexSource` çağırırken parametre paylaşılabilir <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, ve <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> yöntemlerinin <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> koleksiyonu.  
  
-   Belirtilen satır veya satırları çağrılırken paylaşılabilir emin olun `Add(DataGridViewRow)` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> yöntemi, <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> yöntemi, `Insert(Int32,DataGridViewRow)` , aşırı <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> yöntemi ve <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> yöntemi<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>koleksiyonu.  
  
 Bir satır paylaşılan olup olmadığını belirlemek için <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> satır nesnesini almak ve nesnenin denetlemek için yöntem <xref:System.Windows.Forms.DataGridViewBand.Index%2A> özelliği. Paylaşılan satırlar her zaman sahip bir <xref:System.Windows.Forms.DataGridViewBand.Index%2A> – 1 özellik değeri.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Paylaşımı kaldırılabilir olma satırları önleme  
 Paylaşılan satırlar, kod veya kullanıcı eyleminin sonucu olarak paylaşılmayan olabilir. Bir performans etkisi önlemek için satır paylaşılmayan hale gelmesine neden kaçınmalısınız. Uygulama geliştirme sırasında işleyebilir <xref:System.Windows.Forms.DataGridView.RowUnshared> ne zaman satırları paylaşılmayan kazanacağını belirlemek için olay. Satır paylaşma sorun hata ayıklama durumunda faydalı olur.  
  
 Satır paylaşımı kaldırılabilir haline gelmesini engellemek için aşağıdaki kılavuzları kullanın:  
  
-   Dizin oluşturma kaçının <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu veya onunla üzerinden yineleme bir `foreach` döngü. Genellikle satırları doğrudan erişimi gerekmez. <xref:System.Windows.Forms.DataGridView>satırlarda çalışması yöntemleri satır örnekleri yerine satır dizini bağımsız olur. Ayrıca, satır ile ilgili olayları için işleyiciler olay bağımsız değişkeni nesneleri paylaşılmayan hale gelmesine neden olmadan satırları değiştirmek için kullanabileceğiniz satır özellikleri alır.  
  
-   Satır nesnesi erişmeniz gerekiyorsa kullanın <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> yöntemi ve sıranın gerçek dizin geçirin. Ancak, bu yöntemle alınan paylaşılan satır nesnesi değiştirerek bu nesneyi paylaşmak tüm satırları değiştireceğini unutmayın. Herhangi bir satır değiştirdiğinizde, etkilenmez şekilde yeni kayıtlar için satır diğer satırlar, ancak paylaşılmaz. Ayrıca farklı satırlarla tarafından paylaşılan bir satır temsil farklı kısayol menüleri gerekebileceğini unutmayın. Bir paylaşılan satır örneğinden doğru kısayol menüsünün almak kullanın <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> yöntemi ve sıranın gerçek dizin geçirin. Paylaşılan sıranın erişim <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> özelliği bunun yerine,-1 paylaşılan satır dizini kullanır ve doğru kısayol menüsünü almaz.  
  
-   Dizin oluşturma kaçının <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> koleksiyonu. Bir hücre doğrudan erişimini kendi üst satır, yeni bir örneği, paylaşılmayan hale gelmesine neden olacak <xref:System.Windows.Forms.DataGridViewRow>. Hücre ile ilgili olayları için işleyiciler olay bağımsız değişkeni nesneleri satırları paylaşılmayan hale gelmesine neden olmadan hücreleri değiştirmek için kullanabileceğiniz hücre özellikleri alır. Aynı zamanda <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> hücre doğrudan erişmeden geçerli hücre, satır ve sütun dizinleri almak için özellik.  
  
-   Hücre tabanlı seçim modları kaçının. Bu modların satırları paylaşılmayan hale gelmesine neden. Bunun yerine, ayarlamak <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
-   İşlemini yapmayın <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> olaylar. Bu olayları paylaşılmayan olmasını satırları neden. Ayrıca, çağırmayın <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> bu olayları Yükselt yöntemleri.  
  
-   Değil erişim <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> koleksiyonu olduğunda <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Bu, tüm seçili satırları paylaşılmayan olmasını neden olur.  
  
-   Çağırmayın <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, satır paylaşılmayan hale gelmesine neden olabilir.  
  
-   Çağırmayın <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> yöntemi zaman <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özellik değeri <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Bu paylaşılmayan olacak tüm satırları neden olur.  
  
-   Ayarlamayın <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> veya <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> bir hücreye özelliğinin `false` kendi sütunundaki karşılık gelen özelliği ayarlandığında `true`. Bu paylaşılmayan olacak tüm satırları neden olur.  
  
-   Değil erişim <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> özelliği. Bu paylaşılmayan olacak tüm satırları neden olur.  
  
-   Çağırmayın `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi. Özel bir karşılaştırıcı ile sıralama paylaşılmayan olacak tüm satırları neden olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Sanal Mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
