---
title: Windows Forms DataGridView Denetimindeki Hücre Stilleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 41794c5ecadbcdc0b38c7c73afc7c010a4ea6989
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300027"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Hücre Stilleri
İçindeki her bir hücresinde <xref:System.Windows.Forms.DataGridView> denetim metin biçimi, arka plan rengi, ön plan rengini ve yazı tipi gibi kendi stil sahip olabilir. Genellikle, ancak birden çok hücre belirli stil özellikleri paylaşır.  
  
 Grupları hücre stilleri paylaşan tüm hücreleri belirli satırlar veya sütunlar, belirli değerleri içeren tüm hücreleri veya tüm hücreleri denetiminde içerebilir. Bu gruplar çakışıyor çünkü her hücre birden fazla yerde stil bilgilerini alabilirsiniz. Örneğin, her hücre isteyebileceğiniz bir <xref:System.Windows.Forms.DataGridView> aynı yazı tipi, ancak yalnızca para birimi biçimi kullanmak için para birimi sütunlardaki hücrelerde ve yalnızca para birimi hücreleri negatif sayılarla kırmızı ön plan rengi kullanacak şekilde denetim.  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfı  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıfı için görsel stil ilgili aşağıdaki özellikleri içerir:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ayrıca bu sınıf, biçimlendirme için ilgili aşağıdaki özellikleri içerir:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Bu özellikleri ve diğer hücre stili özellikleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataGridViewCellStyle> başvuru belgeleri ve konulara ayrıca aşağıdaki bölümünde listelenen.  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle nesnelerini kullanma  
 Alabileceğiniz <xref:System.Windows.Forms.DataGridViewCellStyle> çeşitli özelliklerini nesnelerden <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, ve <xref:System.Windows.Forms.DataGridViewCell> kendi türetilmiş sınıfları. Değeri alınırken yeni bir oluşturur, bu özelliklerden birini henüz ayarlanmamış ise <xref:System.Windows.Forms.DataGridViewCellStyle> nesne. Kendi başlatabilir <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri ve bunları bu özelliklerin atayın.  
  
 Gereksiz yinelenmesini stil bilgilerini paylaşarak kaçınabilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri arasında birden çok <xref:System.Windows.Forms.DataGridView> öğeleri. Yukarıdaki düzeylerinden farklıdır her düzeyde yalnızca bu stil özellikleri ayarlayarak, stiller, Denetim, sütun ve her hücre düzeyinde düzeyine aracılığıyla aşağı satır düzeylerine filtresi ayarlandığından stil çoğaltma önleyebilirsiniz. Bunu izleyen stil devralımı bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Aşağıdaki tabloda get veya set birincil özellikleri listeler <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri.  
  
|Özellik|Sınıflar|Açıklama|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>ve türetilmiş sınıfları|Alır veya ayarlar (üst bilgi hücreler dahil), tüm denetim bir sütunda veya satırda tüm hücreleri tarafından kullanılan varsayılan stilleri.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya ayarlar denetimindeki tüm satırları tarafından kullanılan varsayılan hücre stilleri. Bu hücre üst bilgisi içermez.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya ayarlar alternatif satırlar denetimi tarafından kullanılan varsayılan hücre stilleri. Büyük defter benzeri efektini oluşturmak için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya ayarlar denetimin satır başlıkları tarafından kullanılan varsayılan hücre stilleri. Görsel stiller etkinleştirilip etkinleştirilmediğini geçerli tema tarafından geçersiz kılındı.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya ayarlar denetimin sütun başlıkları tarafından kullanılan varsayılan hücre stilleri. Görsel stiller etkinleştirilip etkinleştirilmediğini geçerli tema tarafından geçersiz kılındı.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> ve türetilen sınıflar|Alır veya hücre düzeyinde belirtilen stilini ayarlar. Bu stil daha yüksek düzeylerinden devralınan ayarları geçersiz kılar.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>ve türetilmiş sınıfları|Hücre, satır veya sütun üst düzey devralınan stilleri dahil olmak üzere, uygulanan stiller alır.|  
  
 Yukarıda belirtildiği gibi otomatik olarak bir stil özelliğinin değeri alınırken yeni bir örneğini oluşturur <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği daha önce ayarlanmamışsa, nesne. Bu nesneler gereksiz yere oluşturmaktan kaçınmak için satır ve sütun sınıfları sahip bir <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> belirlemek için denetleme özelliği olup olmadığını <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> özelliğini ayarlayın. Benzer şekilde, hücre sınıflara sahip bir <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> gösteren özellik olup olmadığını <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğini ayarlayın.  
  
 Stil özelliklerin her birini karşılık gelen sahip *PropertyName* `Changed` olayda <xref:System.Windows.Forms.DataGridView> denetimi. Satır, sütun ve hücre özellikleri için olay adı ile başlayan "`Row`","`Column`", veya "`Cell`" (örneğin, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Karşılık gelen style özelliği farklı olarak ayarlandığında bu olayların her biri gerçekleşir <xref:System.Windows.Forms.DataGridViewCellStyle> nesne. Bu olaylar oluşmaz nenesi bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi bir stil özelliği ve özellik değerlerini değiştirebilirsiniz. Hücre stili nesnelerinin kendileri yapılan değişikliklere yanıt vermek için tanıtıcı <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> olay.  
  
## <a name="style-inheritance"></a>Stil Devralımı  
 Her <xref:System.Windows.Forms.DataGridViewCell> gelen görünümünü alır, <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği. <xref:System.Windows.Forms.DataGridViewCellStyle> Bu özellik tarafından döndürülen nesne türü özelliklerinin bir hiyerarşiden değerlerini devralır <xref:System.Windows.Forms.DataGridViewCellStyle>. Bu özellikler hangi sırayla aşağıda listelenen <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> üst bilgisi olmayan hücre değerlerini alır.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca hücrelerde için tek dizin numaralarını bulunan satırlar)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır ve sütun üst bilgisi hücreler için <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği, verilen sırayla kaynak özellikleri aşağıdaki listeden değerlerle doldurulur.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Aşağıdaki diyagram bu işlemi göstermektedir.  
  
 ![DataGridViewCellStyle türünün özellikleri](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells devralma diyagramı")  
  
 Ayrıca, belirli satırlar ve sütunlar tarafından devralınan stilleri erişebilir. Sütun <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> özellik değerleri aşağıdaki özelliklerine devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özellik değerleri aşağıdaki özelliklerine devralır.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca hücrelerde için tek dizin numaralarını bulunan satırlar)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Her bir özellik için bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi tarafından döndürülen bir `InheritedStyle` özelliği, özellik değeri öğesinden alınan dışında bir değere ayarlayın karşılık gelen özelliği uygun listedeki ilk hücre stili <xref:System.Windows.Forms.DataGridViewCellStyle> Varsayılanları sınıfı.  
  
 Aşağıdaki tabloda gösterilmiştir nasıl <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> özellik değeri için bir örnek hücre içeren kendi sütundan devralınır.  
  
