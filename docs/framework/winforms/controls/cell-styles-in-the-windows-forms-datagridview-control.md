---
title: DataGridView Denetimindeki Hücre stilleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: fe56033a5adbe7719c64695c8f9ebc4f3644fc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746161"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Hücre Stilleri
<xref:System.Windows.Forms.DataGridView> denetimindeki her bir hücre, metin biçimi, arka plan rengi, ön plan rengi ve yazı tipi gibi kendi stiline sahip olabilir. Bununla birlikte, genellikle birden çok hücre belirli stil özelliklerini paylaşır.  
  
 Stilleri paylaşan hücre grupları belirli satırlar veya sütunlar içindeki tüm hücreleri, belirli değerleri içeren tüm hücreleri veya denetimdeki tüm hücreleri içerebilir. Bu gruplar örtüştiğinden, her hücre stil bilgilerini birden fazla yerden alabilir. Örneğin, bir <xref:System.Windows.Forms.DataGridView> denetimindeki her hücrenin aynı yazı tipini kullanmasını isteyebilirsiniz, ancak yalnızca para birimi biçimi kullanmak için para birimi sütunlarındaki hücrelere ve yalnızca kırmızı bir ön plan rengi kullanmak için negatif sayı olan para birimi hücrelerine sahip olabilirsiniz.  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfı  
 <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, görsel stille ilgili aşağıdaki özellikleri içerir:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Bu sınıf, biçimlendirme ile ilgili aşağıdaki özellikleri de içerir:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Bu özellikler ve diğer hücre stili özellikleri hakkında daha fazla bilgi için, aşağıdaki Ayrıca bkz. <xref:System.Windows.Forms.DataGridViewCellStyle> başvuru belgelerine ve aşağıda Ayrıca bkz. bölümünde listelenen konulara bakın.  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle nesnelerini kullanma  
 <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>ve <xref:System.Windows.Forms.DataGridViewCell> sınıflarının ve bunların türetilmiş sınıflarının çeşitli özelliklerinden <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri alabilirsiniz. Bu özelliklerden biri henüz ayarlanmamışsa, değerini almak yeni bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi oluşturur. Ayrıca kendi <xref:System.Windows.Forms.DataGridViewCellStyle> nesnelerinizi örnekleyebilirsiniz ve bu özelliklere atayabilirsiniz.  
  
 Birden çok <xref:System.Windows.Forms.DataGridView> öğesi arasında <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri paylaşarak stil bilgilerinin gereksiz şekilde çoğaltılmasını önleyebilirsiniz. Denetim, sütun ve satır düzeylerinde ayarlanan stiller her düzeyde hücre düzeyine göre filtreleneceği için, yalnızca yukarıdaki düzeyden farklı olan her bir düzeyde stil özelliklerini ayarlayarak stil çoğaltmasına da kurtulabilirsiniz. Bu, aşağıdaki stil devralma bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri alan veya ayarlanan birincil özellikler listelenmiştir.  
  
|Özellik|Sınıflar|Açıklama|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>ve türetilmiş sınıflar|Tüm denetimdeki (üst bilgi hücreleri dahil), bir sütunda veya bir satırda bulunan tüm hücreler tarafından kullanılan varsayılan stilleri alır veya ayarlar.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimdeki tüm satırlar tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Bu, üst bilgi hücrelerini içermez.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimdeki değişen satırlar tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Defter benzeri bir efekt oluşturmak için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimin satır başlıkları tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Görsel stiller etkinse geçerli Tema tarafından geçersiz kılınır.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimin sütun başlıkları tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Görsel stiller etkinse geçerli Tema tarafından geçersiz kılınır.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş sınıflar|Hücre düzeyinde belirtilen stilleri alır veya ayarlar. Bu stiller, daha yüksek düzeylerde devralınmış olanları geçersiz kılar.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>ve türetilmiş sınıflar|Daha yüksek düzeylerde devralınan stiller de dahil olmak üzere, şu anda hücre, satır veya sütuna uygulanmış olan tüm stilleri alır.|  
  
 Yukarıda belirtildiği gibi, özellik daha önce ayarlanmamışsa bir Style özelliğinin değerini almak otomatik olarak yeni bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi oluşturur. Bu nesneleri gereksiz şekilde oluşturmaktan kaçınmak için, satır ve sütun sınıflarının <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> özelliğinin ayarlanmış olup olmadığını denetlemek için kontrol edebilirsiniz <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> bir özelliği vardır. Benzer şekilde, hücre sınıflarının <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğinin ayarlanmış olup olmadığını belirten bir <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> özelliği vardır.  
  
 Stil özelliklerinin her biri, <xref:System.Windows.Forms.DataGridView> denetiminde karşılık gelen *PropertyName*`Changed` olayına sahiptir. Satır, sütun ve hücre özellikleri için, olayın adı "`Row`", "`Column`" veya "`Cell`" (örneğin, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>) ile başlar. Bu olayların her biri, karşılık gelen Style özelliği farklı bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesine ayarlandığında oluşur. Bu olaylar, bir stil özelliğinden bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi aldığınızda ve özellik değerlerini değiştirirken oluşmaz. Hücre stili nesnelerinde yapılan değişikliklere yanıt vermek için <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> olayı işleyin.  
  
