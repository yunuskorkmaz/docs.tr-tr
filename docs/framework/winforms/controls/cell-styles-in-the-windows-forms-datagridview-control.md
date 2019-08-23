---
title: Windows Forms DataGridView Denetimindeki Hücre Stilleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917763"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Hücre Stilleri
<xref:System.Windows.Forms.DataGridView> Denetimdeki her hücrenin metin biçimi, arka plan rengi, ön plan rengi ve yazı tipi gibi kendi stili olabilir. Bununla birlikte, genellikle birden çok hücre belirli stil özelliklerini paylaşır.  
  
 Stilleri paylaşan hücre grupları belirli satırlar veya sütunlar içindeki tüm hücreleri, belirli değerleri içeren tüm hücreleri veya denetimdeki tüm hücreleri içerebilir. Bu gruplar örtüştiğinden, her hücre stil bilgilerini birden fazla yerden alabilir. Örneğin, bir <xref:System.Windows.Forms.DataGridView> denetimdeki her hücrenin aynı yazı tipini kullanmasını isteyebilirsiniz, ancak yalnızca para birimi biçimi kullanmak için para birimi sütunlarındaki hücreler ve yalnızca kırmızı bir ön plan rengi kullanmak için negatif sayı olan para birimi hücreleri olabilir.  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfı  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıfı, görsel stiliyle ilgili aşağıdaki özellikleri içerir:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Bu sınıf, biçimlendirme ile ilgili aşağıdaki özellikleri de içerir:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Bu özellikler ve diğer hücre stili özellikleri hakkında daha fazla bilgi için aşağıdaki Ayrıca bkz <xref:System.Windows.Forms.DataGridViewCellStyle> . bölümünde listelenen başvuru belgelerine ve konulara bakın.  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle nesnelerini kullanma  
 <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewCellStyle> ,,Ve<xref:System.Windows.Forms.DataGridViewCell> sınıflarının ve bunların türetilmiş sınıflarının çeşitli özelliklerinden nesneleri alabilirsiniz. <xref:System.Windows.Forms.DataGridViewRow> <xref:System.Windows.Forms.DataGridViewColumn> Bu özelliklerden biri henüz ayarlanmamışsa değerinin alınması yeni <xref:System.Windows.Forms.DataGridViewCellStyle> bir nesne oluşturacaktır. Ayrıca kendi <xref:System.Windows.Forms.DataGridViewCellStyle> nesnelerinizi örnekleyebilirsiniz ve bu özelliklere atayabilirsiniz.  
  
 Nesneleri birden çok <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridView> öğe arasında paylaşarak stil bilgisinin gereksiz şekilde çoğaltılmasını önleyebilirsiniz. Denetim, sütun ve satır düzeylerinde ayarlanan stiller her düzeyde hücre düzeyine göre filtreleneceği için, yalnızca yukarıdaki düzeyden farklı olan her bir düzeyde stil özelliklerini ayarlayarak stil çoğaltmasına da kurtulabilirsiniz. Bu, aşağıdaki stil devralma bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Aşağıdaki tabloda nesneleri alan veya ayarlanan <xref:System.Windows.Forms.DataGridViewCellStyle> birincil özellikler listelenmiştir.  
  
|Özellik|Sınıflar|Açıklama|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn> ,<xref:System.Windows.Forms.DataGridViewRow>ve türetilmiş sınıflar|Tüm denetimdeki (üst bilgi hücreleri dahil), bir sütunda veya bir satırda bulunan tüm hücreler tarafından kullanılan varsayılan stilleri alır veya ayarlar.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimdeki tüm satırlar tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Bu, üst bilgi hücrelerini içermez.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimdeki değişen satırlar tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Defter benzeri bir efekt oluşturmak için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimin satır başlıkları tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Görsel stiller etkinse geçerli Tema tarafından geçersiz kılınır.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Denetimin sütun başlıkları tarafından kullanılan varsayılan hücre stillerini alır veya ayarlar. Görsel stiller etkinse geçerli Tema tarafından geçersiz kılınır.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>ve türetilmiş sınıflar|Hücre düzeyinde belirtilen stilleri alır veya ayarlar. Bu stiller, daha yüksek düzeylerde devralınmış olanları geçersiz kılar.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow> ,<xref:System.Windows.Forms.DataGridViewColumn>ve türetilmiş sınıflar|Daha yüksek düzeylerde devralınan stiller de dahil olmak üzere, şu anda hücre, satır veya sütuna uygulanmış olan tüm stilleri alır.|  
  
 Yukarıda belirtildiği gibi, özellik daha önce ayarlanmamışsa bir Style özelliğinin değerini almak otomatik olarak <xref:System.Windows.Forms.DataGridViewCellStyle> yeni bir nesne oluşturur. Bu nesneleri gereksiz şekilde oluşturmaktan kaçınmak için, satır ve sütun sınıflarının <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> özelliğin ayarlanmış olup olmadığını denetlemek için kontrol edebilirsiniz. Benzer şekilde, hücre sınıflarının <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğin ayarlanmış olup olmadığını belirten bir özelliği vardır.  
  
 Stil özelliklerinin her biri <xref:System.Windows.Forms.DataGridView> denetimde karşılık gelen *PropertyName* `Changed` olayına sahiptir. Satır, sütun ve hücre özellikleri için`Row`, olayın adı "", "`Column`" veya "`Cell`" (örneğin, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>) ile başlar. Bu olayların her biri, karşılık gelen Style özelliği farklı <xref:System.Windows.Forms.DataGridViewCellStyle> bir nesneye ayarlandığında oluşur. Bu olaylar, bir stil özelliğinden bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesne aldığınızda ve özellik değerlerini değiştirirken oluşmaz. Hücre stili nesnelerinde yapılan değişikliklere yanıt vermek için <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> olayı işleyin.  
  
