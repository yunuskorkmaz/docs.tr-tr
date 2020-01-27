---
title: DataGridView ve DataGrid denetimleri arasındaki farklar
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745964"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
<xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Windows.Forms.DataGrid> denetiminin yerini alan yeni bir denetimdir. <xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Windows.Forms.DataGrid> denetiminde bulunmayan çok sayıda temel ve gelişmiş özellik sağlar. Ayrıca, <xref:System.Windows.Forms.DataGridView> denetiminin mimarisi, <xref:System.Windows.Forms.DataGrid> denetiminden genişletmenin ve özelleştirmeyi çok daha kolay hale getirir.  
  
 Aşağıdaki tabloda, <xref:System.Windows.Forms.DataGrid> denetiminde bulunmayan <xref:System.Windows.Forms.DataGridView> denetiminde bulunan birincil özelliklerden bazıları açıklanmaktadır.  
  
|DataGridView denetim özelliği|Açıklama|  
|----------------------------------|-----------------|  
|Birden çok sütun türü|<xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGrid> denetiminden daha fazla yerleşik sütun türü sağlar. Bu sütun türleri, en yaygın senaryoların ihtiyaçlarını karşılar, ancak <xref:System.Windows.Forms.DataGrid> denetimindeki sütun türlerine göre genişletmek veya değiştirmek de kolaydır. Daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki sütun türleri](column-types-in-the-windows-forms-datagridview-control.md).|  
|Verileri görüntülemenin birden çok yolu|<xref:System.Windows.Forms.DataGrid> denetimi bir dış veri kaynağından veri görüntülemek için sınırlıdır. Ancak <xref:System.Windows.Forms.DataGridView> denetim, denetimde depolanan ilişkisiz verileri, bağlı bir veri kaynağından gelen verileri veya bağlı ve ilişkisiz verileri birlikte gösterebilir. Ayrıca, özel veri yönetimi sağlamak için <xref:System.Windows.Forms.DataGridView> denetiminde sanal modu da uygulayabilirsiniz. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki veri görüntüleme modları](data-display-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.|  
|Verilerin görüntülenmesini özelleştirmenin birden çok yolu|<xref:System.Windows.Forms.DataGridView> denetimi, verilerin nasıl biçimlendirilip görüntülendiğini belirtmenize imkan tanıyan birçok özellik ve olay sağlar. Örneğin, hücrelerin, satırların ve sütunların görünümünü içerdikleri verilere göre değiştirebilir veya bir veri türünün verilerini başka bir türdeki eşdeğer verilerle değiştirebilirsiniz. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki veri biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)bölümüne bakın.|  
|Hücre, satır, sütun ve üst bilgi görünümünü ve davranışını değiştirmek için birden çok seçenek|<xref:System.Windows.Forms.DataGridView> denetimi, tek tek kılavuz bileşenleriyle çeşitli yollarla çalışmanıza olanak sağlar. Örneğin, kaymasını engellemek için satırları ve sütunları dondurabilirsiniz; satırları, sütunları ve başlıkları gizleyin; satır, sütun ve başlık boyutlarının ayarlandığı şekli değiştirin; Kullanıcıların seçimler yapma şeklini değiştirme; ve tek tek hücreler, satırlar ve sütunlar için araç Ipuçları ve kısayol menüleri sağlar.|  
  
 <xref:System.Windows.Forms.DataGrid> denetimi geriye dönük uyumluluk ve özel gereksinimler için korunur. Neredeyse tüm amaçlar için <xref:System.Windows.Forms.DataGridView> denetimini kullanmanız gerekir. <xref:System.Windows.Forms.DataGridView> denetiminde kullanılamayan <xref:System.Windows.Forms.DataGrid> denetiminde kullanılabilen tek özellik, tek bir denetimdeki iki ilişkili tablodaki bilgilerin hiyerarşik görüntülerdir. Ana/ayrıntı ilişkisindeki iki tablodaki bilgileri göstermek için iki <xref:System.Windows.Forms.DataGridView> denetimi kullanmanız gerekir.  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView denetimine yükseltme  
 Özelleştirmeler olmadan basit veriye dayalı bir senaryoda <xref:System.Windows.Forms.DataGrid> denetimini kullanan mevcut uygulamalarınız varsa, yalnızca eski denetimi yeni denetimle değiştirebilirsiniz. Her iki denetim de standart Windows Forms veri bağlama mimarisini kullanır, bu nedenle <xref:System.Windows.Forms.DataGridView> denetim, bağlantılı verilerinizi ek yapılandırma gerekmeden görüntüler. Veri bağlama geliştirmelerinden faydalanmak isteyebilirsiniz, ancak verilerinizi bir <xref:System.Windows.Forms.BindingSource> bileşenine bağlayarak, daha sonra <xref:System.Windows.Forms.DataGridView> denetimine bağlayabilirsiniz. Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> denetimi tamamen yeni bir mimariye sahip olduğundan, <xref:System.Windows.Forms.DataGrid> özelleştirmelerini <xref:System.Windows.Forms.DataGridView> denetimiyle kullanmanıza imkan tanıyan, doğrudan bir dönüştürme yolu yoktur. Ancak, yeni denetimde bulunan yerleşik özellikler nedeniyle, birçok <xref:System.Windows.Forms.DataGrid> özelleştirmesi <xref:System.Windows.Forms.DataGridView> denetimiyle gereksizdir. <xref:System.Windows.Forms.DataGridView> denetimiyle kullanmak istediğiniz <xref:System.Windows.Forms.DataGrid> denetimi için özel sütun türleri oluşturduysanız, yeni mimariyi kullanarak bunları yeniden uygulamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini özelleştirme](customizing-the-windows-forms-datagridview-control.md).  
  
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
