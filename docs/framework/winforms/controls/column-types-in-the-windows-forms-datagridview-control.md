---
title: DataGridView Denetimindeki sütun türleri
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743860"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Türleri
<xref:System.Windows.Forms.DataGridView> denetimi, bilgilerini göstermek ve kullanıcıların bilgileri değiştirmesini veya eklemesini sağlamak için çeşitli sütun türlerini kullanır.  
  
 Bir <xref:System.Windows.Forms.DataGridView> denetimini bağladığınızda ve <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özelliğini `true`ayarladığınızda, sütunlar, bağlı veri kaynağında yer alan veri türleri için uygun olan varsayılan sütun türleri kullanılarak otomatik olarak oluşturulur.  
  
 Ayrıca, herhangi bir sütun sınıfının örneklerini oluşturup <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği tarafından döndürülen koleksiyona ekleyebilirsiniz. Bu örnekleri ilişkisiz sütunlar olarak kullanılmak üzere oluşturabilir veya el ile bağlayabilirsiniz. El ile bağlantılı sütunlar, örneğin, bir türün otomatik olarak oluşturulan sütununu başka bir tür sütunuyla değiştirmek istediğinizde yararlıdır.  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.DataGridView> denetiminde kullanılabilecek çeşitli sütun sınıfları açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Metin tabanlı değerlerle kullanılır. Sayılara ve dizelere bağlamada otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|<xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleriyle kullanılır. Bu türlerin değerlerine bağlanırken otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Görüntüleri göstermek için kullanılır. Bayt dizilerine, <xref:System.Drawing.Image> nesnelerine veya <xref:System.Drawing.Icon> nesnelerine bağlama yapıldığında otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Hücrelerde düğmeleri göstermek için kullanılır. Bağlama sırasında otomatik olarak oluşturulmaz. Genellikle ilişkisiz sütunlar olarak kullanılır.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Hücrelerde açılan listeleri göstermek için kullanılır. Bağlama sırasında otomatik olarak oluşturulmaz. Genellikle veri ile bağlantılı olarak.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Hücrelerdeki bağlantıları göstermek için kullanılır. Bağlama sırasında otomatik olarak oluşturulmaz. Genellikle veri ile bağlantılı olarak.|  
