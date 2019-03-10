---
title: Windows Forms DataGridView Denetimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 1f9c68ae85d7bad2b8cdcdaa63c1e7b46f9568ed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703341"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Özelleştirme
`DataGridView` Denetim görünümünü ve temel davranışını (Görünüm) kendi hücreler, satırlar ve sütunlarla ayarlamak için kullanabileceğiniz çeşitli özellikler sağlar. Sunulan özelliklerin ötesine geçebilen özel gereksinimleri varsa <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ancak ayrıca sahip çizim denetimi için uygulayan veya özel bir hücre, sütunları ve satırları oluşturarak yeteneklerini genişletir.  
  
 Hücre ve satırları kendiniz boyamak için çeşitli işleyebilir `DataGridView` boyama olayları. Mevcut işlevselliğini değiştirmenize veya yeni işlevsellik sağlamak için mevcut türetilen kendi türlerinizi oluşturabilirsiniz `DataGridViewCell`, `DataGridViewColumn`, ve `DataGridViewRow` türleri. Bir hücre düzenleme modunda olduğunda, seçtiğiniz bir denetimi görüntüleme türetilmiş türleri oluşturarak yeni düzenleme özellikleri de sağlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellPainting> boyamak için olay hücreleri el ile.  
  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> satırlarla gradyan, özel bir arka plan boyama ve içerik için olayları yayılan birden çok sütun.  
  
 [Nasıl yapılır: Davranış ve görünümünü genişleterek hücre ve sütunları Windows Forms DataGridView denetiminde özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Öğesinden türetilen özel türler oluşturmayı açıklar `DataGridViewCell` ve `DataGridViewColumn` için fare işaretçisi üzerinde getirildiğinde hücreleri vurgulayın.  
  
 [Nasıl yapılır: Windows Forms DataGridView denetimindeki bir düğme sütununda düğmeleri devre dışı bırak](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Öğesinden türetilen özel türler oluşturmayı açıklar <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> bir düğme sütununda düğmeleri devre dışı görüntülemek için.  
  
 [Nasıl yapılır: Windows Forms DataGridView hücrelerinde konak denetimleri](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Nasıl uygulanacağını açıklar `IDataGridViewEditingControl` arabirim ve türetilen özel türler oluşturma `DataGridViewCell` ve `DataGridViewColumn` görüntülemek için bir <xref:System.Windows.Forms.DateTimePicker> bir hücre düzenleme modunda olduğunda denetim.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Denetiminin temel görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
