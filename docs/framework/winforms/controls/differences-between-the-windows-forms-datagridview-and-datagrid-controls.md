---
title: Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: d0a82d5724ebe142ae080fc930665733e701e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
<xref:System.Windows.Forms.DataGridView> Denetimidir yerini alan yeni bir denetim <xref:System.Windows.Forms.DataGrid> denetim. <xref:System.Windows.Forms.DataGridView> Denetimi sağlar eksik çok sayıda temel ve Gelişmiş Özellikler <xref:System.Windows.Forms.DataGrid> denetim. Ayrıca, mimarisini <xref:System.Windows.Forms.DataGridView> denetim kolaylaştırır çok genişletmenizi ve özelleştirmenizi daha <xref:System.Windows.Forms.DataGrid> denetim.  
  
 Aşağıdaki tabloda bulunan birincil özellikleri bazılarını açıklanmaktadır <xref:System.Windows.Forms.DataGridView> eksik denetim <xref:System.Windows.Forms.DataGrid> denetim.  
  
|DataGridView denetimi özelliği|Açıklama|  
|----------------------------------|-----------------|  
|Birden çok sütun türleri|<xref:System.Windows.Forms.DataGridView> Denetim sağlar. daha fazla yerleşik sütun türleri <xref:System.Windows.Forms.DataGrid> denetim. Bu sütun türleri en yaygın senaryolar ihtiyaçlarını karşılamak, ancak aynı zamanda genişletmek veya sütun türleri daha değiştirmek daha kolay <xref:System.Windows.Forms.DataGrid> denetim. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Verileri görüntülemek için birden çok yol|<xref:System.Windows.Forms.DataGrid> Denetimidir sınırlı bir dış veri kaynağından verileri görüntülemek için. <xref:System.Windows.Forms.DataGridView> Denetim, ancak görüntüleyebilir bağlanmamış veri denetimi, bir bağımlı veri kaynağı veya ilişkili ve ilişkisiz veri birlikte depolanır. Sanal mod da uygulayabilirsiniz <xref:System.Windows.Forms.DataGridView> özel veri yönetimi sağlamak üzere Denetim. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde veri görüntüleme modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Veri görüntüsünü özelleştirmek için birden çok yol|<xref:System.Windows.Forms.DataGridView> Birçok özellik ve verilerin nasıl biçimlendirilmiş veya görüntülenen belirtmenizi sağlayan olayları denetim sağlar. Örneğin, hücrelerini, satırları ve sütunları içerdikleri verilere bağlı olarak görünümünü değiştirebilirsiniz ya da bir veri türünde başka bir tür eşdeğer veriler ile değiştirebilirsiniz. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde verileri biçimlendirme](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Hücre, satır, sütun ve üstbilgisi görünümünü ve davranışını değiştirmek için birden çok seçenekleri|<xref:System.Windows.Forms.DataGridView> Denetimi çeşitli şekillerde tek tek kılavuz bileşenleri ile çalışmanıza olanak sağlar. Örneğin, satırları ve sütunları kaymasını engellemek için Dondur; Satırlar, sütunlar ve üstbilgilerini gizleme; Satır ve sütun başlığı boyutları ayarlanmış şekilde değiştirin; Kullanıcıların seçim biçimini değiştirme; ve tek tek hücrelerini, satırları ve sütunları için araç ipuçları ve kısayol menüleri sağlayın.|  
  
 <xref:System.Windows.Forms.DataGrid> Denetim özel gereksinimleri ve geriye dönük uyumluluk için tutulur. Neredeyse tüm amaçlar için kullanmanız gereken <xref:System.Windows.Forms.DataGridView> denetim. Kullanılabilir tek özellik <xref:System.Windows.Forms.DataGrid> kullanılamaz denetim <xref:System.Windows.Forms.DataGridView> denetimidir tek bir denetim iki ilişkili tablolardan bilgilerinin hiyerarşik görüntüleme. İki kullanmalısınız <xref:System.Windows.Forms.DataGridView> bir ana öğe/ayrıntı ilişkisi olan iki tablo bilgilerini görüntülemek için kontrol eder.  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView denetimine yükseltme  
 Kullanan uygulamalarınız varsa <xref:System.Windows.Forms.DataGrid> denetim bir basit veri bağlama senaryoda özelleştirmeleri olmadan, yalnızca yeni denetimi ile eski denetiminin değiştirebilirsiniz. Standart Windows Forms veri bağlama mimari, hem denetimleri kullanın böylece <xref:System.Windows.Forms.DataGridView> denetim ek yapılandırma ile ilişkili verilerinizi görüntüler. Veri bağlama geliştirmeleri, ancak, verilerinizi bağlayarak yararlandığından düşünmek isteyebilirsiniz bir <xref:System.Windows.Forms.BindingSource> sonra bağlayabilirsiniz bileşen <xref:System.Windows.Forms.DataGridView> denetim. Daha fazla bilgi için bkz: [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Çünkü <xref:System.Windows.Forms.DataGridView> kontrolünde tamamen yeni bir mimari, kullanmanıza olanak sağlayan basit dönüştürme yol yok <xref:System.Windows.Forms.DataGrid> özelleştirmeleri ile <xref:System.Windows.Forms.DataGridView> denetim. Birçok <xref:System.Windows.Forms.DataGrid> özelleştirmeleri ile gereksiz <xref:System.Windows.Forms.DataGridView> , ancak yeni denetiminde kullanılabilen yerleşik özellikleri nedeniyle denetim. Özel sütun türleri için oluşturduysanız <xref:System.Windows.Forms.DataGrid> ile kullanmak istediğiniz denetim <xref:System.Windows.Forms.DataGridView> denetimi elde edersiniz bunları yeniden yeni mimarisi kullanarak uygulama. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Seçim Modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
