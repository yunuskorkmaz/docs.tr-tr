---
title: Windows Forms DataGridView Denetiminde Sütun Türleri
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: 8fd3ad0da369702c2a5e27c0b8b9a39a71c372ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724576"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Türleri
<xref:System.Windows.Forms.DataGridView> Denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcıları etkinleştirmek için birden fazla sütun türleri kullanır.  
  
 Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetleyin ve ayarlayın <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özelliğini `true`, sütunlar, bağlı veri kaynağında bulunan veri türleri için uygun bir varsayılan sütun türleri kullanarak otomatik olarak oluşturulur.  
  
 Ayrıca herhangi bir sütun sınıfı örneklerini kendiniz oluşturabilir ve bunları tarafından döndürülen bir koleksiyona ekler <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği. Bağlanmamış sütunlar olarak kullanmak için bu örneği oluşturabilir veya bunları el ile bağlayabilirsiniz. El ile ilişkili sütun, örneğin, bir tür otomatik olarak oluşturulan bir sütunu başka bir türe sahip bir sütun değiştirmek istediğinizde yararlıdır.  
  
 İçinde kullanılabilen çeşitli sütun sınıfları aşağıdaki tabloda açıklanmıştır <xref:System.Windows.Forms.DataGridView> denetimi.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Metin tabanlı değerlerle kullanılır. Sayılar ve dizeler için bağlama sırasında otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|İle kullanılan <xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleri. Bu tür değerlere bağlama sırasında otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Resimleri görüntülemek için kullanılır. Bayt dizileri için bağlama sırasında otomatik olarak oluşturulan <xref:System.Drawing.Image> nesneleri veya <xref:System.Drawing.Icon> nesneleri.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Hücrelerde düğmeleri görüntülemek için kullanılır. Bağlama sırasında otomatik olarak oluşturulur. Genellikle, bağlanmamış sütunlar kullanılır.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Hücrelerde açılan listeleri görüntülemek için kullanılır. Bağlama sırasında otomatik olarak oluşturulur. Genellikle veri el ile ilişkili.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Hücrelerde bağlantılarını görüntülemek için kullanılır. Bağlama sırasında otomatik olarak oluşturulur. Genellikle veri el ile ilişkili.|  
