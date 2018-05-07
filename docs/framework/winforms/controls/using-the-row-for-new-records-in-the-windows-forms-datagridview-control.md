---
title: Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: abf62cc9165d74f6bf183e3df30d9a768c0c537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma
Kullandığınızda, bir <xref:System.Windows.Forms.DataGridView> uygulamanızdaki verileri düzenleme için genellikle, kullanıcılarınızın veri deposuna yeni veri satırları ekleme yeteneği vermek istediğiniz. <xref:System.Windows.Forms.DataGridView> Denetimi, bir satır yeni kayıtlar için her zaman son satır olarak gösterilen sağlayarak bu işlevselliği destekler. Satır üstbilgisi içinde bir yıldız işareti (*) simgesiyle işaretlenir. Aşağıdaki bölümlerde, yeni kayıtlar için satır programla etkin olduğunda düşünmelisiniz şeylerden bazıları açıklanmaktadır.  
  
## <a name="displaying-the-row-for-new-records"></a>Yeni kayıtlar için satır görüntüleme  
 Kullanım <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> yeni kayıtlar için satır görüntülenip görüntülenmeyeceğini belirtmek için özelliği. Bu özelliğin varsayılan değeri `true`.  
  
 Durum veri bağlama için yeni kayıtlar için satır gösterilen varsa <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> denetiminin özelliği ve <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> veri kaynağının özelliği olan her ikisi de `true`. Ya da ise `false` satır gösterilmez sonra.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Varsayılan verilerle yeni kayıtlar için satır doldurma  
 Kullanıcı geçerli satır olarak yeni kayıtlar için satır seçtiğinde <xref:System.Windows.Forms.DataGridView> kontrol başlatır <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.  
  
 Bu olay yeni erişim sağlayan <xref:System.Windows.Forms.DataGridViewRow> ve yeni satır varsayılan verilerle doldurmak sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde yeni satırlar için varsayılan değerleri belirtin](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Satır koleksiyonu  
 Yeni kayıtlar için satır içerdiği <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu ancak davranır farklı iki yönden:  
  
-   Yeni kayıtlar için satır kaldırılamaz <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu programlı olarak. Bir <xref:System.InvalidOperationException> bu denenmesi durumunda oluşturulur. Kullanıcı ayrıca yeni kayıtlar için satır silinemiyor. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> Yöntemi bu satırdaki kaldırmaz <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.  
  
-   Yeni kayıtlar için satır sonra satır eklenebilir. Bir <xref:System.InvalidOperationException> bu denenmesi durumunda oluşturulur. Sonuç olarak, yeni kayıtlar için her zaman son satırında satırıdır <xref:System.Windows.Forms.DataGridView> denetim. Yöntemlere <xref:System.Windows.Forms.DataGridViewRowCollection> satırları ekleyin —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, ve <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— tüm çağrı ekleme yöntemleri dahili olarak yeni kayıtlar için satır bulunduğunda.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Yeni kayıtlar için satır görsel özelleştirme  
 Yeni kayıtlar için satır oluşturulduğunda tarafından belirtilen satır bağlı olduğu <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği. Bu satır için belirtilmeyen herhangi hücre stilleri diğer özelliklerinden devralınır. Hücre stili devralma hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Yeni kayıtlar her hücreden 's alınır için satır hücrelerde tarafından görüntülenen ilk değerleri <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> özelliği. Hücreleri türü için <xref:System.Windows.Forms.DataGridViewImageCell>, bu özellik, bir yer tutucu görüntüsünü döndürür. Aksi takdirde, bu özellik döndürür `null`. Özel bir değer döndürmek için bu özelliği geçersiz kılabilirsiniz. Ancak, bu ilk değerleri tarafından değiştirilebilir bir <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> odak yeni kayıtlar için satır girdiğinde olay işleyicisi.  
  
 Olan bir ok ya da bir yıldız işareti, bu satırın üstbilgi standart simgelerini genel olarak açık değildir. Simgeler özelleştirmek istiyorsanız, özel bir oluşturmanız gerekecektir <xref:System.Windows.Forms.DataGridViewRowHeaderCell> sınıfı.  
  
 Standart simgeleri kullanın <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellStyle> satır üst bilgi hücresini tarafından kullanılıyor. Tamamını görüntülemek için yeterli alan yoksa standart simgeler işlenmez.  
  
 Satır üst bilgi hücresini ayarlanmış bir dize değerine sahipse ve metin ve simge için yeterli alan yoksa, simgeyi ilk bırakılır.  
  
## <a name="sorting"></a>Sıralama  
 İlişkisiz modunda yeni kayıtlar her zaman sonuna eklenecek <xref:System.Windows.Forms.DataGridView> kullanıcı içeriğini sıralanmış olsa bile <xref:System.Windows.Forms.DataGridView>. Kullanıcının sıralama satır doğru konuma sıralamak için yeniden uygulamanız gerekir; Bu davranış olarak benzer <xref:System.Windows.Forms.ListView> denetim.  
  
 Veri bağlama ve sanal modları, sıralama uygulandığında ekleme davranışını veri modeli mantığınız bağımlı olur. İçin [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], satırın doğru konumda hemen sıralanır.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Yeni kayıtlar için satır ile ilgili diğer notlar  
 Ayarlayamazsınız <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> özelliği bu satırın `false`. Bir <xref:System.InvalidOperationException> bu denenmesi durumunda oluşturulur.  
  
 Yeni kayıtlar için satır, her zaman seçilmemiş durumunda oluşturulur.  
  
## <a name="virtual-mode"></a>Sanal mod  
 Sanal mod uyguluyorsanız, yeni kayıtlar için bir satır veri modeli ve satır eklenmesi geri almak ne zaman gerektiğinde izlemek gerekir. Bu işlevlerin tam uygulama yürütme kapsam hücre veya satır düzeyinde olup olmadığını veri modeli ve kendi işlem semantikleri uyarlamasını örneğin bağlıdır. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sanal mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetiminde Veri Girişi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
