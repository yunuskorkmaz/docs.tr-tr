---
title: DataGridView Denetimi Senaryoları (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 52c448f21be056e6166334785943356039baf3ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175298"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView Denetimi Senaryoları (Windows Forms)
İle <xref:System.Windows.Forms.DataGridView> denetimi, çeşitli veri kaynaklarından tablo verilerini görüntüleyebilir. El ile doldurabilirsiniz basit kullanımları bir <xref:System.Windows.Forms.DataGridView> ve denetim verilerine doğrudan düzenleyebilirsiniz. Genellikle, ancak bir dış veri kaynağındaki verileri depolamak ve üzerinden denetime bağlamak bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
 Bu konu başlığı altında içeren yaygın senaryolara bazılarını açıklar <xref:System.Windows.Forms.DataGridView> denetimi.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Senaryo 1: Küçük miktarlarda veri görüntüleme  
 İçinde görüntülemek için bir dış veri kaynağındaki verileri depolamak gerekmez <xref:System.Windows.Forms.DataGridView> denetimi. Az miktarda veriniz ile çalışıyorsanız, kendiniz denetimi doldurmak ve verileri denetim yoluyla. Bu adlandırılır *ilişkisiz modu*. Daha fazla bilgi için [nasıl yapılır: Bir bağlantısız bir Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   Bağlantısız modda denetimi el ile doldurun.  
  
-   İlişkisiz Modu, özellikle küçük miktarda salt okunur veriler için uygundur.  
  
-   İlişkisiz modu aynı zamanda benzeyen veya seyrek doldurulmuş tablolar için uygundur.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Senaryo 2: Bir dış veri kaynağında depolanan verileri güncelleştirme ve görüntüleme  
 Kullanabileceğiniz <xref:System.Windows.Forms.DataGridView> denetleyen bir kullanıcı arabirimi (UI) hangi kullanıcıların bir veritabanı tablosu ya da iş nesneleri koleksiyonu gibi bir veri kaynağında tutulan verilere erişebilir. Daha fazla bilgi için [nasıl yapılır: Veri bağlama Windows Forms DataGridView denetiminde](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   Bağlı mod bir veri kaynağına bağlanmak, veri kaynağı özellikleri veya veritabanı sütunlarını göre sütunları otomatik olarak oluşturmak ve denetimi otomatik olarak doldurmak olanak tanır.  
  
-   Bağlı mod verilerle yoğun bir kullanıcı etkileşimi için uygundur. Veri görüntülenmek üzere biçimlendirilebilir ve veri kullanıcı tarafından belirtilen veri kaynağı tarafından beklenen biçime ayrıştırılabilir. Hataları ve veritabanı kısıtlaması hataları biçimlendirme veri girişi, böylece kullanıcılar uyarı ve hatalı hücreleri düzeltilebilir algılanabilir.  
  
-   Sütun sıralama gibi ek işlevler, kullanıcılar kendi iş akışının için en uygun şekilde verileri görüntülemek dondurma ve yeniden etkinleştirin.  
  
-   Kullanıcılar, uygulamanın diğer uygulamalara veri kopyalamak Pano desteği sağlar.  
  
## <a name="scenario-3-advanced-data"></a>Senaryo 3: Gelişmiş veri  
 Standart veri bağlama modelini değil gideren özel gereksinimleriniz varsa, Denetim ve verilerinizi arasındaki etkileşimi uygulayarak yönetebileceğiniz *sanal modu*. Uygulama denetimi isteği hakkında bilgi hücreleri bilgi sağlayan bir veya daha fazla olay işleyicilerini uygulayan sanal modu anlamına gelir gereklidir.  
  
 Örneğin, büyük miktarlarda veri ile çalışıyorsanız, en uygun verimlilik sağlamak için sanal mod uygulamak isteyebilirsiniz. Başka bir veri kaynağından alınan sütunları birlikte görüntüleme bağlanmamış sütunlar değerlerini korumak için sanal mod de yararlıdır.  
  
 Sanal mod hakkında daha fazla bilgi için bkz: [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   Performans üzerinde ince ayar gerektiğinde, çok büyük miktarda veriyi görüntülemek için sanal mod uygundur.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Senaryo 4: Otomatik olarak satırları ve sütunları yeniden boyutlandırma  
 Düzenli olarak güncelleştirilen veri görüntülediğinizde, satır ve sütun tüm içeriğini görünür olduğundan emin olmak için otomatik olarak boyutlandırabilirsiniz. <xref:System.Windows.Forms.DataGridView> Denetimi etkinleştir veya devre dışı bırakma elle, programlı olarak belirli zamanlarda yeniden boyutlandırmak yeniden boyutlandırma olanak tanıyan çeşitli seçenekler sağlar veya yeniden boyutlandırma otomatik olarak değişiklikler olduğunda içerik. Daha fazla bilgi için [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   El ile yeniden boyutlandırma, hücre yükseklik ve genişlik ayarlamak kullanıcıların sağlar.  
  
-   Otomatik yeniden boyutlandırma, böylece hücre içerik hiçbir zaman kırpılır hücre boyutlarını tutmanızı sağlar.  
  
-   Programlı olarak yeniden boyutlandırma, sürekli otomatik yeniden boyutlandırma, performans cezasını önlemek için belirli zamanlarda hücreleri yeniden boyutlandırma sağlar.  
  
## <a name="scenario-5-simple-customization"></a>Senaryo 5: Basit özelleştirme  
 <xref:System.Windows.Forms.DataGridView> Denetim temel görünümünü ve davranışını değiştirmek birçok yol sağlar. Daha fazla bilgi için [Windows Forms DataGridView denetimindeki hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri, renk, yazı tipi, biçimlendirme ve bilgi birden çok düzeyi ve ayrı ayrı öğeler denetimin konumlandırma sağlamanıza olanak tanır.  
  
-   Hücre stilleri, katmanlı ve kodu yeniden izin vererek birden çok öğe tarafından paylaşılır.  
  
## <a name="scenario-6-advanced-customization"></a>6. Senaryo: Gelişmiş özelleştirme  
 <xref:System.Windows.Forms.DataGridView> Denetim görünümünü ve davranışını özelleştirmek birçok yol sağlar.  
  
### <a name="scenario-key-points"></a>Senaryo temel noktaları  
  
-   Kendi hücre boyama kodunuzu sağlayabilir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Kendi satır boyama sağlayabilir. Örneğin, birden fazla sütuna yayılmış içeriğiyle satır oluşturmak için kullanışlıdır. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Hücre görünümünü özelleştirmek için kendi hücre ve sütun sınıflarınızı uygulayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Hücreleri özelleştirme ve sütunları Windows Forms DataGridView denetiminde davranış ve görünümünü genişleterek](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Konak denetimleri yerleşik sütun türleri tarafından sağlanan olanlar dışındaki kendi hücre ve sütun sınıflarına uygulayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
