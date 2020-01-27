---
title: DataGridView Denetimindeki yeni kayıtlar için satır kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728341"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma
Uygulamanızdaki verileri düzenlemekte bir <xref:System.Windows.Forms.DataGridView> kullandığınızda genellikle kullanıcılarınıza veri deposuna yeni veri satırları ekleme olanağı vermek isteyeceksiniz. <xref:System.Windows.Forms.DataGridView> denetimi, her zaman son satır olarak gösterilen yeni kayıtlar için bir satır sağlayarak bu işlevselliği destekler. Satır üstbilgisinde bir yıldız işareti (*) simgesiyle işaretlenir. Aşağıdaki bölümlerde, yeni kayıtların etkin olduğu satırla programlama yaparken göz önünde bulundurmanız gereken bazı şeyler ele alınmaktadır.  
  
## <a name="displaying-the-row-for-new-records"></a>Yeni kayıtlar için satırı görüntüleme  
 Yeni kayıtların satırının görüntülenip görüntülenmediğini göstermek için <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliğini kullanın. Bu özelliğin varsayılan değeri `true`.  
  
 Veri kaynağı, denetimin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliğinin ve veri kaynağının <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> özelliğinin her ikisi de `true`ise yeni kayıtlar için satır görüntülenir. `false`, bu durumda satır gösterilmeyecektir.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Varsayılan verilerle satırı yeni kayıtlar için doldurma  
 Kullanıcı yeni kayıtlar için satırı geçerli satır olarak seçtiğinde, <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olayını başlatır.  
  
 Bu olay yeni <xref:System.Windows.Forms.DataGridViewRow> erişim sağlar ve yeni satırı varsayılan verilerle doldurmanıza olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki yeni satırlar Için varsayılan değerleri belirtme](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Satır koleksiyonu  
 Yeni kayıtların satırı <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunda bulunur, ancak iki yönden farklı şekilde davranır:  
  
- Yeni kayıtların satırı, program aracılığıyla <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonundan kaldırılamaz. Bu denendiğinde bir <xref:System.InvalidOperationException> oluşturulur. Kullanıcı yeni kayıtlar için satırı da silemez. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> yöntemi bu satırı <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonundan kaldırmaz.  
  
- Yeni kayıtlar için satırdan sonra satır eklenemez. Bu denendiğinde <xref:System.InvalidOperationException> tetiklenir. Sonuç olarak, yeni kayıtlar için satır her zaman <xref:System.Windows.Forms.DataGridView> denetimindeki son satırdır. Satırları ekleyen <xref:System.Windows.Forms.DataGridViewRowCollection> (<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>ve <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>), yeni kayıtlar için satır olduğunda tüm çağrı ekleme yöntemleri dahili olarak.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Yeni kayıtlar için satır görsel özelleştirmesi  
 Yeni kayıtlar için satır oluşturulduğunda, <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği tarafından belirtilen satırı temel alır. Bu satır için belirtilmeyen herhangi bir hücre stili diğer özelliklerden devralınır. Hücre stili devralma hakkında daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
 Yeni kayıtlar için satırdaki hücrelere görüntülenen ilk değerler her bir hücrenin <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> özelliğinden alınır. <xref:System.Windows.Forms.DataGridViewImageCell>türündeki hücreler için, bu özellik bir yer tutucu görüntüsünü döndürür. Aksi takdirde, bu özellik `null`döndürür. Özel bir değer döndürmek için bu özelliği geçersiz kılabilirsiniz. Ancak, odak yeni kayıtlar için satıra girdiğinde, bu ilk değerler <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> bir olay işleyicisi ile değiştirilebilir.  
  
 Bu satır üst bilgisi için bir ok veya yıldız işareti olan standart simgeler herkese açık bir şekilde gösterilmez. Simgeleri özelleştirmek isterseniz, özel bir <xref:System.Windows.Forms.DataGridViewRowHeaderCell> sınıfı oluşturmanız gerekecektir.  
  
 Standart simgeler, satır üst bilgisi hücresi tarafından kullanılan <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> özelliğini kullanır. Standart simgeler, tamamen görüntülenmesi için yeterli alan yoksa işlenmez.  
  
 Satır üst bilgisi hücresi bir dize değeri kümesine sahipse ve hem metin hem de simge için yeterli alan yoksa, önce simge bırakılır.  
  
## <a name="sorting"></a>Sıralama  
 İlişkisiz modda, Kullanıcı <xref:System.Windows.Forms.DataGridView>içeriğini sıralamış olsa bile, yeni kayıtlar <xref:System.Windows.Forms.DataGridView> sonuna her zaman eklenecektir. Satırı doğru konuma sıralamak için kullanıcının sıralamayı yeniden uygulaması gerekir; Bu davranış, <xref:System.Windows.Forms.ListView> denetimiyle benzerdir.  
  
 Veri bağlı ve sanal modlarda, bir sıralama uygulandığında ekleme davranışı, veri modeli uygulamasına göre değişir. ADO.NET için, satır hemen doğru konuma sıralanır.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Yeni kayıtlar için satırdaki diğer notlar  
 Bu satırın <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> özelliğini `false`olarak ayarlayamazsınız. Bu denendiğinde <xref:System.InvalidOperationException> tetiklenir.  
  
 Yeni kayıtların satırı her zaman seçilmemiş durumunda oluşturulur.  
  
## <a name="virtual-mode"></a>Sanal mod  
 Sanal modu uygulamadıysanız, veri modelinde yeni kayıtlar için bir satır gerektiğinde ve satırın eklenmesi ne zaman geri alınacağı izlemeniz gerekir. Bu işlevin tam uygulanması, veri modeli ve işlem semantiğinin uygulanmasına bağlıdır, örneğin, işleme kapsamının hücre veya satır düzeyinde olup olmadığı. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki sanal mod](virtual-mode-in-the-windows-forms-datagridview-control.md)' a bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme](specify-default-values-for-new-rows-in-the-datagrid.md)
