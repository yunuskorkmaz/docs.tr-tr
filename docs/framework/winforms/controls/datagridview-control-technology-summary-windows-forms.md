---
title: DataGridView Denetimi Teknoloji Özeti
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742482"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView Denetimi Teknoloji Özeti (Windows Forms)
Bu konu, `DataGridView` denetimi ve kullanımını destekleyen sınıflar hakkındaki bilgileri özetler.  
  
 Verileri tablosal biçimde görüntülemek, sıkça gerçekleştirdiğiniz bir görevdir. `DataGridView` denetim, verileri bir kılavuzda sunmaya yönelik tamamen bir çözüm olacak şekilde tasarlanmıştır.  
  
## <a name="keywords"></a>Anahtar Sözcükler  
 DataGridView, BindingSource, Table, Cell, veri bağlama, sanal mod  
  
## <a name="namespaces"></a>{1&gt;Ad alanları&lt;1}  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>İlgili Teknolojiler  
 `BindingSource`  
  
## <a name="background"></a>Arka Plan  
 Kullanıcı arabirimi (UI) tasarımcıları genellikle tablo verilerini kullanıcılara göstermek için gerekli olan verileri bulur. .NET Framework, verileri bir tablo veya kılavuzda göstermek için çeşitli yollar sağlar. `DataGridView` denetim, bu teknolojinin Windows Forms uygulamalar için en son evini temsil eder.  
  
 `DataGridView` denetimi bir veri deposundan veri satırlarını görüntüleyebilir. Birçok veri deposu türü desteklenir. Veri deposu, tek boyutlu bir dizi gibi basit, türsüz verileri tutabilir veya <xref:System.Data.DataSet>gibi yazılmış verileri tutabilir. Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Forms DataGridView denetimine bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` denetim, verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar. Daha küçük ve çok büyük veri kümelerinin salt okunurdur veya düzenlenebilir görünümlerini göstermek için denetimini kullanabilirsiniz.  
  
 `DataGridView` denetimini, uygulamalarınıza özel davranış oluşturmak için çeşitli yollarla genişletebilirsiniz. Örneğin, kendi sıralama algoritmalarınızı programlı bir şekilde belirtebilir ve kendi hücre türlerinizi oluşturabilirsiniz. `DataGridView` denetiminin görünümünü kolayca özelleştirerek birçok özellik arasından seçim yapabilirsiniz. Birçok veri deposu türü bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetimi bu veri kaynağı ile bağlantılı olmadan çalışabilir.  
  
## <a name="implementing-datagridview-classes"></a>DataGridView sınıfları uygulama  
 `DataGridView` denetiminin genişletilebilirlik özelliklerinden yararlanmak için birkaç yol vardır. Olaylar ve özellikler aracılığıyla denetimin birçok yönünü özelleştirebilirsiniz, ancak bazı özelleştirmeler varolan `DataGridView` sınıflarından türetilmiş yeni sınıflar oluşturmanızı gerektirir.  
  
 En yaygın olarak kullanılan temel sınıflar `DataGridViewCell` ve `DataGridViewColumn`. Kendi hücre sınıfınızı `DataGridViewCell` veya kendi alt sınıflarından türetebilirsiniz. Herhangi bir sütuna herhangi bir hücre türü ekleyebilseniz de, genellikle varsayılan olarak özel hücre türü hücrelerini barındıran `DataGridViewColumn` bir yardımcı sütun sınıfı türetirsiniz.  
  
 Türetilmiş hücre sınıfınıza `IDataGridViewEditingCell` arabirimini uygulayıp, düzen işlevselliğine sahip ancak bir denetimi bir denetim modunda barındırmayan bir hücre türü oluşturmak için uygulayabilirsiniz. Oluşturma modundaki bir hücrede barındırabileceğinizi belirten bir denetim oluşturmak için <xref:System.Windows.Forms.Control>türetilmiş bir sınıfta `IDataGridViewEditingControl` arabirimini uygulayabilirsiniz.  
  
 Daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki hücreleri ve sütunları özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) ve [Windows Forms DataGridView hücrelerinde denetimleri barındırma](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Tek bakışta DataGridView sınıfları  
 <xref:System.Windows.Forms>  
  
|Teknoloji alanı|Sınıflar/arabirimler/yapılandırma öğeleri|  
|---------------------|-------------------------------------------------|  
|Veri Bağlama|<xref:System.Windows.Forms.BindingSource>|  
|Veri sunumu|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> ve türetilmiş sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> genişletilebilirlik|<xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıflar<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Yenilikler  
 <xref:System.Windows.Forms.DataGridView> denetim, Windows Forms tablo verilerini görüntülemek için tamamen bir çözüm olacak şekilde tasarlanmıştır. Yeni bir uygulama yazarken <xref:System.Windows.Forms.DataGrid>gibi diğer çözümlerden önce <xref:System.Windows.Forms.DataGridView> denetimini kullanmayı göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> denetim <xref:System.Windows.Forms.BindingSource> bileşeniyle birlikte çalışabilir. Bu bileşen, bir formun birincil veri kaynağı olacak şekilde tasarlanmıştır. Veri kaynağı türünden bağımsız olarak bir <xref:System.Windows.Forms.DataGridView> denetimi ve veri kaynağı arasındaki etkileşimi yönetebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
