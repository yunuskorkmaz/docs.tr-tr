---
title: Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b8f6048946d367dd79b1ce0d23d84446ffdb1115
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106672"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
<xref:System.Windows.Forms.DataGridView> Sütun sıralama modları üç sahip. Her bir sütunun sıralama modu aracılığıyla belirtilen <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> aşağıdakilerden birini ayarlanabilir sütunun özelliği <xref:System.Windows.Forms.DataGridViewColumnSortMode> sabit listesi değerleri.  
  
|`DataGridViewColumnSortMode` Değer|Açıklama|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Metin kutusu sütunları için varsayılan. Sütun üst bilgilerini seçimi için kullanılmıyorsa, otomatik olarak sütun başlığına tıklayarak sıralar <xref:System.Windows.Forms.DataGridView> bu sütuna göre sıralama düzenini belirten bir simge görüntüler.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Varsayılan olmayan – metin kutusu sütunlar için. Bu sütun programlamayla sıralama; Sıralama glif boşluk ayrılmış şekilde ancak bu sıralama için tasarlanmamıştır.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Bu sütun programlamayla sıralama ve alan sıralama glif ayrılır.|  
  
 Varsayılan olarak bir sütunun sıralama modu değiştirmek isteyebileceğiniz <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> atayamayacağına sıralanabilir değerler içeriyorsa. Öğesi durumları temsil eden bir sayı içeren bir veritabanı sütunu varsa, örneğin, bu sayıları karşılık gelen simgelerle veritabanı sütunu image sütununa bağlayarak görüntüleyebilirsiniz. Görüntü görüntüleme değerleri için bir işleyici olarak sayısal hücre değerlerini daha sonra değiştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. Bu durumda, ayarı <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> sütunu sırala kullanıcılarınıza olanak tanır. Otomatik sıralama sayılara karşılık gelen durumlar doğal bir dizi yoksa bile aynı duruma sahip grup öğeleri kullanıcılarınıza olanak tanır. Onay kutusu başka bir örnek otomatik sıralama ile aynı duruma içinde öğeleri gruplandırma için kullanışlı olduğu sütunlarıdır.  
  
 Sıralayabilir bir <xref:System.Windows.Forms.DataGridView> program aracılığıyla herhangi bir sütun veya bakılmaksızın birden çok sütun değerleri tarafından <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ayarları. Programlı sıralama, sıralama için kendi kullanıcı arabirimini (UI) sağlamak istediğinizde veya özel sıralama uygulamak istediğinizde yararlı olur. Kendi sıralama kullanıcı Arabirimi yararlıdır sağlanması, örneğin, ayarladığınızda <xref:System.Windows.Forms.DataGridView> sütun üst bilgisi seçimini etkinleştirmek için seçim modu. Sütun başlıkları, sıralama için kullanılamaz ancak bu durumda, yine de ayarlarsınız için uygun sıralama glif görüntülenecek üstbilgileri istiyor <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Programlı sıralama moduna sütunları sıralama glif otomatik olarak görüntülenmez. Bu sütunlar için simge kendiniz ayarlayarak görüntülemelidir <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> özelliği. Özel sıralama esneklik istiyorsanız bu gereklidir. Örneğin, sıralama <xref:System.Windows.Forms.DataGridView> birden çok sütuna göre sıralama birden çok karakter veya hiçbir sıralama glif görüntülemek isteyebilirsiniz.  
  
 Programlamayla sıralama rağmen bir <xref:System.Windows.Forms.DataGridView> herhangi bir sütuna göre atayamayacağına sıralanabilir değerleri düğmesi sütunlar gibi bazı sütunları içermeyebilir. Bu sütun için bir <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> sıralama glif üstbilgisinde alan ayırmak gerekmez. Bu nedenle, hiçbir zaman sıralama için kullanılacağını gösterir.  
  
 Olduğunda bir <xref:System.Windows.Forms.DataGridView> olan sıralı, hem sıralama sütunu ve sıralama düzenini değerlerini kontrol ederek belirleyebilirsiniz <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri. Bu değerler sonra özel bir sıralama işlemi anlamlı değildir. Özel sıralama hakkında daha fazla bilgi için bu konunun devamındaki özel sıralama bölümüne bakın.  
  
 Olduğunda bir <xref:System.Windows.Forms.DataGridView> ilişkili ve ilişkisiz sütunlarını içeren bir denetim sıralandığı, ilişkisiz sütunlardaki değerleri otomatik olarak korunmasını olamaz. Bu değerleri tutmak için sanal mod ayarlayarak uygulamalıdır <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` ve işleme <xref:System.Windows.Forms.DataGridView.CellValueNeeded> ve <xref:System.Windows.Forms.DataGridView.CellValuePushed> olayları. Daha fazla bilgi için [nasıl yapılır: Sanal modu Windows Forms DataGridView denetiminde](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Bağlanmamış sütunlar ilişkili modunda sıralama desteklenmiyor.  
  
## <a name="programmatic-sorting"></a>Programlı sıralama  
 Sıralayabilir bir <xref:System.Windows.Forms.DataGridView> çağırarak programlama yoluyla kendi <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi bir <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.ComponentModel.ListSortDirection> parametre olarak sabit listesi değeri. Bu aşırı yükleme atayamayacağına sıralanabilir ancak yapılandırmak otomatik sıralama için istediğiniz değil değerlerle sütuna göre sıralama sırasında yararlı olur. Ne zaman bu aşırı yüklemesini çağırmak ve bir sütunla geçirin bir <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği değerinin <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri otomatik olarak ayarlanır ve sütun başlığına uygun sıralama karakteri görüntülenir.  
  
> [!NOTE]
>  Zaman <xref:System.Windows.Forms.DataGridView> denetimin bağlı bir dış veri kaynağına ayarlayarak <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği `Sort(DataGridViewColumn,ListSortDirection)` yöntemi aşırı yüklemesini bağlanmamış sütunlar için çalışmaz. Ayrıca, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`, yalnızca bağlı sütun için bu aşırı yüklemesini çağırabilirsiniz. Bir sütun verilere bağlı olup olmadığını belirlemek için denetleme <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> özellik değeri. Bağlanmamış sütunlar ilişkili modunda sıralama desteklenmiyor.  
  
