---
title: Windows Forms DataGridView Denetiminde Sanal Mod
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 2e5724da4442bbfcb0928c864f78744b946acc18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sanal Mod
Sanal mod ile arasındaki etkileşimi yönetebilirsiniz <xref:System.Windows.Forms.DataGridView> denetimi ve bir özel veri önbelleği. Sanal mod uygulamak için ayarlanmış <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğine `true` ve bir veya daha fazla bu konuda açıklanan olayları işlemek. Genellikle işleyecek en az `CellValueNeeded` değerleri veri önbelleğindeki denetim Ara sağlayan olay.  
  
## <a name="bound-mode-and-virtual-mode"></a>Bağlı mod ve sanal mod  
 Sanal mod, yalnızca desteklemek veya ilişkili modunu değiştirmek gerektiğinde gereklidir. İlişkili modunda ayarladığınız <xref:System.Windows.Forms.DataGridView.DataSource%2A> özellik denetimi otomatik olarak belirtilen kaynaktan verileri yükler ve kullanıcı değişiklikleri yeniden gönderir. Veri kaynağı genellikle sıralama gibi işlemleri gerçekleştirir ve ilişkili sütunların görüntülendiği denetleyebilirsiniz.  
  
## <a name="supplementing-bound-mode"></a>Bağlı mod ekleme  
 Bağlanmamış sütunlar bağlı sütunlar birlikte görüntüleyerek bağlı mod destekleyebilirsiniz. Bu bazen "karma mod" olarak adlandırılır ve hesaplanan değerler veya kullanıcı arabirimi (UI) denetimleri gibi işlemler görüntülemek için yararlıdır.  
  
 Bağlanmamış sütunlar veri kaynağı dışında olduğundan, veri kaynağının sıralama işlemleri tarafından göz ardı edilir. Bu nedenle, karma modda sıralama etkinleştirdiğinizde, yerel bir önbellek bağlanmamış verileri yönetmek ve gerekir izin vermek için sanal modu uygulama <xref:System.Windows.Forms.DataGridView> denetimi ile etkileşim.  
  
 Örneklerde ilişkisiz sütunlardaki değerleri tutmak için sanal modu kullanma hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> sınıf başvuru konuları.  
  
## <a name="replacing-bound-mode"></a>İlişkili modunu değiştirme  
 Bağlı mod performans gereksinimlerinizi karşılamıyorsa, tüm verilerinizi özel Önbellek modu sanal olay işleyicileri aracılığıyla yönetebilirsiniz. Örneğin, yalnızca saat veri yalnızca alır mekanizması yükleme uygulamak için sanal modu kullanabilirsiniz en iyi performans için gerekli olduğu kadar veritabanındaki verileri bir ağa bağlı. Bu senaryo, büyük miktarlarda verinin bir yavaş ağ bağlantısı üzerinden veya sınırlı miktarda RAM veya depolama alanı sahip istemci makineler ile çalışırken, özellikle yararlı olacaktır.  
  
 Yalnızca zaman senaryosunda sanal modu kullanma hakkında daha fazla bilgi için bkz: [Just-In-Time verileri yüklenirken Windows Forms DataGridView denetiminde ile sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Sanal mod olayları  
 Verilerinizi salt okunur ise `CellValueNeeded` olay işleme gerekir yalnızca olay olabilir. Ek sanal modu olaylar, kullanıcı düzenlemeleri, satır ekleme ve silme ve satır düzeyi işlemleri gibi belirli işlevleri etkinleştirmenize olanak tanır.  
  
 Bazı standart <xref:System.Windows.Forms.DataGridView> olayları (kullanıcılar eklediğinizde veya satırları silmek veya ne zaman, değerleri hücre gerçekleşen olaylara düzenlenemez, ayrıştırılır, doğrulanmış biçimlendirilmiş veya gibi) sanal modunda de yararlıdır. Ayrıca, normal hücre araç ipucu metni, hücre ve satır hata metni, hücre ve satır kısayol menüsü veri ve satır yüksekliği veri gibi bir bağımlı veri kaynağında depolanan değerleri tutmanıza olanak tanıyan olayları işleyebilir.  
  
 Satır düzeyi yürütme kapsamlı okuma/yazma veri yönetmek için sanal modu uygulama hakkında daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Bir hücre düzeyi yürütme kapsamı ile sanal modu uygulayan bir örnek için bkz: <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği başvuru konusu.  
  
 Yalnızca aşağıdaki olaylar gerçekleşir zaman <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği ayarlanmış `true`.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Görüntülenecek veri önbelleğinden bir hücre değerini almak için denetim tarafından kullanılır. Bu olay için yalnızca ilişkisiz sütunlardaki hücrelerde gerçekleşir.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Kullanıcı girişi için bir hücre veri önbelleğine yürütmek için denetim tarafından kullanılır. Bu olay için yalnızca ilişkisiz sütunlardaki hücrelerde gerçekleşir.<br /><br /> Çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> dışında bir önbelleğe alınan değer değiştirirken yöntemi bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> olay işleyicisi geçerli değeri, denetimi görüntülendiğinden emin olun ve tüm otomatik boyutlandırma modlarında şu anda etkin uygulamak için.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Yeni bir satır veri önbelleğindeki gereksinimini göstermek için denetim tarafından kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Bir satır uygulanmayan değişiklikleri olup olmadığını belirlemek için denetim tarafından kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Bir satır için önbelleğe alınmış değerlerini geri belirtmek için denetim tarafından kullanılır.|  
  
 Aşağıdaki olaylar sanal modda kullanışlıdır ancak bağımsız olarak, kullanılabilir <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik ayarı.  
  
|Olaylar|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Denetim tarafından ne zaman silinen satır veya eklenen, olanak tanıyarak, veri önbelleği güncellemenize göstermek için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Hücre değerlerini biçimlendirmek için denetimi tarafından görüntülenmesi için ayrıştırma ve kullanıcı girişi doğrulamak için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Hücre araç ipucu metni almak için denetim tarafından kullanılan zaman <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlanmış veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.<br /><br /> Hücre araç ipuçları görüntülenir yalnızca <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özellik değeri `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Hücre veya satır hata metni almak için denetim tarafından kullanılan zaman <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlanmış veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.<br /><br /> Çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> yöntemi veya <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> geçerli değeri, denetimi görüntülendiğinden emin olmak için bir hücre veya satır hata metni değiştirdiğinizde yöntemi.<br /><br /> Hücre ve satır hata karakterlerin görüntülenir, <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> ve <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> özellik değerlerini olduğunuz `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Bir hücrenin veya satır almak için denetim tarafından kullanılan <xref:System.Windows.Forms.ContextMenuStrip> zaman Denetim <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlanmış veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Denetim tarafından almak veya veri önbelleğindeki satır yüksekliği bilgilerini depolamak için kullanılır. Çağrı <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> dışında önbelleğe alınmış satır yüksekliği bilgileri değiştirildiğinde yöntemi bir <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> geçerli değeri denetim görünümünde kullanıldığından emin olmak için olay işleyicisi.|  
  
## <a name="best-practices-in-virtual-mode"></a>Sanal mod'ndaki en iyi yöntemler  
 Büyük miktarda veriyi verimli bir şekilde çalışması için sanal modu uyguluyorsanız, ayrıca, verimli bir şekilde ile çalıştığından emin olun istersiniz <xref:System.Windows.Forms.DataGridView> denetimi. Hücre stilleri, otomatik boyutlandırma, seçimleri ve satır paylaşma verimli kullanımı hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
