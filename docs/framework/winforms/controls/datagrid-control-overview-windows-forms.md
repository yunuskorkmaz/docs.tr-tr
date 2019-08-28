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
ms.openlocfilehash: ce149ed25d3326daa9096596fe8d542a13759a96
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046209"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid Denetimine Genel Bakış (Windows Forms)

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Windows Forms <xref:System.Windows.Forms.DataGrid> denetim verileri bir dizi satır ve sütunda görüntüler. En basit durum, kılavuzun hiçbir ilişki içermeyen tek bir tabloyla bir veri kaynağına bağlanması durumunda olur. Bu durumda, veriler bir elektronik tabloda olduğu gibi basit satırlarda ve sütunlarda görüntülenir. Verileri diğer denetimlere bağlama hakkında daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).

<xref:System.Windows.Forms.DataGrid> Birden çok ilişkili tablo içeren verilere bağlıysa ve kılavuzda gezinti etkinse, kılavuz her satırda Genişleticileri görüntülenecektir. Bir genişleticiyle, Kullanıcı üst tablodan bir alt tabloya geçiş yapabilir. Bir düğüme tıkladığınızda alt tablo görüntülenir ve geri düğmesine tıklandığında özgün üst tablo görüntülenir. Bu şekilde, kılavuz, tablolar arasındaki hiyerarşik ilişkileri görüntüler.

Aşağıdaki ekran görüntüsünde, birden çok tablo içeren verilere yönelik bir DataGrid gösterilmektedir:

![Birden çok tablo içeren verilere yönelik DataGrid 'i gösteren bir WinForms uygulaması.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

, <xref:System.Windows.Forms.DataGrid> Bir veri kümesi için Kullanıcı arabirimi, ilişkili tablolar arasında gezinti ve zengin biçimlendirme ve düzen özellikleri sağlayabilir.

Verilerin görüntülenmesi ve işlenmesi ayrı işlevlerdir: Denetim Kullanıcı arabirimini işler, ancak veri güncelleştirmeleri Windows Forms veri bağlama mimarisi ve .NET Framework veri sağlayıcıları tarafından işlenir. Bu nedenle, aynı veri kaynağıyla bağlantılı birden çok denetim eşitlenmiş olarak kalır.

> [!NOTE]
> Visual Basic 6,0 ' de DataGrid denetimine alışkın değilseniz, Windows Forms <xref:System.Windows.Forms.DataGrid> denetiminde bazı önemli farklılıklar bulacaksınız.

Kılavuz bir <xref:System.Data.DataSet>öğesine bağlandığında, sütunlar ve satırlar otomatik olarak oluşturulur, biçimlendirilir ve doldurulur. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md). <xref:System.Windows.Forms.DataGrid> Denetimin üretilmesini izleyerek, gereksinimlerinize bağlı olarak sütunları ve satırları ekleyebilir, silebilir, yeniden düzenleyebilir ve biçimlendirebilirsiniz.

## <a name="binding-data-to-the-control"></a>Verileri denetime bağlama

Denetimin çalışması için, tasarım zamanında <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> ve çalışma zamanında yöntemikullanılarakbirverikaynağınabağlanmasıgerekir.<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid> Bu bağlama, <xref:System.Windows.Forms.DataGrid> veya <xref:System.Data.DataTable>gibi bir <xref:System.Data.DataSet> örneklenmiş veri kaynağı nesnesine işaret eder. <xref:System.Windows.Forms.DataGrid> Denetimde, verilerde gerçekleştirilen eylemlerin sonuçları gösterilir. Verilere özgü çoğu eylem, veri kaynağı aracılığıyla değil, <xref:System.Windows.Forms.DataGrid> aracılığıyla gerçekleştirilmez.

Bağlantılı veri kümesindeki veriler herhangi bir mekanizmaya göre güncelleştirilirse, <xref:System.Windows.Forms.DataGrid> Denetim değişiklikleri yansıtır. Veri kılavuzunda ve Tablo stillerinde ve sütun stillerinde `ReadOnly` özelliği olarak `false`ayarlandıysa, veri kümesindeki veriler <xref:System.Windows.Forms.DataGrid> denetim aracılığıyla güncelleştirilebilen olabilir.

Tek seferde yalnızca bir tablo gösterilebilir <xref:System.Windows.Forms.DataGrid> . Tablolar arasında üst-alt ilişkisi tanımlanmışsa, Kullanıcı <xref:System.Windows.Forms.DataGrid> denetimde görüntülenecek tabloyu seçmek için ilgili tablolar arasında hareket edebilir. Bir <xref:System.Windows.Forms.DataGrid> denetimi bir ADO.NET veri kaynağına tasarım zamanında veya çalışma zamanında bağlama hakkında bilgi için bkz [. nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)bağlayın.