## <a name="custom-sorting"></a>Özel sıralama  
 Özelleştirebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi veya işleme <xref:System.Windows.Forms.DataGridView.SortCompare> olay.  
  
 `Sort(IComparer)` Yöntemi aşırı yüklemesini uygulayan bir sınıf örneğini alır <xref:System.Collections.IComparer> arabirimi bir parametre olarak. Bu aşırı yükleme, özel sıralama sağlamak istediğinizde kullanışlıdır. Örneğin, bir sütundaki değerleri doğal bir sıralama yok veya doğal sıralama düzeni ne zaman uygun değildir. Bu durumda, Otomatik sıralama kullanamaz, ancak yine de sütun başlıklarını tıklatarak sıralama kullanıcılarınıza isteyebilirsiniz. İçin bir işleyici içinde bu aşırı yüklemesini çağırabilirsiniz <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> seçimi için sütun üst bilgilerini kullanmıyorsanız olay.  
  
> [!NOTE]
>  `Sort(IComparer)` Yöntemi aşırı yüklemesini yalnızca çalışır <xref:System.Windows.Forms.DataGridView> denetim için dış veri kaynağına bağlı değil ve <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik değeri `false`. Bir dış veri kaynağına bağlı sütunlar için sıralama özelleştirmek için veri kaynağı tarafından sağlanan sıralama işlemleri kullanmanız gerekir. Sanal modda bağlanmamış sütunlar için sıralama kendi işlemleri sağlamanız gerekir.  
  
 Kullanılacak `Sort(IComparer)` yöntemi aşırı yüklemesi, uygulayan kendi sınıf oluşturmalısınız <xref:System.Collections.IComparer> arabirimi. Bu arabirim uygulamak için kendi sınıfınızı gerektirir <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> yöntemi, hangi <xref:System.Windows.Forms.DataGridView> geçirir <xref:System.Windows.Forms.DataGridViewRow> nesneler olarak giriş `Sort(IComparer)` yöntemi aşırı yüklemesini çağrılır. Bu, değerlere herhangi bir sütuna göre sıralama doğru satır hesaplayabilirsiniz.  
  
 `Sort(IComparer)` Yöntemi aşırı yüklemesini ayarlı değil <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri her zaman ayarlamanız gerekir, <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> sıralama glif görüntülenecek özelliği.  
  
 Alternatif olarak `Sort(IComparer)` yöntemi aşırı yüklemesi, özel bir işleyici uygulayarak sıralama sağlayabilir <xref:System.Windows.Forms.DataGridView.SortCompare> olay. Bu olay, kullanıcılar otomatik sıralama veya çağırdığınızda için yapılandırılmış sütun başlıklarını tıkladığında gerçekleşir `Sort(DataGridViewColumn,ListSortDirection)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi. Her satır, bunların doğru sırada hesaplamak etkinleştirme denetiminde çifti için olayı oluşur.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Olay oluşmaz olduğunda <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik değeri `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
