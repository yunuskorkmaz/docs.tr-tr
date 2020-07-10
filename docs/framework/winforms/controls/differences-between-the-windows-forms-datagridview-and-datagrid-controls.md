---
title: DataGridView ve DataGrid denetimleri arasındaki farklar
description: Windows Forms DataGridView ve DataGrid denetimleri özelliklerinin yanı sıra mimarisindeki farklılıklar arasındaki çeşitli farklılıkları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174594"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar
<xref:System.Windows.Forms.DataGridView>Denetim, denetimin yerini alan yeni bir denetimdir <xref:System.Windows.Forms.DataGrid> . <xref:System.Windows.Forms.DataGridView>Denetim, denetimde bulunmayan çok sayıda temel ve gelişmiş özellik sağlar <xref:System.Windows.Forms.DataGrid> . Ayrıca, denetimin mimarisi, <xref:System.Windows.Forms.DataGridView> denetime göre genişletmeyi ve özelleştirmeyi çok daha kolay hale getirir <xref:System.Windows.Forms.DataGrid> .  
  
 Aşağıdaki tabloda denetimde bulunmayan denetimdeki bazı birincil özellikler açıklanmaktadır <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGrid> .  
  
|DataGridView denetim özelliği|Açıklama|  
|----------------------------------|-----------------|  
|Birden çok sütun türü|<xref:System.Windows.Forms.DataGridView>Denetim, denetimden daha fazla yerleşik sütun türü sağlar <xref:System.Windows.Forms.DataGrid> . Bu sütun türleri, en yaygın senaryoların ihtiyaçlarını karşılar, ancak aynı zamanda denetimdeki sütun türlerinden daha kolay bir şekilde genişletilir veya değiştirilebilir <xref:System.Windows.Forms.DataGrid> . Daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki sütun türleri](column-types-in-the-windows-forms-datagridview-control.md).|  
|Verileri görüntülemenin birden çok yolu|<xref:System.Windows.Forms.DataGrid>Denetim, dış bir veri kaynağından verileri görüntüleyecek şekilde sınırlandırılmıştır. <xref:System.Windows.Forms.DataGridView>Ancak denetim, denetimde depolanan ilişkisiz verileri, bağlı bir veri kaynağından gelen verileri veya bağlı ve ilişkisiz verileri birlikte gösterebilir. Ayrıca, <xref:System.Windows.Forms.DataGridView> özel veri yönetimi sağlamak için denetimde sanal modu da uygulayabilirsiniz. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki veri görüntüleme modları](data-display-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.|  
|Verilerin görüntülenmesini özelleştirmenin birden çok yolu|<xref:System.Windows.Forms.DataGridView>Denetim, verilerin nasıl biçimlendirilip görüntülendiğini belirtmenize imkan tanıyan birçok özellik ve olay sağlar. Örneğin, hücrelerin, satırların ve sütunların görünümünü içerdikleri verilere göre değiştirebilir veya bir veri türünün verilerini başka bir türdeki eşdeğer verilerle değiştirebilirsiniz. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki veri biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)bölümüne bakın.|  
|Hücre, satır, sütun ve üst bilgi görünümünü ve davranışını değiştirmek için birden çok seçenek|<xref:System.Windows.Forms.DataGridView>Denetim, tek tek kılavuz bileşenleriyle çeşitli yollarla çalışmanıza olanak sağlar. Örneğin, kaymasını engellemek için satırları ve sütunları dondurabilirsiniz; satırları, sütunları ve başlıkları gizleyin; satır, sütun ve başlık boyutlarının ayarlandığı şekli değiştirin; Kullanıcıların seçimler yapma şeklini değiştirme; ve tek tek hücreler, satırlar ve sütunlar için araç Ipuçları ve kısayol menüleri sağlar.|  
  
 <xref:System.Windows.Forms.DataGrid>Denetim, geriye dönük uyumluluk ve özel gereksinimler için korunur. Neredeyse tüm amaçlar için, denetimi kullanmanız gerekir <xref:System.Windows.Forms.DataGridView> . Denetimde kullanılamayan tek özellik, <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> tek bir denetimdeki iki ilişkili tablodaki bilgilerin hiyerarşik görüntülerdir. <xref:System.Windows.Forms.DataGridView>Ana/ayrıntı ilişkisindeki iki tablodaki bilgileri göstermek için iki denetim kullanmanız gerekir.  
  
## <a name="upgrading-to-the-datagridview-control"></a>DataGridView denetimine yükseltme  
 <xref:System.Windows.Forms.DataGrid>Özelleştirme olmadan basit veriye dayalı bir senaryoda denetimi kullanan mevcut uygulamalarınız varsa, eski denetimi yeni denetimle değiştirebilirsiniz. Her iki denetim de standart Windows Forms veri bağlama mimarisini kullanır, bu nedenle <xref:System.Windows.Forms.DataGridView> Denetim, bağlantılı verilerinizi ek yapılandırma gerekmeden görüntüler. Ancak, verilerinizi bir bileşene bağlayarak, <xref:System.Windows.Forms.BindingSource> daha sonra denetime bağlayabileceğiniz veri bağlama geliştirmelerinden faydalanmak isteyebilirsiniz <xref:System.Windows.Forms.DataGridView> . Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView>Denetimde tamamen yeni bir mimari olduğundan, <xref:System.Windows.Forms.DataGrid> Denetim ile özelleştirmeler kullanmanıza imkan tanıyan basit bir dönüştürme yolu yoktur <xref:System.Windows.Forms.DataGridView> . <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> Ancak, yeni denetimde bulunan yerleşik özellikler nedeniyle, denetimde birçok özelleştirme gereksizdir. Denetimle birlikte kullanmak istediğiniz denetim için özel sütun türleri oluşturduysanız <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> , bunları yeni mimariyi kullanarak yeniden uygulamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini özelleştirme](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView denetimi](datagridview-control-windows-forms.md)
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
