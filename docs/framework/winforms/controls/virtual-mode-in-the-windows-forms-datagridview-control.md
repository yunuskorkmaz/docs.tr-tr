---
title: Windows Forms DataGridView Denetiminde Sanal Mod
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f284835578221ad1fe859f260e37bb829cd64b2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124728"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sanal Mod
Arasındaki etkileşimi yönetebileceğiniz ile sanal modu, <xref:System.Windows.Forms.DataGridView> denetimi ve bir özel veri önbelleği. Sanal modu uygulamak için ayarlanmış <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` ve bir veya daha fazla bu konuda açıklanan olayları işler. Genellikle işleyecek en az `CellValueNeeded` değerleri önbellekteki denetimi arama sağlayan bir olay.  
  
## <a name="bound-mode-and-virtual-mode"></a>Bağlı mod ve sanal mod  
 Bağlı mod değiştirmek veya desteklemek yalnızca ihtiyacınız olduğunda sanal modu gereklidir. İlişkili modunda ayarladığınız <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ve denetimi, otomatik olarak belirtilen kaynaktan verileri yükler ve kullanıcı değişiklikleri yeniden gönderir. Veri kaynağı, genellikle sıralama gibi işlemleri gerçekleştirir ve ilişkili sütunların görüntülenme denetleyebilirsiniz.  
  
## <a name="supplementing-bound-mode"></a>Bağlı mod ekleme  
 Bağlanmamış sütunlar bağlı sütun birlikte görüntüleyerek bağımlı modu destekleyebilirsiniz. Bu, bazen "karma mod" olarak adlandırılır ve hesaplanan değerler veya kullanıcı arabirimi (UI) denetimleri gibi işlemler görüntülemek için yararlıdır.  
  
 Bağlanmamış sütunlar, veri kaynağının dışında olduğundan, veri kaynağının sıralama işlemleri tarafından göz ardı edilir. Bu nedenle, karma modda sıralama etkinleştirdiğinizde, yerel önbellekteki ilişkisiz verileri yönetmek ve gerekir izin vermek için sanal mod uygulamak <xref:System.Windows.Forms.DataGridView> denetimi ile etkileşim.  
  
 Örneklerde ilişkisiz sütunlardaki değerlerin korumak için sanal mod kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> sınıfı başvuru konuları.  
  
## <a name="replacing-bound-mode"></a>Bağımlı modu değiştirme  
 Bağlı mod performans gereksinimlerinizi karşılamıyorsa, tüm verilerinizi özel bir önbellek modu sanal olay işleyicileri aracılığıyla yönetebilirsiniz. Örneğin, yalnızca alır mekanizması yüklenirken just-ın-time Veri uygulamak için sanal mod kullanabilirsiniz kadar veri en iyi performans için gerekli olan bir ağa bağlı veritabanından. Bu senaryo, büyük miktarlarda verinin bir yavaş ağ bağlantısı veya sınırlı miktarda RAM veya depolama alanı olan istemci makineler ile çalışırken, özellikle yararlı olur.  
  
 Just-ın-time senaryoda sanal modu kullanma hakkında daha fazla bilgi için bkz. [ile tam zamanında veri yükleme Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Sanal modda olayları  
 Verilerinizi salt okunur ise `CellValueNeeded` olay ihtiyaç duyacağınız işlemek için yalnızca olay olabilir. Ek sanal modu olaylarını kullanıcı düzenlemeleri, satır eklemeyi ve silmeyi ve satır düzeyinde işlemleri gibi belirli işlevleri etkinleştirme olanak tanır.  
  
 Bazı standart <xref:System.Windows.Forms.DataGridView> olayları (kullanıcılar eklediğinizde veya satırları silmek veya ne zaman, değerleri hücre meydana gelen olayları düzenlendi, ayrıştırıldığında, doğrulanmış biçimlendirilmiş veya gibi) sanal modda da yararlıdır. Ayrıca, normal hücresi araç ipucu metni, hücre ve satır hata metni, hücre ve satır kısayol menüsünde veri ve satır yüksekliği veri gibi bir bağımlı veri kaynağında depolanan değerleri tutmanıza olanak tanıyan olayları işleyebilir.  
  
 Okuma/yazma verileri satır düzeyinde işleme kapsamlı yönetmek için sanal modu uygulama hakkında daha fazla bilgi için bkz. [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Hücre düzeyinde işleme kapsamı ile sanal modu uygulayan bir örnek için bkz: <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik başvuru konusu.  
  
 Yalnızca aşağıdaki olaylar gerçekleşir, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Veri önbelleğini görüntülemek için bir hücre değerini almak için denetim tarafından kullanılır. İlişkisiz sütunlardaki hücrelerde için yalnızca bu olayı oluşur.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Kullanıcı girişi için bir hücre verileri önbelleğe kaydetmek için denetim tarafından kullanılır. İlişkisiz sütunlardaki hücrelerde için yalnızca bu olayı oluşur.<br /><br /> Çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> dışında bir önbelleğe alınan değeri değiştirirken yöntemi bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> denetimdeki geçerli değeri görüntülendiğinden emin olun ve tüm otomatik boyutlandırma modu şu anda etkin uygulamak için olay işleyicisi.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Veri önbelleğini yeni bir satır için gereken göstermek için denetim tarafından kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Bir satır kaydedilmemiş değişiklikleri olup olmadığını belirlemek için denetim tarafından kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Bir satır için önbelleğe alınan değerleri geri belirtmek için denetim tarafından kullanılır.|  
  
 Aşağıdaki olaylar sanal modda kullanışlıdır ancak bağımsız olarak, kullanılabilir <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik ayarı.  
  
|Olaylar|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Denetim tarafından ne zaman silinmiş satırları veya eklenen, olanak tanıyarak veri önbelleğini uygun şekilde güncelleştirme belirtmek için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Hücre değerlerini biçimlendirmek için bir denetim tarafından görüntülemek ve ayrıştırmak ve kullanıcı girişini doğrulama için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Hücre araç ipucu metnini almak için denetim tarafından kullanılan zaman <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.<br /><br /> Hücre araç ipuçları görüntülenir yalnızca <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özellik değeri `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Bir veya daha fazla satır hata metnini almak için denetim tarafından kullanılan zaman <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.<br /><br /> Çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> yöntemi veya <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> geçerli değer denetiminde görüntülendiğinden emin olmak için bir veya daha fazla satır hata metni değiştirdiğinizde yöntemi.<br /><br /> Hücre ve satır hata kabartması görüntülenir, <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> ve <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> özellik değerleri `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Bir satır veya hücre almak için denetim tarafından kullanılan <xref:System.Windows.Forms.ContextMenuStrip> olduğunda denetim <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Denetim tarafından almak veya satır yüksekliği bilgi verileri önbelleğe depolamak için kullanılır. Çağrı <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> yöntemi önbelleğe alınan satır yüksekliği bilgileri dışında değiştirildiğinde bir <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> geçerli değeri denetimin ekranda kullanıldığından emin olmak için olay işleyicisi.|  
  
## <a name="best-practices-in-virtual-mode"></a>Sanal modda en iyi uygulamalar  
 Büyük miktarda veriyi verimli bir şekilde çalışması için sanal mod uyguluyorsanız, ayrıca verimli bir şekilde çalıştığınız emin olmak isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetiminin kendisini. Hücre stilleri, otomatik boyutlandırma, seçim ve satır paylaşma verimli kullanımı hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
