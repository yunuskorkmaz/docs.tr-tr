---
title: Windows Forms DataGridView Denetimindeki Hücre Stilleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 463fbbffe1e88991934f08fbe7e7445b2e233081
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529665"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Hücre Stilleri
Her hücrede <xref:System.Windows.Forms.DataGridView> denetim metin biçimi, arka plan rengi, ön plan renk ve yazı tipi gibi kendi stil sahip olabilir. Genellikle, ancak, birden çok hücreyi belirli stil özellikleri paylaşır.  
  
 Stilleri paylaşmak hücre grupları belirli satır veya sütun, belirli değerleri içeren tüm hücreleri veya tüm hücre içindeki tüm hücreleri denetiminde içerebilir. Bu gruplar çakışıyor olduğundan, her bir hücre birden fazla yerde stil bilgilerini alabilirsiniz. Örneğin, her hücre istediğiniz bir <xref:System.Windows.Forms.DataGridView> kırmızı ön plan rengini kullanmak için negatif sayıları ile aynı yazı tipi, ancak yalnızca para birimi biçimi kullanılacak para birimi sütunlardaki hücrelerde ve yalnızca para birimi hücreleri kullanılacak denetim.  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfı  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıfı için görsel stil ilgili aşağıdaki özellikleri içerir:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> Ve <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> Ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Ayrıca bu sınıf, biçimlendirme için ilgili aşağıdaki özellikleri içerir:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Ve <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> Ve <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Bu özellikler ve diğer hücre stili özellikleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.DataGridViewCellStyle> başvuru belgeleri ve konuları ayrıca aşağıdaki bölümde listelenen.  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle nesnelerini kullanma  
 Alabilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle> çeşitli özelliklerini nesnelerden <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, ve <xref:System.Windows.Forms.DataGridViewCell> sınıflar ve onların türetilmiş sınıflar. Değerini alma yeni bir oluşturur, bu özelliklerden birini henüz ayarlanmamış, <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi. Ayrıca kendi örneğini oluşturabilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri ve bu özellikler atayın.  
  
 Stil bilgilerini, gereksiz çoğaltılmasını paylaşarak önleyebilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri arasında birden çok <xref:System.Windows.Forms.DataGridView> öğeler. Yukarıdaki düzeylerinden farklı her düzeyde yalnızca bu stil özellikleri ayarlayarak, Denetim, sütun ve her düzeyini hücre düzeye aşağı satır düzeyleri filtresinden stilleri ayarlama çünkü stili çoğaltma önleyebilirsiniz. Bunu izleyen stil devralma bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Aşağıdaki tabloda almak veya ayarlamak birincil özellikleri listeler <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri.  
  
