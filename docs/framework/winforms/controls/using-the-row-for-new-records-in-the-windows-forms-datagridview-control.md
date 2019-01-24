---
title: Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 86e61afd0882fea9015cdfe3b40e6d3cd329391b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734967"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma
Kullandığınızda, bir <xref:System.Windows.Forms.DataGridView> uygulamanızdaki verileri düzenlemek için genellikle, kullanıcılarınızın veri deposuna veri yeni satır ekleme olanağı sağlayacak istersiniz. <xref:System.Windows.Forms.DataGridView> Denetimi, bir satır yeni kayıtlar için her zaman son satır gösterilen sağlayarak bu işlevselliği destekler. Kendi satır üst bilgisi olarak bir yıldız işareti (*) simgesiyle işaretlenir. Aşağıdaki bölümlerde yeni kayıtlar için satır programla etkin olduğunda dikkate almanız gereken şeylerden bazıları açıklanmaktadır.  
  
## <a name="displaying-the-row-for-new-records"></a>Yeni kayıtlar için satır görüntüleme  
 Kullanım <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> yeni kayıtlar için satır görüntülenip görüntülenmeyeceğini belirtmek için özelliği. Bu özelliğin varsayılan değeri `true`.  
  
 Durum veri bağlama için yeni kayıtlar için satır gösterilir, <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> denetimin özellik ve <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> veri kaynağının özelliği olan hem de `true`. Geçerli olduğunda `false` sonra satır gösterilmez.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Varsayılan veri ile yeni kayıtlar için satır doldurma  
 Kullanıcı geçerli satır olarak, yeni kayıtlar için satır seçtiğinde <xref:System.Windows.Forms.DataGridView> denetim harekete geçirirse <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.  
  
 Bu olay yeni erişim sağlayan <xref:System.Windows.Forms.DataGridViewRow> ve yeni satır varsayılan verilerle doldurmak sağlar. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde yeni satırlar için varsayılan değerleri belirtme](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Satır koleksiyonu  
 Yeni kayıtlar için satır içerdiği <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyon ancak davranışını farklı iki yönden:  
  
-   Yeni kayıtlar için satır alanından kaldırılamaz <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyon programlı olarak. Bir <xref:System.InvalidOperationException> bu denenirse oluşturulur. Kullanıcı ayrıca yeni kayıtlar için satır silinemiyor. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> Yöntemi bu satırdan kaldırmaz <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.  
  
-   Hiçbir satır, yeni kayıtlar için satır sonra eklenebilir. Bir <xref:System.InvalidOperationException> bu denenirse tetiklenir. Sonuç olarak yeni kayıtlar için her zaman son satıra satırdır <xref:System.Windows.Forms.DataGridView> denetimi. Yöntemlerde <xref:System.Windows.Forms.DataGridViewRowCollection> satır ekleme —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, ve <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— tüm çağrı ekleme yöntemleri dahili olarak yeni kayıtlar için satır olduğunda.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Yeni kayıtlar için satır Visual özelleştirme  
 Yeni kayıtlar için satır oluşturulduğunda tarafından belirtilen satır bağlı olduğu <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği. Bu satır için belirtilmeyen herhangi bir hücre stilleri, diğer özelliklerden devralınır. Hücre stili devralma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Yeni kayıtlar her hücrenin alınır satır hücrelerde tarafından gösterilen ilk değerleri <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> özelliği. Hücreleri türü <xref:System.Windows.Forms.DataGridViewImageCell>, bu özellik, bir yer tutucu resminin döndürür. Aksi takdirde, bu özellik döndürür `null`. Özel bir değer döndürmek için bu özellik geçersiz kılabilirsiniz. Ancak, bu ilk değerleri tarafından değiştirilebilir bir <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> odak yeni kayıtlar için satır girdiğinde olay işleyicisi.  
  
 Bu satırın üst bilgi, bir ok ya da bir yıldız işareti olan standart simgelerini herkese açık şekilde gösterilmez. Simgeleri özelleştirmek istiyorsanız, özel bir oluşturmanız gerekecektir <xref:System.Windows.Forms.DataGridViewRowHeaderCell> sınıfı.  
  
 Standart simgeleri kullanın <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> satır üst bilgi hücresini tarafından kullanılıyor. Tamamını görüntülemek için yeterli alan yoksa, standart simgeleri işlenmez.  
  
 Simgesi, ilk satırı üst bilgi hücresini kümesi bir dize değeri varsa ve hem metin hem de simge için yeterli alan yoksa, bırakılır.  
  
## <a name="sorting"></a>Sıralama  
 Bağlantısız modda, yeni kayıtlar her zaman sonuna eklenecek <xref:System.Windows.Forms.DataGridView> kullanıcı içeriğini sıralanmış olsa bile <xref:System.Windows.Forms.DataGridView>. Kullanıcı sıralama satır doğru konuma sıralamak için yeniden uygulamanız gerekir; Bu benzer, davranıştır <xref:System.Windows.Forms.ListView> denetimi.  
  
 Veri ilişkili ve sanal modda bir sıralama uygulandığında ekleme davranışını ve veri modelinin uygulamasına bağımlı olacaktır. İçin [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], satırın doğru konumda hemen sıralanır.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Yeni kayıtlar için satır ilgili diğer notlar  
 Ayarlayamazsınız <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> özelliği için bu satırın `false`. Bir <xref:System.InvalidOperationException> bu denenirse tetiklenir.  
  
 Yeni kayıtlar için satır, seçili olmayan durumunda her zaman oluşturulur.  
  
## <a name="virtual-mode"></a>Sanal mod  
 Sanal mod uyguluyorsanız, yeni kayıtlar için bir satır veri modeli ve satır eklenmesi geri almak ne zaman gerektiğinde izlemek gerekir. Bu işlevlerin tam uygulama işleme kapsamı bir veya daha fazla satır düzeyinde olup olmadığını uygulamasının veri modeli ve kendi işlem semantiği, örneğin, bağlıdır. Daha fazla bilgi için [Windows Forms DataGridView denetiminde sanal mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Veri Girişi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde yeni satırlar için varsayılan değerleri belirtme](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
