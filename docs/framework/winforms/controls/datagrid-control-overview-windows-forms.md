---
title: DataGrid Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
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
ms.openlocfilehash: 7c9442635bb193c13ca30fd1e271631a43b33e55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589024"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetim dizi satır ve sütun verilerini görüntüler. Kılavuz hiçbir ilişki içeren tek bir tablo ile bir veri kaynağına bağlandığında en basit durum geçerlidir. Bu durumda, verileri basit satırları ve sütunları, bir elektronik tablo olduğu gibi görüntülenir. Diğer denetimlere veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).  
  
 Varsa <xref:System.Windows.Forms.DataGrid> birden çok veri bağlı ilgili tabloları ve gezinti Kılavuzu'nun etkinleştirilirse, kılavuz Genişleticileri her satır görüntülenir. İle bir genişletici, kullanıcı, üst tablodan alt tabloya taşıyabilirsiniz. Bir düğüm tıklayarak alt tablo ve geri düğmesine tıklayarak özgün üst tablo görüntüler. Bu şekilde, kılavuz tablolar arasındaki hiyerarşik ilişkileri görüntüler.  
  
 Bir DataGrid birden fazla tabloyu verilerle ilişkili aşağıdaki ekran görüntüsünde gösterilmektedir:  
  
 ![Bir DataGrid gösteren bir WinForms uygulaması birden fazla tabloyu verilerle ilişkili.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)  
  
 <xref:System.Windows.Forms.DataGrid> Bir kullanıcı arabirimi için bir veri kümesi, ilgili tabloları ve zengin biçimlendirme ve düzenleme özellikleri arasında gezinmeyi sağlayabilir.  
  
 Veri işleme ve görüntü ayrı işlevler şunlardır: Veri güncelleştirmeleri, Windows Forms veri bağlama mimarisi ve .NET Framework veri sağlayıcıları tarafından işlenir ancak kullanıcı arabirimi denetimi gerçekleştirir. Bu nedenle, aynı veri kaynağına bağlı birden çok denetimin eşitlenmiş durumda kalır.  
  
> [!NOTE]
>  Visual Basic 6.0 DataGrid denetiminde biliyorsanız, bazı önemli farklılıklar Windows Forms bulabilirsiniz <xref:System.Windows.Forms.DataGrid> denetimi.  
  
 Ne zaman kılavuz bağlı bir <xref:System.Data.DataSet>, satırlar ve sütunlar otomatik olarak oluşturulan, biçimlendirilmiş doldurulmuş ve. Daha fazla bilgi için [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md). Oluşturulmasını izleyen <xref:System.Windows.Forms.DataGrid> denetimi ekleyin, silebilir, yeniden ve sütunları ve satırları gereksinimlerinize bağlı olarak biçimlendirin.  
  