|Özel sütun türü|Kendi sütun sınıfı devralarak oluşturabileceğiniz <xref:System.Windows.Forms.DataGridViewColumn> sınıfı veya özel görünüşünü, davranış veya barındırılan denetim sağlamak için ondan türetilen sınıflardan biri. Daha fazla bilgi için [nasıl yapılır: Davranış ve görünümünü genişleterek hücre ve sütunları Windows Forms DataGridView denetiminde özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Bu sütun türleri, aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Sayılar ve dizeler gibi metin tabanlı değerleri ile kullanmak için bir genel amaçlı sütunu türü. Düzenleme modundaki bir <xref:System.Windows.Forms.TextBox> denetim hücre değerini değiştirmek kullanıcıların etkin hücreye görüntülenir.  
  
 Hücre değerlerini otomatik olarak görüntülemek için dizelere dönüştürülür. Girilen veya kullanıcı tarafından değiştirilmiş değerleri uygun veri türünün bir hücre değerini oluşturmak için otomatik olarak ayrıştırılır. Bu dönüştürmeler işleyerek özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> ve <xref:System.Windows.Forms.DataGridView.CellParsing> olayları <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 Bir sütunun hücre değeri veri türü belirtilen <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> sütunun özelliği.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> İle kullanılan <xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleri. <xref:System.Boolean> değerleri görüntülemek için iki veya üç durumu onay kutularını değerine göre olarak <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> özelliği. Ne zaman sütunu bağlı <xref:System.Windows.Forms.CheckState> değerleri <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> özellik değeri `true` varsayılan olarak.  
  
 Genellikle, onay kutusunu hücre değerlerini gibi diğer herhangi bir veri depolama veya toplu işlemleri gerçekleştirmek için tasarlanmıştır. Kullanıcılar bir onay kutusu hücreyi tıklatın, işleyebileceği hemen yanıt vermek istiyorsanız <xref:System.Windows.Forms.DataGridView.CellClick> olay, ancak bu olay bir hücre değerini güncelleştirilmeden önce gerçekleşir. Tıklamanın zaman yeni bir değer gerekiyorsa, beklenen değer ne olacağını hesaplamak için bir seçenek olan geçerli değere göre. Değişikliği hemen işleyin ve işlemek için başka bir yaklaşımdır <xref:System.Windows.Forms.DataGridView.CellValueChanged> yanıtlamak için olay. Hücre tıklandığında değişikliği kaydetmek için işlemelidir <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> olay. Geçerli hücreyi bir onay kutusu hücreyse işleyicisinde çağrı <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> yöntemi ve geçişinde <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> değeri.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Resimleri görüntülemek için kullanılır. Resim sütunları bir veri kaynağından otomatik olarak doldurulur, bağlanmamış sütunlar için el ile doldurulmuş veya dinamik olarak bir işleyicisindeki doldurulmuş <xref:System.Windows.Forms.DataGridView.CellFormatting> olay.  
  
 Görüntü biçimlerini tarafından desteklenen tüm biçimler dahil olmak üzere, çeşitli bayt dizileri ile birlikte çalışır bir görüntü sütunu bir veri kaynağından otomatik popülasyonu <xref:System.Drawing.Image> sınıfı ve Microsoft® Access ve Northwind örnek veritabanı tarafından kullanılan OLE resim biçimi.  
  
 Bir görüntü sütunu el ile doldurma yararlıdır işlevselliğini sağlamak istediğinizde bir <xref:System.Windows.Forms.DataGridViewButtonColumn>, ancak özelleştirilmiş bir görünüm. İşleyebilirsiniz <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olayı bir görüntü hücresi içinde tıklamalara yanıt verme.  
  
 Bir görüntü sütunu için bir işleyici Hücre doldurma <xref:System.Windows.Forms.DataGridView.CellFormatting> olay, hesaplanan değerler ya da resmi olmayan biçimde değerler için görüntüleri sağlamak istediğinizde yararlıdır. Örneğin, dize değerlerini içeren bir "Risk" sütun gibi olabilir `"high"`, `"middle"`, ve `"low"` simgeler olarak görüntülemek istediğiniz. Alternatif olarak, görüntüleri yerine ikili içeriğini yüklenmesi gereken görüntüleri konumlarını içeren bir "Görüntü" sütunu olabilir.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 İle <xref:System.Windows.Forms.DataGridViewButtonColumn>, düğmelerini içeren hücre içeren bir sütun görüntüleyebilirsiniz. Kullanıcılarınızın sipariş verme veya ayrı bir pencerede alt kayıtları görüntüleme gibi belirli kayıtlarda eylemleri gerçekleştirmek kolay bir yol sağlamak istediğinizde bu kullanışlıdır.  
  
 Düğme sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetimi. Düğme sütunları kullanmak için bunları el ile oluşturmanız ve tarafından döndürülen bir koleksiyonda eklemek <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> özelliği.  
  
 Düğme hücrelerini kullanıcı tıklamayla işleyerek yanıt verebilirsiniz <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olay.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 İle <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, aşağı açılan liste kutuları içeren hücre içeren bir sütun görüntüleyebilirsiniz. Bu, yalnızca kategori sütunu Northwind örnek veritabanındaki Ürünler tablosunun gibi belirli değerleri içeren alanları veri girişi için kullanışlıdır.  
  
 Açılan listenin doldurmak aynı şekilde tüm hücreler için kullanılan doldurabilirsiniz bir <xref:System.Windows.Forms.ComboBox> aşağı açılan listesinde, el ile tarafından döndürülen koleksiyon üzerinden <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> özelliği veya veri kaynağına bağlama <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri. Daha fazla bilgi için [ComboBox denetimi](combobox-control-windows-forms.md).  
  
 Veri kaynağı tarafından kullanılan gerçek hücre değerlerinin bağlayabilirsiniz <xref:System.Windows.Forms.DataGridView> ayarlayarak denetim <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> özelliği <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Birleşik giriş kutusu sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetimi. Birleşik giriş kutusu sütunları kullanmak için el ile oluşturun ve bunları tarafından döndürülen bir koleksiyona ekler <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 İle <xref:System.Windows.Forms.DataGridViewLinkColumn>, köprüler içeren hücre içeren bir sütun görüntüleyebilirsiniz. Bu, veri kaynağına veya alternatif olarak alt kayıtları bir pencere açarak gibi özel davranışları için düğme sütununda URL değerleri için kullanışlıdır.  
  
 Bağlantı sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetimi. Bağlantı sütunları kullanmak için el ile oluşturmak ve bunları tarafından döndürülen bir koleksiyona ekler <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği.  
  
 İşleyerek bağlantılarında kullanıcı tıklamalara yanıt verebilir <xref:System.Windows.Forms.DataGridView.CellContentClick> olay. Bu olay kodundan <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick> kullanıcı bir hücreye herhangi bir yere tıkladığında oluşan olaylar.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Sınıfı önce sırasında ve sonrasında bağlantıların görünümünü değiştirmek için çeşitli özellikler sağlar bunlar tıkladı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminin hücrelerinde görüntü görüntüleme](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde görüntü sütunlarıyla çalışma](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
