---
title: "DataGridView Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4209866f63931fb3d80f35e211bd5f9b35ed48bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView Denetimine Genel Bakış (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi görüntülemek ve birçok farklı türde veri kaynaklarını tablo verileri düzenleyin.  
  
 Veri bağlama <xref:System.Windows.Forms.DataGridView> denetimidir basit ve sezgisel ve çoğu durumda ayarı olarak kadar basit hale <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği. Birden çok listeleri veya tablo içeren bir veri kaynağına bağlama ayarlanmadığında <xref:System.Windows.Forms.DataGridView.DataMember%2A> liste veya bağlamak için tabloyu belirten bir dize özelliği.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi, aşağıdaki listede açıklanan sınıfların örnekleri bağlamak için standart Windows Forms veri bağlama modelini destekler:  
  
-   Uygulayan herhangi bir sınıf <xref:System.Collections.IList> tek boyutlu diziler dahil olmak üzere arabirimi.  
  
-   Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IListSource> gibi arabirim <xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları.  
  
-   Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingList> gibi arabirim <xref:System.ComponentModel.BindingList%601> sınıfı.  
  
-   Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingListView> gibi arabirim <xref:System.Windows.Forms.BindingSource> sınıfı.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi veri bağlamasını bu arabirimleri tarafından döndürülen nesne genel özelliklerine veya tarafından döndürülen özellikleri koleksiyonuna destekler bir <xref:System.ComponentModel.ICustomTypeDescriptor> , döndürülen nesnelerin uygulanırsa, arabirim.  
  
 Genellikle, bağlayacaksınız bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bağ <xref:System.Windows.Forms.BindingSource> başka bir bileşen veri kaynağı veya iş nesneleri ile doldurur. <xref:System.Windows.Forms.BindingSource> Bileşeni olduğundan tercih edilen veri kaynağı çok çeşitli veri kaynaklarına bağlayabilirsiniz ve birçok veri bağlama sorunları otomatik olarak çözebilirsiniz. Daha fazla bilgi için bkz: [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi de kullanılabilir *ilişkisiz* moduyla alttaki hiç veri deposu. İlişkisiz bir kullanan bir kod örneği için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetimidir yüksek oranda yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve görünümünü ve davranışını özelleştirmek için olayları sağlar. Tablo verileri görüntülemek için Windows Forms uygulaması istediğinizde kullanmayı <xref:System.Windows.Forms.DataGridView> diğerlerinden önce denetim (örneğin, <xref:System.Windows.Forms.DataGrid>). Salt okunur değerlerini oluşan küçük bir kılavuz görüntülüyorsanız veya kayıtları, milyonlarca içeren bir tablo düzenlemek bir kullanıcı etkinleştiriyorsanız <xref:System.Windows.Forms.DataGridView> denetimi, bir yedeğe programlanabilir, bellek verimli çözümüyle sağlayacaktır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView denetimi teknoloji özeti](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Özetler <xref:System.Windows.Forms.DataGridView> kavramları ve ilgili sınıfların kullanımını denetleme.  
  
 [DataGridView denetimi mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Mimarisini açıklar <xref:System.Windows.Forms.DataGridView> türü hiyerarşi ve devralma yapısını açıklayan denetim.  
  
 [DataGridView denetimi senaryoları](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 En yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> denetimleri kullanılır.  
  
 [DataGridView denetimi kod dizini](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Kod örneklerinde çeşitli belgelerine ait bağlantılar sağlanmıştır <xref:System.Windows.Forms.DataGridView> görevler. Bu örnekler görev türü tarafından ayrılır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Windows Forms'ta sütun türleri açıklanmaktadır <xref:System.Windows.Forms.DataGridView> denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcılara izin vermek için kullanılır.  
  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 El ile veya bir dış veri kaynağından veri denetimiyle doldurmak nasıl açıklayan konulara sağlar.  
  
 [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama açıklayan konulara sağlar <xref:System.Windows.Forms.DataGridView> hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.  
  
 [Performans ayarlama Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konulara sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView denetimi](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Varsayılan işlevsellik Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Varsayılan klavye ve fare Windows Forms DataGridView denetiminde işleme](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