|Özel sütun türü|Özel görünüm, davranış veya barındırılan denetimler sağlamak için <xref:System.Windows.Forms.DataGridViewColumn> sınıfını veya türetilmiş sınıflarından herhangi birini devralarak kendi sütun sınıfınızı oluşturabilirsiniz. Daha fazla bilgi için bkz [. nasıl yapılır: davranış ve görünümünü genişleterek Windows Forms DataGridView Denetimindeki hücreleri ve sütunları özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Bu sütun türleri aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>, sayılar ve dizeler gibi metin tabanlı değerlerle kullanılmak üzere genel amaçlı bir sütun türüdür. Düzenleme modunda, etkin hücrede kullanıcıların hücre değerini değiştirmesine olanak sağlayan bir <xref:System.Windows.Forms.TextBox> denetimi görüntülenir.  
  
 Hücre değerleri, ekran için otomatik olarak dizelere dönüştürülür. Kullanıcı tarafından girilen veya değiştirilen değerler, uygun veri türünün bir hücre değeri oluşturacak şekilde otomatik olarak ayrıştırılır. <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellFormatting> ve <xref:System.Windows.Forms.DataGridView.CellParsing> olaylarını işleyerek bu dönüşümleri özelleştirebilirsiniz.  
  
 Sütunun hücre değeri veri türü, sütunun <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> özelliğinde belirtilmiştir.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>, <xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleriyle kullanılır. <xref:System.Boolean> değerler, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> özelliğinin değerine bağlı olarak iki durumlu veya üç durumlu onay kutuları olarak görüntülenir. Sütun <xref:System.Windows.Forms.CheckState> değerlere bağlandığında, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> Özellik değeri varsayılan olarak `true`.  
  
 Genellikle, onay kutusu hücre değerleri depolama için, diğer veriler gibi veya toplu işlemler gerçekleştirmek üzere tasarlanmıştır. Kullanıcılar bir onay kutusu hücresine tıkladığınızda hemen yanıt vermek istiyorsanız, <xref:System.Windows.Forms.DataGridView.CellClick> olayını işleyebilirsiniz, ancak bu olay hücre değeri güncellenmeye başlamadan önce oluşur. Tıklama sırasında yeni değere ihtiyacınız varsa, tek bir seçenek, beklenen değerin geçerli değere göre ne olacağını hesaplamalıdır. Başka bir yaklaşım ise değişikliği hemen yürütmeniz ve bu uygulamaya yanıt vermek için <xref:System.Windows.Forms.DataGridView.CellValueChanged> olayıdır. Hücre tıklandığında değişikliği yürütmek için <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> olayını işlemeniz gerekir. İşleyicide, geçerli hücre bir onay kutusu hücresi ise <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> yöntemi çağırın ve <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> değerini geçirin.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> görüntüleri göstermek için kullanılır. Resim sütunları bir veri kaynağından otomatik olarak doldurulabilir, İlişkisiz sütunlarda el ile doldurulabilir veya <xref:System.Windows.Forms.DataGridView.CellFormatting> olayı için bir işleyicide dinamik olarak doldurulamaz.  
  
 Bir veri kaynağından bir görüntü sütununun otomatik olarak popülasyon, <xref:System.Drawing.Image> sınıfı tarafından desteklenen tüm biçimler ve Microsoft® Access ve Northwind örnek veritabanı tarafından kullanılan OLE resim biçimi dahil olmak üzere çeşitli görüntü biçimlerinde bayt dizileri ile çalışmaktadır.  
  
 Bir görüntü sütununu el ile doldurmak, bir <xref:System.Windows.Forms.DataGridViewButtonColumn>işlevlerini sağlamak istediğinizde, ancak özelleştirilmiş bir görünümle birlikte yararlı olur. Bir resim hücresinin içindeki tıklamaların yanıt vermesi için <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olayını işleyebilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> olayına ilişkin bir görüntü sütununun hücrelerini doldurmak, görüntü dışı biçimlerdeki Hesaplanmış değerler veya değerler için görüntü sağlamak istediğinizde faydalıdır. Örneğin, simge olarak görüntülenmesini istediğiniz `"high"`, `"middle"`ve `"low"` gibi dize değerleri içeren bir "risk" sütununuz olabilir. Alternatif olarak, görüntülerin ikili içeriği yerine yüklenmesi gereken görüntülerin konumlarını içeren bir "Image" sütunu olabilir.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, düğme içeren bir hücre sütununu görüntüleyebilirsiniz. Bu, kullanıcılarınızın belirli kayıtlar üzerinde (sipariş yerleştirme veya alt kayıtları ayrı bir pencereye görüntüleme gibi) eylemleri gerçekleştirmesi için kolay bir yol sağlamak istediğinizde yararlıdır.  
  
 Veri bağlama <xref:System.Windows.Forms.DataGridView> denetimi sırasında düğme sütunları otomatik olarak oluşturulmaz. Düğme sütunlarını kullanmak için bunları el ile oluşturmanız ve <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> özelliği tarafından döndürülen koleksiyona eklemeniz gerekir.  
  
 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olayını işleyerek düğme hücrelerinde Kullanıcı tıklamalarına yanıt verebilirsiniz.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, açılan liste kutuları içeren bir hücre sütununu görüntüleyebilirsiniz. Bu, Northwind örnek veritabanındaki Products tablosunun Kategori sütunu gibi yalnızca belirli değerleri içerebilen alanlarda veri girişi için yararlıdır.  
  
 Tüm hücreler için kullanılan aşağı açılan listeyi, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> özelliği tarafından döndürülen koleksiyon üzerinden el ile veya <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri aracılığıyla bir veri kaynağına bağlayarak <xref:System.Windows.Forms.ComboBox> bir açılan liste ile aynı şekilde doldurabilirsiniz. Daha fazla bilgi için bkz. [ComboBox denetimi](combobox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType><xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> özelliğini ayarlayarak, gerçek hücre değerlerini <xref:System.Windows.Forms.DataGridView> denetimi tarafından kullanılan veri kaynağına bağlayabilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi veri bağlama sırasında Birleşik giriş kutusu sütunları otomatik olarak oluşturulmaz. Birleşik giriş kutusu sütunlarını kullanmak için bunları el ile oluşturmanız ve <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği tarafından döndürülen koleksiyona eklemeniz gerekir.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>, köprü içeren bir hücre sütununu görüntüleyebilirsiniz. Bu, veri kaynağındaki URL değerleri için veya alt kayıtlarla bir pencere açmak gibi özel davranışlar için düğme sütununa alternatif olarak faydalıdır.  
  
 Veri bağlama bir <xref:System.Windows.Forms.DataGridView> denetimi olduğunda bağlantı sütunları otomatik olarak oluşturulmaz. Bağlantı sütunlarını kullanmak için bunları el ile oluşturmanız ve <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği tarafından döndürülen koleksiyona eklemeniz gerekir.  
  
 <xref:System.Windows.Forms.DataGridView.CellContentClick> olayını işleyerek, bağlantılara Kullanıcı tıklamasına yanıt verebilirsiniz. Bu olay, bir kullanıcı hücrede herhangi bir yere tıkladığında ortaya çıkan <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick> olaylarından farklıdır.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> sınıfı, ve tıklandıktan sonra bağlantıların görünümünü değiştirmek için çeşitli özellikler sağlar.  
  
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
- [Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Görüntü Sütunlarıyla Çalışma](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
