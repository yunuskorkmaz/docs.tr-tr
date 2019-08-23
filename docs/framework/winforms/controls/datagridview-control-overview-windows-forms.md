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
ms.openlocfilehash: 992bf57642c955a87cd7675e0bbe7c52131e8039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969143"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetimiyle birçok farklı türde veri kaynağından tablo verilerini görüntüleyebilir ve düzenleyebilirsiniz.  
  
 Verileri <xref:System.Windows.Forms.DataGridView> denetime bağlama basittir ve sezgisel olur ve çoğu durumda <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğin ayarlanması kadar basittir. Birden çok liste veya tablo içeren bir veri kaynağına bağladığınızda, <xref:System.Windows.Forms.DataGridView.DataMember%2A> özelliği bağlamak için listeyi veya tabloyu belirten bir dizeye ayarlayın.  
  
 <xref:System.Windows.Forms.DataGridView> Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle aşağıdaki listede açıklanan sınıf örneklerine bağlanır:  
  
- Tek boyutlu diziler dahil olmak <xref:System.Collections.IList> üzere arabirimi uygulayan herhangi bir sınıf.  
  
- <xref:System.Data.DataTable> <xref:System.ComponentModel.IListSource> Ve<xref:System.Data.DataSet> sınıfları gibi arabirimi uygulayan herhangi bir sınıf.  
  
- Sınıfı gibi arabirimi<xref:System.ComponentModel.IBindingList> uygulayan herhangi bir sınıf. <xref:System.ComponentModel.BindingList%601>  
  
- Sınıfı gibi arabirimi<xref:System.ComponentModel.IBindingListView> uygulayan herhangi bir sınıf. <xref:System.Windows.Forms.BindingSource>  
  
 Denetim <xref:System.Windows.Forms.DataGridView> , bu arabirimlerin döndürdüğü nesnelerin ortak özelliklerine veya döndürülen nesneler üzerinde uygulanmışsa bir <xref:System.ComponentModel.ICustomTypeDescriptor> arabirim tarafından döndürülen özellikler koleksiyonuna veri bağlamayı destekler.  
  
 Genellikle, bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır ve <xref:System.Windows.Forms.BindingSource> bileşeni başka bir veri kaynağına bağlayabilir veya iş nesneleriyle dolduracaksınız. Çok <xref:System.Windows.Forms.BindingSource> çeşitli veri kaynaklarına bağlanabileceğinden ve birçok veri bağlama sorununu otomatik olarak çözümleyebildiğinden, bileşen tercih edilen veri kaynağıdır. Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).  
  
 Denetim, temel alınan veri deposu olmadan ilişkisiz modda da kullanılabilir. <xref:System.Windows.Forms.DataGridView> İlişkisiz <xref:System.Windows.Forms.DataGridView> denetim kullanan bir kod örneği için bkz [. İzlenecek yol: Ilişkisiz Windows Forms DataGridView denetimi](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)oluşturma.  
  
 <xref:System.Windows.Forms.DataGridView> Denetim, yüksek oranda yapılandırılabilir ve genişletilebilir ve görünümünü ve davranışını özelleştirmek için birçok özellik, yöntem ve olay sağlar. Windows Forms uygulamanızın tablo verilerini görüntülemesini istediğinizde, <xref:System.Windows.Forms.DataGridView> denetimi diğerlerinden önce kullanmayı düşünün (örneğin, <xref:System.Windows.Forms.DataGrid>). Salt okunurdur, salt okunurdur veya bir kullanıcının milyonlarca kayıt <xref:System.Windows.Forms.DataGridView> içeren bir tabloyu düzenlemesini sağladıysanız, denetim size kolayca programlanabilir, bellek açısından verimli bir çözüm sunar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView Denetimi Teknoloji Özeti](datagridview-control-technology-summary-windows-forms.md)  
 Denetim <xref:System.Windows.Forms.DataGridView> kavramlarını ve ilgili sınıfların kullanımını özetler.  
  
 [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)  
 Tür hiyerarşisini ve devralma yapısını <xref:System.Windows.Forms.DataGridView> açıklayan denetim mimarisini açıklar.  
  
 [DataGridView Denetimi Senaryoları](datagridview-control-scenarios-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> Denetimlerin kullanıldığı en yaygın senaryoları açıklar.  
  
 [DataGridView Denetimi Kod Dizini](datagridview-control-code-directory-windows-forms.md)  
 Çeşitli <xref:System.Windows.Forms.DataGridView> görevler için belgelerde kod örneklerine bağlantılar sağlar. Bu örnekler, görev türüne göre kategorilere ayrılmıştır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)  
 Bilgileri göstermek ve kullanıcıların bilgileri değiştirmesine veya <xref:System.Windows.Forms.DataGridView> eklemesine izin vermek için kullanılan Windows Forms denetimindeki sütun türlerini açıklar.  
  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.  
  
 [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama <xref:System.Windows.Forms.DataGridView> hücrelerini ve satırları betimleyen ve türetilmiş hücre, sütun ve satır türleri oluşturan konuları sağlar.  
  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetimindeki Varsayılan İşlevler](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
