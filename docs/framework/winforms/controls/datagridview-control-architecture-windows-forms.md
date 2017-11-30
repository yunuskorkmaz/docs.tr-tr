---
title: DataGridView Denetimi Mimarisi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb44a32e63fd7a0ff0e480c205d5459da2ce2bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView Denetimi Mimarisi (Windows Forms)
<xref:System.Windows.Forms.DataGridView> Denetim ve ilişkili sınıfları görüntüleme ve tablo veri düzenlemek için esnek ve Genişletilebilir bir sistem olacak şekilde tasarlanmıştır. Bu sınıfların tüm bulunan <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ve tüm adlı "DataGridView" öneki.  
  
## <a name="architecture-elements"></a>Mimari öğeleri  
 Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları türetilen <xref:System.Windows.Forms.DataGridViewElement>. Aşağıdaki nesne modeli gösterilmektedir <xref:System.Windows.Forms.DataGridViewElement> Devralma Hiyerarşisi.  
  
 ![DataGridViewElement nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")  
DataGridViewElement nesne modeli  
  
 <xref:System.Windows.Forms.DataGridViewElement> Sınıfı, üst bir başvuru sağlar <xref:System.Windows.Forms.DataGridView> denetlemek ve sahip bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> değerlerinden bileşimini temsil eden bir değer tutan özelliği <xref:System.Windows.Forms.DataGridViewElementStates> numaralandırması.  
  
 Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> Yahoo! companion daha ayrıntılı sınıfları.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Bu numaralandırma değerlerinin Bitsel mantıksal işleçlerle birleştirilebilir böylece <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği express birden fazla durum aynı anda. Örneğin, bir <xref:System.Windows.Forms.DataGridViewElement> aynı anda olabilir <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Hücreleri ve bantları  
 <xref:System.Windows.Forms.DataGridView> Denetim nesneleri iki temel tür oluşur: hücreleri ve bantları. Tüm hücreleri türetin <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı. Bantlar, iki tür <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, her ikisi de öğesinden türetilen <xref:System.Windows.Forms.DataGridViewBand> temel sınıfı.  
  
 <xref:System.Windows.Forms.DataGridView> Denetim birkaç sınıfları ile birlikte çalışır, ancak en yaygın olarak karşılaşılan olan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, ve <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Hücre etkileşim için temel birimidir <xref:System.Windows.Forms.DataGridView>. Görüntü hücreleri ortalanır ve veri girişini genellikle hücreleri gerçekleştirilir. Hücreleri kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonu <xref:System.Windows.Forms.DataGridViewRow> sınıfı ve erişebilir seçili hücreleri kullanarak <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonu <xref:System.Windows.Forms.DataGridView> denetim. Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewCell> Devralma Hiyerarşisi.  
  
 ![DataGridViewCell nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
DataGridViewCell nesne modeli  
  
 <xref:System.Windows.Forms.DataGridViewCell> Türüdür kendisinden türetilen tüm hücre türleri Özet temel sınıf. <xref:System.Windows.Forms.DataGridViewCell>ve türetilmiş türlerini Windows Forms denetimleri, ancak bazı ana bilgisayar Windows Forms denetimleri olup olmadığı. Bir hücre tarafından desteklenen herhangi bir düzenleme işlevsellik genellikle barındırılan denetim tarafından işlenir.  
  
 <xref:System.Windows.Forms.DataGridViewCell>Windows Forms denetimleri gibi nesneleri kendi Görünüm ve boyama özellikleri aynı şekilde kontrol etmez. Bunun yerine, <xref:System.Windows.Forms.DataGridView> görünümünü için sorumlu kendi <xref:System.Windows.Forms.DataGridViewCell> nesneleri. İle etkileşim kurarak görünümünü ve davranışını hücrelerin önemli ölçüde etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimin özellikleri ve olayları. Özellikleri dışında olan özelleştirmeler için özel gereksinimleri olduğunda <xref:System.Windows.Forms.DataGridView> denetim, türetilen kendi sınıfı uygulayabilirsiniz <xref:System.Windows.Forms.DataGridViewCell> ya da alt sınıflarından biri.  
  
 Aşağıdaki liste öğesinden türetilmiş sınıfları gösterir <xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   Özel hücre türleri  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Şeması <xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposu olarak ifade edilir <xref:System.Windows.Forms.DataGridView> denetimin sütun. Erişebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin sütunları <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu. Seçili sütunları kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonu. Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewColumn> Devralma Hiyerarşisi.  
  
 ![DataGridViewColumn nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
DataGridViewColumn nesne modeli  
  
 Anahtar hücresi türlerinden bazıları karşılık gelen sütun türleri vardır. Bu türetilmiş <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfı.  
  
 Aşağıdaki liste öğesinden türetilmiş sınıfları gösterir <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Özel sütun türleri  
  
### <a name="datagridview-editing-controls"></a>DataGridView düzenleme denetimleri  
 Gelişmiş düzenleme işlevi genellikle destek hücreleri bir Windows Forms denetiminden türetilen barındırılan bir denetimi kullanın. Ayrıca bu denetimleri uygulayın <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi. Aşağıdaki nesne modeli bu denetimlerinin kullanımını göstermektedir.  
  
 ![DataGridView denetimi nesne modeli düzenleme](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
DataGridView düzenleme denetimi nesne modeli  
  
 Aşağıdaki düzenleme denetimleri ile sağlanan <xref:System.Windows.Forms.DataGridView> denetimi:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Kendi düzenleme denetimleri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView hücrelerinde ana bilgisayar denetimleri](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Aşağıdaki tabloda hücre türleri, sütun türleri ve düzenleme denetimleri arasındaki ilişkiyi gösterir.  
  
|Hücre türü|Barındırılan denetimi|Sütun türü|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|yok|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|yok|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|yok|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|yok|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Sınıfı görüntüler bir kaydın veri alanları verileri depolamak için <xref:System.Windows.Forms.DataGridView> denetim eklenmiş olmasıdır. Erişebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin satırları <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu. Seçili satırları kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonu. Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewRow> Devralma Hiyerarşisi.  
  
 ![DataGridViewRow nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
DataGridViewRow nesne modeli  
  
 Kendi türlerinden türetilemeyeceğini <xref:System.Windows.Forms.DataGridViewRow> bu genellikle gerekmeyecektir rağmen sınıf. <xref:System.Windows.Forms.DataGridView> Kontrolünde birkaç satır ile ilgili olayları ve özellikleri davranışını özelleştirmek için kendi <xref:System.Windows.Forms.DataGridViewRow> nesneleri.  
  
 Etkinleştirirseniz, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, yeni satır eklemek için özel bir satır son satır olarak görünür. Bu satır parçası olan <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu, ancak dikkat etmeniz gereken özel işlevselliği vardır. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
