---
title: DataGridView Denetimine Genel Bakış
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742487"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> denetimiyle, birçok farklı türdeki veri kaynağından tablo verilerini görüntüleyebilir ve düzenleyebilirsiniz.  
  
 <xref:System.Windows.Forms.DataGridView> denetimine veri bağlama basittir ve sezgisel hale gelir ve çoğu durumda, <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlamak kadar basittir. Birden çok liste veya tablo içeren bir veri kaynağına bağladığınızda <xref:System.Windows.Forms.DataGridView.DataMember%2A> özelliğini, bağlanacak listeyi veya tabloyu belirten bir dizeye ayarlayın.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi standart Windows Forms veri bağlama modelini destekler, bu nedenle aşağıdaki listede açıklanan sınıfların örneklerine bağlanır:  
  
- Tek boyutlu diziler dahil <xref:System.Collections.IList> arabirimini uygulayan herhangi bir sınıf.  
  
- <xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları gibi <xref:System.ComponentModel.IListSource> arabirimini uygulayan herhangi bir sınıf.  
  
- <xref:System.ComponentModel.BindingList%601> sınıfı gibi <xref:System.ComponentModel.IBindingList> arabirimini uygulayan herhangi bir sınıf.  
  
- <xref:System.Windows.Forms.BindingSource> sınıfı gibi <xref:System.ComponentModel.IBindingListView> arabirimini uygulayan herhangi bir sınıf.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi, bu arabirimlerin döndürdüğü nesnelerin ortak özelliklerine veya döndürülen nesneler üzerinde uygulanmışsa bir <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi tarafından döndürülen özellikler koleksiyonuna veri bağlamayı destekler.  
  
 Genellikle, bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır ve <xref:System.Windows.Forms.BindingSource> bileşenini başka bir veri kaynağına bağlayabilir veya iş nesneleriyle dolduracaksınız. <xref:System.Windows.Forms.BindingSource> bileşeni tercih edilen veri kaynağıdır çünkü çok çeşitli veri kaynaklarına bağlanabilir ve birçok veri bağlama sorununu otomatik olarak çözümleyebilir. Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> denetimi, temel alınan veri deposu olmadan *ilişkisiz* modda da kullanılabilir. İlişkisiz <xref:System.Windows.Forms.DataGridView> denetimi kullanan bir kod örneği için bkz. [Izlenecek yol: ilişkisiz Windows Forms DataGridView denetimi oluşturma](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> denetimi yüksek oranda yapılandırılabilir ve Genişletilebilir olur ve görünümünü ve davranışını özelleştirmek için birçok özellik, yöntem ve olay sağlar. Windows Forms uygulamanızın tablo verilerini görüntülemesini istediğinizde, başkalarından önce <xref:System.Windows.Forms.DataGridView> denetimini kullanmayı düşünün (örneğin, <xref:System.Windows.Forms.DataGrid>). Salt okunurdur, salt okunurdur veya bir kullanıcının milyonlarca kayıt içeren bir tabloyu düzenlemesini sağladıysanız, <xref:System.Windows.Forms.DataGridView> denetimi size kolayca programlanabilir, bellek açısından verimli bir çözüm sunar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView Denetimi Teknoloji Özeti](datagridview-control-technology-summary-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> denetim kavramlarını ve ilgili sınıfların kullanımını özetler.  
  
 [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)  
 Tür hiyerarşisini ve devralma yapısını açıklayan <xref:System.Windows.Forms.DataGridView> denetiminin mimarisini açıklar.  
  
 [DataGridView Denetimi Senaryoları](datagridview-control-scenarios-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> denetimlerinin kullanıldığı en yaygın senaryoları açıklar.  
  
 [DataGridView Denetimi Kod Dizini](datagridview-control-code-directory-windows-forms.md)  
 Çeşitli <xref:System.Windows.Forms.DataGridView> görevleri için belgelerde kod örneklerine bağlantılar sağlar. Bu örnekler, görev türüne göre kategorilere ayrılmıştır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)  
 Bilgileri göstermek ve kullanıcıların bilgileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms <xref:System.Windows.Forms.DataGridView> denetimindeki sütun türlerini açıklar.  
  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.  
  
 [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama <xref:System.Windows.Forms.DataGridView> hücreleri ve satırları tanımlayan ve türetilmiş hücre, sütun ve satır türlerini oluşturan konuları sağlar.  
  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetimindeki Varsayılan İşlevler](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
