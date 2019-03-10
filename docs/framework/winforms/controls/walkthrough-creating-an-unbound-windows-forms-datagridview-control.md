---
title: 'İzlenecek yol: Bağlantısız bir Windows Forms DataGridView denetimi'
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
ms.openlocfilehash: ebbfeaa2d6a7734aa0f2b214be65e64111d28ac0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708122"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>İzlenecek yol: Bağlantısız bir Windows Forms DataGridView denetimi
Sık veritabanından kaynaklanmayan tablosal verileri görüntülemek isteyebilirsiniz. Örneğin, iki boyutlu bir dizisini içeriğini göstermek isteyebilirsiniz. <xref:System.Windows.Forms.DataGridView> Sınıfı, bir veri kaynağına bağlama olmadan verileri görüntülemek için kolay ve özelleştirilebilir bir yol sağlar. Bu izlenecek yol nasıl doldurulacağını gösterir bir <xref:System.Windows.Forms.DataGridView> denetlemek ve eklenmesini ve "bağlantısız" modda satırların silinmesi yönetin. Varsayılan olarak, kullanıcının yeni bir satır ekleyebilirsiniz. Satır ekleme önleyecek şekilde ayarlanmış <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği `false`.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Bir bağlantısız bir Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>İlişkisiz bir DataGridView denetimi kullanmak için  
  
1.  Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve aşağıdaki değişken bildirimlerini içerir ve `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Uygulama bir `SetupLayout` formunuzun sınıfı tanımında'form düzeni'kurmak için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Oluşturma bir `SetupDataGridView` yöntemi ayarlamak için <xref:System.Windows.Forms.DataGridView> sütun ve özellikler.  
  
     Bu yöntem ilk ekler <xref:System.Windows.Forms.DataGridView> formun denetimine <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu. Ardından, görüntülenecek sütun sayısını kullanılarak ayarlanabilir <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> özelliği. Sütun başlıkları için varsayılan stili ayarlayarak ayarlanır <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, ve <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliklerini <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> özelliği.  
  
     Düzeninin ve görünümünün özelliklerini ayarlayın ve ardından sütun adlarını atanır. Bu yöntem çıktığında <xref:System.Windows.Forms.DataGridView> doldurulacak denetim hazır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Oluşturma bir `PopulateDataGridView` satırlar eklemek için yöntemi <xref:System.Windows.Forms.DataGridView> denetimi.  
  
     Her satır, bir şarkı ve ilişkili bilgilerini temsil eder.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Yerinde yardımcı program yöntemleri ile olay işleyicileri ekleyebilirsiniz.  
  
     Ele alacaksınız **Ekle** ve **Sil** düğmeleri <xref:System.Windows.Forms.Control.Click> olaylar, formun <xref:System.Windows.Forms.Form.Load> olay ve <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellFormatting> olay.  
  
     Zaman **Ekle** düğmenin <xref:System.Windows.Forms.Control.Click> olayı yükseltildiğinde, yeni ve boş bir satır eklenir <xref:System.Windows.Forms.DataGridView>.  
  
     Zaman **Sil** düğmenin <xref:System.Windows.Forms.Control.Click> olayı, kullanıcı sağlayan yeni kayıtlar için satır olduğu sürece yeni satır ekleme seçili satır silindi. Bu satır her zaman son satırda olduğu <xref:System.Windows.Forms.DataGridView> denetimi.  
  
     Formun <xref:System.Windows.Forms.Form.Load> olayı oluşturulur, `SetupLayout`, `SetupDataGridView`, ve `PopulateDataGridView` yardımcı program yöntemleri çağrılır.  
  
     Zaman <xref:System.Windows.Forms.DataGridView.CellFormatting> olayı oluşturulur, her bir hücresinde `Date` sütun hücrenin değeri ayrıştırılamaz sürece bir uzun tarih biçimlendirilmiş.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Uygulamayı çalıştırmak için F5'e basın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> listelenen şarkıya görüntüleyen denetim `PopulateDataGridView`. Yeni satırları ekleyebilirsiniz **Satır Ekle** düğmesi ve seçili satırları silebilirsiniz **Satır Sil** düğmesi. İlişkisiz <xref:System.Windows.Forms.DataGridView> denetimi veri deposu ve verileri gibi herhangi bir dış kaynak bağımsız bir <xref:System.Data.DataSet> veya bir dizi.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamayı size temel bir anlayış <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
-   Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için [nasıl yapılır: Değiştirme kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Etkinleştirmek veya kısıtlamak için kullanıcı girişi <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Kullanıcı girişi için veritabanı ile ilgili hataları kontrol edin. Daha fazla bilgi için [izlenecek yol: Windows veri girişi sırasında oluşan hataları ele alma Forms DataGridView denetiminde](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Çok büyük veri kümeleri ile sanal modu kullanarak işleyin. Daha fazla bilgi için [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Bir bağlantısız bir Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
