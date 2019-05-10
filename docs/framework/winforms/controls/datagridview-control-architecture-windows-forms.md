---
title: DataGridView Denetimi Mimarisi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 15d10ed2ec0bc78acfe887fe583d4850425eeab9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648103"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView Denetimi Mimarisi (Windows Forms)
<xref:System.Windows.Forms.DataGridView> Denetimi ve ilişkili sınıflarının görüntüleme ve düzenleme sekmeli veri için esnek, Genişletilebilir bir sistem için tasarlanmıştır. Bu sınıfların tümü bulunur <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ve tüm adlandırılmış "DataGridView" ön ekine sahip.  
  
## <a name="architecture-elements"></a>Mimari öğeler  
 Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıflar türetilen <xref:System.Windows.Forms.DataGridViewElement>. Aşağıdaki nesne modelini göstermektedir <xref:System.Windows.Forms.DataGridViewElement> Devralma Hiyerarşisi.  
  
 ![DataGridViewElement nesne modeli hiyerarşisi gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement> Sınıfı üst öğeye bir başvuru sağlar <xref:System.Windows.Forms.DataGridView> denetlemek ve sahip bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> değerlerinden bir birleşimini gösteren bir değer tutuyor özelliği <xref:System.Windows.Forms.DataGridViewElementStates> sabit listesi.  
  
 Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> Yahoo! companion daha ayrıntılı sınıfları.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Bu numaralandırma değerlerinin bit düzeyinde mantıksal işleçler ile birleştirilebilir böylece <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği express birden fazla durum tek seferde. Örneğin, bir <xref:System.Windows.Forms.DataGridViewElement> aynı anda olabilir <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Hücreleri ve bantları  
 <xref:System.Windows.Forms.DataGridView> Denetimi içeren iki temel nesne türleri: hücreleri ve bantları. Tüm hücrelerini türetir <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı. Bant, iki tür <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, hem türetilen <xref:System.Windows.Forms.DataGridViewBand> temel sınıfı.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi birkaç sınıflarla birlikte çalışır, ancak en sık karşılaşılan olan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, ve <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Hücre etkileşimi için temel birimdir <xref:System.Windows.Forms.DataGridView>. Görüntü hücreleri ortalanır ve veri girişini çoğunlukla hücreleri gerçekleştirilir. Hücreleri kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonunu <xref:System.Windows.Forms.DataGridViewRow> sınıfı ve seçili hücreleri kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonunu <xref:System.Windows.Forms.DataGridView> denetimi. Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewCell> Devralma Hiyerarşisi.  
  
 ![DataGridViewCell nesne modeli hiyerarşisi gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell> Tüm hücre türleri türettiğiniz soyut temel sınıf türüdür. <xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş türlerini Windows Forms denetimleri, ancak bazı ana bilgisayar Windows Forms denetimleri değildir. Bir hücreyi tarafından desteklenen herhangi bir düzenleme işlevi genellikle barındırılan bir denetim tarafından işlenir.  
  
 <xref:System.Windows.Forms.DataGridViewCell> Windows Forms denetimleri gibi nesneleri kendi Görünüm ve bir boyama özellikleri aynı şekilde kontrol. Bunun yerine, <xref:System.Windows.Forms.DataGridView> görünümünü için sorumlu kendi <xref:System.Windows.Forms.DataGridViewCell> nesneleri. İle etkileşim kurarak görünümünü ve davranışını hücre önemli ölçüde etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimin özellikleri ve olayları. Sunulan özelliklerin ötesine olan özelleştirmeleri özel gereksinimleriniz varsa <xref:System.Windows.Forms.DataGridView> denetimi, türetilen kendi sınıfınızı uygulayabilirsiniz <xref:System.Windows.Forms.DataGridViewCell> veya onun alt sınıflarından birini.  
  
 Aşağıdaki liste öğelerinden türetilen sınıfları gösterir <xref:System.Windows.Forms.DataGridViewCell>:  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- Özel hücre türlerinizi  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Şemasını <xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposu olarak ifade edilir <xref:System.Windows.Forms.DataGridView> denetimin sütunları. Erişebildiğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin sütunları <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu. Seçili sütunları kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonu. Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewColumn> Devralma Hiyerarşisi.  
  
 ![DataGridViewColumn nesne modeli hiyerarşisi gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Bazı anahtar hücresi türlerine karşılık gelen sütun türleri vardır. Bu türetilmiş <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfı.  
  
 Aşağıdaki liste öğelerinden türetilen sınıfları gösterir <xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Özel sütun türleri  
  
### <a name="datagridview-editing-controls"></a>DataGridView denetimi düzenleme  
 Gelişmiş düzenleme işlevi genellikle destekleyen hücreleri bir Windows Forms denetiminden türetilen bir denetimden kullanın. Bu denetimler Ayrıca uygulama <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi. Aşağıdaki nesne modeli, bu denetimleri kullanımını gösterir.  
  
 ![DataGridView düzenleme denetimi nesne modeli hiyerarşisi gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Aşağıdaki düzenleme denetimleri ile sağlanan <xref:System.Windows.Forms.DataGridView> denetimi:  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Kendi düzenleme denetimler oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Aşağıdaki tabloda, düzenleme denetimleri hücre türleri ve sütun türleri arasındaki ilişkiyi gösterir.  
  
|Hücresi türü|Barındırılan denetim|Sütun türü|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|yok|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|yok|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|yok|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|yok|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Sınıfı görüntüler bir kaydın veri alanları verileri depolamak istediğiniz <xref:System.Windows.Forms.DataGridView> denetimi eklenir. Erişebildiğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetiminin satırları <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu. Seçili satırları kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonu. Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewRow> Devralma Hiyerarşisi.  
  
 ![DataGridViewRow nesne modeli hiyerarşisi gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Kendi türlerinden türetebilirsiniz <xref:System.Windows.Forms.DataGridViewRow> sınıfı, ancak bu genellikle gerekli olmaz. <xref:System.Windows.Forms.DataGridView> Denetim sahip birkaç satır ile ilgili olayları ve özelliklerini davranışını özelleştirmek için kendi <xref:System.Windows.Forms.DataGridViewRow> nesneleri.  
  
 Etkinleştirirseniz <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, yeni satır eklemek için özel bir satır son satırı görünür. Bu satırı parçasıdır <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu, ancak ilgilenmenizi gerektiren özel işlevler sahiptir. Daha fazla bilgi için [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
