---
title: DataGridView Denetimi Teknoloji Özeti (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: ca8268137f2a154c782388d0f13cdd02504cbb64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217425"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView Denetimi Teknoloji Özeti (Windows Forms)
Bu konu hakkında bilgiler için özetlenmiştir `DataGridView` denetimi ve kullanımını destekleyen sınıflar.  
  
 Verileri tablo biçiminde görüntülemek, sık gerçekleştirmek muhtemelen bir görevdir. `DataGridView` Denetimi bir kılavuzda verileri sunmak için eksiksiz bir çözüm olarak tasarlanmıştır.  
  
## <a name="keywords"></a>anahtar sözcükler  
 DataGridView, BindingSource, tablo, hücre, veri bağlama, sanal mod  
  
## <a name="namespaces"></a>Ad Alanları  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>İlgili Teknolojiler  
 `BindingSource`  
  
## <a name="background"></a>Arka Plan  
 Kullanıcı Arabirimi (UI) tasarımcıları sık, kullanıcılara tablosal verileri görüntülemek gerekli bulur. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Verileri bir tablo veya kılavuz göstermek için birçok yol sağlar. `DataGridView` Denetimi bu teknoloji Windows Forms uygulamaları için en son evrimini temsil eder.  
  
 `DataGridView` Denetimi, bir veri deposundan veri satırı görüntüleyebilirsiniz. Birçok veri depolarının türleri desteklenir. Veri deposu, tek boyutlu bir dizi gibi basit, yazılmamış veri tutabilir veya türü belirtilmiş veri gibi tutabilen bir <xref:System.Data.DataSet>. Daha fazla bilgi için [nasıl yapılır: Veri bağlama Windows Forms DataGridView denetiminde](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar. Denetim, küçük ve büyük veri kümelerini salt okunur veya düzenlenebilir görünümlerini göstermek için kullanabilirsiniz.  
  
 Genişletebileceğiniz `DataGridView` denetim çeşitli şekillerde uygulamalarınızda özel davranışlar oluşturun. Örneğin, program aracılığıyla kendi algoritmaların sıralanması belirtebilirsiniz ve hücrelerin kendi türlerinizi oluşturabilirsiniz. Kolayca görünümünü özelleştirebilirsiniz `DataGridView` arasında çeşitli özellikleri seçerek denetimi. Birçok veri depolarının türde bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetim, kendisiyle ilişkili bir veri kaynağı olmadan çalışabilir.  
  
## <a name="implementing-datagridview-classes"></a>DataGridView sınıfları uygulama  
 Yararlanmak birkaç yol vardır `DataGridView` denetimin genişletilebilirlik özellikleri. Denetim olayları ve özellikleri birçok yönden özelleştirebilirsiniz, ancak bazı özelleştirmeler varolan türetilmiş yeni sınıflar oluşturmak ihtiyaç duyduğunuz `DataGridView` sınıfları.  
  
 En yaygın kullanılan temel sınıflar `DataGridViewCell` ve `DataGridViewColumn`. Kendi hücre sınıftan türetilip `DataGridViewCell` veya onun alt sınıfları. Herhangi bir sütun hücresi her türlü ekleyebilirsiniz, ancak, genellikle de yardımcı sütun öğesinden bir sınıf türetin `DataGridViewColumn` varsayılan olarak, özel hücresi türü hücrelerinin barındıran.  
  
 Uygulayabileceğiniz `IDataGridViewEditingCell` türetilmiş hücre sınıfınızda, düzenleme işlevi sahip, ancak düzenleme modu, bir denetimin barındırmamalıdır hücresi türü oluşturmak için arabirim. Bir hücrede düzenleme moduna barındırabilecek bir denetim oluşturmak için uygulayabileceğiniz `IDataGridViewEditingControl` sınıfından türetilen bir sınıfta arabirimi <xref:System.Windows.Forms.Control>.  
  
 Daha fazla bilgi için [nasıl yapılır: Hücreleri özelleştirme ve sütunları Windows Forms DataGridView denetiminde davranış ve görünümünü genişleterek](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) ve [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Bir bakışta DataGridView sınıfları  
 <xref:System.Windows.Forms>  
  
|Teknoloji alanı|Sınıf/arabirim/yapılandırma öğeleri|  
|---------------------|-------------------------------------------------|  
|Veri Bağlama|<xref:System.Windows.Forms.BindingSource>|  
|Veri sunumu|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Genişletilebilirlik|<xref:System.Windows.Forms.DataGridViewCell> ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Yenilikler  
 <xref:System.Windows.Forms.DataGridView> Denetimini Windows Forms tablo verilerini görüntülemek için eksiksiz bir çözüm olarak tasarlanmıştır. Kullanmayı düşünmelisiniz <xref:System.Windows.Forms.DataGridView> diğer çözümleri önce denetimini <xref:System.Windows.Forms.DataGrid>, yeni bir uygulama yazarken. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetim Kapat birlikte çalışabilir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu bileşen, birincil veri kaynağına bir formun olacak şekilde tasarlanmıştır. Arasındaki etkileşimi yönetebilirsiniz bir <xref:System.Windows.Forms.DataGridView> denetim ve veri bağımsız olarak kendi veri kaynağı kaynak türü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
