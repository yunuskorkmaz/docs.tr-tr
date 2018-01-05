---
title: "Windows Forms DataGridView Denetiminde Sütun Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92c6881fe876bba3fe0224a358a9b12767d53f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Türleri
<xref:System.Windows.Forms.DataGridView> Denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcıların sağlamak için birkaç sütun türleri kullanır.  
  
 Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetleyin ve ayarlayın <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özelliğine `true`, sütunları, varsayılan sütun türleri bağlı veri kaynağında bulunan veri türleri için uygun kullanarak otomatik olarak oluşturulur.  
  
 Ayrıca sütun sınıflarından herhangi biriyle örneklerini kendiniz oluşturabilir ve bunları tarafından döndürülen koleksiyonuna ekleyin <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği. Bağlanmamış sütunlar olarak kullanmak için bu örnekler oluşturabilir veya bunları el ile bağlayabilirsiniz. El ile ilişkili sütun, örneğin, başka bir türünde bir sütun türünün otomatik olarak oluşturulan bir sütun değiştirmek istediğinizde faydalıdır.  
  
 Aşağıdaki tabloda kullanılabilir çeşitli sütun sınıflar açıklanmaktadır <xref:System.Windows.Forms.DataGridView> denetim.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Metin tabanlı değerlerle kullanılır. Sayılara hem de dizelere için bağlama sırasında otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|İle kullanılan <xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleri. Bu tür değerler için bağlama sırasında otomatik olarak oluşturulur.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Görüntüleri göstermek için kullanılır. Bayt dizileri için bağlama sırasında otomatik olarak oluşturulan <xref:System.Drawing.Image> nesneleri veya <xref:System.Drawing.Icon> nesneleri.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Hücrelerde düğmeleri görüntülemek için kullanılır. Otomatik olarak bağlama sırasında oluşturulmadı. Genellikle, bağlantısız sütun olarak kullanılır.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Aşağı açılır listeler hücrelerde görüntülemek için kullanılır. Otomatik olarak bağlama sırasında oluşturulmadı. Genellikle veri el ile ilişkili.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Hücrelerde bağlantıları görüntülemek için kullanılır. Otomatik olarak bağlama sırasında oluşturulmadı. Genellikle veri el ile ilişkili.|  
