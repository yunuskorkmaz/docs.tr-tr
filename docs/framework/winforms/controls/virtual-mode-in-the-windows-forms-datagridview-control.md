---
title: DataGridView denetiminde sanal mod
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745438"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sanal Mod
Sanal mod ile, <xref:System.Windows.Forms.DataGridView> denetimi ile özel veri önbelleği arasındaki etkileşimi yönetebilirsiniz. Sanal modu uygulamak için <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` olarak ayarlayın ve bu konuda açıklanan olaylardan birini veya daha fazlasını işleyin. Genellikle en az `CellValueNeeded` olayını işleyecektir ve bu sayede denetim, veri önbelleğindeki değerleri arayabilir.  
  
## <a name="bound-mode-and-virtual-mode"></a>Sınırlı mod ve sanal mod  
 Sanal mod yalnızca, sınırlı modu eklemeniz veya değiştirmeniz gerektiğinde gereklidir. Bağlantılı modda <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlarsınız ve denetim belirtilen kaynaktan verileri otomatik olarak yükler ve Kullanıcı değişikliklerini buna geri gönderir. Hangi bağlantılı sütunların gösterileceğini denetleyebilir ve veri kaynağının genellikle sıralama gibi işlemleri gerçekleştirir.  
  
## <a name="supplementing-bound-mode"></a>Bağlanma modunun takıma  
 Bağlı sütunlarla birlikte ilişkisiz sütunları görüntüleyerek, ilişkili modu destekleyebilirsiniz. Bu bazen "karışık mod" olarak adlandırılır ve Hesaplanmış değerler veya Kullanıcı arabirimi (UI) denetimleri gibi şeyleri görüntülemek için yararlıdır.  
  
 İlişkisiz sütunlar veri kaynağının dışında olduğundan, veri kaynağının sıralama işlemleri tarafından yok sayılır. Bu nedenle, karma modda sıralamayı etkinleştirdiğinizde, bağlı olmayan verileri yerel bir önbellekte yönetmeniz ve <xref:System.Windows.Forms.DataGridView> denetiminin onunla etkileşime geçmesini sağlamak için sanal mod uygulamanız gerekir.  
  
 İlişkisiz sütunlardaki değerleri korumak için sanal modu kullanma hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> özelliğindeki örneklere ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> sınıfı başvuru konularına bakın.  
  
## <a name="replacing-bound-mode"></a>Sınırlı modu değiştirme  
 Sınırlı mod, performans ihtiyaçlarınızı karşılamıyorsa, sanal mod olay işleyicileri aracılığıyla tüm verilerinizi özel bir önbellekte yönetebilirsiniz. Örneğin, en iyi performans için gerekli olduğu gibi, ağa bağlı bir veritabanından yalnızca çok fazla veri alan bir tam zamanında veri yükleme mekanizması uygulamak için sanal modu kullanabilirsiniz. Bu senaryo, yavaş bir ağ bağlantısı üzerinden veya sınırlı miktarda RAM veya depolama alanı olan istemci makineler ile büyük miktarlarda verilerle çalışırken özellikle faydalıdır.  
  
 Tam zamanında bir senaryoda sanal modu kullanma hakkında daha fazla bilgi için, [Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)bölümüne bakın.  
  
## <a name="virtual-mode-events"></a>Sanal mod olayları  
 Verileriniz salt okunurdur, `CellValueNeeded` olay uygulamanız gereken tek olay olabilir. Ek sanal mod olayları, Kullanıcı düzenlemeleri, satır ekleme ve silme gibi belirli işlevleri ve satır düzeyi işlemleri yapmanızı sağlar.  
  
 Bazı standart <xref:System.Windows.Forms.DataGridView> olayları (kullanıcılar satır eklerken veya silirse ya da hücre değerleri düzenlendiğinde, ayrıştırıldığında, doğrulandığında veya biçimlendirildiğinde), sanal modda yararlı olduğunda meydana gelen olaylar. Ayrıca, hücre araç Ipucu metni, hücre ve satır hata metni, hücre ve satır kısayol menü verileri ve satır yüksekliği verileri gibi, genellikle bir bağlantılı veri kaynağında depolanmayan değerleri korumanıza olanak sağlayan olayları işleyebilirsiniz.  
  
 Satır düzeyinde bir kayıt kapsamıyla okuma/yazma verilerini yönetmek üzere sanal modu uygulama hakkında daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Hücre düzeyinde bir kayıt kapsamıyla sanal mod uygulayan bir örnek için <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> Özellik Başvurusu konusuna bakın.  
  
 Aşağıdaki olaylar yalnızca <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`olarak ayarlandığında oluşur.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Denetim tarafından görüntülenmek üzere veri önbelleğinden bir hücre değeri almak için kullanılır. Bu olay yalnızca ilişkisiz sütunlardaki hücrelerde oluşur.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Bir hücre için Kullanıcı girişini veri önbelleğine yürütmek üzere denetim tarafından kullanılır. Bu olay yalnızca ilişkisiz sütunlardaki hücrelerde oluşur.<br /><br /> Geçerli değerin denetimde görüntülenmesini sağlamak ve şu anda etkin olan tüm otomatik boyutlandırma modlarını uygulamak için, bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> olay işleyicisi dışında önbelleğe alınmış bir değeri değiştirirken <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> yöntemini çağırın.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Denetim tarafından veri önbelleğinde yeni bir satır gereksinimini göstermek için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Bir satırda kaydedilmemiş değişiklikler olup olmadığını belirlemede denetim tarafından kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Bir satırın önbelleğe alınmış değerlerine dönmesi gerektiğini göstermek için denetim tarafından kullanılır.|  
  
 Aşağıdaki olaylar sanal modda faydalıdır, ancak <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik ayarından bağımsız olarak kullanılabilir.  
  
