---
title: 'İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: 26c2241f4b0a3b23255de15b3d0c9f8bdd15de02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541160"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma
Sık veritabanından kaynaklanmayan tablo verileri görüntülemek isteyebilirsiniz. Örneğin, iki boyutlu bir dize dizisi içeriğini göster isteyebilirsiniz. <xref:System.Windows.Forms.DataGridView> Sınıfı bir veri kaynağına bağlama olmadan verileri görüntülemek için kolay ve yüksek oranda özelleştirilebilir bir yol sağlar. Bu anlatımda doldurmak nasıl gösterilir bir <xref:System.Windows.Forms.DataGridView> denetlemek ve eklenmesini ve "bağlantısız" modunda satırların silinmesi yönetin. Varsayılan olarak, kullanıcı yeni satırlar ekleyebilirsiniz. Satır ekleme engelleyecek şekilde ayarlanmışsa <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği `false`.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>İlişkisiz bir DataGridView denetimi kullanmak için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve aşağıdaki değişken bildirimlerini içerir ve `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Uygulama bir `SetupLayout` yöntemi, formun sınıf tanımında form düzeni kurmak için.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Oluşturma bir `SetupDataGridView` ayarlamak için yöntemi <xref:System.Windows.Forms.DataGridView> sütunlar ve özellikler.  
  
     Bu yöntem ilk ekler <xref:System.Windows.Forms.DataGridView> formun denetimine <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu. Ardından, görüntülenecek sütun sayısını ayarlanmış <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> özelliği. Sütun üstbilgileri varsayılan stilini ayarlayarak ayarlanır <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, ve <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliklerini <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> özelliği.  
  
     Düzen ve görünüm özelliklerini ayarlayın ve ardından sütun adlarını atanır. Bu yöntem çıktığında <xref:System.Windows.Forms.DataGridView> denetimidir doldurulması için hazır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Oluşturma bir `PopulateDataGridView` satır eklemek için yöntemini <xref:System.Windows.Forms.DataGridView> denetim.  
  
     Her satır bir şarkıyı ve ilişkili bilgilerini temsil eder.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Yerinde yardımcı program yöntemleri ile olay işleyicileri ekleyebilirsiniz.  
  
     İşler mi **Ekle** ve **silmek** düğmeleri <xref:System.Windows.Forms.Control.Click> olaylar, formun <xref:System.Windows.Forms.Form.Load> olayı ve <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellFormatting> olay.  
  
     Zaman **Ekle** düğmenin <xref:System.Windows.Forms.Control.Click> olayı yükseltildiğinde, yeni, boş bir satır eklenir <xref:System.Windows.Forms.DataGridView>.  
  
     Zaman **silmek** düğmenin <xref:System.Windows.Forms.Control.Click> olayı, seçilen satırın silinir, kullanıcı sağlayan yeni kayıtlar için satır olduğu sürece yeni satırlar ekleyin. Bu her zaman son satırında satırıdır <xref:System.Windows.Forms.DataGridView> denetim.  
  
     Formun <xref:System.Windows.Forms.Form.Load> olayı, `SetupLayout`, `SetupDataGridView`, ve `PopulateDataGridView` yardımcı program yöntemleri çağrılır.  
  
     Zaman <xref:System.Windows.Forms.DataGridView.CellFormatting> olayı, her hücrede `Date` sütun hücrenin değeri ayrıştırılamıyor sürece uzun bir tarih olarak biçimlendirilmiş.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> listelenen şarkıya görüntüleyen denetim `PopulateDataGridView`. Yeni satırları ekleyin **Satır Ekle** düğmesi ve seçili satırları silebilirsiniz **Satır Sil** düğmesi. İlişkisiz <xref:System.Windows.Forms.DataGridView> denetim veri deposu ve verileri gibi herhangi bir dış kaynağını bağımsız bir <xref:System.Data.DataSet> veya bir dizi.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
-   Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için bkz: [nasıl yapılır: kenarlık ve kılavuz çizgisi stilleri Windows Forms DataGridView denetiminde değiştirme](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Etkinleştirmek veya kullanıcı girişini kısıtlamak <xref:System.Windows.Forms.DataGridView> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: önlemek satır ekleme ve silme Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Windows Forms DataGridView denetiminde sütunları salt okunur hale](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Kullanıcı girişi veritabanı ile ilgili hataları denetleyin. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetimine veri girişi sırasında bu Occur hataları işleme](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Sanal mod kullanarak çok büyük veri kümeleri işleyin. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için bkz [nasıl yapılır: görünümü hücre Windows Forms DataGridView denetiminde özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: ayarlama varsayılan hücre stilleri Windows Forms DataGridView denetimi için](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