## <a name="style-inheritance"></a>Stil Devralımı  
 Her <xref:System.Windows.Forms.DataGridViewCell> biri <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliğinden görünümünü alır. Bu özellik tarafından döndürülen <xref:System.Windows.Forms.DataGridViewCellStyle> nesne,bunesnenindeğerlerinitüründekiÖzelliklerhiyerarşisindendevralır.<xref:System.Windows.Forms.DataGridViewCellStyle> Bu özellikler, <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> üst bilgi olmayan hücrelerin değerlerini aldığı sırada aşağıda listelenmiştir.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(yalnızca tek dizin numaralarına sahip satırlardaki hücreler için)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır ve sütun üst bilgisi hücreleri için, <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği verilen sırada aşağıdaki kaynak özellikleri listesinden alınan değerlere göre doldurulur.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Aşağıdaki diyagramda bu işlem gösterilmektedir.  
  
 ![DataGridViewCellStyle türündeki Özellikler](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCell devralma diyagramı")  
  
 Belirli satırlar ve sütunlar tarafından devralınan stillere de erişebilirsiniz. Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> özelliği, değerlerini aşağıdaki özelliklerden devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özelliği, değerlerini aşağıdaki özelliklerden devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(yalnızca tek dizin numaralarına sahip satırlardaki hücreler için)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Özelliği tarafından döndürülen bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnedeki her bir `InheritedStyle` özellik için, özellik değeri, karşılık gelen özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> sınıf varsayılan değerleri dışında bir değere ayarlanmış olan uygun listedeki ilk hücre stilinden elde edilir.  
  
 Aşağıdaki tabloda, örnek bir hücrenin <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> Özellik değerinin kapsayan sütundan nasıl Devralındığı gösterilmektedir.  
  
|Türünün özelliği`DataGridViewCellStyle`|Alınan `ForeColor` nesne için örnek değer|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Bu durumda, <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> hücrenin satırındaki değer listedeki ilk gerçek değerdir. Bu, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>hücrenin özellik değeri olur.  
  
 Aşağıdaki diyagramda farklı <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerin değerlerini farklı yerlerden nasıl devraldığı gösterilmektedir.  
  
 ![DataGridView özellik&#45;değeri devralma](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCell değer devralma diyagramı")  
  
 Stil devralma özelliğinden yararlanarak, aynı bilgileri birden çok yerde belirtmeye gerek kalmadan tüm denetim için uygun stiller sağlayabilirsiniz.  
  
 Başlık hücreleri açıklandığı şekilde stil devralmaya katılırsanız, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView> denetimin ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliklerinin tarafından döndürülen nesneler, tarafından döndürülen nesnenin özellik değerlerini geçersiz kılan ilk özellik değerlerine sahiptir <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> Özelliği tarafından döndürülen nesne için ayarlanan özelliklerin satır ve sütun başlıklarına uygulanmasını istiyorsanız, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellikleri tarafından döndürülen nesnelerin karşılık gelen özelliklerini belirtilen varsayılanlar olarak ayarlamanız gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> sınıf için.  
  
> [!NOTE]
> Görsel stiller etkinleştirilmişse, satır ve sütun üst bilgileri (hariç <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>), geçerli Tema tarafından otomatik olarak stillendirilmiş ve bu özellikler tarafından belirtilen tüm stilleri geçersiz kılar.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, ,<xref:System.Windows.Forms.DataGridViewImageColumn>Ve <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> türleri deColumnözelliğitarafındandöndürülennesneninbazıdeğerlerinibaşlatır.<xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Daha fazla bilgi için bu türlerin başvuru belgelerine bakın.  
  
## <a name="setting-styles-dynamically"></a>Stilleri dinamik olarak ayarlama  
 Belirli değerlere sahip hücrelerin stillerini özelleştirmek için, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay için bir işleyici uygulayın. Bu olay için işleyiciler <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> türün bir bağımsız değişkenini alır. Bu nesne, <xref:System.Windows.Forms.DataGridView> denetimin konumuyla birlikte biçimlendirmekte olan hücrenin değerini belirlemenizi sağlayan özellikler içerir. Bu nesne, biçimlendirilmekte <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> olan hücrenin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliğinin değerine başlatılan bir özelliği de içerir. Hücre değeri ve konumuna uygun stil bilgilerini belirtmek için hücre stili özelliklerini değiştirebilirsiniz.  
  
> [!NOTE]
> Ve olayları olay verilerinde bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesne alır, ancak bu durumda satır <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özelliğinin salt okuma amacıyla bir kopyasıdır ve üzerinde yapılan değişiklikler denetimi etkilemez. <xref:System.Windows.Forms.DataGridView.RowPostPaint> <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
 Ayrıca, <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olayları gibi olaylara yanıt olarak tek tek hücrelerin stillerini dinamik olarak değiştirebilirsiniz. Örneğin, <xref:System.Windows.Forms.DataGridView.CellMouseEnter> olay için bir İşleyicide, hücre arka plan renginin ( <xref:System.Windows.Forms.DataGridViewCell.Style%2A> hücrenin özelliğinden alınan) geçerli değerini saklayabilir, sonra fare üzerine geldiğinde hücreyi vurgulayacak yeni bir renge ayarlayabilirsiniz. <xref:System.Windows.Forms.DataGridView.CellMouseLeave> Olay için bir İşleyicide, arka plan rengini özgün değerine geri yükleyebilirsiniz.  
  
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
- [Nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
