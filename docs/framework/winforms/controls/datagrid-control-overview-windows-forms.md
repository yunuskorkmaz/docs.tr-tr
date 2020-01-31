---
title: DataGrid Denetimine Genel Bakış
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
ms.openlocfilehash: df559926dbc9141276f0a03deb99e340fd7212da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742572"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid Denetimine Genel Bakış (Windows Forms)

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi verileri bir dizi satır ve sütunda görüntüler. En basit durum, kılavuzun hiçbir ilişki içermeyen tek bir tabloyla bir veri kaynağına bağlanması durumunda olur. Bu durumda, veriler bir elektronik tabloda olduğu gibi basit satırlarda ve sütunlarda görüntülenir. Verileri diğer denetimlere bağlama hakkında daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).

<xref:System.Windows.Forms.DataGrid> birden çok ilişkili tablo içeren verilere bağlıysa ve kılavuzda gezinti etkinse, kılavuz her satırda Genişleticileri görüntülenecektir. Bir genişleticiyle, Kullanıcı üst tablodan bir alt tabloya geçiş yapabilir. Bir düğüme tıkladığınızda alt tablo görüntülenir ve geri düğmesine tıklandığında özgün üst tablo görüntülenir. Bu şekilde, kılavuz, tablolar arasındaki hiyerarşik ilişkileri görüntüler.

Aşağıdaki ekran görüntüsünde, birden çok tablo içeren verilere yönelik bir DataGrid gösterilmektedir:

![Birden çok tablo içeren verilere yönelik DataGrid 'i gösteren bir WinForms uygulaması.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

<xref:System.Windows.Forms.DataGrid>, bir veri kümesi için Kullanıcı arabirimi, ilişkili tablolar arasında gezinti ve zengin biçimlendirme ve düzen özellikleri sağlayabilir.

Verilerin görüntülenmesi ve işlenmesi ayrı işlevlerdir: denetim kullanıcı arabirimini işler, ancak veri güncelleştirmeleri Windows Forms veri bağlama mimarisi ve .NET Framework veri sağlayıcıları tarafından işlenir. Bu nedenle, aynı veri kaynağıyla bağlantılı birden çok denetim eşitlenmiş olarak kalır.

> [!NOTE]
> Visual Basic 6,0 ' de DataGrid denetimine alışkın değilseniz, Windows Forms <xref:System.Windows.Forms.DataGrid> denetiminde bazı önemli farklılıklar bulacaksınız.

Kılavuz bir <xref:System.Data.DataSet>bağlandığında, sütunlar ve satırlar otomatik olarak oluşturulur, biçimlendirilir ve doldurulur. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md). <xref:System.Windows.Forms.DataGrid> denetiminin üretilmesini izleyerek, gereksinimlerinize bağlı olarak sütunları ve satırları ekleyebilir, silebilir, yeniden düzenleyebilir ve biçimlendirebilirsiniz.

## <a name="binding-data-to-the-control"></a>Verileri denetime bağlama

<xref:System.Windows.Forms.DataGrid> denetiminin çalışması için, tasarım zamanında <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri kullanılarak bir veri kaynağına veya çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemine bağlanılmalıdır. Bu bağlama, <xref:System.Windows.Forms.DataGrid> <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>) bir örneklenmiş veri kaynağı nesnesine işaret eder. <xref:System.Windows.Forms.DataGrid> denetim, verilerde gerçekleştirilen eylemlerin sonuçlarını gösterir. Verilere özgü çoğu eylem <xref:System.Windows.Forms.DataGrid>, ancak bunun yerine veri kaynağı aracılığıyla gerçekleştirilmez.

Bağlantılı veri kümesindeki veriler herhangi bir mekanizmaya göre güncelleştirilirse, <xref:System.Windows.Forms.DataGrid> denetimi değişiklikleri yansıtır. Veri kılavuzunda ve Tablo stillerinde ve sütun stillerinde `ReadOnly` özelliği `false`olarak ayarlandıysa, veri kümesindeki veriler <xref:System.Windows.Forms.DataGrid> denetimi aracılığıyla güncelleştirilebilen olabilir.

