---
title: "DataGridView Denetimi Senaryoları (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 919197d8fdb40f0e0fb7b91fecae38f4e0e061bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView Denetimi Senaryoları (Windows Forms)
İle <xref:System.Windows.Forms.DataGridView> denetimi, çeşitli veri kaynakları tablo verilerini görüntüleyebilir. Basit kullanımları, el ile doldurabilirsiniz bir <xref:System.Windows.Forms.DataGridView> ve denetim aracılığıyla doğrudan verileri işlemek. Genellikle, ancak bir dış veri kaynağında verilerinizi depolamak ve üzerinden denetimi bağlamak bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
 Bu konu ile ilgili yaygın senaryolardan bazıları açıklanmaktadır <xref:System.Windows.Forms.DataGridView> denetim.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Senaryo 1: Küçük miktarda veri görüntüleme  
 İçinde görüntülemek için bir dış veri kaynağında verilerinizi depolamak gerekmez <xref:System.Windows.Forms.DataGridView> denetim. Çok küçük miktarda veri ile çalışıyorsanız, Denetim kendiniz doldurmak ve denetimi verilerine arabirimidir. Bu adlı *ilişkisiz modu*. Daha fazla bilgi için bkz: [nasıl yapılır: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   Bağlantısız modda denetimi el ile doldurun.  
  
-   İlişkisiz Modu, özellikle küçük miktarda salt okunur veri için uygundur.  
  
-   İlişkisiz Modu ayrıca elektronik tablo benzeri veya seyrek doldurulmuş tablolar için uygundur.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Senaryo 2: Görüntüleme ve bir dış veri kaynağında depolanan verileri güncelleştirme  
 Kullanabileceğiniz <xref:System.Windows.Forms.DataGridView> denetleyen bir kullanıcı arabirimi (UI) hangi kullanıcıların bir veri kaynağında bir veritabanı tablosu veya iş nesneleri koleksiyonu gibi tutulan verilere erişebilir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   Bağlı mod, bir veri kaynağına bağlanmak, veri kaynağı özellikleri veya veritabanı sütunlarına dayalı sütunları otomatik olarak oluşturmak ve denetimi otomatik olarak doldurulması sağlar.  
  
-   Bağlı mod verilerle ağır kullanıcı etkileşimi için uygundur. Veri görüntülenmek üzere biçimlendirilebilir ve kullanıcı tanımlı veri veri kaynağı tarafından beklenen biçime ayrıştırılabilir. Veri girişini biçimlendirme hataları ve veritabanı kısıtlama hataları, böylece kullanıcılar uyarı ve hatalı hücreleri düzeltilebilir algılanabilir.  
  
-   Sütun sıralama gibi ek işlevler dondurma ve yeniden sıralama kullanıcılar kendi iş akışı için en uygun şekilde verileri görüntülemek etkinleştirin.  
  
-   Pano desteği, uygulamanızın diğer uygulamalara veri kopyalamak kullanıcıların sağlar.  
  
## <a name="scenario-3-advanced-data"></a>Senaryo 3: Gelişmiş veri  
 Standart veri bağlama modelini olmayan adres özel gereksinimleri varsa, Denetim ve verilerinizi arasındaki etkileşimi uygulayarak yönetebileceğiniz *sanal modu*. Sanal mod anlamına gelir denetim isteği bilgileri hücreler hakkında bilgi olarak sağlayan bir veya daha fazla olay işleyicileri uygulama uygulama gereklidir.  
  
 Örneğin, büyük miktarlarda veri çalışıyorsanız, en iyi verimlilik sağlamak için sanal modu uygulamak isteyebilirsiniz. Sanal mod, başka bir veri kaynağından alınan sütunları birlikte görüntüleme ilişkisiz sütun değerleri de sürdürmek için yararlıdır.  
  
 Sanal modu hakkında daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   Sanal mod performans ince ayar gerektiğinde çok büyük miktarda veri görüntülemek için uygundur.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Senaryo 4: Satırları ve sütunları otomatik olarak yeniden boyutlandırma  
 Düzenli olarak güncelleştirilen verileri görüntülediğinizde, satırları ve sütunları tüm içeriği görünür olduğundan emin olmak için otomatik olarak boyutlandırabilirsiniz. <xref:System.Windows.Forms.DataGridView> Denetimini etkinleştirme veya devre dışı bırak elle, programlı olarak belirli zamanlarda yeniden boyutlandırmak yeniden boyutlandırma olanak tanıyan çeşitli seçenekler sağlar ya da yeniden boyutlandırma otomatik olarak değişiklikler olduğunda içerik. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   El ile yeniden boyutlandırma kullanıcıların hücre yükseklik ve genişlik ayarlamanıza olanak tanır.  
  
-   Otomatik yeniden boyutlandırma, böylece hücre içerik hiçbir zaman kırpılır hücre boyutları tutmanızı sağlar.  
  
-   Program yeniden boyutlandırma yaşanan sürekli otomatik yeniden boyutlandırma, performans sorunları önlemek için belirli zamanlarda hücreleri yeniden boyutlandırma olanak tanır.  
  
## <a name="scenario-5-simple-customization"></a>Senaryo 5: Basit özelleştirme  
 <xref:System.Windows.Forms.DataGridView> Denetimi temel görünümünü ve davranışını değiştirmek birçok yol sağlar. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle>nesneleri renk, yazı tipi, biçimlendirme ve birden çok düzeyi ve denetim ayrı ayrı öğeler için bilgi konumlandırma sağlamanıza olanak tanır.  
  
-   Hücre stilleri katmanlı ve kodunu yeniden izin vererek birden çok öğe tarafından paylaşılan.  
  
## <a name="scenario-6-advanced-customization"></a>6. Senaryo: Gelişmiş özelleştirme  
 <xref:System.Windows.Forms.DataGridView> Denetimi görünümünü ve davranışını özelleştirmek birçok yol sağlar.  
  
### <a name="scenario-key-points"></a>Senaryo önemli noktaları  
  
-   Kendi hücre boyama kodunuzu sağlayabilir. Daha fazla bilgi için bkz: [nasıl yapılır: görünümü hücre Windows Forms DataGridView denetiminde özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Kendi satır boyama sağlayabilir. Örneğin, birden çok sütuna yayılan içerikle satırları oluşturmak için kullanışlıdır. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde görünümü, satırları özelleştirmek](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Hücre görünümünü özelleştirmek için kendi hücre ve sütun sınıfları uygulayabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: hücre özelleştirme ve genişletme Their davranış ve görünümünü göre Windows Forms DataGridView denetiminde sütunları](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Kendi ana bilgisayar denetimleri yerleşik sütun türleri tarafından sağlanan dışındaki hücre ve sütun sınıflarına uygulayabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView hücrelerinde ana bilgisayar denetimleri](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
