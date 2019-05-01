---
title: DataGridView Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 095c89fd305b1eeb73e2919760abe48e848c6aa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902323"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi, görüntüleyebilir ve tablosal verilerden birçok farklı türde veri kaynaklarını düzenleyin.  
  
 Veri bağlama <xref:System.Windows.Forms.DataGridView> denetimidir basit ve sezgisel ve çoğu durumda ayarı olarak basit <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği. Birden çok listeler veya tablolar içeren bir veri kaynağına bağlandığınızda ayarlamak <xref:System.Windows.Forms.DataGridView.DataMember%2A> liste veya bağlamak için tabloyu belirten bir dize özelliği.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi için aşağıda açıklanan sınıfların örneklerini bağlamak için standart Windows Forms veri bağlama modelini destekler:  
  
- Uygulayan sınıfa <xref:System.Collections.IList> arabirimi, tek boyutlu diziler de dahil olmak üzere.  
  
- Uygulayan sınıfa <xref:System.ComponentModel.IListSource> gibi arabirim <xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları.  
  
- Uygulayan sınıfa <xref:System.ComponentModel.IBindingList> gibi arabirim <xref:System.ComponentModel.BindingList%601> sınıfı.  
  
- Uygulayan sınıfa <xref:System.ComponentModel.IBindingListView> gibi arabirim <xref:System.Windows.Forms.BindingSource> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi bu arabirimleri tarafından döndürülen nesnelerin genel özelliklerini veya özellikler koleksiyonu tarafından döndürülen veri bağlamayı destekler bir <xref:System.ComponentModel.ICustomTypeDescriptor> döndürülen nesnelerin uygulanırsa, arabirim.  
  
 Genellikle, bağlayacaksınız bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bağlama <xref:System.Windows.Forms.BindingSource> bileşen başka bir veri kaynağı veya iş nesneleri ile doldurur. <xref:System.Windows.Forms.BindingSource> Bileşeni olduğundan tercih edilen veri kaynağı çok çeşitli veri kaynakları bağlayabilirsiniz ve çok sayıda veri bağlama sorunlarını otomatik olarak çözebilirsiniz. Daha fazla bilgi için [BindingSource bileşeni](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi ayrıca kullanılabilir *ilişkisiz* moduyla temel alınan veri depo yok. İlişkisiz bir kullanan bir kod örnek <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: Oluşturma bağlantısız bir Windows Forms DataGridView denetiminde](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetimidir son derece yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve onun görünümünü ve davranışını özelleştirmek için olayları sağlar. Tablosal verileri görüntülemek için Windows Forms uygulaması istediğinizde kullanmayı <xref:System.Windows.Forms.DataGridView> diğerlerinden önce denetim (örneğin, <xref:System.Windows.Forms.DataGrid>). Salt okunur değerleri küçük bir kılavuz görüntülüyorsanız ya da milyonlarca kayıt içeren bir tablo düzenlemek bir kullanıcı etkinleştiriyorsanız <xref:System.Windows.Forms.DataGridView> denetimi, bir kolayca programlanabilir, belleği verimli kullanan Çözümle sağlayacaktır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView Denetimi Teknoloji Özeti](datagridview-control-technology-summary-windows-forms.md)  
 Özetler <xref:System.Windows.Forms.DataGridView> kavramları ve ilişkili sınıflarının kullanımını denetler.  
  
 [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)  
 Mimarisini açıklar <xref:System.Windows.Forms.DataGridView> türü ve devralma hiyerarşisi yapısını açıklayan denetimi.  
  
 [DataGridView Denetimi Senaryoları](datagridview-control-scenarios-windows-forms.md)  
 En yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> denetimleri kullanılır.  
  
 [DataGridView Denetimi Kod Dizini](datagridview-control-code-directory-windows-forms.md)  
 Kod örnekleri çeşitli belgelerine bağlantılar sağlar <xref:System.Windows.Forms.DataGridView> görevleri. Bu örnekler, görev türüne göre kategorize edilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)  
 Windows Forms'ta sütun türleri ele alınmaktadır <xref:System.Windows.Forms.DataGridView> denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcılara izin vermek için kullanılır.  
  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)  
 El ile veya bir dış veri kaynağından denetimi veriyle doldurmak nasıl açıklayan konuları sağlar.  
  
 [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama açıklayan konuları sağlar <xref:System.Windows.Forms.DataGridView> hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.  
  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetimindeki Varsayılan İşlevler](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
