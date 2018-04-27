---
title: DataGrid Denetimine Genel Bakış (Windows Forms)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd74ed0e31fff211f0197ad27f297f9fbecf5cab
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetim dizi satırları ve sütunları verileri görüntüler. Kılavuz hiçbir ilişki içeren tek bir tablo ile bir veri kaynağına bağlandığında basit bir durumdur. Bu durumda, verileri basit satırları ve sütunları, elektronik tablo olduğu gibi görüntülenir. Diğer denetimlere veri bağlama hakkında daha fazla bilgi için bkz: [verileri bağlama ve Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
 Varsa <xref:System.Windows.Forms.DataGrid> birden çok verilerle bağlı ilgili tabloları ve gezinti kılavuzda etkinleştirilirse, kılavuz her satır Genişleticileri görüntüleyin. Bulunan bir genişletici, kullanıcı bir üst tablodan alt tabloya taşıyabilirsiniz. Bir düğüm tıklatarak alt tablo ve geri düğmesini tıklatarak özgün üst tablo görüntüler. Bu şekilde, tablolar arasındaki hiyerarşik ilişkileri kılavuz görüntüler.  
  
 Aşağıdaki ekran görüntüsünde, birden çok tablo ile veri DataGrid bağlı gösterir.  
  
 ![DataGrid verilerle birden çok tablo ile ilişkili](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
Birden çok tablo verileriyle ilişkili bir DataGrid  
  
 <xref:System.Windows.Forms.DataGrid> Bir kullanıcı arabirimi bir veri kümesi, ilişkili tablolar ve biçimlendirme ve düzenleme özellikleri zengin arasında gezinme için sağlayabilir.  
  
 Veri işleme ve görüntü ayrı işlevlerdir: veri güncelleştirmeleri Windows Forms veri bağlama mimarisi ve göre işlenir ancak kullanıcı arabirimi denetim işleme [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları. Bu nedenle, aynı veri kaynağına bağlı birden çok denetimin eşitlenmiş kalır.  
  
> [!NOTE]
>  Visual Basic 6.0 DataGrid denetiminde biliyorsanız, Windows Forms önemli farklılıklar bulacaksınız <xref:System.Windows.Forms.DataGrid> denetim.  
  
 Ne zaman kılavuz bağlı bir <xref:System.Data.DataSet>, satırları ve sütunları otomatik olarak oluşturulan, biçimlendirilmiş doldurulmuş ve. Daha fazla bilgi için bkz: [verileri bağlama ve Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md). Nesil aşağıdaki <xref:System.Windows.Forms.DataGrid> denetimi ekleyebilir, silin, yeniden ve sütunları ve satırları gereksinimlerinize bağlı olarak biçimlendirme.  
  
## <a name="binding-data-to-the-control"></a>Denetimine veri bağlama  
 İçin <xref:System.Windows.Forms.DataGrid> çalışmaya denetlemek, kullanarak bir veri kaynağı bağlanmalıdır <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> tasarım zamanında özelliklerini veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> çalışma zamanında yöntemi. Bu bağlama noktaları <xref:System.Windows.Forms.DataGrid> örneklenen veri kaynağı nesneye gibi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Denetim verileri üzerinde gerçekleştirilen eylemler sonuçlarını gösterir. Çoğu veri özel eylemler ile gerçekleştirilmez <xref:System.Windows.Forms.DataGrid> , ancak bunun yerine veri kaynağı üzerinden.  
  
 Veri bağlama kümesindeki herhangi bir mekanizma aracılığıyla güncelleştirdiyseniz <xref:System.Windows.Forms.DataGrid> denetimi değişiklikleri yansıtır. Veri Kılavuzu ve tablo stilleri ve sütun stilleri varsa `ReadOnly` özelliğini `false`, veri kümesindeki aracılığıyla güncelleştirilebilir <xref:System.Windows.Forms.DataGrid> denetim.  
  
 Yalnızca bir tablo içinde gösterilmesi <xref:System.Windows.Forms.DataGrid> birer birer. Tablolar arasında bir üst-alt ilişkisi tanımlanmış olması durumunda, kullanıcı görüntülenmesini tabloyu seçmek için ilişkili tablolar arasında taşıyabilirsiniz <xref:System.Windows.Forms.DataGrid> denetim. Bağlama hakkında bilgi için bir <xref:System.Windows.Forms.DataGrid> denetimini bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] tasarım zamanında veya çalışma zamanı, veri kaynağı [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Geçerli veri kaynakları için <xref:System.Windows.Forms.DataGrid> içerir:  
  
-   <xref:System.Data.DataTable> sınıfı  
  
-   <xref:System.Data.DataView> sınıfı  
  
-   <xref:System.Data.DataSet> sınıfı  
  
-   <xref:System.Data.DataViewManager> sınıfı  
  
 Kaynağınız bir veri kümesi ise, veri kümesi biçiminde bir nesne veya forma bir XML Web hizmeti tarafından geçirilen bir nesne olabilir. Yazılı veya yazılmayan veri kümeleri ile bağlayabilirsiniz.  
  
 Ayrıca bağlayabileceğiniz bir <xref:System.Windows.Forms.DataGrid> yapısında bir dizideki öğeler gibi nesneler genel özelliklerini ortaya varsa ek yapılara denetim. Kılavuz öğeleri tüm ortak özellikleri yapısında görüntüler. Örneğin, bağlarsanız <xref:System.Windows.Forms.DataGrid> müşterinin bir dizi denetim nesneleri, kılavuz tüm ortak bu müşteri nesnelerin özelliklerini görüntüler. Bazı durumlarda, bu yapısına bağlayabilirsiniz ancak elde edilen ilişkili yapısı pratik uygulama olmayabilir anlamına gelir. Örneğin, tamsayı, bir dizi bağlayabilirsiniz ancak çünkü `Integer` kılavuz herhangi bir veri görüntüleyemiyor, veri türü ortak bir özelliği desteklemiyor.  
  
 Ortak Özellikler öğelerini kullanıma varsa aşağıdaki yapıları bağlayabilirsiniz:  
  
-   Uygulayan herhangi bir bileşenin <xref:System.Collections.IList> arabirimi. Bu, tek boyutlu diziler içerir.  
  
-   Uygulayan herhangi bir bileşenin <xref:System.ComponentModel.IListSource> arabirimi.  
  
-   Uygulayan herhangi bir bileşenin <xref:System.ComponentModel.IBindingList> arabirimi.  
  
 Olası veri kaynakları hakkında daha fazla bilgi için bkz: [veri kaynaklarını Windows Forms tarafından desteklenen](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Kılavuz görüntüleme  
 Yaygın kullanımı <xref:System.Windows.Forms.DataGrid> denetimidir veri kümesinden tek bir tabloyu görüntülemek için. Ancak, Denetim ilişkili tabloları dahil olmak üzere birden çok tablo görüntülemek için de kullanılabilir. Izgaranın görüntü veri kaynağına göre otomatik olarak düzeltilir. Aşağıdaki tabloda, çeşitli yapılandırmaları görüntülenenleri gösterir.  
  
|Veri kümesi içeriğini|Görüntülenenleri|  
|--------------------------|-----------------------|  
|Tek tablo.|Tablo kılavuzda görüntülenir.|  
|Birden çok tablo.|Kılavuz kullanıcılar görüntülemek istedikleri tablo bulmaya gezinebilir ağaç görünümünde görüntüleyebilirsiniz.|  
|Birden fazla ilgili tablo.|Kılavuz tablolarla seçmek için ağaç görünümünde görüntüleyebilir veya kılavuz üst tablo görüntüleme belirtebilirsiniz. Üst tablo kayıtlarında ilgili alt satırlara gitmek açmalarına olanak tanır.|  
  
> [!NOTE]
>  Bir veri kümesi tablolarda kullanarak ilgili bir <xref:System.Data.DataRelation>.  Ayrıca bkz. [HYPERLINK "http://msdn.microsoft.com/library/dbwcse3d(v=vs.110)" kümelerindeki ilişkiler](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\)) veya [kümelerindeki ilişkiler](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\)).  
  
 Zaman <xref:System.Windows.Forms.DataGrid> denetim bir tablo görüntüleme ve <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> özelliği ayarlanmış `true`, veri tekrar sütun üstbilgilerini tıklatarak. Kullanıcı ayrıca satır ekleme ve hücreleri düzenleyin.  
  
 Bir tablo kümesi arasındaki ilişkileri Gezinti üst/alt yapısını kullanarak kullanıcılara görüntülenir. Üst tablo en yüksek düzeyde veri, ve alt tablolar üst tablolar tek tek listelerinde türetilmiş veri tabloları. Genişleticileri alt tabloyu içeren her üst satır görüntülenir. Bir Genişletici tıklatarak alt tablolar için Web benzeri bağlantıların listesini oluşturur. Kullanıcı bağlantısını seçtiğinde alt tablo görüntülenir. Göster/Gizle üst satırları simgesine tıklayarak (![Göster&#47;üst satırları simgesini gizle](../../../../docs/framework/winforms/controls/media/vbicon.gif "vbIcon")) üst tablo hakkında bilgi gizlemek veya kullanıcı daha önce gizli değilse yeniden neden. Kullanıcı daha önce görüntülenen tabloya geri taşımak için bir geri düğmesini tıklatabilirsiniz.  
  
## <a name="columns-and-rows"></a>Satırları ve sütunları  
 <xref:System.Windows.Forms.DataGrid> Bir koleksiyonundan oluşur <xref:System.Windows.Forms.DataGridTableStyle> bulunan nesneleri <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği. Tablo Stili koleksiyonu içerebilir <xref:System.Windows.Forms.DataGridColumnStyle> bulunan nesneleri <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>... Düzenleyebileceğiniz <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ve <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> üzerinden erişilen koleksiyon düzenleyiciler kullanarak özellikleri **özellikleri** penceresi.  
  
 Tüm <xref:System.Windows.Forms.DataGridTableStyle> ile ilişkili <xref:System.Windows.Forms.DataGrid> denetim üzerinden erişilebilir <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> İle Tasarımcısı'nda düzenlenebilir <xref:System.Windows.Forms.DataGridTableStyle> koleksiyon Düzenleyicisi'ni veya üzerinden programlı olarak <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği.  
  
 ![DataGrid denetimine eklenen nesneler](../../../../docs/framework/winforms/controls/media/vbcolumns1.gif "vbColumns1")  
Aşağıdaki çizimde DataGrid denetiminde dahil olan nesneleri gösterir.  
  
 Tablo Stilleri ve sütun stilleri ile eşitlenir <xref:System.Data.DataTable> nesneleri ve <xref:System.Data.DataColumn> ayarlayarak nesneleri kendi `MappingName` uygun özellikleri <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataColumn.ColumnName%2A> özellikleri. Zaman bir <xref:System.Windows.Forms.DataGridTableStyle> hiçbir sütun olan stiller eklenir bir <xref:System.Windows.Forms.DataGrid> geçerli bir veri kaynağı için bağlı olan denetim ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Bu tablo stili özelliği geçerli bir ayarlanmış <xref:System.Data.DataTable.TableName%2A> özelliği, bir koleksiyonu <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri için oluşturulur Tablo stili. Her <xref:System.Data.DataColumn> bulunan <xref:System.Data.DataTable.Columns%2A> koleksiyonu <xref:System.Data.DataTable>, karşılık gelen <xref:System.Windows.Forms.DataGridColumnStyle> eklenen <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> üzerinden erişilen <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>. Sütun eklenemez veya kılavuz kullanımından silinmiş <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> veya <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> yöntemi <xref:System.Windows.Forms.GridColumnStylesCollection>. Daha fazla bilgi için bkz: [nasıl yapılır: eklemek tabloları ve sütunları Windows Forms DataGrid denetimi için](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) ve [nasıl yapılır: Delete ya da Windows Forms DataGrid denetiminde sütunları gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Sütun türleri koleksiyonunu genişletir <xref:System.Windows.Forms.DataGridColumnStyle> zengin biçimlendirme ve düzenleme özellikleri ile sınıfı. Tüm sütun türleri devralınmalıdır <xref:System.Windows.Forms.DataGridColumnStyle> temel sınıfı. Oluşturulan sınıf bağlıdır <xref:System.Data.DataColumn.DataType%2A> özelliği <xref:System.Data.DataColumn> içinden <xref:System.Web.UI.WebControls.DataGridColumn> dayanır. Örneğin, bir <xref:System.Data.DataColumn> olan kendi <xref:System.Data.DataColumn.DataType%2A> özelliğini <xref:System.Boolean> ile ilişkili <xref:System.Windows.Forms.DataGridBoolColumn>. Aşağıdaki tabloda bu sütun türleri açıklanmaktadır.  
  
|Sütun türü|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Kabul eder ve veri biçimlendirilmiş veya biçimlendirilmemiş dizeleri görüntüler. Düzenleme yetenekleri olan, aynı, basit bir veri düzenleme için oldukları gibi <xref:System.Windows.Forms.TextBox>. Öğesinden devralınan <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Kabul eder ve görüntüler `true`, `false`ve null değerleri. Öğesinden devralınan <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Bir sütun sağ köşesine çift kendi tam başlık ve geniş girdiye görüntülenecek sütun yeniden boyutlandırır.  
  
## <a name="table-styles-and-column-styles"></a>Tablo Stilleri ve sütun stilleri  
 Varsayılan biçimi kurulan hemen <xref:System.Windows.Forms.DataGrid> denetimi, belirli tabloları veri ızgara içinde görüntülendiğinde, kullanılacak renkleri özelleştirebilirsiniz.  
  
 Bu örnekleri oluşturarak elde edilir <xref:System.Windows.Forms.DataGridTableStyle> sınıfı. Tablo Stilleri belirtin belirli tablolar, varsayılan biçimlendirmesini öğesinden farklı biçimlendirme <xref:System.Windows.Forms.DataGrid> denetimi. Her tablo yalnızca bir tablo stili aynı anda tanımlı olabilir.  
  
 Bazı durumlarda, belirli veri tablonun sütunlarının geri kalanından farklı bir özel sütun görünüm isteyeceksiniz. Özelleştirilmiş bir sütun stilleri kullanarak oluşturabileceğiniz <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği.  
  
 Sütun stilleri tablo stilleri veri tablolarına yalnızca ilişkili gibi bir veri kümesinde sütun ilgilidir. Yalnızca her tablo yalnızca sahip çok her sütun için aynı anda, bu nedenle tanımlı bir tablo stili yalnızca olarak bir sütun stili onun için belirli Tablo stilinde tanımladınız. Bu ilişki sütunun içinde tanımlanan <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliği.  
  
 Kendisine eklenmiş sütun stilleri olmadan bir tablo stili oluşturduysanız, Visual Studio çalışma zamanında form ve kılavuz oluşturduğunuzda varsayılan sütun stilleri ekler. Ancak, Visual Studio tablo stili oluşturduysanız ve tüm sütun stilleri kendisine eklenmiş sütun stilleri oluşturmaz. Ayrıca, sütun stilleri tanımlayın ve onlara kılavuzunda görünmesini istediğiniz sütunları için eşleme adla atamak gerekir.  
  
 Bir sütun stili atayarak veri kılavuzunda dahil hangi sütunları belirtin ve hiçbir sütun stili sütunlara atanmış olduğundan kılavuzda görüntülenmez dataset veri sütunlarını dahil edebilirsiniz. Ancak, veri sütun kümesinde yer aldığından görüntülenmez verileri programlı olarak düzenleyebilirsiniz.  
  
> [!NOTE]
>  Genel olarak, sütun stilleri oluşturabilir ve bunları tablo stilleri tablo stilleri koleksiyona eklemeden önce sütunu stilleri koleksiyonuna ekleyin. Koleksiyona bir boş tablo stili eklediğinizde, sütun stilleri sizin için otomatik olarak oluşturulur. Yeni sütun stilleri yinelenen ile eklemeyi denediğinizde sonuç olarak, bir özel durum oluşturulacak <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sütun stilleri koleksiyonunda değerleri.  
>   
>  Bazı durumlarda, yalnızca bir sütun birçok sütunlar arasında ince ayar istersiniz; Örneğin, 50 sütunları veri kümesini içerir ve bunların 49 yalnızca istiyorsunuz. Bu durumda, tüm 50 sütunları almak ve program aracılığıyla bir kaldırmak daha kolay yerine istediğiniz program aracılığıyla her 49 tek tek sütun ekleme.  
  
## <a name="formatting"></a>Biçimlendirme  
 Uygulanabilir biçimlendirme <xref:System.Windows.Forms.DataGrid> Denetim kenarlık stilleri, kılavuz çizgisi stilleri, yazı tipi, resim yazısı özellikleri, veri hizalama ve arka plan renklerini satırları arasında değişen içerir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Olaylar  
 Ortak yanı sıra denetim olayları gibi <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, ve <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> denetimi, düzenleme ve kılavuz içinde gezinme ilişkili olayları destekler. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Özelliği, hangi hücrenin seçili belirler. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Olay kullanıcı yeni hücreye gittiğinde oluşur. Kullanıcı yeni bir tablo üst/alt ilişkisi aracılığıyla gittiğinde <xref:System.Windows.Forms.DataGrid.Navigate> olayı oluşturulur. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Kullanıcı geri düğmesini tıklattığında kullanıcının bir alt tablo görüntülerken olayı oluşturulur ve <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> Göster/Gizle üst satırları simgesine tıklandığında olayı oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)
