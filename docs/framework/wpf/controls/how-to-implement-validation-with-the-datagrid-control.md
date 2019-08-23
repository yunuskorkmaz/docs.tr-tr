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
ms.openlocfilehash: 8ae651b3085b39673a51cf8d5f65e9bfb9da87d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962037"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama
<xref:System.Windows.Controls.DataGrid> Denetim, hem hücrede hem de satır düzeyinde doğrulama gerçekleştirmenize olanak sağlar. Hücre düzeyinde doğrulamayla, bir Kullanıcı bir değeri güncelleştiriyorsa, bağlantılı bir veri nesnesinin tek tek özelliklerini doğrularsınız. Satır düzeyinde doğrulamayla, bir Kullanıcı bir satıra değişiklik yaptığı zaman tüm veri nesnelerini doğrularsınız. Ayrıca doğrulama hataları için özelleştirilmiş görsel geri bildirim sağlayabilir veya <xref:System.Windows.Controls.DataGrid> denetimin sağladığı varsayılan görsel geri bildirimini kullanabilirsiniz.  
  
 Aşağıdaki yordamlarda, <xref:System.Windows.Controls.DataGrid> bağlamalara doğrulama kurallarının nasıl uygulanacağı ve görsel geri bildirimin nasıl özelleştirileceği açıklanır.  
  
### <a name="to-validate-individual-cell-values"></a>Bağımsız hücre değerlerini doğrulamak için  
  
- Bir sütunla kullanılan bağlamada bir veya daha fazla doğrulama kuralı belirtin. Bu, [veri bağlamaya genel bakış](../data/data-binding-overview.md)bölümünde açıklandığı gibi basit denetimlerde verileri doğrulamaya benzer.  
  
     Aşağıdaki örnek, bir iş <xref:System.Windows.Controls.DataGrid> nesnesinin farklı özelliklerine sınırlı dört sütunlu bir denetim gösterir. Sütunun üçü, <xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğini olarak `true`ayarlayarak belirler.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Kullanıcı geçersiz bir değer girdiğinde (kurs KIMLIĞI sütununda tamsayı olmayan gibi), hücrenin etrafında kırmızı bir kenarlık görünür. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı gibi değiştirebilirsiniz.  
  
### <a name="to-customize-cell-validation-feedback"></a>Hücre doğrulama geri bildirimini özelleştirmek için  
  
- Sütunun <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> özelliğini sütunun Editing denetimine uygun bir stil olarak ayarlayın. Çalışma zamanında düzenlemenin denetimleri oluşturulduğundan, bu özelliği basit denetimlerle yaptığınız gibi kullanamazsınız <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> .  
  
     Aşağıdaki örnek, doğrulama kurallarına sahip üç sütun tarafından paylaşılan bir hata stili ekleyerek önceki örneği günceller. Kullanıcı geçersiz bir değer girdiğinde, stil hücre arka plan rengini değiştirir ve bir araç Ipucu ekler. Bir doğrulama hatası olup olmadığını anlamak için tetikleyicinin kullanımını aklınızda yapın. Bu, şu anda hücreler için adanmış bir hata şablonu bulunmadığından gereklidir.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Sütunu tarafından <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> kullanılan öğesini değiştirerek daha kapsamlı özelleştirmeler uygulayabilirsiniz.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Tek bir satırdaki birden çok değeri doğrulamak için  
  
1. Bağlanan veri <xref:System.Windows.Controls.ValidationRule> nesnesinin birden çok özelliğini denetleyen bir alt sınıf uygulayın. Yöntem uygulamanızda `value` parametre değerini bir <xref:System.Windows.Data.BindingGroup> örneğe atayın. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Daha sonra, veri nesnesine <xref:System.Windows.Data.BindingGroup.Items%2A> özelliği aracılığıyla erişebilirsiniz.  
  
     Aşağıdaki örnek, bir `StartDate` `Course` nesnenin özellik değerinin özellik değerinden daha önce olup olmadığını doğrulamak için bu işlemi gösterir. `EndDate`  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Doğrulama kuralını <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> koleksiyona ekleyin. Özelliği, denetim tarafından kullanılan tüm bağlamaları <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> gruplandıran bir <xref:System.Windows.Data.BindingGroup> örnek özelliğine doğrudan erişim sağlar. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>  
  
     Aşağıdaki örnek xaml 'de <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> özelliğini ayarlar. Özelliği, doğrulamanın yalnızca bağlantılı <xref:System.Windows.Controls.ValidationStep.UpdatedValue> veri nesnesi güncelleştirildikten sonra oluşması için olarak ayarlanır. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Bir kullanıcı başlangıç tarihinden önceki bir bitiş tarihini belirttiğinde, satır üstbilgisinde kırmızı bir ünlem işareti (!) belirir. Bu varsayılan doğrulama geri bildirimini aşağıdaki yordamda açıklandığı gibi değiştirebilirsiniz.  
  
### <a name="to-customize-row-validation-feedback"></a>Satır doğrulama geri bildirimini özelleştirmek için  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> Özelliği ayarlayın. Bu özellik ayrı <xref:System.Windows.Controls.DataGrid> denetimler için satır doğrulama geri bildirimini özelleştirmenizi sağlar. <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> Özelliği ayarlamak için örtük bir satır stili kullanarak birden çok denetimi de etkileyebilirsiniz.  
  
     Aşağıdaki örnek, varsayılan satır doğrulama geri bildirimini daha görünür bir göstergeyle değiştirir. Kullanıcı geçersiz bir değer girdiğinde, satır üstbilgisinde beyaz ünlem işaretine sahip kırmızı bir daire görünür. Bu durum hem satır hem de hücre doğrulama hataları için oluşur. İlişkili hata iletisi bir araç Ipucunda görüntülenir.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hücre ve satır doğrulama için kapsamlı bir tanıtım sağlar. Sınıfı `Course` , işlemleri desteklemek için uygulayan <xref:System.ComponentModel.IEditableObject> bir örnek veri nesnesi sağlar. Denetim <xref:System.Windows.Controls.DataGrid> , kullanıcıların ESC <xref:System.ComponentModel.IEditableObject> tuşuna basarak değişiklikleri döndürmenize olanak tanımak için ile etkileşime girer.  
  
> [!NOTE]
> Visual Basic kullanıyorsanız, MainWindow. xaml ' in ilk satırında ile `x:Class="DataGridValidation.MainWindow"` `x:Class="MainWindow"`değiştirin.  
  
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
- [Veri Bağlama](../data/data-binding-wpf.md)
- [Bağlama Doğrulaması Uygulama](../data/how-to-implement-binding-validation.md)
- [Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama](../data/how-to-implement-validation-logic-on-custom-objects.md)
