---
title: DataGridView Denetimine Genel Bakış
description: Birçok farklı türdeki veri kaynağından tablo verilerini göstermek ve düzenlemek için Windows Forms DataGridView denetimini kullanmayı öğrenin.
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
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174620"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView>Denetim yerini alır ve denetime işlevsellik ekler <xref:System.Windows.Forms.DataGrid> ; ancak, isterseniz <xref:System.Windows.Forms.DataGrid> Denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView>Denetimiyle birçok farklı türde veri kaynağından tablo verilerini görüntüleyebilir ve düzenleyebilirsiniz.  
  
 Verileri <xref:System.Windows.Forms.DataGridView> denetime bağlama basittir ve sezgisel olur ve çoğu durumda özelliğin ayarlanması kadar basittir <xref:System.Windows.Forms.DataGridView.DataSource%2A> . Birden çok liste veya tablo içeren bir veri kaynağına bağladığınızda, <xref:System.Windows.Forms.DataGridView.DataMember%2A> özelliği bağlamak için listeyi veya tabloyu belirten bir dizeye ayarlayın.  
  
 <xref:System.Windows.Forms.DataGridView>Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle aşağıdaki listede açıklanan sınıf örneklerine bağlanır:  
  
- <xref:System.Collections.IList>Tek boyutlu diziler dahil olmak üzere arabirimi uygulayan herhangi bir sınıf.  
  
- Ve sınıfları gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IListSource> <xref:System.Data.DataTable> <xref:System.Data.DataSet> .  
  
- Sınıfı gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingList> <xref:System.ComponentModel.BindingList%601> .  
  
- Sınıfı gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingListView> <xref:System.Windows.Forms.BindingSource> .  
  
 <xref:System.Windows.Forms.DataGridView>Denetim, bu arabirimlerin döndürdüğü nesnelerin ortak özelliklerine veya <xref:System.ComponentModel.ICustomTypeDescriptor> döndürülen nesneler üzerinde uygulanmışsa bir arabirim tarafından döndürülen özellikler koleksiyonuna veri bağlamayı destekler.  
  
 Genellikle, bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır ve <xref:System.Windows.Forms.BindingSource> bileşeni başka bir veri kaynağına bağlayabilir veya iş nesneleriyle dolduracaksınız. Çok <xref:System.Windows.Forms.BindingSource> çeşitli veri kaynaklarına bağlanabileceğinden ve birçok veri bağlama sorununu otomatik olarak çözümleyebildiğinden, bileşen tercih edilen veri kaynağıdır. Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView>Denetim, temel alınan veri deposu olmadan *ilişkisiz* modda da kullanılabilir. İlişkisiz denetim kullanan bir kod örneği için <xref:System.Windows.Forms.DataGridView> bkz. [izlenecek yol: Ilişkisiz Windows Forms DataGridView denetimi oluşturma](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView>Denetim, yüksek oranda yapılandırılabilir ve genişletilebilir ve görünümünü ve davranışını özelleştirmek için birçok özellik, yöntem ve olay sağlar. Windows Forms uygulamanızın tablo verilerini görüntülemesini istediğinizde, <xref:System.Windows.Forms.DataGridView> denetimi diğerlerinden önce kullanmayı düşünün (örneğin, <xref:System.Windows.Forms.DataGrid> ). Salt okunurdur, salt okunurdur veya bir kullanıcının milyonlarca kayıt içeren bir tabloyu düzenlemesini <xref:System.Windows.Forms.DataGridView> sağladıysanız, denetim size kolayca programlanabilir, bellek açısından verimli bir çözüm sunar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView Denetimi Teknoloji Özeti](datagridview-control-technology-summary-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView>Denetim kavramlarını ve ilgili sınıfların kullanımını özetler.  
  
 [DataGridView Denetim Mimarisi](datagridview-control-architecture-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView>Tür hiyerarşisini ve devralma yapısını açıklayan denetim mimarisini açıklar.  
  
 [DataGridView Denetimi Senaryoları](datagridview-control-scenarios-windows-forms.md)  
 Denetimlerin kullanıldığı en yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> .  
  
 [DataGridView Denetimi Kod Dizini](datagridview-control-code-directory-windows-forms.md)  
 Çeşitli görevler için belgelerde kod örneklerine bağlantılar sağlar <xref:System.Windows.Forms.DataGridView> . Bu örnekler, görev türüne göre kategorilere ayrılmıştır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)  
 <xref:System.Windows.Forms.DataGridView>Bilgileri göstermek ve kullanıcıların bilgileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms denetimindeki sütun türlerini açıklar.  
  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.  
  
 [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama <xref:System.Windows.Forms.DataGridView> hücrelerini ve satırları betimleyen ve türetilmiş hücre, sütun ve satır türleri oluşturan konuları sağlar.  
  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetimindeki Varsayılan İşlevler](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
