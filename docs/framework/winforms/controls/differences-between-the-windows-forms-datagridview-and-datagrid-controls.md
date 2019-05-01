---
title: Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 6802ef375d8d15826725e68f5065317192523178
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972217"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
<xref:System.Windows.Forms.DataGridView> Denetimidir yerini alan yeni bir denetim <xref:System.Windows.Forms.DataGrid> denetimi. <xref:System.Windows.Forms.DataGridView> Denetim eksik olan çok sayıda temel ve gelişmiş özellikler sağlar <xref:System.Windows.Forms.DataGrid> denetimi. Ayrıca, mimarisi <xref:System.Windows.Forms.DataGridView> denetimi yapar, genişletmek ve daha özelleştirmek çok daha kolay <xref:System.Windows.Forms.DataGrid> denetimi.  
  
 Aşağıdaki tabloda bulunan birincil özellikleri birkaçını açıklanmaktadır <xref:System.Windows.Forms.DataGridView> eksik denetim <xref:System.Windows.Forms.DataGrid> denetimi.  
  
|DataGridView denetimi özelliği|Açıklama|  
|----------------------------------|-----------------|  
|Birden çok sütun türleri|<xref:System.Windows.Forms.DataGridView> Denetim sağlayan daha fazla yerleşik sütun türleri <xref:System.Windows.Forms.DataGrid> denetimi. Bu sütun türleri en sık karşılaşılan senaryolardan ihtiyaçlarını, ancak ayrıca genişletmek veya sütun türlerinde daha kolay <xref:System.Windows.Forms.DataGrid> denetimi. Daha fazla bilgi için [Windows Forms DataGridView denetiminde sütun türleri](column-types-in-the-windows-forms-datagridview-control.md).|  
|Verileri görüntülemek için birden çok yol|<xref:System.Windows.Forms.DataGrid> Denetimidir sınırlı bir dış veri kaynağından verileri görüntülemek için. <xref:System.Windows.Forms.DataGridView> Denetimi, Bununla birlikte, Denetim, bağlı veri kaynağı veya ilişkili ve ilişkisiz verileri birlikte depolanan ilişkisiz veri görüntüler. Sanal modda da uygulayabilirsiniz <xref:System.Windows.Forms.DataGridView> denetimi özel veri yönetimi sağlayın. Daha fazla bilgi için [Windows Forms DataGridView denetiminde veri görüntüleme modları](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Veri görüntüsünü özelleştirmek için birden çok yol|<xref:System.Windows.Forms.DataGridView> Birçok özellik ve verilerin nasıl biçimlendirilmiş ve görüntülenen belirtmenize olanak verir olayları denetim sağlar. Örneğin, hücreler, satırlar ve sütunlar içerdikleri verilere bağlı olarak görünümünü değiştirebilirsiniz ya da bir veri türünde başka bir tür eşdeğeri veri ile değiştirin. Daha fazla bilgi için [Windows Forms DataGridView denetiminde veri biçimlendirmeyi](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Hücre, satır, sütun ve üst bilgi görünümünü ve davranışını değiştirmek için birden fazla seçenek|<xref:System.Windows.Forms.DataGridView> Denetim çeşitli şekillerde bireysel kılavuz bileşenleri ile çalışmanıza olanak sağlar. Örneğin, satır ve sütun kaymasını engellemek için dondurma; Satırlar, sütunlar ve üst bilgileri Gizle; Satır ve sütun üst bilgisi boyutları ayarlanmış şeklini değiştirmek; Kullanıcıların seçim biçimini değiştirmek; ve tek hücre, satır ve sütunları için araç ipuçları ve kısayol menüleri sağlar.|  
  
 <xref:System.Windows.Forms.DataGrid> Denetimi özel gereksinimleri ve geriye dönük uyumluluk için tutuluyor. Neredeyse tüm amaçlar için kullanmanız gereken <xref:System.Windows.Forms.DataGridView> denetimi. Kullanılabilir tek özellik <xref:System.Windows.Forms.DataGrid> kullanılamaz denetim <xref:System.Windows.Forms.DataGridView> bilgilerin tek bir denetimde ilgili iki tablodan hiyerarşik görüntü denetimidir. İki kullanmalısınız <xref:System.Windows.Forms.DataGridView> içinde bir ana/ayrıntı ilişkisi olan iki tablodaki bilgileri görüntülemek için denetimler.  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView denetimine yükseltme  
 Kullanan mevcut uygulamalarınız varsa <xref:System.Windows.Forms.DataGrid> denetimi bir basit veri bağlama senaryoda özelleştirme olmadan, yalnızca yeni denetimi ile eski denetimi değiştirebilirsiniz. Her iki denetim standart Windows Forms veri bağlama mimarisi kullanan böylece <xref:System.Windows.Forms.DataGridView> denetim gereken ek yapılandırma ile ilişkili verilerinizi görüntülenir. Ancak, veri bağlama geliştirmelerin sağladığı avantajlardan yararlanarak verilerinizi bağlayarak dikkate isteyebileceğiniz bir <xref:System.Windows.Forms.BindingSource> ardından adlarınıza bağlayabileceğiniz bileşeni <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [BindingSource bileşeni](bindingsource-component.md).  
  
 Çünkü <xref:System.Windows.Forms.DataGridView> kontrolünde yepyeni bir mimari, kullanmanızı sağlayacak basit dönüştürme yolu yoktur <xref:System.Windows.Forms.DataGrid> özelleştirmelerle <xref:System.Windows.Forms.DataGridView> denetimi. Birçok <xref:System.Windows.Forms.DataGrid> özelleştirmeler ile gereksiz <xref:System.Windows.Forms.DataGridView> ancak, yeni denetimde bulunan yerleşik özellikler nedeniyle denetimi. Özel sütun türleri için oluşturduysanız <xref:System.Windows.Forms.DataGrid> ile kullanmak istediğiniz denetim <xref:System.Windows.Forms.DataGridView> denetimi, bunları yeniden yeni mimarisini kullanarak uygulama gerekir. Daha fazla bilgi için [Windows Forms DataGridView denetimini özelleştirme](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [BindingSource Bileşeni](bindingsource-component.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
