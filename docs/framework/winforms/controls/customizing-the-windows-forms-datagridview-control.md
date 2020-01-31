---
title: DataGridView denetimini özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744029"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimini Özelleştirme
`DataGridView` denetimi, hücrelerinin, satırlarının ve sütunlarının görünümünü ve temel davranışını (görünüm) ayarlamak için kullanabileceğiniz çeşitli özellikler sağlar. Ancak, <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının yeteneklerini aşmaya yönelik özel gereksinimleriniz varsa, denetimin sahip çizimini de uygulayabilir veya özel hücreler, sütunlar ve satırlar oluşturarak yeteneklerini genişletebilirsiniz.  
  
 Hücreleri ve satırları kendiniz boyamak için çeşitli `DataGridView` boyama olaylarını işleyebilirsiniz. Mevcut işlevleri değiştirmek veya yeni işlevsellik sağlamak için, mevcut `DataGridViewCell`, `DataGridViewColumn`ve `DataGridViewRow` türlerinden türetilmiş kendi türlerinizi oluşturabilirsiniz. Ayrıca, bir hücre düzenleme modundayken seçtiğiniz bir denetimi görüntüleyen türetilmiş türler oluşturarak yeni düzenleme olanakları sağlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Hücreleri el ile boyamak için <xref:System.Windows.Forms.DataGridView.CellPainting> olayının nasıl işleneceğini açıklar.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Özel, gradyan arka planı ve birden çok sütuna yayılan içerikle satırları boyamak için <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> olaylarının nasıl işleneceğini açıklar.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Fare işaretçisi üzerinde bekletildiğinde hücreleri vurgulamak için `DataGridViewCell` ve `DataGridViewColumn` türetilmiş özel türlerin nasıl oluşturulduğunu açıklar.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Düğme sütununda devre dışı bırakılan düğmeleri göstermek için <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> türetilmiş özel türlerin nasıl oluşturulduğunu açıklar.  
  
 [Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 `IDataGridViewEditingControl` arabirimini nasıl uygulayacağınızı ve bir hücre düzenleme modundayken bir <xref:System.Windows.Forms.DateTimePicker> denetimini göstermek için `DataGridViewCell` ve `DataGridViewColumn` türetilmiş özel türler oluşturmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell> sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow> sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn> sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi için başvuru belgeleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Denetimin temel görünümünün ve hücre verilerinin görüntüleme biçimlendirmesinin nasıl değiştirileceğini betimleyen konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimi](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