|özellik türü `DataGridViewCellStyle`|Örnek `ForeColor` alınan nesne değeri|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Bu durumda, <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> değerdir hücrenin satırdan listedeki ilk gerçek değeri. Bu duruma <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hücrenin özelliği değerinin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Aşağıdaki diyagramda gösterilmektedir nasıl farklı <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerini farklı yerden değerlerini devralır.  
  
 ![DataGridView özelliği&#45;değeri devralma](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells değeri devralma diyagramı")  
  
 Stil devralımı avantajlarından yararlanarak, aynı bilgilerin birden fazla yerde belirtmenize gerek kalmadan tüm denetim için uygun stiller sağlayabilir.  
  
 Üstbilgi hücresi içinde stil devralımı açıklandığı katılmak olsa da, nesneler tarafından döndürülen <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView> denetim sahibi tarafından döndürülen nesnenin özellik değerlerini geçersiz kılar, ilk özellik değerleri <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği. Tarafından döndürülen nesne için ayarlanan özellikleri isteyip istemediğinizi <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> satır ve sütun üst bilgileri için uygulanacak özelliği tarafından döndürülen nesnelere karşılık gelen özelliklerini ayarlamalısınız <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> gösterilen özellikler için varsayılan için <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı.  
  
> [!NOTE]
>  Görsel stiller etkinleştirilirse, satır ve sütun üst bilgilerinin (dışında <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) bu özellikleri tarafından belirtilen herhangi bir stil geçersiz kılma geçerli temayı tarafından otomatik olarak biçimlendirilmiş.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, Ve <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> türleri de bazı değerler sütunu tarafından döndürülen nesne başlatmak <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliği. Daha fazla bilgi için bkz. Bu türler için başvuru belgeleri.  
  
## <a name="setting-styles-dynamically"></a>Dinamik olarak stillerini ayarlama  
 Belirli değerlerle hücre stilleri özelleştirmek için bir işleyici uygulamak <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. Bu olay işleyicilerine bağımsız değişkeninin alma <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> türü. Bu nesne konumunda birlikte biçimlendirilen hücrenin değerini belirlemenize olanak tanıyan özellikler içerir <xref:System.Windows.Forms.DataGridView> denetimi. Bu nesne de içeren bir <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> değeri olarak başlatılan özelliği <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> biçimlendirilen hücrenin özelliği. Hücre değerini ve konum için uygun stil bilgilerini belirtmek için hücre stili özellikleri değiştirebilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> Ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> olaylar ayrıca Al bir <xref:System.Windows.Forms.DataGridViewCellStyle> olay veri nesnesi, ancak isteğe bağlı olarak kendi durumda satır kopyası olan <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özellik salt okunur amaçları ve bu değişiklikler, Denetim etkilemez.  
  
 Olaylara yanıt olarak tek tek hücre stilleri gibi de dinamik olarak değiştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olayları. Örneğin, bir işleyici içinde <xref:System.Windows.Forms.DataGridView.CellMouseEnter> olay hücre arka plan rengi geçerli değerini saklayabilirsiniz (hücrenin alınan <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği), üzerine fare geldiğinde hücreyi vurgulayın yeni bir renk kümesi. İçin bir işleyici içinde <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olay, arka plan rengi sonra özgün değerine geri yükleyebilirsiniz.  
  
> [!NOTE]
>  Hücrenin içinde depolanan değerleri önbelleğe alma <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği belirli stil değeri ayarlanma şeklinden bağımsız olarak önemlidir. Geçici olarak bir stil ayarı değiştirirseniz, özgün "ayarlı değil" durumuna geri da style ayarını daha yüksek bir düzeyinden devralınması için hücre geri gider sağlar. Hücre stili olup devralınır bağımsız olarak geçerli bir hücre gerçek stilini belirlemek gerekiyorsa kullanın <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği.  
  
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
- [Windows Forms DataGridView Denetimindeki Veri Biçimleri](data-formatting-in-the-windows-forms-datagridview-control.md)
