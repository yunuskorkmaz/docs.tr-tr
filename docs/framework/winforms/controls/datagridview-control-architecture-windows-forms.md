---
title: DataGridView Denetimi Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742532"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView Denetimi Mimarisi (Windows Forms)
<xref:System.Windows.Forms.DataGridView> denetimi ve ilgili sınıfları tablo verilerini görüntülemek ve görüntülemek için esnek, genişletilebilir bir sistem olacak şekilde tasarlanmıştır. Bu sınıfların hepsi <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanında yer alır ve hepsi "DataGridView" ön ekiyle adlandırılmaktadır.  
  
## <a name="architecture-elements"></a>Mimari öğeleri  
 Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları <xref:System.Windows.Forms.DataGridViewElement>türetilir. Aşağıdaki nesne modelinde <xref:System.Windows.Forms.DataGridViewElement> devralma hiyerarşisi gösterilmektedir.  
  
 ![DataGridViewElement nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement> sınıfı üst <xref:System.Windows.Forms.DataGridView> denetimine bir başvuru sağlar ve <xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırmadaki değerlerin birleşimini temsil eden bir değer tutan bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliğine sahiptir.  
  
 Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları daha ayrıntılı olarak açıklanır.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Bu sabit listesinin değerleri bit düzeyinde mantıksal işleçlerle birleştirilebilir, bu nedenle <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği bir seferde birden fazla durum ifade edebilir. Örneğin, <xref:System.Windows.Forms.DataGridViewElement> aynı anda <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>olabilir.  
  
### <a name="cells-and-bands"></a>Hücreler ve şeritler  
 <xref:System.Windows.Forms.DataGridView> denetimi iki temel nesne türünü kapsar: hücreler ve bantlar. Tüm hücreler <xref:System.Windows.Forms.DataGridViewCell> temel sınıfından türetilir. İki tür bant, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, her ikisi de <xref:System.Windows.Forms.DataGridViewBand> temel sınıfından türetilir.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi çeşitli sınıflarla birlikte çalışır, ancak en sık karşılaşılan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>ve <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Hücre, <xref:System.Windows.Forms.DataGridView>için temel etkileşim birimidir. Görüntü hücrelerde ortalanır ve veri girişi genellikle hücreler aracılığıyla gerçekleştirilir. <xref:System.Windows.Forms.DataGridViewRow> sınıfının <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonunu kullanarak hücrelere erişebilirsiniz ve <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonunu kullanarak seçili hücrelere erişebilirsiniz. Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewCell> devralma hiyerarşisi gösterilmektedir.  
  
 ![DataGridViewCell nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell> türü, tüm hücre türlerinin türeten bir soyut temel sınıftır. <xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş türleri Windows Forms denetimler değildir ancak bazı konak Windows Forms denetimleri. Bir hücre tarafından desteklenen tüm Düzenle işlevleri genellikle barındırılan bir denetim tarafından işlenir.  
  
 <xref:System.Windows.Forms.DataGridViewCell> nesneler, Windows Forms denetimleriyle aynı şekilde kendi görünüm ve boyama özelliklerini denetlemez. Bunun yerine, <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCell> nesnelerinin görünüşünün sorumluluğundadır. <xref:System.Windows.Forms.DataGridView> denetiminin özellikleri ve olayları ile etkileşime girerek hücrelerin görünümünü ve davranışını önemli ölçüde etkileyebilirsiniz. <xref:System.Windows.Forms.DataGridView> denetiminin özelliklerinden daha fazla olan özelleştirmeler için özel gereksinimleriniz varsa, <xref:System.Windows.Forms.DataGridViewCell> veya alt sınıflarından türeyen kendi sınıfınızı uygulayabilirsiniz.  
  
 Aşağıdaki listede <xref:System.Windows.Forms.DataGridViewCell>türetilen sınıflar gösterilmektedir:  
  
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
  
- Özel hücre türlerinizin  
  
### <a name="datagridviewcolumn"></a>'In  
 <xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposunun şeması, <xref:System.Windows.Forms.DataGridView> denetimin sütunlarında ifade edilir. <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonunu kullanarak <xref:System.Windows.Forms.DataGridView> denetiminin sütunlarına erişebilirsiniz. Seçilen sütunlara <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonunu kullanarak erişebilirsiniz. Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewColumn> devralma hiyerarşisi gösterilmektedir.  
  
 ![DataGridViewColumn nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Bazı anahtar hücresi türleri karşılık gelen sütun türlerine sahiptir. Bunlar <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfından türetilir.  
  
 Aşağıdaki listede <xref:System.Windows.Forms.DataGridViewColumn>türetilen sınıflar gösterilmektedir:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Özel sütun türleriniz  
  
### <a name="datagridview-editing-controls"></a>DataGridView Editing denetimleri  
 Gelişmiş Düzenle işlevini destekleyen hücreler genellikle Windows Forms denetiminden türetilen bir barındırılan denetim kullanır. Bu denetimler <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimini de uygular. Aşağıdaki nesne modelinde bu denetimlerin kullanımı gösterilmektedir.  
  
 ![DataGridView Editing Control nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Aşağıdaki düzen denetimleri <xref:System.Windows.Forms.DataGridView> denetimiyle birlikte sağlanır:  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Kendi düzen denetimlerinizi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri barındırma](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Aşağıdaki tabloda, hücre türleri, sütun türleri ve düzen denetimleri arasındaki ilişki gösterilmektedir.  
  
|Hücre türü|Barındırılan denetim|Sütun türü|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|yok|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|yok|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|yok|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|yok|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>'A  
 <xref:System.Windows.Forms.DataGridViewRow> sınıfı, <xref:System.Windows.Forms.DataGridView> denetiminin eklendiği veri deposundaki bir kaydın veri alanlarını görüntüler. <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunu kullanarak <xref:System.Windows.Forms.DataGridView> denetiminin satırlarına erişebilirsiniz. Seçili satırlara <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonunu kullanarak erişebilirsiniz. Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewRow> devralma hiyerarşisi gösterilmektedir.  
  
 ![DataGridViewRow nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <xref:System.Windows.Forms.DataGridViewRow> sınıfından kendi türlerinizi türetebilirsiniz, ancak bu genellikle gerekli olmayacaktır. <xref:System.Windows.Forms.DataGridView> denetiminde, <xref:System.Windows.Forms.DataGridViewRow> nesnelerinin davranışını özelleştirmeye yönelik birkaç satırla ilgili olay ve özellik bulunur.  
  
 <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliğini etkinleştirirseniz, son satır olarak yeni satır eklemek için özel bir satır görüntülenir. Bu satır <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunun bir parçasıdır, ancak ilgilenmeniz gereken özel işlevlere sahiptir. Daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki yeni kayıtlar Için satırı kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
