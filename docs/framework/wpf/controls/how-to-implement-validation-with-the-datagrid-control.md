---
title: 'Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 401949aa4bea924b458a91dc00c454c97aff4895
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458460"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama
<xref:System.Windows.Controls.DataGrid> denetimi hem hücrede hem de satır düzeyinde doğrulama gerçekleştirmenize olanak sağlar. Hücre düzeyinde doğrulamayla, bir Kullanıcı bir değeri güncelleştiriyorsa, bağlantılı bir veri nesnesinin tek tek özelliklerini doğrularsınız. Satır düzeyinde doğrulamayla, bir Kullanıcı bir satıra değişiklik yaptığı zaman tüm veri nesnelerini doğrularsınız. Ayrıca, doğrulama hataları için özelleştirilmiş görsel geri bildirim sağlayabilir veya <xref:System.Windows.Controls.DataGrid> denetiminin sağladığı varsayılan görsel geri bildirimi de kullanabilirsiniz.  
  
 Aşağıdaki yordamlarda, <xref:System.Windows.Controls.DataGrid> bağlamalarına doğrulama kurallarının nasıl uygulanacağı ve görsel geri bildirimin nasıl özelleştirileceği açıklanır.  
  
### <a name="to-validate-individual-cell-values"></a>Bağımsız hücre değerlerini doğrulamak için  
  
- Bir sütunla kullanılan bağlamada bir veya daha fazla doğrulama kuralı belirtin. Bu, [veri bağlamaya genel bakış](../data/data-binding-overview.md)bölümünde açıklandığı gibi basit denetimlerde verileri doğrulamaya benzer.  
  
     Aşağıdaki örnek, bir iş nesnesinin farklı özelliklerine sınırlı dört sütunlu bir <xref:System.Windows.Controls.DataGrid> denetimi gösterir. Sütun üçü, <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğini `true`olarak ayarlayarak <xref:System.Windows.Controls.ExceptionValidationRule> belirtir.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Kullanıcı geçersiz bir değer girdiğinde (kurs KIMLIĞI sütununda tamsayı olmayan gibi), hücrenin etrafında kırmızı bir kenarlık görünür. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı gibi değiştirebilirsiniz.  
  
### <a name="to-customize-cell-validation-feedback"></a>Hücre doğrulama geri bildirimini özelleştirmek için  
  
- Sütunun <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> özelliğini sütunun düzenlenme denetimine uygun bir stil olarak ayarlayın. Çalışma zamanında denetim denetimleri oluşturulduğundan, basit denetimlerde yaptığınız gibi <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli özelliğini kullanamazsınız.  
  
     Aşağıdaki örnek, doğrulama kurallarına sahip üç sütun tarafından paylaşılan bir hata stili ekleyerek önceki örneği günceller. Kullanıcı geçersiz bir değer girdiğinde, stil hücre arka plan rengini değiştirir ve bir araç Ipucu ekler. Bir doğrulama hatası olup olmadığını anlamak için tetikleyicinin kullanımını aklınızda yapın. Bu, şu anda hücreler için adanmış bir hata şablonu bulunmadığından gereklidir.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Sütun tarafından kullanılan <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> değiştirerek daha kapsamlı özelleştirme uygulayabilirsiniz.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Tek bir satırdaki birden çok değeri doğrulamak için  
  
1. Bağlanan veri nesnesinin birden çok özelliğini denetleyen bir <xref:System.Windows.Controls.ValidationRule> alt sınıfı uygulayın. <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi uygulamanızda `value` parametre değerini bir <xref:System.Windows.Data.BindingGroup> örneğine atayın. Daha sonra <xref:System.Windows.Data.BindingGroup.Items%2A> özelliği aracılığıyla veri nesnesine erişebilirsiniz.  
  
     Aşağıdaki örnek, bir `Course` nesnesinin `StartDate` Özellik değerinin `EndDate` özellik değerinden daha önce olup olmadığını doğrulamak için bu işlemi gösterir.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Doğrulama kuralını <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> koleksiyonuna ekleyin. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> özelliği, denetim tarafından kullanılan tüm bağlamaları gruplandıran bir <xref:System.Windows.Data.BindingGroup> örneğinin <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> özelliğine doğrudan erişim sağlar.  
  
     Aşağıdaki örnek, XAML 'de <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> özelliğini ayarlar. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> özelliği, doğrulamanın yalnızca bağlantılı veri nesnesi güncelleştirildikten sonra oluşması için <xref:System.Windows.Controls.ValidationStep.UpdatedValue> olarak ayarlanır.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Bir kullanıcı başlangıç tarihinden önceki bir bitiş tarihini belirttiğinde, satır üstbilgisinde kırmızı bir ünlem işareti (!) belirir. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı gibi değiştirebilirsiniz.  
  
### <a name="to-customize-row-validation-feedback"></a>Satır doğrulama geri bildirimini özelleştirmek için  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> özelliğini ayarlayın. Bu özellik ayrı <xref:System.Windows.Controls.DataGrid> denetimleri için satır doğrulama geri bildirimini özelleştirmenize olanak sağlar. Ayrıca, <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> özelliğini ayarlamak için örtük bir satır stili kullanarak birden çok denetimi de etkileyebilirsiniz.  
  
     Aşağıdaki örnek, varsayılan satır doğrulama geri bildirimini daha görünür bir göstergeyle değiştirir. Kullanıcı geçersiz bir değer girdiğinde, satır üstbilgisinde beyaz ünlem işaretine sahip kırmızı bir daire görünür. Bu durum hem satır hem de hücre doğrulama hataları için oluşur. İlişkili hata iletisi bir araç Ipucunda görüntülenir.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hücre ve satır doğrulama için kapsamlı bir tanıtım sağlar. `Course` sınıfı, işlemleri desteklemek için <xref:System.ComponentModel.IEditableObject> uygulayan bir örnek veri nesnesi sağlar. <xref:System.Windows.Controls.DataGrid> denetimi, kullanıcıların ESC tuşuna basarak değişiklikleri döndürmenize olanak tanımak için <xref:System.ComponentModel.IEditableObject> etkileşime girer.  
  
> [!NOTE]
> Visual Basic kullanıyorsanız, MainWindow. xaml ' in ilk satırında `x:Class="DataGridValidation.MainWindow"` ' yı `x:Class="MainWindow"`ile değiştirin.  
  
 Doğrulamayı test etmek için aşağıdakileri deneyin:  
  
- Kurs KIMLIĞI sütununda, tamsayı olmayan bir değer girin.  
  
- Bitiş tarihi sütununda, başlangıç tarihinden önceki bir tarih girin.  
  
- Kurs KIMLIĞI, başlangıç tarihi veya bitiş tarihi değerlerini silin.  
  
- Geçersiz bir hücre değerini geri almak için imleci hücreye geri koyun ve ESC tuşuna basın.  
  
- Geçerli hücre düzenleme modundayken bir satırın tamamına ait değişiklikleri geri almak için ESC tuşuna iki kez basın.  
  
- Bir doğrulama hatası oluştuğunda, ilişkili hata iletisini görmek için fare işaretçinizi satır üstbilgisindeki göstergenin üzerine taşıyın.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Veri Bağlama](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağlama Doğrulaması Uygulama](../data/how-to-implement-binding-validation.md)
- [Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama](../data/how-to-implement-validation-logic-on-custom-objects.md)