<xref:System.Windows.Forms.DataGrid> Şunlar için geçerli veri kaynakları:

- <xref:System.Data.DataTable>sınıfı

- <xref:System.Data.DataView>sınıfı

- <xref:System.Data.DataSet>sınıfı

- <xref:System.Data.DataViewManager>sınıfı

Kaynağınız bir veri kümesi ise, veri kümesi formdaki bir nesne veya bir XML Web hizmeti tarafından forma geçirilmiş bir nesne olabilir. Türü belirtilmiş ya da türsüz veri kümelerine bağlanabilirsiniz.

Ayrıca, yapıdaki nesneler gibi <xref:System.Windows.Forms.DataGrid> bir dizideki nesneler ortak özellikleri kullanıma sunduğundan, bir denetimi ek yapılara bağlayabilirsiniz. Izgara, yapıdaki öğelerin tüm ortak özelliklerini görüntüler. Örneğin, <xref:System.Windows.Forms.DataGrid> denetimi bir müşteri nesneleri dizisine bağlarsanız, kılavuz bu müşteri nesnelerinin tüm ortak özelliklerini görüntüler. Bazı örneklerde bu, yapıya bağlayabilseniz de, sonuçta elde edilen bağlı yapının pratik bir uygulama olmayabilir. Örneğin, bir tamsayı dizisine bağlayabilirsiniz, ancak `Integer` veri türü ortak bir özelliği desteklemediğinden, kılavuz herhangi bir veri görüntüleyemez.

Öğeleri ortak özellikleri açığa çıkarmak için aşağıdaki yapılara bağlayabilirsiniz:

- <xref:System.Collections.IList> Arabirimi uygulayan herhangi bir bileşen. Bu, tek boyutlu dizileri içerir.

- <xref:System.ComponentModel.IListSource> Arabirimi uygulayan herhangi bir bileşen.

- <xref:System.ComponentModel.IBindingList> Arabirimi uygulayan herhangi bir bileşen.

 Olası veri kaynakları hakkında daha fazla bilgi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Izgara görüntüsü

<xref:System.Windows.Forms.DataGrid> Denetimin yaygın kullanımı bir veri kümesinden tek bir veri tablosunu görüntülemektir. Ancak, denetim, ilgili tablolar dahil olmak üzere birden çok tabloyu göstermek için de kullanılabilir. Kılavuzun görünümü veri kaynağına göre otomatik olarak ayarlanır. Aşağıdaki tabloda, çeşitli yapılandırmalarda nelerin gösterileceği gösterilmektedir.

|Veri kümesinin içeriği|Ne görüntülenir|
|--------------------------|-----------------------|
|Tek tablo.|Tablo bir kılavuzda görüntülenir.|
|Birden çok tablo.|Izgara, kullanıcıların görüntülemek istedikleri tabloyu bulmak için gezinebilecekleri bir ağaç görünümü gösterebilir.|
|Birden çok ilişkili tablo.|Izgara, tabloları seçmek için bir ağaç görünümü görüntüleyebilir veya Kılavuzun üst tabloyu göstermesini belirtebilirsiniz. Üst tablodaki kayıtlar, kullanıcıların ilgili alt satırlara gitmesini sağlar.|

> [!NOTE]
> Bir veri kümesindeki tablolar, ile <xref:System.Data.DataRelation>ilgilidir. Ayrıca bkz. [veri kümeleri arasında Ilişki oluşturma](/visualstudio/data-tools/relationships-in-datasets).

Denetim bir tabloyu görüntülerken <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> ve özelliği olarak `true`ayarlandığında, veriler sütun başlıklarına tıklanarak yeniden oluşturulabilir. <xref:System.Windows.Forms.DataGrid> Kullanıcı ayrıca satır ekleyebilir ve hücreleri düzenleyebilir.