|Olaylar|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Denetim tarafından, satırların ne zaman silindiğini veya eklendiğini göstermek için kullanılır ve veri önbelleğini buna göre güncelleştirmenizi sağlar.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Denetim tarafından, görüntüleme ve Kullanıcı girişini ayrıştırmak ve doğrulamak için hücre değerlerini biçimlendirmek için kullanılır.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|<xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlandığında veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`olduğunda hücre araç Ipucu metnini almak için denetim tarafından kullanılır.<br /><br /> Hücre araç Ipuçları yalnızca <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> Özellik değeri `true`olduğunda görüntülenir.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|<xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlandığında veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`olduğunda hücre veya satır hata metnini almak için denetim tarafından kullanılır.<br /><br /> Geçerli değerin denetimde görüntülendiğinden emin olmak için hücre veya satır hata metnini değiştirdiğinizde <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> yöntemini veya <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> yöntemini çağırın.<br /><br /> <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> ve <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> özellik değerleri `true`olduğunda hücre ve satır hatası glifleri görüntülenir.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Denetim <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlandığında veya <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`olduğunda bir hücre veya satır almak için denetim tarafından kullanılır <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Denetim tarafından veri önbelleğindeki satır yüksekliği bilgilerini almak veya depolamak için kullanılır. Geçerli değerin denetimin görüntüsüne kullanılmadığından emin olmak için, bir <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> olay işleyicisi dışında önbelleğe alınmış satır yüksekliği bilgilerini değiştirirken <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> yöntemini çağırın.|  
  
## <a name="best-practices-in-virtual-mode"></a>Sanal moddaki en iyi uygulamalar  
 Büyük miktarlarda verilerle verimli bir şekilde çalışmak için sanal modu uyguırdıysanız, <xref:System.Windows.Forms.DataGridView> denetimi ile de verimli bir şekilde çalıştığınızdan emin olmanız gerekir. Hücre stillerinin verimli kullanımı, otomatik boyutlandırma, seçimler ve satır paylaşımı hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetiminin ölçeklendirilmesi Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](implementing-virtual-mode-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