|Özellik|Sınıflar|Açıklama|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>ve türetilmiş sınıflar|Alır veya ayarlar (üstbilgi hücreler dahil), tüm denetiminde bir sütun veya satır tüm hücreleri tarafından kullanılan varsayılan stilleri.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya tüm satırları denetimi tarafından kullanılan varsayılan hücre stillerini ayarlar. Bu üst bilgi hücresini içermez.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya denetiminde satırların değişerek tarafından kullanılan varsayılan hücre stillerini ayarlar. Büyük defter benzeri efekti oluşturmak için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya denetimin satır üstbilgilerinin tarafından kullanılan varsayılan hücre stillerini ayarlar. Görsel stiller etkinleştirilirse geçerli tema tarafından geçersiz kılındı.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Alır veya denetimin sütun üstbilgileri tarafından kullanılan varsayılan hücre stillerini ayarlar. Görsel stiller etkinleştirilirse geçerli tema tarafından geçersiz kılındı.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> ve türetilen sınıflar|Alır veya hücre düzeyinde belirtilen stilini ayarlar. Bu stiller yüksek düzeylerinden devralınan geçersiz kılar.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>ve türetilmiş sınıflar|Hücre, satır veya sütun, daha yüksek düzeylerinden devralınan stilleri dahil olmak üzere uygulanan tüm stilleri alır.|  
  
 Yukarıda belirtildiği gibi bir stil özelliğinin değeri otomatik olarak alma yeni bir örneğini oluşturur <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği daha önce ayarlanmamışsa, nesne. Bu nesneler gereksiz yere oluşturmamak için satır ve sütun sınıfları sahip bir <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> belirlemek için kontrol edebilirsiniz özelliği olup olmadığını <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> özelliğini ayarlayın. Benzer şekilde, hücre sınıfları sahip bir <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> gösteren özellik olup olmadığını <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliğini ayarlayın.  
  
 Her bir stil özelliğine karşılık gelen bir vardır *PropertyName* `Changed` olayda <xref:System.Windows.Forms.DataGridView> denetim. Satır, sütun ve hücre özellikleri için olayın adı ile başlayan "`Row`","`Column`", veya "`Cell`" (örneğin, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Karşılık gelen stil özelliği farklı olarak ayarlandığında bu olayların her biri oluşur <xref:System.Windows.Forms.DataGridViewCellStyle> nesnesi. Bu olaylar, aldığınızda gerçekleşmez bir <xref:System.Windows.Forms.DataGridViewCellStyle> nesne stili özelliğinden ve özellik değerlerini değiştirin. Hücre stili nesnelerinin kendilerini yapılan değişikliklere yanıt vermesi işlemek <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> olay.  
  
## <a name="style-inheritance"></a>Stil devralma  
 Her <xref:System.Windows.Forms.DataGridViewCell> gelen görünümünü alır, <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği. <xref:System.Windows.Forms.DataGridViewCellStyle> Bu özellik tarafından döndürülen nesne türünün özelliklerini hiyerarşiden değerlerini devralır <xref:System.Windows.Forms.DataGridViewCellStyle>. Bu özellikler aşağıda hangi sırayla listelenir <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> üstbilgi olmayan hücre değerlerini alır.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca hücrelerde için tek dizin numaralarını bulunan satırlar)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Üstbilgi hücre, satır ve sütun için <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği, verilen sırayla kaynak özelliklerinin aşağıdaki listeden değerlerle doldurulur.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> Veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Aşağıdaki diyagram bu işlemi gösterilmektedir.  
  
 ![DataGridViewCellStyle türünün özellikleri](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 Belirli satırlar ve sütunlarla devralınan stilleri de erişebilirsiniz. Sütun <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> özellik değerlerini aşağıdaki özelliklerinden devralır.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Satır <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özellik değerlerini aşağıdaki özelliklerinden devralır.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (yalnızca hücrelerde için tek dizin numaralarını bulunan satırlar)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Her bir özellik için bir <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen nesne bir `InheritedStyle` özelliği, özellik değeri elde edilir değerine dışında karşılık gelen özelliği ayarlanmış uygun listedeki ilk hücre stili gelen <xref:System.Windows.Forms.DataGridViewCellStyle> sınıf Varsayılanları.  
  
 Aşağıdaki tabloda gösterilmektedir nasıl <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> bir örnek hücre için özellik değeri içeren sütundan devralınır.  
  
|özellik türü `DataGridViewCellStyle`|Örnek `ForeColor` alınan nesne için değer|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Bu durumda, <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> değerdir hücrenin satırdan listedeki ilk gerçek değer. Bu duruma <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hücrenin özellik değerinin <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Aşağıdaki diyagramda gösterilmektedir nasıl farklı <xref:System.Windows.Forms.DataGridViewCellStyle> özellikleri farklı yerlerden değerlerine devral.  
  
 ![DataGridView özellik&#45;değer devralma](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 Stil devralma yararlanarak, aynı bilgilerin birden fazla yerde belirtmek zorunda kalmadan için tüm denetim uygun stiller sağlayabilir.  
  
 Üstbilgi hücre stili devralma açıklandığı gibi katılmak rağmen nesneleri tarafından döndürülen <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView> denetiminiz tarafından döndürülen nesnenin özellik değerleri geçersiz kılmak başlangıç özellik değerlerini <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği. Özellikleri tarafından döndürülen nesne için ayarlanmış isteyip istemediğinizi <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> satır ve sütun üstbilgilerini uygulamak için özellik tarafından döndürülen nesnelerin karşılık gelen özelliklerini ayarlamanız gerekir <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> Varsayılanları özelliklerine belirtilen için <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı.  
  
> [!NOTE]
>  Görsel stiller etkinleştirilirse, satır ve sütun başlıkları (dışında <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) bu özellikleri tarafından belirtilen stillerini geçersiz kılma geçerli tema tarafından otomatik olarak biçimlendirilmiş.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, Ve <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> türleri ayrıca bazı değerler sütunu tarafından döndürülen nesnenin başlatma <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliği. Daha fazla bilgi için bu tür için başvuru belgelerine bakın.  
  
## <a name="setting-styles-dynamically"></a>Stilleri dinamik olarak ayarlama  
 Belirli değerleri içeren bir hücre stilleri özelleştirmek için bir işleyici uygulamak <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. Bu olay işleyicileri alma bağımsız değişkeninin <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> türü. Bu nesne konumunda birlikte biçimlendirilen hücrenin değerini belirlemenize olanak sağlayan özellikler içerir <xref:System.Windows.Forms.DataGridView> denetim. Bu nesne de içeren bir <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> değerine başlatılmış özelliği <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> biçimlendirilen hücrenin özelliği. İçin bir hücre değerini ve konum uygun stil bilgilerini belirtmek için hücre stili özelliklerini değiştirebilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> Ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> olayları de alırsınız bir <xref:System.Windows.Forms.DataGridViewCellStyle> olay veri nesnesi, ancak kendi durumda da, bu satırın bir kopyasını <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> özelliği salt okunur amaçlıdır ve yapılan değişikliklerin için denetimi etkilemez.  
  
 Olaylarına yanıt olarak tek tek hücre stilleri gibi ayrıca dinamik olarak değiştirmek <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olaylar. Örneğin, bir işleyici içinde <xref:System.Windows.Forms.DataGridView.CellMouseEnter> olay, hücre arka plan rengi geçerli değeri saklayabilirsiniz (hücrenin alınan <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği), fare üzerine geldiğinde, hücre vurgular yeni bir renk kümesi. İçin bir işleyici içinde <xref:System.Windows.Forms.DataGridView.CellMouseLeave> olay, arka plan rengi daha sonra özgün değere geri yükleyebilirsiniz.  
  
> [!NOTE]
>  Hücrenin içinde depolanan verileri önbelleğe alma <xref:System.Windows.Forms.DataGridViewCell.Style%2A> özelliği belirli stili değerini ayarlayın bağımsız olarak önemlidir. Geçici olarak bir stil ayarı değiştirirseniz, özgün "ayarlı değil" durumuna geri daha yüksek bir düzeyinden stil ayarı devralma için hücre geri gider sağlar. Stil olup devralınan bağımsız olarak bir hücre yürürlükte gerçek stilini belirlemek gereksinim duyarsanız hücrenin kullanın <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
