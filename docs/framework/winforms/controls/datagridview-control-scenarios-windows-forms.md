---
title: DataGridView Denetimi Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742465"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView Denetimi Senaryoları (Windows Forms)
<xref:System.Windows.Forms.DataGridView> denetimiyle, çeşitli veri kaynaklarından tablosal verileri görüntüleyebilirsiniz. Basit kullanımlar için bir <xref:System.Windows.Forms.DataGridView> el ile doldurabilir ve verileri doğrudan denetim aracılığıyla işleyebilirsiniz. Ancak, genellikle verilerinizi bir dış veri kaynağında depolar ve bir <xref:System.Windows.Forms.BindingSource> bileşeni aracılığıyla denetimi buna bağlarsınız.  
  
 Bu konu, <xref:System.Windows.Forms.DataGridView> denetimini içeren bazı yaygın senaryolardan bazılarını açıklamaktadır.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Senaryo 1: küçük miktarlarda veri görüntüleme  
 <xref:System.Windows.Forms.DataGridView> denetiminde göstermek için verilerinizi bir dış veri kaynağına depolamanız gerekmez. Az miktarda veriyle çalışıyorsanız, denetimi kendiniz doldurabilir ve verileri denetim aracılığıyla düzenleyebilirsiniz. Buna *ilişkisiz mod*denir. Daha fazla bilgi için bkz. [nasıl yapılır: ilişkisiz Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- İlişkisiz modda, denetimi el ile doldurursunuz.  
  
- İlişkisiz mod özellikle küçük miktarlarda salt okunan veriler için uygundur.  
  
- İlişkisiz mod ayrıca elektronik tablo gibi veya en seyrek doldurulmuş tablolar için de uygundur.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Senaryo 2: dış veri kaynağında depolanan verileri görüntüleme ve güncelleştirme  
 <xref:System.Windows.Forms.DataGridView> denetimini, kullanıcıların veritabanı tablosu veya iş nesneleri koleksiyonu gibi bir veri kaynağında tutulan verilere erişebileceği Kullanıcı arabirimi (UI) olarak kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Forms DataGridView denetimine bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- Bağlama modu bir veri kaynağına bağlanmanıza, veri kaynağı özelliklerine veya veritabanı sütunlarına göre otomatik olarak sütun oluşturmanıza ve denetimi otomatik olarak doldurmasına olanak sağlar.  
  
- Sınırlı modu, verilerle ağır Kullanıcı etkileşimi için uygundur. Veriler görüntülenmek üzere biçimlendirilebilir ve Kullanıcı tarafından belirtilen veriler veri kaynağı tarafından beklenen biçimde ayrıştırılabilir. Veri girişi biçimlendirme hataları ve veritabanı kısıtlama hataları, kullanıcıların uyarılabilmesi ve hatalı hücrelerin düzeltibilmesi için algılanabilir.  
  
- Sütun sıralama, dondurma ve yeniden düzenleme gibi ek işlevler, kullanıcıların verileri iş akışları için en uygun şekilde görüntülemesine olanak tanır.  
  
- Pano desteği, kullanıcıların uygulamanızdan diğer uygulamalara veri kopyalamasını sağlar.  
  
## <a name="scenario-3-advanced-data"></a>Senaryo 3: Gelişmiş veriler  
 Standart veri bağlama modelinin ele gerekmediği özel gereksinimleriniz varsa, *sanal mod*'u uygulayarak denetim ve verileriniz arasındaki etkileşimi yönetebilirsiniz. Sanal modu uygulamak, bir veya daha fazla olay işleyicisinin, bilgilerin gerekli olduğu şekilde hücreler hakkında bilgi istemesine izin veren bir veya daha fazla olay işleyicisini uygulama  
  
 Örneğin, büyük miktarlarda verilerle çalışıyorsanız, en iyi verimliliği sağlamak için sanal modu uygulamak isteyebilirsiniz. Sanal mod ayrıca, başka bir veri kaynağından alınan sütunlarla birlikte görüntülenen ilişkisiz sütunların değerlerini korumak için de kullanışlıdır.  
  
 Sanal mod hakkında daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- Sanal mod, performansı hassas bir şekilde ayarlamanız gerektiğinde çok büyük miktarlarda veri görüntülemek için uygundur.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Senaryo 4: satırları ve sütunları otomatik olarak yeniden boyutlandırma  
 Düzenli olarak güncellenen verileri görüntülediğinizde, tüm içeriğin görünür olmasını sağlamak için satırları ve sütunları otomatik olarak yeniden boyutlandırabilirsiniz. <xref:System.Windows.Forms.DataGridView> denetim, el ile yeniden boyutlandırmayı etkinleştirmenizi veya devre dışı bırakmanızı, belirli zamanlarda programlama yoluyla yeniden boyutlandırmayı veya içerik değiştiğinde otomatik olarak yeniden boyutlandırmayı sağlayan çeşitli seçenekler sağlar. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- El ile yeniden boyutlandırma, kullanıcıların hücre yüksekliklerini ve genişliklerini ayarlamasına olanak sağlar.  
  
- Otomatik yeniden boyutlandırma, hücre içeriğinin hiçbir şekilde kırpılmaması için hücre boyutlarını korumanıza olanak sağlar.  
  
- Programlı yeniden boyutlandırma, sürekli otomatik yeniden boyutlandırmanın performans cezasından kaçınmak için hücreleri belirli zamanlarda yeniden boyutlandırmanızı sağlar.  
  
## <a name="scenario-5-simple-customization"></a>Senaryo 5: basit özelleştirme  
 <xref:System.Windows.Forms.DataGridView> denetimi, temel görünümünü ve davranışını değiştirmek için birçok yol sunar. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> nesneler, birden çok düzeyde ve denetimin bağımsız öğeleri için renk, yazı tipi, biçimlendirme ve konumlama bilgilerini sağlamanıza olanak tanır.  
  
- Hücre stilleri birden çok öğe tarafından katmanlanmış olabilir ve kodu yeniden kullanmanıza olanak tanır.  
  
## <a name="scenario-6-advanced-customization"></a>Senaryo 6: Gelişmiş özelleştirme  
 <xref:System.Windows.Forms.DataGridView> denetimi, görünümünü ve davranışını özelleştirmek için birçok yol sunar.  
  
### <a name="scenario-key-points"></a>Senaryo anahtar noktaları  
  
- Kendi hücre boyama kodunuzu sağlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
- Kendi satır boyamayı sağlayabilirsiniz. Bu, örneğin, birden çok sütuna yayılan içeriğe sahip satırlar oluşturmak için kullanışlıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki satırların görünümünü özelleştirme](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
- Hücre görünümünü özelleştirmek için kendi hücre ve sütun sınıflarınızı uygulayabilirsiniz. Daha fazla bilgi için, bkz. [nasıl yapılır: davranış ve görünümünü genişleterek Windows Forms DataGridView Denetimindeki hücreleri ve sütunları özelleştirme](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
- Yerleşik sütun türleri tarafından sağlandıklardan farklı denetimleri barındırmak için kendi hücre ve sütun sınıflarınızı uygulayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri barındırma](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView Denetimine Genel Bakış](datagridview-control-overview-windows-forms.md)
