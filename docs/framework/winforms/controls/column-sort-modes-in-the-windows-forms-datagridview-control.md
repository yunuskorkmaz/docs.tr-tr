---
title: Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918455"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
<xref:System.Windows.Forms.DataGridView>sütunlarda üç sıralama modu vardır. Her bir sütunun sıralama modu, sütunun <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği aracılığıyla belirtilir ve bu, aşağıdaki <xref:System.Windows.Forms.DataGridViewColumnSortMode> sabit listesi değerlerinden birine ayarlanabilir.  
  
|`DataGridViewColumnSortMode`deeri|Açıklama|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Metin kutusu sütunları için varsayılan. Sütun başlıkları seçim için kullanılmamışsa, sütun başlığına tıkladığınızda bu sütuna <xref:System.Windows.Forms.DataGridView> göre otomatik olarak sıralama yapılır ve sıralama düzenini gösteren bir karakter görüntülenir.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Metin kutusu olmayan sütunlar için varsayılan değer. Bu sütunu programlı bir şekilde sıralayabilirsiniz; Ancak sıralama için düşünülmemiştir, bu nedenle sıralama karakteri için hiçbir alan ayrılmamıştır.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Bu sütunu programlı bir şekilde sıralayabilirsiniz ve sıralama glifi için boşluk ayrılır.|  
  
 Varsayılan olarak, anlamlı bir şekilde <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> sıralanabilmesi gereken değerler içeriyorsa, varsayılan olan bir sütunun sıralama modunu değiştirmek isteyebilirsiniz. Örneğin, öğe durumlarını temsil eden sayılar içeren bir veritabanı sütununuz varsa, bu numaraları bir görüntü sütununu veritabanı sütununa bağlayarak ilgili simgeler olarak görüntüleyebilirsiniz. Daha sonra sayısal hücre değerlerini, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay için bir işleyicide görüntü görüntüleme değerleriyle değiştirebilirsiniz. Bu durumda, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğinin olarak <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> ayarlanması, kullanıcılarınızın sütunu sıralamasını sağlayacaktır. Otomatik sıralama, numaralara karşılık gelen durumların doğal bir sırası olmasa bile, kullanıcılarınızın aynı duruma sahip öğeleri gruplandırmasına olanak sağlar. Onay kutusu sütunları, otomatik sıralamanın aynı durumdaki öğeleri gruplandırmak için yararlı olduğu başka bir örnektir.  
  
 Ayarlardan<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> bağımsız olarak, <xref:System.Windows.Forms.DataGridView> herhangi bir sütundaki veya birden fazla sütundaki değerleri programlı bir şekilde sıralayabilirsiniz. Programlı sıralama, sıralama için kendi Kullanıcı arabiriminizi (UI) sağlamak istediğinizde veya özel sıralamayı uygulamak istediğinizde faydalıdır. Kendi sıralama Kullanıcı arabiriminizi sağlamak, örneğin <xref:System.Windows.Forms.DataGridView> seçim modunu sütun başlığı seçimini etkinleştirecek şekilde ayarladığınızda yararlıdır. Bu durumda, sütun başlıkları sıralama için kullanılamaz olsa da, üst bilgilerin uygun sıralama kabartmasını görüntülemesini istiyorsanız <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği olarak <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>ayarlamanız gerekir.  
  
 Programlı sıralama moduna ayarlanan sütunlar otomatik olarak bir sıralama karakteri görüntülemez. Bu sütunlarda, <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> özelliği ayarlayarak glifi kendiniz görüntümalısınız. Özel sıralamada esneklik istiyorsanız bu gereklidir. Örneğin, öğesini birden çok sütuna <xref:System.Windows.Forms.DataGridView> göre sıralarsanız, birden fazla sıralama karakteri veya sıralama karakteri göstermek isteyebilirsiniz.  
  
 Bir sütuna program aracılığıyla sıralama yapabilseniz de, düğme sütunları gibi bazı sütunlarda anlamlı bir <xref:System.Windows.Forms.DataGridView> şekilde sıralanmış olabilecek değerler bulunmamalıdır. Bu sütunlarda, bir <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> ayarı sıralama için hiçbir şekilde kullanılmayacağını gösterir, bu nedenle sıralama glifi için üst bilgide alan ayırmak gerekmez.  
  
 Bir <xref:System.Windows.Forms.DataGridView> sıralandığında, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özelliklerinin değerlerini denetleyerek sıralama sütununu ve sıralama düzenini belirleyebilirsiniz. Bu değerler, özel bir sıralama işleminden sonra anlamlı değildir. Özel sıralama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan özel sıralama bölümüne bakın.  
  
 Hem bağlı <xref:System.Windows.Forms.DataGridView> hem de ilişkisiz sütunları içeren bir denetim sıralanmışsa, ilişkisiz sütunlardaki değerler otomatik olarak korunabilir. Bu <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> değerleri korumak için, `true` özelliğini <xref:System.Windows.Forms.DataGridView.CellValueNeeded> ve olaylarını ve <xref:System.Windows.Forms.DataGridView.CellValuePushed> işlemesini ayarlayarak sanal modu uygulamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)sanal modu uygulayın. İlişkisiz sütunlara göre sıralama, ilişkili modda desteklenmez.  
  
