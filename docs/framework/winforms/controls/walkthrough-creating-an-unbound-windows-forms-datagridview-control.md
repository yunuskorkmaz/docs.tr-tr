---
title: Ilişkisiz bir DataGridView denetimi oluşturma
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
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740180"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma
Genellikle bir veritabanından gelmeyen tablo verilerini göstermek isteyebilirsiniz. Örneğin, iki boyutlu dizeler dizisinin içeriğini göstermek isteyebilirsiniz. <xref:System.Windows.Forms.DataGridView> sınıfı, verileri bir veri kaynağına bağlamasız görüntülemenin kolay ve yüksek düzeyde özelleştirilebilir bir yolunu sağlar. Bu izlenecek yol, bir <xref:System.Windows.Forms.DataGridView> denetiminin nasıl doldurulacağını ve "ilişkisiz" modda satırların eklenmesi ve silinmesini nasıl yöneteceğinizi gösterir. Varsayılan olarak, Kullanıcı yeni satırlar ekleyebilir. Satır eklemeyi engellemek için <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği `false`olarak ayarlayın.  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: ilişkisiz Windows Forms DataGridView denetimi oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>İlişkisiz bir DataGridView denetimini kullanmak için  
  
1. <xref:System.Windows.Forms.Form> türetilen ve aşağıdaki değişken bildirimlerini ve `Main` yöntemini içeren bir sınıf oluşturun.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Formun yerleşimini ayarlamak için formunuzun sınıf tanımına bir `SetupLayout` yöntemi uygulayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. <xref:System.Windows.Forms.DataGridView> sütunları ve özellikleri ayarlamak için bir `SetupDataGridView` yöntemi oluşturun.  
  
     Bu yöntem, önce <xref:System.Windows.Forms.DataGridView> denetimini formun <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonuna ekler. Sonra, görüntülenecek sütun sayısı <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> özelliği kullanılarak ayarlanır. Sütun üst bilgileri için varsayılan stil, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> özelliği tarafından döndürülen <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>ve <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özellikleri ayarlanarak ayarlanır.  
  
     Düzen ve görünüm özellikleri ayarlanır ve ardından sütun adları atanır. Bu yöntem çıktığında <xref:System.Windows.Forms.DataGridView> denetimi doldurulmaya hazırlanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. <xref:System.Windows.Forms.DataGridView> denetimine satır eklemek için bir `PopulateDataGridView` yöntemi oluşturun.  
  
     Her satır bir şarkıyı ve onunla ilişkili bilgileri temsil eder.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Yardımcı program yöntemleriyle olay işleyicileri ekleyebilirsiniz.  
  
     ' <xref:System.Windows.Forms.Control.Click> olaylarını, formun <xref:System.Windows.Forms.Form.Load> olayını ve <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellFormatting> olayını **Ekle** ve **Sil** düğmelerini işleyirsiniz.  
  
     **Add** düğmesinin <xref:System.Windows.Forms.Control.Click> olayı oluşturulduğunda, <xref:System.Windows.Forms.DataGridView>yeni, boş bir satır eklenir.  
  
     **Sil** düğmesinin <xref:System.Windows.Forms.Control.Click> olayı ortaya çıktığında, yeni kayıtlar için satır olmadığı ve kullanıcının yeni satır eklemesini sağlayan seçili satır silinir. Bu satır her zaman <xref:System.Windows.Forms.DataGridView> denetimindeki son satırdır.  
  
     Formun <xref:System.Windows.Forms.Form.Load> olayı ortaya çıktığında, `SetupLayout`, `SetupDataGridView`ve `PopulateDataGridView` yardımcı program yöntemleri çağrılır.  
  
     <xref:System.Windows.Forms.DataGridView.CellFormatting> olayı ortaya çıktığında, hücrenin değeri ayrıştırılamadıkça, `Date` sütunundaki her bir hücre uzun bir tarih olarak biçimlendirilir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu test etmek için  
  
- Uygulamayı çalıştırmak için F5'e basın.  
  
     `PopulateDataGridView`listelenen şarkıları görüntüleyen bir <xref:System.Windows.Forms.DataGridView> denetimi görürsünüz. **Satır ekle** düğmesine sahip yeni satırlar ekleyebilir ve seçili satırları **satırı sil** düğmesi ile silebilirsiniz. İlişkisiz <xref:System.Windows.Forms.DataGridView> denetimi veri deposudur ve verileri, <xref:System.Data.DataSet> veya dizi gibi herhangi bir dış kaynaktan bağımsızdır.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar. <xref:System.Windows.Forms.DataGridView> denetiminin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:  
  
- Kenarlık ve başlık stillerini değiştirin. Daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki sınır ve kılavuz çizgisi stillerini değiştirme](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- <xref:System.Windows.Forms.DataGridView> denetimine Kullanıcı girişini etkinleştirin veya kısıtlayın. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-datagridview.md)ve [Windows Forms DataGridView denetiminde sütunları salt okuma yapma](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Veritabanıyla ilgili hatalar için Kullanıcı girişini denetleyin. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Sanal modu kullanarak çok büyük veri kümelerini işleyin. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Hücrelerin görünümünü özelleştirin. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