## <a name="style-inheritance"></a>Stil Devralımı  
 Her <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliğinden görünümünü alır. Bu özellik tarafından döndürülen <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi, değerlerini <xref:System.Windows.Forms.DataGridViewCellStyle>türündeki özelliklerin hiyerarşisinden devralır. Bu özellikler, üst bilgi olmayan hücreler için <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> değerlerini elde eden sıralamada aşağıda listelenmiştir.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca tek dizin numaralarına sahip satırlardaki hücreler için)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır ve sütun üst bilgisi hücreleri için <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği, belirtilen sıradaki kaynak özellikleri listesinden aşağıdaki değerlere göre doldurulur.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Aşağıdaki diyagramda bu işlem gösterilmektedir.  
  
 ![DataGridViewCellStyle türündeki Özellikler](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCell devralma diyagramı")  
  
 Belirli satırlar ve sütunlar tarafından devralınan stillere de erişebilirsiniz. Sütun <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> özelliği, aşağıdaki özelliklerden değerlerini devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özelliği, aşağıdaki özelliklerden değerlerini devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca tek dizin numaralarına sahip satırlardaki hücreler için)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Bir `InheritedStyle` özelliği tarafından döndürülen <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesindeki her bir özellik için, özellik değeri, karşılık gelen özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> sınıf varsayılanlarından farklı bir değere ayarlanmış olan uygun listedeki ilk hücre stilinden elde edilir.  
  
 Aşağıdaki tabloda, örnek bir hücrenin <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> Özellik değerinin kapsayan sütundan nasıl Devralındığı gösterilmektedir.  
  
|`DataGridViewCellStyle` türü özelliği|Alınan nesne için örnek `ForeColor` değeri|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Bu durumda, hücrenin satırındaki <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> değeri, listedeki ilk gerçek değerdir. Bu, hücrenin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A><xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> Özellik değeri haline gelir.  
  
 Aşağıdaki diyagramda farklı <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerinin farklı yerlerden değerlerini nasıl devraldığı gösterilmektedir.  
  
 ![DataGridView özellik&#45;değeri devralma](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCell değer devralma diyagramı")  
  
 Stil devralma özelliğinden yararlanarak, aynı bilgileri birden çok yerde belirtmeye gerek kalmadan tüm denetim için uygun stiller sağlayabilirsiniz.  
  
 Başlık hücreleri açıklandığı şekilde stil devralmasına katılırsanız, <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellikleri tarafından döndürülen nesneler, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği tarafından döndürülen nesnenin özellik değerlerini geçersiz kılan ilk özellik değerlerine sahiptir. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği tarafından döndürülen nesne için ayarlanan özelliklerin satır ve sütun başlıklarına uygulanmasını istiyorsanız, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellikleri tarafından döndürülen nesnelerin karşılık gelen özelliklerini <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı için gösterilen varsayılanlar olarak ayarlamanız gerekir.  
  
> [!NOTE]
> Görsel stiller etkinleştirilmişse, satır ve sütun üst bilgileri (<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>hariç) otomatik olarak geçerli Tema tarafından belirlenir ve bu özellikler tarafından belirtilen stillerin üzerine yazılır.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>ve <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> türleri, sütun <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliği tarafından döndürülen nesnenin bazı değerlerini de başlatır. Daha fazla bilgi için bu türlerin başvuru belgelerine bakın.  
  
## <a name="setting-styles-dynamically"></a>Stilleri dinamik olarak ayarlama  
 Belirli değerlere sahip hücrelerin stillerini özelleştirmek için <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı için bir işleyici uygulayın. Bu olaya yönelik işleyiciler <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> türünün bir bağımsız değişkenini alır. Bu nesne, <xref:System.Windows.Forms.DataGridView> denetimindeki konumuyla birlikte biçimlendirmekte olan hücrenin değerini belirlemenizi sağlayan özellikler içerir. Bu nesne, biçimlendirilmekte olan hücrenin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliğinin değerine başlatılan bir <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> özelliğini de içerir. Hücre değeri ve konumuna uygun stil bilgilerini belirtmek için hücre stili özelliklerini değiştirebilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> olaylar ayrıca olay verilerinde bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi alır, ancak bu durumda, salt okunurdur ve bu özellik için satır <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özelliğinin bir kopyasıdır ve üzerinde yapılan değişiklikler denetimi etkilemez.  
  
 Ayrıca, <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olayları gibi olaylara yanıt olarak tek tek hücrelerin stillerini dinamik olarak değiştirebilirsiniz. Örneğin, <xref:System.Windows.Forms.DataGridView.CellMouseEnter> olayına yönelik bir İşleyicide, hücre arka plan renginin (hücrenin <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği aracılığıyla alınan) geçerli değerini saklayabilir, sonra fare üzerine geldiğinde hücreyi vurgulayacak yeni bir renge ayarlayabilirsiniz. <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olayı için bir İşleyicide, arka plan rengini özgün değerine geri yükleyebilirsiniz.  
  
> [!NOTE]
> Hücrenin <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğinde depolanan değerlerin önbelleğe alınması, belirli bir stil değerinin ayarlanmış olup olmamasına bakılmaksızın önemlidir. Bir stil ayarını geçici olarak değiştirirseniz özgün "ayarlanmamış" durumuna geri yüklemek, hücrenin stil ayarının daha yüksek bir düzeyden devralınmasını sağlar. Stilin devralınmadığına bakılmaksızın bir hücrede gerçek stil ' i belirlemeniz gerekiyorsa, hücrenin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliğini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