Tek seferde <xref:System.Windows.Forms.DataGrid> yalnızca bir tablo gösterilebilir. Tablolar arasında üst-alt ilişkisi tanımlanmışsa, Kullanıcı <xref:System.Windows.Forms.DataGrid> denetimde görüntülenecek tabloyu seçmek için ilgili tablolar arasında hareket edebilir. Tasarım zamanında veya çalışma zamanında bir <xref:System.Windows.Forms.DataGrid> denetimini bir ADO.NET veri kaynağına bağlama hakkında bilgi için bkz. [nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

<xref:System.Windows.Forms.DataGrid> için geçerli veri kaynakları şunlardır:

- <xref:System.Data.DataTable> sınıfı

- <xref:System.Data.DataView> sınıfı

- <xref:System.Data.DataSet> sınıfı

- <xref:System.Data.DataViewManager> sınıfı

Kaynağınız bir veri kümesi ise, veri kümesi formdaki bir nesne veya bir XML Web hizmeti tarafından forma geçirilmiş bir nesne olabilir. Türü belirtilmiş ya da türsüz veri kümelerine bağlanabilirsiniz.

Ayrıca, yapıdaki nesneler gibi bir dizideki nesneler ortak özellikleri açığa çıkarmak için bir <xref:System.Windows.Forms.DataGrid> denetimini ek yapılara bağlayabilirsiniz. Izgara, yapıdaki öğelerin tüm ortak özelliklerini görüntüler. Örneğin, <xref:System.Windows.Forms.DataGrid> denetimini bir müşteri nesneleri dizisine bağlarsanız, kılavuz bu müşteri nesnelerinin tüm ortak özelliklerini görüntüler. Bazı örneklerde bu, yapıya bağlayabilseniz de, sonuçta elde edilen bağlı yapının pratik bir uygulama olmayabilir. Örneğin, bir tamsayı dizisine bağlayabilirsiniz, ancak `Integer` veri türü ortak bir özelliği desteklemediğinden, kılavuz herhangi bir veri görüntüleyemez.

Öğeleri ortak özellikleri açığa çıkarmak için aşağıdaki yapılara bağlayabilirsiniz:

- <xref:System.Collections.IList> arabirimini uygulayan herhangi bir bileşen. Bu, tek boyutlu dizileri içerir.

- <xref:System.ComponentModel.IListSource> arabirimini uygulayan herhangi bir bileşen.

- <xref:System.ComponentModel.IBindingList> arabirimini uygulayan herhangi bir bileşen.

 Olası veri kaynakları hakkında daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Izgara görüntüsü

<xref:System.Windows.Forms.DataGrid> denetiminin yaygın kullanımı, veri kümesinden tek bir veri tablosunu görüntülemektir. Ancak, denetim, ilgili tablolar dahil olmak üzere birden çok tabloyu göstermek için de kullanılabilir. Kılavuzun görünümü veri kaynağına göre otomatik olarak ayarlanır. Aşağıdaki tabloda, çeşitli yapılandırmalarda nelerin gösterileceği gösterilmektedir.

|Veri kümesinin içeriği|Ne görüntülenir|
|--------------------------|-----------------------|
|Tek tablo.|Tablo bir kılavuzda görüntülenir.|
|Birden çok tablo.|Izgara, kullanıcıların görüntülemek istedikleri tabloyu bulmak için gezinebilecekleri bir ağaç görünümü gösterebilir.|
|Birden çok ilişkili tablo.|Izgara, tabloları seçmek için bir ağaç görünümü görüntüleyebilir veya Kılavuzun üst tabloyu göstermesini belirtebilirsiniz. Üst tablodaki kayıtlar, kullanıcıların ilgili alt satırlara gitmesini sağlar.|

> [!NOTE]
> Bir veri kümesindeki tablolar <xref:System.Data.DataRelation>ile ilgilidir. Ayrıca bkz. [veri kümeleri arasında Ilişki oluşturma](/visualstudio/data-tools/relationships-in-datasets).

<xref:System.Windows.Forms.DataGrid> denetimi bir tabloyu görüntülerken ve <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> özelliği `true`olarak ayarlandığında, veriler sütun başlıklarına tıklanarak yeniden oluşturulabilir. Kullanıcı ayrıca satır ekleyebilir ve hücreleri düzenleyebilir.

Bir tablo kümesi arasındaki ilişkiler, bir üst/alt gezinti yapısı kullanılarak kullanıcılara görüntülenir. Üst tablolar en yüksek veri düzeyidir ve alt tablolar üst tablolardaki tek listelerden türetilmiş veri tablolarıdır. Genişletmeleri, alt tablo içeren her bir üst satırda görüntülenir. Bir genişleticiye tıklamak, alt tablolara yönelik Web benzeri bağlantıların bir listesini oluşturur. Kullanıcı bir bağlantı seçtiğinde alt tablo görüntülenir. Üst satırları göster/gizle simgesine tıklamak (![Üst satırları göster/gizle simgesi](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) üst tabloyla ilgili bilgileri gizler veya Kullanıcı daha önce gizlenmişse yeniden görünür hale gelir. Kullanıcı daha önce görüntülenen tabloya geri dönmek için geri düğmesine tıklayabilirsiniz.

## <a name="columns-and-rows"></a>Sütunlar ve satırlar

<xref:System.Windows.Forms.DataGrid>, <xref:System.Windows.Forms.DataGrid> denetiminin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliğinde yer alan <xref:System.Windows.Forms.DataGridTableStyle> nesnelerden oluşan bir koleksiyondan oluşur. Tablo stili, <xref:System.Windows.Forms.DataGridTableStyle><xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliğinde bulunan <xref:System.Windows.Forms.DataGridColumnStyle> nesnelerinin bir koleksiyonunu içerebilir. **Özellikler** penceresinden erişilen koleksiyon düzenleyicilerini kullanarak <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ve <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliklerini düzenleyebilirsiniz.

<xref:System.Windows.Forms.DataGrid> denetimiyle ilişkili <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.GridTableStylesCollection>üzerinden erişilebilir. <xref:System.Windows.Forms.GridTableStylesCollection>, tasarımcıda <xref:System.Windows.Forms.DataGridTableStyle> koleksiyonu Düzenleyicisi ile veya <xref:System.Windows.Forms.DataGrid> denetiminin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği aracılığıyla programlama yoluyla düzenlenebilir.

Aşağıdaki çizimde DataGrid denetimine eklenen nesneler gösterilmektedir:

![DataGrid denetiminde içerilen nesneleri gösteren diyagram.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Tablo stilleri ve sütun stilleri, `MappingName` özelliklerini uygun <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataColumn.ColumnName%2A> özelliklerine ayarlayarak <xref:System.Data.DataTable> nesneleriyle ve <xref:System.Data.DataColumn> nesneleriyle eşitlenir. Sütun stilleri olmayan bir <xref:System.Windows.Forms.DataGridTableStyle> geçerli bir veri kaynağına bağlanan bir <xref:System.Windows.Forms.DataGrid> denetimine eklendiğinde ve bu tablo stilinin <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği geçerli bir <xref:System.Data.DataTable.TableName%2A> özelliğine ayarlandığında, bu tablo stili için bir <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri koleksiyonu oluşturulur. <xref:System.Data.DataTable><xref:System.Data.DataTable.Columns%2A> koleksiyonunda bulunan her <xref:System.Data.DataColumn> için <xref:System.Windows.Forms.GridColumnStylesCollection>buna karşılık gelen bir <xref:System.Windows.Forms.DataGridColumnStyle> eklenir. <xref:System.Windows.Forms.GridColumnStylesCollection>, <xref:System.Windows.Forms.DataGridTableStyle><xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği aracılığıyla erişilir. <xref:System.Windows.Forms.GridColumnStylesCollection><xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> veya <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> yöntemi kullanılarak kılavuzdan sütunlar eklenebilir veya silinebilir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGrid denetimine tablo ve sütun ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) ve [nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).

Sütun türleri koleksiyonu, <xref:System.Windows.Forms.DataGridColumnStyle> sınıfını zengin biçimlendirme ve Düzenle özellikleri ile genişletir. Tüm sütun türleri <xref:System.Windows.Forms.DataGridColumnStyle> temel sınıftan devralınır. Oluşturulan sınıf, <xref:System.Web.UI.WebControls.DataGridColumn> temel aldığı <xref:System.Data.DataColumn> <xref:System.Data.DataColumn.DataType%2A> özelliğine bağlıdır. Örneğin, <xref:System.Data.DataColumn.DataType%2A> özelliği <xref:System.Boolean> olarak ayarlanmış bir <xref:System.Data.DataColumn>, <xref:System.Windows.Forms.DataGridBoolColumn>ile ilişkilendirilir. Aşağıdaki tabloda bu sütun türlerinin her biri açıklanmaktadır.

|Sütun türü|Açıklama|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Verileri, biçimli veya biçimlendirilmemiş dizeler olarak kabul eder ve görüntüler. Düzenlemenin özellikleri, basit bir <xref:System.Windows.Forms.TextBox>verileri düzenlemekte oldukları gibidir. <xref:System.Windows.Forms.DataGridColumnStyle>devralır.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|`true`, `false`ve null değerlerini kabul eder ve görüntüler. <xref:System.Windows.Forms.DataGridColumnStyle>devralır.|

Sütunun sağ kenarına çift tıklamak sütunu, tam başlığını ve en geniş girişi göstermek için yeniden boyutlandırır.

## <a name="table-styles-and-column-styles"></a>Tablo stilleri ve sütun stilleri

<xref:System.Windows.Forms.DataGrid> denetiminin varsayılan biçimini kurandan hemen sonra, veri kılavuzunda belirli tablolar görüntülenirken kullanılacak renkleri özelleştirebilirsiniz.

Bu, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının örnekleri oluşturularak elde edilir. Tablo stilleri, <xref:System.Windows.Forms.DataGrid> denetimin kendisinin varsayılan formatlarından farklı şekilde belirli tabloların biçimlendirmesini belirtir. Her tablo için aynı anda yalnızca bir tablo stili tanımlanmış olabilir.

Bazen belirli bir sütunun, belirli bir veri tablosunun geri kalanından farklı görünmesini isteyeceksiniz. <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliğini kullanarak, özelleştirilmiş bir sütun stili kümesi oluşturabilirsiniz.

Sütun stilleri, tablo stillerinin tıpkı veri tabloları ile ilişkili olduğu gibi bir veri kümesindeki sütunlarla ilgilidir. Her tablo için aynı anda yalnızca bir tablo stili tanımlanmış olabilir, bu nedenle her sütunda yalnızca bir sütun stili tanımlanmış, belirli bir tablo stilinde bulunabilir. Bu ilişki, sütunun <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliğinde tanımlanmıştır.

Sütun stilleri eklenmeksizin tablo stili oluşturduysanız, form ve kılavuz çalışma zamanında oluşturulduğunda Visual Studio varsayılan sütun stilleri ekler. Ancak, bir tablo stili oluşturduysanız ve buna herhangi bir sütun stili eklediyseniz, Visual Studio herhangi bir sütun stili oluşturmaz. Ayrıca, sütun stilleri tanımlamanız ve bunları, kılavuzda görünmesini istediğiniz sütunları olacak şekilde eşleme adıyla atamanız gerekir.

Veri kılavuzunda hangi sütunların sütun stili atayarak ve sütunlara sütun stili atanmadığından emin olduğunuz için, kılavuzda görüntülenmeyen veri kümesindeki veri sütunlarını dahil edebilirsiniz. Ancak veri sütunu veri kümesine dahil edildiğinden, görüntülenmeyen verileri program aracılığıyla düzenleyebilirsiniz.

> [!NOTE]
> Genel olarak, tablo stilleri koleksiyonuna tablo stilleri eklemeden önce sütun stilleri oluşturun ve bunları sütun stilleri koleksiyonuna ekleyin. Koleksiyona boş bir tablo stili eklediğinizde, sütun stilleri sizin için otomatik olarak oluşturulur. Sonuç olarak, sütun stilleri koleksiyonuna yinelenen <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> değerleri olan yeni sütun stilleri eklemeye çalışırsanız bir özel durum oluşturulur.
>
> Bazen çok sayıda sütun arasında yalnızca bir sütun ince ayar istersiniz; Örneğin, veri kümesi 50 sütun içerir ve yalnızca 49 ' i istiyorsunuz. Bu durumda, her 50 sütunu içeri aktarmak ve tek başına her bir 49 ayrı sütunu eklemek yerine program aracılığıyla bir tane kaldırmak daha kolaydır.

## <a name="formatting"></a>Biçimlendirme

<xref:System.Windows.Forms.DataGrid> denetimine uygulanabilen biçimlendirme kenarlık stilleri, kılavuz çizgisi stilleri, yazı tipleri, açıklamalı alt yazı özellikleri, veri hizalaması ve satırlar arasında değişen arka plan renkleri içerir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme](how-to-format-the-windows-forms-datagrid-control.md).

## <a name="events"></a>Olaylar

<xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>ve <xref:System.Windows.Forms.DataGrid.Scroll>gibi ortak denetim olaylarının yanı sıra, <xref:System.Windows.Forms.DataGrid> denetimi kılavuz içinde düzenlemeyle ve gezintide ilişkili olayları destekler. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> özelliği hangi hücrenin seçili olduğunu belirler. <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> olay, Kullanıcı yeni bir hücreye gittiğinde tetiklenir. Kullanıcı üst/alt ilişkiler aracılığıyla yeni bir tabloya gittiğinde <xref:System.Windows.Forms.DataGrid.Navigate> olayı tetiklenir. <xref:System.Windows.Forms.DataGrid.BackButtonClick> olayı, Kullanıcı bir alt tabloyu görüntülerken geri düğmesine tıkladığında ve üst satırları göster/gizle simgesine tıklandığında <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> olay tetiklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme](how-to-format-the-windows-forms-datagrid-control.md)
