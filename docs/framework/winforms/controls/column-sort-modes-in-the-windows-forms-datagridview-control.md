---
title: DataGridView Denetimindeki sütun sıralama modları
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d1e2f582c9759332e0ed963cb7f88ee052616c45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744199"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
<xref:System.Windows.Forms.DataGridView> sütunlarda üç sıralama modu vardır. Her bir sütunun sıralama modu, sütunun <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği aracılığıyla belirtilir ve bu, aşağıdaki <xref:System.Windows.Forms.DataGridViewColumnSortMode> sabit listesi değerlerinden birine ayarlanabilir.  
  
|`DataGridViewColumnSortMode` değeri|Açıklama|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Metin kutusu sütunları için varsayılan. Sütun başlıkları seçim için kullanılmamışsa, sütun başlığına tıkladığınızda <xref:System.Windows.Forms.DataGridView> bu sütuna göre otomatik olarak sıralanır ve sıralama düzenini gösteren bir karakter görüntülenir.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Metin kutusu olmayan sütunlar için varsayılan değer. Bu sütunu programlı bir şekilde sıralayabilirsiniz; Ancak sıralama için düşünülmemiştir, bu nedenle sıralama karakteri için hiçbir alan ayrılmamıştır.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Bu sütunu programlı bir şekilde sıralayabilirsiniz ve sıralama glifi için boşluk ayrılır.|  
  
 Anlamlı bir şekilde sıralanmış değerler içeriyorsa, <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> varsayılan olan bir sütunun sıralama modunu değiştirmek isteyebilirsiniz. Örneğin, öğe durumlarını temsil eden sayılar içeren bir veritabanı sütununuz varsa, bu numaraları bir görüntü sütununu veritabanı sütununa bağlayarak ilgili simgeler olarak görüntüleyebilirsiniz. Daha sonra, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı için bir işleyicide sayısal hücre değerlerini görüntü görüntüleme değerleriyle değiştirebilirsiniz. Bu durumda, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğinin <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> olarak ayarlanması, kullanıcılarınızın sütunu sıralaması için izin verecek. Otomatik sıralama, numaralara karşılık gelen durumların doğal bir sırası olmasa bile, kullanıcılarınızın aynı duruma sahip öğeleri gruplandırmasına olanak sağlar. Onay kutusu sütunları, otomatik sıralamanın aynı durumdaki öğeleri gruplandırmak için yararlı olduğu başka bir örnektir.  
  
 <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ayarlarından bağımsız olarak, herhangi bir sütundaki veya birden çok sütundaki değerler aracılığıyla programlı bir şekilde sıralayabilirsiniz. Programlı sıralama, sıralama için kendi Kullanıcı arabiriminizi (UI) sağlamak istediğinizde veya özel sıralamayı uygulamak istediğinizde faydalıdır. Kendi sıralama Kullanıcı arabiriminizi sağlamak, örneğin, sütun üst bilgisi seçimini etkinleştirmek için <xref:System.Windows.Forms.DataGridView> seçim modunu ayarladığınızda yararlıdır. Bu durumda, sütun başlıkları sıralama için kullanılamaz olsa da, üst bilgilerin uygun sıralama kabartmasını görüntülemesini istiyorsanız, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>olarak ayarlamanız gerekir.  
  
 Programlı sıralama moduna ayarlanan sütunlar otomatik olarak bir sıralama karakteri görüntülemez. Bu sütunlar için, <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> özelliğini ayarlayarak glifi kendiniz görüntüetmeniz gerekir. Özel sıralamada esneklik istiyorsanız bu gereklidir. Örneğin, <xref:System.Windows.Forms.DataGridView> birden çok sütuna göre sıralarsanız, birden fazla sıralama karakteri veya sıralama karakteri göstermek isteyebilirsiniz.  
  
 Bir <xref:System.Windows.Forms.DataGridView> program aracılığıyla herhangi bir sütuna göre sıralamak mümkün olsa da, düğme sütunları gibi bazı sütunlarda anlamlı bir şekilde sıralanmış olabilecek değerler bulunmamalıdır. Bu sütunlarda, <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik ayarı sıralama için hiçbir şekilde kullanılmayacağını gösterir, bu nedenle sıralama glifi için üst bilgide alan ayırmak gerekmez.  
  
 <xref:System.Windows.Forms.DataGridView> sıralandığında, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özelliklerinin değerlerini denetleyerek sıralama sütununu ve sıralama düzenini belirleyebilirsiniz. Bu değerler, özel bir sıralama işleminden sonra anlamlı değildir. Özel sıralama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan özel sıralama bölümüne bakın.  
  
 Hem bağlı hem de ilişkisiz sütunları içeren bir <xref:System.Windows.Forms.DataGridView> denetimi sıralanmışsa, ilişkisiz sütunlardaki değerler otomatik olarak korunabilir. Bu değerleri korumak için, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` ve <xref:System.Windows.Forms.DataGridView.CellValueNeeded> ve <xref:System.Windows.Forms.DataGridView.CellValuePushed> olaylarını işleyerek sanal modu uygulamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). İlişkisiz sütunlara göre sıralama, ilişkili modda desteklenmez.  
  
## <a name="programmatic-sorting"></a>Programlı sıralama  
 Bir <xref:System.Windows.Forms.DataGridView> programlı bir şekilde <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemini çağırarak sıralayabilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(DataGridViewColumn,ListSortDirection)` aşırı yüklemesi, bir <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.ComponentModel.ListSortDirection> numaralandırma değerini parametre olarak alır. Bu aşırı yükleme, sütunları anlamlı bir şekilde sıralanmış, ancak otomatik sıralama için yapılandırmak istemediğiniz değerlerle sıralama yaparken faydalıdır. Bu aşırı yüklemeyi çağırdığınızda ve <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType><xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik değerine sahip bir sütuna geçirdiğinizde, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri otomatik olarak ayarlanır ve sütun üstbilgisinde uygun sıralama karakteri görüntülenir.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlayarak bir dış veri kaynağına bağlandığında, `Sort(DataGridViewColumn,ListSortDirection)` yöntemi aşırı yüklemesi ilişkisiz sütunlar için çalışmaz. Ayrıca, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`, bu aşırı yüklemeyi yalnızca bağlantılı sütunlar için çağırabilirsiniz. Bir sütunun veriye dayalı olup olmadığını anlamak için <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> özellik değerini denetleyin. İlişkisiz sütunları ilişkili modda sıralama desteklenmiyor.  
  
## <a name="custom-sorting"></a>Özel sıralama  
 <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini kullanarak veya <xref:System.Windows.Forms.DataGridView.SortCompare> olayını işleyerek <xref:System.Windows.Forms.DataGridView> özelleştirebilirsiniz.  
  
 `Sort(IComparer)` yöntemi aşırı yüklemesi, <xref:System.Collections.IComparer> arabirimini bir parametre olarak uygulayan bir sınıfın örneğini alır. Bu aşırı yükleme, özel sıralama sağlamak istediğinizde yararlıdır; Örneğin, bir sütundaki değerlerin doğal bir sıralama düzeni olmadığında veya doğal sıralama düzeni uygun olmadığında. Bu durumda, otomatik sıralamayı kullanamazsınız, ancak kullanıcılarınızın sütun başlıklarına tıklayarak sıralamayı tercih edebilirsiniz. Seçim için sütun üst bilgileri kullanmıyorsanız, bu aşırı yüklemeyi <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> olayına yönelik bir işleyicide çağırabilirsiniz.  
  
> [!NOTE]
> `Sort(IComparer)` yöntemi aşırı yüklemesi, yalnızca <xref:System.Windows.Forms.DataGridView> denetimi bir dış veri kaynağına bağlanmazsa ve <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> Özellik değeri `false`olduğunda işe yarar. Dış veri kaynağına göre sıralamayı özelleştirmek için, veri kaynağı tarafından sunulan sıralama işlemlerini kullanmanız gerekir. Sanal modda, ilişkisiz sütunlar için kendi sıralama işlemlerinizi sağlamanız gerekir.  
  
 `Sort(IComparer)` yöntemi aşırı yüklemesini kullanmak için, <xref:System.Collections.IComparer> arabirimini uygulayan kendi sınıfınızı oluşturmanız gerekir. Bu arabirim, `Sort(IComparer)` yöntem aşırı yüklemesi çağrıldığında <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewRow> nesneleri girdi olarak geçirirse <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> yöntemini uygulamak için sınıfınızın kullanılmasını gerektirir. Bu şekilde, herhangi bir sütundaki değerlere göre doğru satır sıralamasını hesaplayabilirsiniz.  
  
 `Sort(IComparer)` yöntemi aşırı yüklemesi <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özelliklerini ayarlanmamış, bu nedenle <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> özelliğini her zaman sıralama glifi görüntüleyecek şekilde ayarlamanız gerekir.  
  
 `Sort(IComparer)` yöntemi aşırı yüküne alternatif olarak, <xref:System.Windows.Forms.DataGridView.SortCompare> olayı için bir işleyici uygulayarak özel sıralama sağlayabilirsiniz. Bu olay, kullanıcılar otomatik sıralama için yapılandırılan sütunların üst bilgilerine tıkladıklarında veya <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(DataGridViewColumn,ListSortDirection)` aşırı yüklemesini çağırdığınızda oluşur. Olay, denetimdeki her satır çiftliğine meydana gelir ve doğru sıralarını hesaplamanıza olanak sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView.SortCompare> olayı, <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlandığında veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> Özellik değeri `true`olduğunda oluşmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