|Özel sütun türü|Kendi sütun sınıfı devralarak oluşturabileceğiniz <xref:System.Windows.Forms.DataGridViewColumn> sınıf veya herhangi bir özel görünüm, davranışı ya da barındırılan denetimlerin sağlamak türetilmiş. Daha fazla bilgi için bkz: [nasıl yapılır: hücre özelleştirme ve genişletme Their davranış ve görünümünü göre Windows Forms DataGridView denetiminde sütunları](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Bu sütun türleri aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Numaraları ve dizeler gibi metin tabanlı değerler ile kullanmak için genel amaçlı sütunun türü. Düzenleme modundaki bir <xref:System.Windows.Forms.TextBox> hücre değerini değiştirmek kullanıcıları etkinleştirme denetim etkin hücreye görüntülenir.  
  
 Hücre değerlerini otomatik olarak görüntülenecek dizelerin dönüştürülür. Girilen veya kullanıcı tarafından değiştirilmiş değerleri uygun veri türünde bir hücre değerini oluşturmak üzere otomatik olarak ayrıştırılır. Bu dönüşümleri işleyerek özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting> ve <xref:System.Windows.Forms.DataGridView.CellParsing> olayları <xref:System.Windows.Forms.DataGridView> denetim.  
  
 Bir sütunun hücre değeri veri türü belirtilen <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> sütunun özelliği.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> İle kullanılan <xref:System.Boolean> ve <xref:System.Windows.Forms.CheckState> değerleri. <xref:System.Boolean>değerleri görüntüler iki durumlu veya üç durumlu onay kutularını değerine bağlı olarak olarak <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> özelliği. Ne zaman sütun bağlı <xref:System.Windows.Forms.CheckState> değerleri, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> özellik değeri `true` varsayılan olarak.  
  
 Genellikle, onay kutusunu hücre değerlerini gibi diğer herhangi bir veri depolama veya toplu işlemleri gerçekleştirmek için tasarlanmıştır. Kullanıcılar bir onay kutusu hücreyi tıklattığınızda işleyebilir hemen yanıt vermek istiyorsanız <xref:System.Windows.Forms.DataGridView.CellClick> olay ancak bu olay hücre değerini güncelleştirilmeden önce oluşur. Yeni değer tıklatın aynı anda gerekiyorsa, beklenen değer ne olacağını hesaplamak için bir seçenek olan geçerli değere göre. Değişikliği hemen kaydetmek ve işlemek için başka bir yaklaşımdır <xref:System.Windows.Forms.DataGridView.CellValueChanged> yanıtlamak için olay. Hücre tıklatıldığında değişikliği kaydetmek için işlemelidir <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> olay. Geçerli hücreyi bir onay kutusu hücreyse işleyicisinde çağrısı <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> yöntemi ve geçişinde <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> değeri.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Görüntüleri göstermek için kullanılır. Görüntü sütunları otomatik olarak bir veri kaynağından doldurulur, bağlanmamış sütunlar için el ile doldurulur veya için bir işleyici içinde dinamik olarak doldurulan <xref:System.Windows.Forms.DataGridView.CellFormatting> olay.  
  
 Bayt dizileri resim biçimleri tarafından desteklenen tüm biçimleri dahil olmak üzere, çeşitli veri kaynağından bir görüntü sütunu otomatik popülasyonunu çalışır <xref:System.Drawing.Image> sınıfı ve Microsoft® Access ve Northwind örnek veritabanı tarafından kullanılan OLE resim biçimi.  
  
 Bir görüntü sütunu el ile doldurma yararlıdır işlevselliğini sağlamak istediğinizde bir <xref:System.Windows.Forms.DataGridViewButtonColumn>, ancak bir özelleştirilmiş görünüm. İşleyebilir <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> tıklama bir görüntü hücre içinde yanıt verecek şekilde olay.  
  
 Bir görüntü sütunu için bir işleyici hücrelerinin doldurma <xref:System.Windows.Forms.DataGridView.CellFormatting> olay, görüntüleri veya görüntü olmayan biçimlerini değerler hesaplanan değerler sağlamak istediğinizde yararlıdır. Örneğin, dize değerleri "Riskli" bir sütunla gibi olabilir `"high"`, `"middle"`, ve `"low"` simgelerle görüntülemek istediğiniz. Alternatif olarak, görüntüleri ikili içerik yerine yüklenmesi gereken görüntüleri konumlarını içeren bir "Görüntü" sütun olabilir.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 İle <xref:System.Windows.Forms.DataGridViewButtonColumn>, bir sütun düğmelerini içeren bir hücre görüntüleyebilirsiniz. Bir sipariş yerleştirme veya ayrı bir pencerede alt kayıtları görüntüleme gibi belirli kayıtlarda eylemleri gerçekleştirmek, kullanıcılar için kolay bir yol sağlamak istediğinizde kullanışlıdır.  
  
 Düğme sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetim. Düğme sütunları kullanmak için bunları el ile oluşturmak ve bunları tarafından döndürülen koleksiyonuna ekleyin <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> özelliği.  
  
 Kullanıcı tıklatma düğme hücrelerini ile işleyerek yanıt verebilirsiniz <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olay.  
  
## <a name="datagridviewcomboboxcolumn"></a>ÖzelliðiniDataGridViewComboBoxColumn  
 İle <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, aşağı açılan liste kutuları içeren hücre bir sütun görüntüleyebilirsiniz. Bu, yalnızca Northwind örnek veritabanı Ürünler tablosunun kategori sütunu gibi belirli değerler içerebilir alanları veri girişi için kullanışlıdır.  
  
 Doldurmak aynı şekilde tüm hücreler için kullanılan açılan listeyi doldurmak bir <xref:System.Windows.Forms.ComboBox> aşağı açılan listesinde, el ile tarafından döndürülen koleksiyonu aracılığıyla ya da <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> özelliği veya bir veri kaynağına bağlama tarafından <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri. Daha fazla bilgi için bkz: [ComboBox denetimi](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Tarafından kullanılan veri kaynağı gerçek hücre değerlerini bağlayabilirsiniz <xref:System.Windows.Forms.DataGridView> ayarlayarak denetim <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> özelliği <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Birleşik giriş kutusu sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetim. Birleşik giriş kutusu sütunları kullanmak için bunları el ile oluşturun ve bunları tarafından döndürülen koleksiyonuna ekleyin <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 İle <xref:System.Windows.Forms.DataGridViewLinkColumn>, bir sütun köprüler içeren bir hücre görüntüleyebilirsiniz. Bu, veri kaynağı veya alt kayıtlarıyla bir pencere açarak gibi özel davranışları düğme sütununda alternatif olarak URL değerleri için kullanışlıdır.  
  
 Bağlantı sütunları oluşturulmaz otomatik olarak veri bağlama sırasında bir <xref:System.Windows.Forms.DataGridView> denetim. Bağlantı sütunları kullanmak için bunları el ile oluşturun ve bunları tarafından döndürülen koleksiyonuna ekleyin <xref:System.Windows.Forms.DataGridView.Columns%2A> özelliği.  
  
 Kullanıcı tıklama bağlantılarında işleyerek yanıt verebilirsiniz <xref:System.Windows.Forms.DataGridView.CellContentClick> olay. Bu olay farklıdır <xref:System.Windows.Forms.DataGridView.CellClick> ve <xref:System.Windows.Forms.DataGridView.CellMouseClick> bir kullanıcı herhangi bir yerden bir hücreye tıkladığında oluşan olaylar.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Sınıfı bağlantıların görünümünü önce sırasında ve sonrasında değiştirmek için çeşitli özellikler sağlayan tıklattığınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Görüntü Sütunlarıyla Çalışma](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
