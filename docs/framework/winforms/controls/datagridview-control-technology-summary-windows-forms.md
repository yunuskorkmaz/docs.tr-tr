---
title: "DataGridView Denetimi Teknoloji Özeti (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f172d28e5f03e1177db6ad1bd9e98f4c68267765
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView Denetimi Teknoloji Özeti (Windows Forms)
Bu konu hakkında bilgileri özetler `DataGridView` denetimi ve kullanımını destekleyen sınıflar.  
  
 Tablo biçiminde veri görüntüleme sık gerçekleştirmek büyük olasılıkla bir görevdir. `DataGridView` Denetim kılavuzda verileri sunmak için eksiksiz bir çözüm olacak şekilde tasarlanmıştır.  
  
## <a name="keywords"></a>Anahtar Sözcükler  
 DataGridView, BindingSource, tablo, hücre, veri bağlama, sanal mod  
  
## <a name="namespaces"></a>Ad Alanları  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>İlgili Teknolojiler  
 `BindingSource`  
  
## <a name="background"></a>Arka Plan  
 Kullanıcı Arabirimi (UI) tasarımcıları sık Bu tablo veri kullanıcılarına görüntülemek için gerekli bulur. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Bir tablo veya kılavuz verilerini görüntülemek için çeşitli yöntemler sağlar. `DataGridView` Denetimi bu teknoloji Windows Forms uygulamaları için son evrimi temsil eder.  
  
 `DataGridView` Denetimi, bir veri deposundan veri satırı görüntüleyebilirsiniz. Veri depoları birçok türleri desteklenir. Veri deposu tek boyutlu dizi gibi basit, türsüz verileri tutabilir veya belirtilmiş veri gibi tutabilen bir <xref:System.Data.DataSet>. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar. Küçük ve büyük veri kümelerinin salt okunur veya düzenlenebilir görünümlerini göstermek için denetimi kullanın.  
  
 Genişletebilirsiniz `DataGridView` özel davranış kullanarak uygulamalarınızı oluşturmak için çeşitli şekillerde denetim. Örneğin, program aracılığıyla kendi algoritmaları sıralama belirtebilirsiniz ve hücrelerin kendi türlerinizi oluşturabilirsiniz. Kolayca görünümünü özelleştirebilirsiniz `DataGridView` çeşitli özellikler arasında seçerek denetim. Veri depoları birçok türde bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetim kendisiyle ilişkili bir veri kaynağı olmadan çalışabilir.  
  
## <a name="implementing-datagridview-classes"></a>DataGridView sınıflarını uygulama  
 Yararlanmak birkaç yol vardır `DataGridView` denetimin genişletilebilirlik özellikleri. Denetim olayları ve özellikler aracılığıyla pek çok görünüşünün özelleştirebilirsiniz, ancak bazı özelleştirmeler mevcut türetilmiş yeni sınıflar oluşturmak ihtiyaç duyduğunuz `DataGridView` sınıfları.  
  
 En yaygın kullanılan temel sınıfları `DataGridViewCell` ve `DataGridViewColumn`. Kendi hücre sınıfından türetilen `DataGridViewCell` veya herhangi bir alt sınıfı. Herhangi bir sütun için herhangi bir hücre türü eklemesi mümkün olsa da, genellikle de yardımcı sütun öğesinden bir sınıf türetin `DataGridViewColumn` varsayılan olarak, özel hücre türden hücreleri barındıran.  
  
 Uygulayabileceğiniz `IDataGridViewEditingCell` türetilmiş hücre sınıfınızda düzenleme işlevi vardır, ancak düzenleme modunda bir kontrol barındırmayan bir hücre türü oluşturmak için arabirim. Düzenleme modundaki bir hücreye barındırabilir bir denetim oluşturmak için uygulayabileceğiniz `IDataGridViewEditingControl` bir sınıf arabiriminde türetilen <xref:System.Windows.Forms.Control>.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: hücre özelleştirme ve genişletme Their davranış ve görünümünü göre Windows Forms DataGridView denetiminde sütunları](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) ve [nasıl yapılır: Windows Forms DataGridView hücrelerindeanabilgisayardenetimleri](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Bir bakışta DataGridView sınıfları  
 <xref:System.Windows.Forms>  
  
|Teknoloji alanı|Arabirimleri/sınıfları/yapılandırma öğeleri|  
|---------------------|-------------------------------------------------|  
|Veri Bağlama|<xref:System.Windows.Forms.BindingSource>|  
|Veri sunumu|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell>ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewRow>ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn>ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView>Genişletilebilirlik|<xref:System.Windows.Forms.DataGridViewCell>ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn>ve türetilen sınıflar<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Yenilikler  
 <xref:System.Windows.Forms.DataGridView> Denetimi Windows Forms ile tablo verilerini görüntüleme için eksiksiz bir çözüm olacak şekilde tasarlanmıştır. Kullanmayı düşünmelisiniz <xref:System.Windows.Forms.DataGridView> diğer çözümleri önce denetimini <xref:System.Windows.Forms.DataGrid>, yeni bir uygulama yazarken. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Denetim Kapat birlikte çalışabilir <xref:System.Windows.Forms.BindingSource> bileşeni. Bu bileşen, birincil veri kaynağını bir biçimde olacak şekilde tasarlanmıştır. Arasındaki etkileşimi yönetebilirsiniz bir <xref:System.Windows.Forms.DataGridView> kaynak denetim ve veri bağımsız olarak kendi veri kaynağı türü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [DataGridView denetimi mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Bağlantı bilgileri koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
