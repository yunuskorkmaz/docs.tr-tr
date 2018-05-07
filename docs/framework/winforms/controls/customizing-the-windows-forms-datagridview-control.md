---
title: Windows Forms DataGridView Denetimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 92bbace4d0869aca67025f1e4ac8c451fe073219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Özelleştirme
`DataGridView` Denetim görünüm ve temel davranışını (Görünüm) hücrelerini, satırları ve sütunları ayarlamak için kullanabileceğiniz çeşitli özellikler sunar. Yeteneklerini gidin özel gereksinimleri olup olmadığını <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ancak denetim için çizim sahibi uygulamak ya da özel hücreler, sütunları ve satırları oluşturarak yeteneklerini genişletir.  
  
 Hücre ve satırları kendiniz boyamak için çeşitli işleyebilir `DataGridView` boyama olaylar. Varolan işlevlerini değiştirin veya yeni işlevsellik sağlamak için mevcut türetilmiş kendi türlerinizi oluşturabilirsiniz `DataGridViewCell`, `DataGridViewColumn`, ve `DataGridViewRow` türleri. Bir hücre düzenleme modunda olduğunda seçtiğiniz bir denetimi görüntüleme türetilmiş türler oluşturarak yeni düzenleme yetenekleri de sağlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellPainting> boyamak için olay hücreleri el ile.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> satırları gradyan, özel bir arka plan boyama ve içerik için olayları yayılan birden çok sütun.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Türetilen özel türlerinin nasıl oluşturulacağı açıklanır `DataGridViewCell` ve `DataGridViewColumn` fare işaretçisi üzerlerinde getirildiğinde hücreleri vurgulamak için.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Türetilen özel türlerinin nasıl oluşturulacağı açıklanır <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> bir düğme sütununda düğmeleri devre dışı görüntülemek için.  
  
 [Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Nasıl uygulandığı açıklanır `IDataGridViewEditingControl` arabirim ve türetilen özel türler oluşturma `DataGridViewCell` ve `DataGridViewColumn` görüntülemek için bir <xref:System.Windows.Forms.DateTimePicker> bir hücre düzenleme modunda olduğunda denetim.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGridView Denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
