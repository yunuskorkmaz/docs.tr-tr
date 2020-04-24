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
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646095"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama
Denetim, <xref:System.Windows.Controls.DataGrid> hem hücre hem de satır düzeyinde doğrulama gerçekleştirmenizi sağlar. Hücre düzeyinde doğrulama ile, bir kullanıcı bir değeri güncelleştirdiğinde bağlı bir veri nesnesinin tek tek özelliklerini doğrularsınız. Satır düzeyinde doğrulama ile, bir kullanıcı bir satırdeğişiklikleri taahhüt ettiğinde tüm veri nesneleri doğrular. Ayrıca doğrulama hataları için özelleştirilmiş görsel geri bildirim sağlayabilir veya <xref:System.Windows.Controls.DataGrid> denetimin sağladığı varsayılan görsel geri bildirimi kullanabilirsiniz.  
  
 Aşağıdaki <xref:System.Windows.Controls.DataGrid> yordamlar, bağlamalara doğrulama kurallarının nasıl uygulanacağı ve görsel geri bildirimin nasıl özelleştirilen açıklanmıştır.  
  
### <a name="to-validate-individual-cell-values"></a>Tek tek hücre değerlerini doğrulamak için  
  
- Bir sütunla birlikte kullanılan bağlamaüzerinde bir veya daha fazla doğrulama kuralı belirtin. Bu, [Veri Bağlama Genel Bakışı'nda](../../../desktop-wpf/data/data-binding-overview.md)açıklandığı gibi, basit denetimlerde verileri doğrulamaya benzer.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Controls.DataGrid> bir iş nesnesinin farklı özelliklerine bağlı dört sütunlu bir denetim gösterilmektedir. Sütunlardan <xref:System.Windows.Controls.ExceptionValidationRule> üçü <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği . `true`  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Kullanıcı geçersiz bir değer (Kurs Kimliği sütunundaki tamsayı gibi) girdiğinde, hücrenin çevresinde kırmızı kenarlık görüntülenir. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı şekilde değiştirebilirsiniz.  
  
### <a name="to-customize-cell-validation-feedback"></a>Hücre doğrulama geri bildirimini özelleştirmek için  
  
- Sütunun <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> özelliğini sütunun düzenleme denetimine uygun bir stil olarak ayarlayın. Düzenleme denetimleri çalışma zamanında oluşturulduğundan, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli özelliği basit denetimlerde olduğu gibi kullanamazsınız.  
  
     Aşağıdaki örnek, doğrulama kuralları yla birlikte üç sütun tarafından paylaşılan bir hata stili ekleyerek önceki örneği güncelleştirir. Bir kullanıcı geçersiz bir değer girdiğinde, stil hücre arka planı rengini değiştirir ve bir Araç İpucu ekler. Doğrulama hatası olup olmadığını belirlemek için tetikleyici nin kullanımına dikkat edin. Şu anda hücreler için özel bir hata şablonu olmadığından bu gereklidir.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Sütun tarafından <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> kullanılan değiştirerek daha kapsamlı özelleştirme uygulayabilirsiniz.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Tek bir satırda birden çok değeri doğrulamak için  
  
1. Bağlı <xref:System.Windows.Controls.ValidationRule> veri nesnesinin birden çok özelliklerini denetleyen bir alt sınıf uygulayın. Yöntem <xref:System.Windows.Controls.ValidationRule.Validate%2A> uygulamanızda, `value` parametre değerini bir <xref:System.Windows.Data.BindingGroup> örne atın. Daha sonra özellik üzerinden veri <xref:System.Windows.Data.BindingGroup.Items%2A> nesnesi erişebilirsiniz.  
  
     Aşağıdaki örnek, bir `StartDate` `Course` nesnenin özellik değerinin `EndDate` özellik değerinden önce olup olmadığını doğrulamak için bu işlemi gösterir.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Koleksiyona doğrulama kuralını <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> ekleyin. Özellik, <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> denetim tarafından <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> kullanılan tüm <xref:System.Windows.Data.BindingGroup> bağlamaları gruplayan bir örneğin özelliğine doğrudan erişim sağlar.  
  
     Aşağıdaki örnek, <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML özelliğini ayarlar. Özellik, <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> doğrulamanın <xref:System.Windows.Controls.ValidationStep.UpdatedValue> yalnızca bağlı veri nesnesi güncelleştirildikten sonra gerçekleşmesi için ayarlanır.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Bir kullanıcı başlangıç tarihinden önce bir bitiş tarihi belirttiğinde, satır üstbilgisinde kırmızı bir ünlem işareti (!) görüntülenir. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı şekilde değiştirebilirsiniz.  
  
### <a name="to-customize-row-validation-feedback"></a>Satır doğrulama geri bildirimini özelleştirmek için  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> Özelliği ayarlayın. Bu özellik, tek tek <xref:System.Windows.Controls.DataGrid> denetimler için satır doğrulama geri bildirimini özelleştirmenize olanak tanır. Ayrıca <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği ayarlamak için örtülü bir satır stili kullanarak birden çok denetimi etkileyebilir.  
  
     Aşağıdaki örnekte, varsayılan satır doğrulama geri bildiriminin yerine daha görünür bir gösterge gelir. Kullanıcı geçersiz bir değer girdiğinde, satır üstbilgisinde beyaz ünlem işareti olan kırmızı bir daire görüntülenir. Bu, hem satır hem de hücre doğrulama hataları için oluşur. İlişkili hata iletisi Araç İpucu'nda görüntülenir.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hücre ve satır doğrulama için tam bir gösteri sağlar. Sınıf, `Course` hareketleri desteklemek <xref:System.ComponentModel.IEditableObject> için uygulayan bir örnek veri nesnesi sağlar. Denetim, <xref:System.Windows.Controls.DataGrid> kullanıcıların <xref:System.ComponentModel.IEditableObject> ESC tuşuna basarak değişiklikleri geri almalarını sağlamak için etkileşime girerek.  
  
> [!NOTE]
> Visual Basic kullanıyorsanız, MainWindow.xaml'ın ilk `x:Class="DataGridValidation.MainWindow"` satırında `x:Class="MainWindow"`değiştirin.  
  
 Doğrulamayı test etmek için aşağıdakileri deneyin:  
  
- Ders Kimliği sütununa tamsayı olmayan bir değer girin.  
  
- Bitiş Tarihi sütununa, Başlangıç Tarihi'nden önceki bir tarih girin.  
  
- Kurs Kimliği, Başlangıç Tarihi veya Bitiş Tarihi'ndeki değeri silin.  
  
- Geçersiz hücre değerini geri almak için imleci hücreye geri koyun ve ESC tuşuna basın.  
  
- Geçerli hücre edit modundayken tüm satırdaki değişiklikleri geri almak için ESC tuşuna iki kez basın.  
  
- Doğrulama hatası oluştuğunda, ilişkili hata iletisini görmek için fare işaretçinizi satır üstbilgisindeki göstergenin üzerine taşıyın.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Veri Bağlama](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağlama Doğrulamauygula](../data/how-to-implement-binding-validation.md)
- [Özel Nesnelerde Doğrulama Mantığı Uygulama](../data/how-to-implement-validation-logic-on-custom-objects.md)