## <a name="programmatic-sorting"></a>Programlı sıralama  
 Yöntemini çağırarak programlı bir <xref:System.Windows.Forms.DataGridView> şekilde sıralayabilirsiniz. <xref:System.Windows.Forms.DataGridView.Sort%2A>  
  
 Yönteminin aşırı yüklemesi<xref:System.Windows.Forms.DataGridViewColumn> birvebirnumaralandırmadeğeriniparametreolarakalır.<xref:System.ComponentModel.ListSortDirection> `Sort(DataGridViewColumn,ListSortDirection)` <xref:System.Windows.Forms.DataGridView.Sort%2A> Bu aşırı yükleme, sütunları anlamlı bir şekilde sıralanmış, ancak otomatik sıralama için yapılandırmak istemediğiniz değerlerle sıralama yaparken faydalıdır. Bu aşırı yüklemeyi çağırdığınızda <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ve özellik <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>değeri olan bir sütunu geçirdiğinizde, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri otomatik olarak ayarlanır ve sütun üstbilgisinde uygun sıralama karakteri görüntülenir.  
  
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlanarak bir dış veri kaynağına bağlandığında, `Sort(DataGridViewColumn,ListSortDirection)` bu yöntem aşırı yüklemesi ilişkisiz sütunlar için çalışmaz. <xref:System.Windows.Forms.DataGridView> Ayrıca, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`özelliği olduğunda, bu aşırı yüklemeyi yalnızca bağlantılı sütunlar için çağırabilirsiniz. Bir sütunun veriye dayalı olup olmadığını anlamak için <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> özellik değerini denetleyin. İlişkisiz sütunları ilişkili modda sıralama desteklenmiyor.  
  
## <a name="custom-sorting"></a>Özel sıralama  
 Yöntemini<xref:System.Windows.Forms.DataGridView.Sort%2A> <xref:System.Windows.Forms.DataGridView> kullanarak veya olayı işleyerek<xref:System.Windows.Forms.DataGridView.SortCompare> özelleştirebilirsiniz. `Sort(IComparer)`  
  
 Yöntem `Sort(IComparer)` aşırı yüklemesi, <xref:System.Collections.IComparer> arabirimi bir parametre olarak uygulayan sınıfın bir örneğini alır. Bu aşırı yükleme, özel sıralama sağlamak istediğinizde yararlıdır; Örneğin, bir sütundaki değerlerin doğal bir sıralama düzeni olmadığında veya doğal sıralama düzeni uygun olmadığında. Bu durumda, otomatik sıralamayı kullanamazsınız, ancak kullanıcılarınızın sütun başlıklarına tıklayarak sıralamayı tercih edebilirsiniz. Seçim için sütun üst bilgileri kullanmıyorsanız, bu aşırı yüklemeyi <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> olaya yönelik bir işleyicide çağırabilirsiniz.  
  
> [!NOTE]
> Yöntem aşırı yüklemesi yalnızca <xref:System.Windows.Forms.DataGridView> denetim bir <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> dış veri kaynağına bağlanmazsa `false`ve özellik değeri olduğunda işe yarar. `Sort(IComparer)` Dış veri kaynağına göre sıralamayı özelleştirmek için, veri kaynağı tarafından sunulan sıralama işlemlerini kullanmanız gerekir. Sanal modda, ilişkisiz sütunlar için kendi sıralama işlemlerinizi sağlamanız gerekir.  
  
 `Sort(IComparer)` Yöntem aşırı yüklemesini kullanmak için, <xref:System.Collections.IComparer> arabirimini uygulayan kendi sınıfınızı oluşturmanız gerekir. Bu arabirim, sınıfının yöntem aşırı yüklemesi çağrıldığında <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> nesneleri giriş `Sort(IComparer)` olarak <xref:System.Windows.Forms.DataGridView> geçireceğini <xref:System.Windows.Forms.DataGridViewRow> yöntemi uygulaması için sınıfını gerektirir. Bu şekilde, herhangi bir sütundaki değerlere göre doğru satır sıralamasını hesaplayabilirsiniz.  
  
 Yöntem aşırı yüklemesi <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A>özellikleriniayarlanmamış , bu nedenle her zaman özelliğisıralamakarakterinigörüntüleyecekşekildeayarlamanızgerekir.<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> `Sort(IComparer)`  
  
 `Sort(IComparer)` Yöntem aşırı yüküne alternatif olarak, <xref:System.Windows.Forms.DataGridView.SortCompare> olay için bir işleyici uygulayarak özel sıralama sağlayabilirsiniz. Bu olay, kullanıcılar otomatik sıralama için yapılandırılan sütunların üst bilgilerine tıkladıklarında veya `Sort(DataGridViewColumn,ListSortDirection)` <xref:System.Windows.Forms.DataGridView.Sort%2A> metodun aşırı yüklemesini çağırdığınızda oluşur. Olay, denetimdeki her satır çiftliğine meydana gelir ve doğru sıralarını hesaplamanıza olanak sağlar.  
  
> [!NOTE]
> Özellik ayarlandığında veya özellik<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> değeri <xref:System.Windows.Forms.DataGridView.SortCompare> olduğunda`true`olayoluşmaz. <xref:System.Windows.Forms.DataGridView.DataSource%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki sütunlar için sıralama modlarını ayarlama](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