## <a name="binding-data-to-the-control"></a>Veriyi denetime bağlama  
 İçin <xref:System.Windows.Forms.DataGrid> çalışmaya denetlemek, kullanarak bir veri kaynağına bağlanması gereken <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> tasarım zamanında özellikleri veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> çalışma zamanında yöntemi. Bu bağlama noktaları <xref:System.Windows.Forms.DataGrid> için oluşturulmuş veri kaynaklı bir nesne gibi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>). <xref:System.Windows.Forms.DataGrid> Denetimi veriler üzerinde gerçekleştirilen eylemler sonuçlarını gösterir. Çoğu veri özgü eylemleri aracılığıyla gerçekleştirilmediğinden <xref:System.Windows.Forms.DataGrid> , ancak bunun yerine veri kaynağı aracılığıyla.  
  
 Herhangi bir mekanizma aracılığıyla ilişkili veri kümesindeki veriler güncelleştirilirse <xref:System.Windows.Forms.DataGrid> denetimi değişiklikleri yansıtır. Veri Kılavuzu ve tablo stillerini ve sütun stil varsa `ReadOnly` özelliğini `false`, veri kümesindeki verileri aracılığıyla güncelleştirilebilir <xref:System.Windows.Forms.DataGrid> denetimi.  
  
 Yalnızca bir tabloya gösterilebileceği <xref:System.Windows.Forms.DataGrid> birer güncelleştirir. Tablolar arasında üst-alt ilişkisi tanımlanmışsa, kullanıcı görüntülenecek tabloyu ilişkili tablolar arasında taşıyabilirsiniz <xref:System.Windows.Forms.DataGrid> denetimi. Bağlama hakkında bilgi için bir <xref:System.Windows.Forms.DataGrid> denetimi bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] tasarım zamanı veya çalışma zamanı, veri kaynağı [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Geçerli veri kaynakları için <xref:System.Windows.Forms.DataGrid> içerir:  
  
- <xref:System.Data.DataTable> Sınıfı  
  
- <xref:System.Data.DataView> Sınıfı  
  
- <xref:System.Data.DataSet> Sınıfı  
  
- <xref:System.Data.DataViewManager> Sınıfı  
  
 Kaynak veri kümesi ise veri kümesi biçiminde bir nesne veya forma bir XML Web hizmeti tarafından geçirilen nesne olabilir. Yazılmış veya yazılmamış veri kümelerine bağlayabilirsiniz.  
  
 Ayrıca adlarınıza bağlayabileceğiniz bir <xref:System.Windows.Forms.DataGrid> denetimini ek yapılarını yapısı, bir dizideki öğeler gibi nesneler genel özellikleri kullanıma sunar. Kılavuz öğeleri tüm genel özelliklerini yapısında görüntüler. Örneğin, bağlarsanız <xref:System.Windows.Forms.DataGrid> müşteri bir dizi denetimi nesneler, kılavuz, tüm genel nesnelerin özelliklerini bu müşteri görüntülenir. Bazı durumlarda, bu yapıya bağlayabilirsiniz olsa da, sonuçta elde edilen ilişkili yapısı uygulaması pratik olmayabilir anlamına gelir. Örneğin, bir tamsayılar dizisi olarak bağlayabilirsiniz, ancak çünkü `Integer` veri türü, ortak bir özelliği desteklemiyor, kılavuz tüm veriler görüntülenemiyor.  
  
 Genel Özellikler öğeleri kullanıma aşağıdaki yapılarını bağlayabilirsiniz:  
  
- Uygulayan herhangi bir bileşeni <xref:System.Collections.IList> arabirimi. Bu, tek boyutlu diziler içerir.  
  
- Uygulayan herhangi bir bileşeni <xref:System.ComponentModel.IListSource> arabirimi.  
  
- Uygulayan herhangi bir bileşeni <xref:System.ComponentModel.IBindingList> arabirimi.  
  
 Olası veri kaynakları hakkında daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Kılavuzu görüntüle  
 Yaygın <xref:System.Windows.Forms.DataGrid> veri kümesinden tek bir tabloyu görüntülenecek denetimidir. Bununla birlikte, Denetim ilişkili tablolar da dahil olmak üzere birden fazla tabloyu görüntülemek için de kullanılabilir. Kılavuz görünümünü veri kaynağına göre otomatik olarak ayarlanır. Aşağıdaki tabloda neler için çeşitli yapılandırmalar görüntülendiğini gösterir.  
  
|Veri kümesi içeriği|Ne görüntülenir|  
|--------------------------|-----------------------|  
|Tek tablo.|Tablo, bir kılavuz şeklinde görüntülenir.|  
|Birden çok tablo.|Kılavuz, kullanıcıların bulmak görüntülenmesini istediğiniz tabloyu gidebilirsiniz ağaç görünümünde görüntüleyebilirsiniz.|  
|Birden çok ilişkili tabloyla.|Kılavuz üst tablo görüntüleme belirtebilirsiniz veya kılavuz tablolarla seçmek için ağaç görünümünde görüntüleyebilirsiniz. Üst tablodaki kayıtların izin ilgili alt satırları gidin.|  
  
> [!NOTE]
> Bir veri kümesindeki tabloları kullanarak ilgili bir <xref:System.Data.DataRelation>. Ayrıca bkz: [veri kümeleri arasında ilişki oluşturma](/visualstudio/data-tools/relationships-in-datasets).
  
 Zaman <xref:System.Windows.Forms.DataGrid> denetimi bir tabloda görüntüleyen ve <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> özelliği `true`, veri tekrar sütun üstbilgilerini tıklatarak. Kullanıcı ayrıca satır ekleme ve hücre düzenleme.  
  
 Bir dizi tablolar arasındaki ilişkileri Gezinti üst/alt yapısını kullanarak kullanıcılara görüntülenir. Üst tablo verileri en üst düzey, ve alt tablolar veri tabloların üst tablolar tek tek kayıtlara türetilmiştir. Genişleticileri alt tabloyu içeren her üst satır görüntülenir. Bir expander tıklayarak alt tablolar Web benzeri bağlantılar listesini oluşturur. Kullanıcı bağlantısını seçtiğinde, alt tablo görüntülenir. Tıklayarak Göster/Gizle üst satırları simgesini ()![Üst satırları simgesini Göster/Gizle](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) üst tablo hakkındaki bilgileri gizlemek veya kullanıcının daha önce bu gizledi, yeniden neden olabilir. Kullanıcı daha önce görüntülenen tabloya geri taşımak için bir geri düğmesine tıklayabilirsiniz.  
  
## <a name="columns-and-rows"></a>Satırları ve sütunları  
 <xref:System.Windows.Forms.DataGrid> Oluşan bir koleksiyonunu <xref:System.Windows.Forms.DataGridTableStyle> bulunan nesneleri <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği. Tablo stili bir koleksiyonu içerebilir <xref:System.Windows.Forms.DataGridColumnStyle> bulunan nesneleri <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>... Düzenleyebileceğiniz <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ve <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özellikleri aracılığıyla erişilen koleksiyon düzenleyicileri kullanarak **özellikleri** penceresi.  
  
 Tüm <xref:System.Windows.Forms.DataGridTableStyle> ilişkili <xref:System.Windows.Forms.DataGrid> denetimi üzerinden erişilebilir <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> Tasarımcı ile düzenlenebilir <xref:System.Windows.Forms.DataGridTableStyle> Koleksiyonu Düzenleyicisi veya üzerinden programlı olarak <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği.  

 DataGrid denetiminde bulunan nesneleri aşağıda gösterilmiştir:

 ![DataGrid denetiminde bulunan nesneleri gösteren diyagram.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)  
  
 Tablo stillerini ve sütun stillerini ile eşitlenir <xref:System.Data.DataTable> nesneleri ve <xref:System.Data.DataColumn> ayarlayarak nesneleri kendi `MappingName` uygun özellikler <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataColumn.ColumnName%2A> özellikleri. Olduğunda bir <xref:System.Windows.Forms.DataGridTableStyle> hiçbir sütun olan stilleri eklenir bir <xref:System.Windows.Forms.DataGrid> geçerli bir veri kaynağına bağlı denetim ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Bu tablo stili özelliğine geçerli bir ayarlanmış <xref:System.Data.DataTable.TableName%2A> özelliği, bir koleksiyonunu <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri için oluşturulur Tablo stili. Her <xref:System.Data.DataColumn> bulunan <xref:System.Data.DataTable.Columns%2A> koleksiyonunu <xref:System.Data.DataTable>, karşılık gelen <xref:System.Windows.Forms.DataGridColumnStyle> eklenir <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> üzerinden erişilen <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>. Sütunları eklenebilir veya kılavuz kullanarak silinmiş <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> veya <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> metodunda <xref:System.Windows.Forms.GridColumnStylesCollection>. Daha fazla bilgi için [nasıl yapılır: Tablolar ekleyebilir ve sütunları Windows Forms DataGrid denetiminde](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) ve [nasıl yapılır: Sütunları silme veya gizleme içinde Windows Forms DataGrid denetiminde](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Sütun türleri koleksiyonunu genişletir <xref:System.Windows.Forms.DataGridColumnStyle> zengin biçimlendirme ve düzenleme özellikleri içeren sınıf. Devralınan tüm sütun türleri <xref:System.Windows.Forms.DataGridColumnStyle> temel sınıfı. Oluşturulan sınıf bağımlı <xref:System.Data.DataColumn.DataType%2A> özelliği <xref:System.Data.DataColumn> içinden <xref:System.Web.UI.WebControls.DataGridColumn> temel alır. Örneğin, bir <xref:System.Data.DataColumn> olan kendi <xref:System.Data.DataColumn.DataType%2A> özelliğini <xref:System.Boolean> ilişkilendirileceği <xref:System.Windows.Forms.DataGridBoolColumn>. Aşağıdaki tabloda bu sütun türlerinden her biri açıklanmaktadır.  
  
|Sütun türü|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Kabul eder ve veri biçimlendirilmiş veya biçimlendirilmemiş dize olarak görüntüler. Düzenleme özellikleri olan, aynı, basit bir veri düzenleme için oldukları gibi <xref:System.Windows.Forms.TextBox>. Devralınan <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Kabul eder ve görüntüler `true`, `false`ve null değerleri. Devralınan <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Bir sütunun sağ kenarı çift, tam bir açıklamalı alt yazı ve geniş bir girdi görüntülenecek sütun yeniden boyutlandırır.  
  
## <a name="table-styles-and-column-styles"></a>Tablo stillerini ve sütun stilleri  
 Varsayılan biçimi sağladıktan hemen sonra <xref:System.Windows.Forms.DataGrid> denetimi, belirli tablolar içinde veri kılavuzunda görüntülenirken kullanılacak renkleri özelleştirebilirsiniz.  
  
 Bu örneği oluşturularak elde edilir <xref:System.Windows.Forms.DataGridTableStyle> sınıfı. Tablo Stilleri belirtmek belirli tablolar, varsayılan biçimlendirmesini öğesinden farklı biçimlendirme <xref:System.Windows.Forms.DataGrid> denetiminin kendisini. Her tabloda yalnızca bir tablo stili aynı anda tanımlı olabilir.  
  
 Bazen, belirli veri tablosunun sütunları geri kalanından farklı bir özel sütunu görünüme sahip isteyeceksiniz. Özelleştirilmiş bir sütun stilleri kullanarak oluşturabileceğiniz <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği.  
  
 Sütun stillerini tablo stilleri veri tablolarına yalnızca ilgili gibi bir veri kümesindeki sütunları ilgilidir. Yalnızca her tablo çok her sütun için bir zaman, bu nedenle tanımlı bir tablo stili yalnızca yeni sahip olarak bir sütun stili, belirli stilini tanımladınız. Bu ilişki, sütunun içinde tanımlanan <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliği.  
  
 Sütun stillerini eklendiğinde olmadan bir tablo stili oluşturduysanız, Visual Studio form ve kılavuz çalışma zamanında oluşturulduğunda varsayılan sütun stillerini ekler. Ancak, bir tablo stili oluşturulmuş ve sütun stilleri eklendiğinde, Visual Studio sütun stilleri oluşturmaz. Ayrıca, sütun stillerini tanımlamak ve kılavuzunda görüntülenmesini istediğiniz sütunları için eşleme adı ile atamanız gerekir.  
  
 Belirttiğiniz bir sütun stili atayarak, hangi sütunların veri kılavuzunda dahil edilir ve hiçbir sütun stili sütunlara atanmış olduğundan, kılavuz görüntülenmez veri kümesini veri sütunlarını dahil edebilirsiniz. Ancak, veri sütun kümesinde yer aldığından görüntülenmez verileri programlı olarak düzenleyebilirsiniz.  
  
> [!NOTE]
>  Genel olarak, sütun stil oluşturma ve bunları tablo stilleri koleksiyona tablo stilleri eklemeden önce sütunu stilleri koleksiyonuna ekleyin. Boş bir tablo stili koleksiyona eklemek, sütun stil sizin için otomatik olarak üretilir. Yeni sütun stil yinelenen ile eklemeyi denediğinizde sonuç olarak, bir özel durum oluşturulur <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sütun stillerini koleksiyonuna değerleri.  
>   
>  Bazı durumlarda, yalnızca bir sütun birçok sütunlar arasında ince ayarlamalar yapmak istersiniz; Örneğin, 50 sütunları veri kümesini içeren ve yalnızca bunların 49 istiyorsunuz. Bu durumda, tüm 50 sütunları içeri aktarma ve programlı bir kaldırma kolaydır yerine istediğiniz program aracılığıyla her 49 tek tek sütun ekleme.  
  
## <a name="formatting"></a>Biçimlendirme  
 Uygulanabilir biçimlendirme <xref:System.Windows.Forms.DataGrid> kenarlık stillerini, kılavuz çizgisi stilleri, yazı tipi, başlık özellikleri, veri hizalama ve satırlar arasında arka plan rengini değiştirme denetimi içerir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme](how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Olaylar  
 Ortak yanı sıra gibi olayları kontrol <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, ve <xref:System.Windows.Forms.DataGrid.Scroll>, <xref:System.Windows.Forms.DataGrid> denetimi, düzenleme ve gezinti kılavuzda ile ilişkili olayları destekler. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Özellik, hangi hücresi seçili belirler. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Olayı kullanıcı yeni bir hücre geçtiğinde oluşturulur. Kullanıcı yeni bir tablo üst/alt ilişkilerini gittiğinde <xref:System.Windows.Forms.DataGrid.Navigate> olayı oluşturulur. <xref:System.Windows.Forms.DataGrid.BackButtonClick> Olayı, kullanıcı bir alt tabloda görüntülerken kullanıcı geri düğmesine tıkladığında oluşturulur ve <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> olayı Göster/Gizle üst satırları simgesine tıklandığında oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Silme veya Windows Forms DataGrid denetiminde sütunları gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme](how-to-format-the-windows-forms-datagrid-control.md)