Bir tablo kümesi arasındaki ilişkiler, bir üst/alt gezinti yapısı kullanılarak kullanıcılara görüntülenir. Üst tablolar en yüksek veri düzeyidir ve alt tablolar üst tablolardaki tek listelerden türetilmiş veri tablolarıdır. Genişletmeleri, alt tablo içeren her bir üst satırda görüntülenir. Bir genişleticiye tıklamak, alt tablolara yönelik Web benzeri bağlantıların bir listesini oluşturur. Kullanıcı bir bağlantı seçtiğinde alt tablo görüntülenir. Üst satırları göster/gizle simgesine tıklamak (![Üst satırları göster/gizle simgesi](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) üst tabloyla ilgili bilgileri gizler veya Kullanıcı daha önce gizlenmişse yeniden görünür hale gelir. Kullanıcı daha önce görüntülenen tabloya geri dönmek için geri düğmesine tıklayabilirsiniz.

## <a name="columns-and-rows"></a>Sütunlar ve satırlar

, <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridTableStyle> Denetimin özelliğinde<xref:System.Windows.Forms.DataGrid.TableStyles%2A> yer alan nesneler koleksiyonundan oluşur. Tablo stili, <xref:System.Windows.Forms.DataGridColumnStyle> <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> öğesinin<xref:System.Windows.Forms.DataGridTableStyle>özelliğinde yer alan bir nesne koleksiyonu içerebilir. **Özellikler** penceresi aracılığıyla erişilen <xref:System.Windows.Forms.DataGrid.TableStyles%2A> koleksiyon <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> düzenleyicilerini kullanarak ve özelliklerini düzenleyebilirsiniz.

Denetimiyle ilişkili <xref:System.Windows.Forms.DataGridTableStyle> herhangi birine aracılığıyla <xref:System.Windows.Forms.GridTableStylesCollection>erişilebilir. <xref:System.Windows.Forms.DataGrid> , <xref:System.Windows.Forms.GridTableStylesCollection> <xref:System.Windows.Forms.DataGridTableStyle> Koleksiyon Düzenleyicisi ile tasarımcıda düzenlenebilir veya <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği aracılığıyla programlı bir şekilde düzenlenebilirler.

Aşağıdaki çizimde DataGrid denetimine eklenen nesneler gösterilmektedir:

![DataGrid denetiminde içerilen nesneleri gösteren diyagram.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Tablo stilleri ve sütun stilleri, <xref:System.Data.DataTable> `MappingName` özellikleri uygun <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataColumn.ColumnName%2A> özelliklere <xref:System.Data.DataColumn> ayarlayarak nesneler ve nesnelerle eşitlenir. Bir sütun <xref:System.Windows.Forms.DataGridTableStyle> stili olmayan bir <xref:System.Windows.Forms.DataGrid> denetime geçerli bir <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> veri kaynağına bağlanan bir denetim eklendiğinde ve bu tablo stilinin özelliği geçerli <xref:System.Data.DataTable.TableName%2A> bir özelliğe ayarlandığında, bunun için bir <xref:System.Windows.Forms.DataGridColumnStyle> nesne koleksiyonu oluşturulur tablo stili. Öğesinin <xref:System.Data.DataColumn> <xref:System.Data.DataTable.Columns%2A> <xref:System.Windows.Forms.DataGridColumnStyle> koleksiyonunda bulunan her biri için öğesine karşılık gelen öğesine <xref:System.Windows.Forms.GridColumnStylesCollection>eklenir. <xref:System.Data.DataTable> <xref:System.Windows.Forms.GridColumnStylesCollection>öğesinin özelliği<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> aracılığıyla erişilir. <xref:System.Windows.Forms.DataGridTableStyle> İçindeki <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> or <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> yöntemi kullanılarakkılavuzdansütunlareklenebilirveyasilinebilir.<xref:System.Windows.Forms.GridColumnStylesCollection> Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimine](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) tablolar ve sütunlar ekleyin ve [şunları yapın: Windows Forms DataGrid denetimindeki](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)sütunları silin veya gizleyin.

Sütun türleri koleksiyonu, <xref:System.Windows.Forms.DataGridColumnStyle> sınıfı zengin biçimlendirme ve Düzenle özellikleri ile genişletir. Tüm sütun türleri <xref:System.Windows.Forms.DataGridColumnStyle> taban sınıftan devralınır. Oluşturulan sınıf, temel aldığı <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn> <xref:System.Web.UI.WebControls.DataGridColumn> öğesinin özelliğine bağlıdır. Örneğin, <xref:System.Data.DataColumn.DataType%2A> özelliği olarak <xref:System.Data.DataColumn> <xref:System.Boolean> ayarlanmış olan bir, ile <xref:System.Windows.Forms.DataGridBoolColumn>ilişkilendirilecektir. Aşağıdaki tabloda bu sütun türlerinin her biri açıklanmaktadır.

|Sütun türü|Açıklama|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Verileri, biçimli veya biçimlendirilmemiş dizeler olarak kabul eder ve görüntüler. Düzenlemenin özellikleri, verileri basit <xref:System.Windows.Forms.TextBox>bir şekilde düzenlemekte oldukları gibidir. Öğesinden <xref:System.Windows.Forms.DataGridColumnStyle>devralır.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|`true` ,`false`Ve null değerlerini kabul eder ve görüntüler. Öğesinden <xref:System.Windows.Forms.DataGridColumnStyle>devralır.|

Sütunun sağ kenarına çift tıklamak sütunu, tam başlığını ve en geniş girişi göstermek için yeniden boyutlandırır.

## <a name="table-styles-and-column-styles"></a>Tablo stilleri ve sütun stilleri

<xref:System.Windows.Forms.DataGrid> Denetimin varsayılan biçimini kurandan hemen sonra, veri kılavuzunda belirli tablolar görüntülenirken kullanılacak renkleri özelleştirebilirsiniz.

Bu, <xref:System.Windows.Forms.DataGridTableStyle> sınıfının örnekleri oluşturularak elde edilir. Tablo stilleri, <xref:System.Windows.Forms.DataGrid> denetimin kendisinin varsayılan formatlarından farklı şekilde belirli tabloların biçimlendirmesini belirtir. Her tablo için aynı anda yalnızca bir tablo stili tanımlanmış olabilir.

Bazen belirli bir sütunun, belirli bir veri tablosunun geri kalanından farklı görünmesini isteyeceksiniz. <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> Özelliğini kullanarak, özelleştirilmiş bir sütun stili kümesi oluşturabilirsiniz.

Sütun stilleri, tablo stillerinin tıpkı veri tabloları ile ilişkili olduğu gibi bir veri kümesindeki sütunlarla ilgilidir. Her tablo için aynı anda yalnızca bir tablo stili tanımlanmış olabilir, bu nedenle her sütunda yalnızca bir sütun stili tanımlanmış, belirli bir tablo stilinde bulunabilir. Bu ilişki, sütunun <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliğinde tanımlanmıştır.

Sütun stilleri eklenmeksizin tablo stili oluşturduysanız, form ve kılavuz çalışma zamanında oluşturulduğunda Visual Studio varsayılan sütun stilleri ekler. Ancak, bir tablo stili oluşturduysanız ve buna herhangi bir sütun stili eklediyseniz, Visual Studio herhangi bir sütun stili oluşturmaz. Ayrıca, sütun stilleri tanımlamanız ve bunları, kılavuzda görünmesini istediğiniz sütunları olacak şekilde eşleme adıyla atamanız gerekir.

Veri kılavuzunda hangi sütunların sütun stili atayarak ve sütunlara sütun stili atanmadığından emin olduğunuz için, kılavuzda görüntülenmeyen veri kümesindeki veri sütunlarını dahil edebilirsiniz. Ancak veri sütunu veri kümesine dahil edildiğinden, görüntülenmeyen verileri program aracılığıyla düzenleyebilirsiniz.

> [!NOTE]
> Genel olarak, tablo stilleri koleksiyonuna tablo stilleri eklemeden önce sütun stilleri oluşturun ve bunları sütun stilleri koleksiyonuna ekleyin. Koleksiyona boş bir tablo stili eklediğinizde, sütun stilleri sizin için otomatik olarak oluşturulur. Sonuç olarak, sütun stilleri koleksiyonuna yinelenen <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> değerler içeren yeni sütun stilleri eklemeye çalışırsanız bir özel durum oluşturulur.
>
> Bazen çok sayıda sütun arasında yalnızca bir sütun ince ayar istersiniz; Örneğin, veri kümesi 50 sütun içerir ve yalnızca 49 ' i istiyorsunuz. Bu durumda, her 50 sütunu içeri aktarmak ve tek başına her bir 49 ayrı sütunu eklemek yerine program aracılığıyla bir tane kaldırmak daha kolaydır.

## <a name="formatting"></a>Biçimlendirme

<xref:System.Windows.Forms.DataGrid> Denetime uygulanabilen biçimlendirme kenarlık stilleri, kılavuz çizgisi stilleri, yazı tipleri, açıklamalı alt yazı özellikleri, veri hizalaması ve satırlar arasında değişen arka plan renkleri içerir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini](how-to-format-the-windows-forms-datagrid-control.md)biçimlendirin.

## <a name="events"></a>Olaylar

<xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>Ve gibi<xref:System.Windows.Forms.DataGrid.Scroll>ortakdenetim olaylarının yanı sıra, Denetimkılavuz<xref:System.Windows.Forms.DataGrid> içinde düzenlemeyle ve gezintide ilişkili olayları destekler. <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> Özelliği hangi hücrenin seçili olduğunu belirler. Kullanıcı yeni bir hücreye gittiğinde olaytetiklenir.<xref:System.Windows.Forms.DataGrid.CurrentCellChanged> Kullanıcı üst/alt ilişkiler aracılığıyla yeni bir tabloya gittiğinde, <xref:System.Windows.Forms.DataGrid.Navigate> olay tetiklenir. Kullanıcı bir alt tabloyu görüntülerken geri düğmesine tıkladığında olay tetiklenir <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> ve üst satırları göster/gizle simgesi tıklandığında olay tetiklenir. <xref:System.Windows.Forms.DataGrid.BackButtonClick>

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme](how-to-format-the-windows-forms-datagrid-control.md)
