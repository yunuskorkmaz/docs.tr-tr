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
ms.openlocfilehash: aead8cbd500262a4cba535fd023dd9701d50257a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086814"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama
<xref:System.Windows.Controls.DataGrid> Denetimi hücre ve satır düzeyinde doğrulama yapmanıza olanak sağlar. Bir kullanıcı bir değer güncelleştirdiğinde hücre düzeyinde doğrulama ile tek bir bağımlı veri nesnesinin özelliklerini doğrulayın. Bir kullanıcı bir satır için değişiklikleri onayladığında ile satır düzeyinde doğrulama, tüm veri nesnelerini doğrulayın. Ayrıca, doğrulama hataları için özelleştirilmiş görsel geri bildirim sağlamak veya varsayılan görsel geri bildirim kullanabilirsiniz, <xref:System.Windows.Controls.DataGrid> denetim sağlar.  
  
 Aşağıdaki yordamlarda, doğrulama kuralları uygulamak açıklanır <xref:System.Windows.Controls.DataGrid> bağlamaları ve görsel geri bildirim özelleştirin.  
  
### <a name="to-validate-individual-cell-values"></a>Tek tek hücre değerlerini doğrulamak için  
  
-   Bir veya daha fazla doğrulama kurallarını içeren bir sütun kullanılan bağlama belirtin. Bu bölümünde anlatıldığı gibi basit denetimler, veri doğrulamaya benzer [Data Binding Overview](../data/data-binding-overview.md).  
  
     Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.DataGrid> farklı bir iş nesnesi özelliklerine bağlı olarak dört sütun denetimi. Üç sütun belirtin <xref:System.Windows.Controls.ExceptionValidationRule> ayarlayarak <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğini `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Bir kullanıcı (örneğin, bir tamsayı olmayan, kurs kimliği sütununda) geçersiz bir değer girdiğinde, hücre etrafında kırmızı bir kenarlık görünür. Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirim değiştirebilirsiniz.  
  
### <a name="to-customize-cell-validation-feedback"></a>Hücre doğrulama geri bildirim özelleştirmek için  
  
-   Sütun kümesi <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> kullanıcının düzenleme denetiminde sütun için bir stil özelliğini uygun. Çalışma zamanında düzenleme denetimleri oluşturduğundan kullanamazsınız <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli ile basit denetimler gibi özellik.  
  
     Aşağıdaki örnek, önceki örnekte doğrulama kuralları ile üç sütun tarafından paylaşılan bir hata stili ekleyerek güncelleştirir. Bir kullanıcı geçersiz bir değer girdiğinde, stili hücre arka plan rengi değişir ve bir araç ipucu ekler. Bir doğrulama hatası olup olmadığını belirlemek için bir tetikleyici kullanımına dikkat edin. Şu anda hücreler için hiçbir özel hata şablonunu olduğundan, bu gereklidir.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Daha kapsamlı özelleştirme değiştirerek uygulayabileceğiniz <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> sütun tarafından kullanılır.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Birden çok değeri tek bir satır nasıl doğrulamak için  
  
1.  Uygulama bir <xref:System.Windows.Controls.ValidationRule> bağlanan veri nesnesi birden çok özellikleri denetleyen alt sınıfı. İçinde <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntem uygulaması, cast `value` parametre değeri bir <xref:System.Windows.Data.BindingGroup> örneği. Veri nesnesi aracılığıyla erişebiliyorsa <xref:System.Windows.Data.BindingGroup.Items%2A> özelliği.  
  
     Aşağıdaki örnek, doğrulamak için bu işlemi göstermektedir olmadığını `StartDate` için özellik değeri bir `Course` nesnedir öncesi kendi `EndDate` özellik değeri.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Doğrulama kuralı ekleme <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> koleksiyonu. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Özelliği doğrudan erişim sağlayan <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> özelliği bir <xref:System.Windows.Data.BindingGroup> denetim tarafından kullanılan tüm bağlamaları grupları örneği.  
  
     Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML özelliği. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Özelliği <xref:System.Windows.Controls.ValidationStep.UpdatedValue> böylece doğrulama bağlanan veri nesnesi yalnızca güncelleştirildikten sonra oluşur.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Bir kullanıcı bir bitiş tarihi başlangıç tarihinden önceki belirttiğinde, kırmızı bir ünlem işareti (!) satır üst bilgisi görünür. Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirim değiştirebilirsiniz.  
  
### <a name="to-customize-row-validation-feedback"></a>Satır doğrulama geri bildirim özelleştirmek için  
  
-   Ayarlama <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği. Bu özellik tek satır doğrulama geri bildirim özelleştirmenize olanak tanıyan <xref:System.Windows.Controls.DataGrid> kontrol eder. Ayarlanacak bir örtük satır stili kullanarak birden çok denetim etkileyebilir <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği.  
  
     Aşağıdaki örnek, varsayılan satır doğrulama geri bildirim ile daha görünür bir gösterge değiştirir. Bir kullanıcı geçersiz bir değer girdiğinde, satır üst bilgisi içinde beyaz bir ünlem işareti bulunan kırmızı bir daire görünür. Bu, hem satır hem de hücre doğrulama hataları ortaya çıkar. Bir araç ipucunda ilişkili hata iletisi görüntülenir.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hücre ve satır doğrulama için eksiksiz bir örnek sağlar. `Course` SAX uygulayan örnek bir veri nesnesi <xref:System.ComponentModel.IEditableObject> işlemleri desteklemek için. <xref:System.Windows.Controls.DataGrid> Denetim ile etkileşime <xref:System.ComponentModel.IEditableObject> kullanıcıların ESC tuşuna basarak değişiklikleri geri almak için.  
  
> [!NOTE]
>  Visual Basic kullanıyorsanız MainWindow.xaml öğesinin ilk satırı değiştirin `x:Class="DataGridValidation.MainWindow"` ile `x:Class="MainWindow"`.  
  
 Doğrulama test etmek için aşağıdakileri deneyin:  
  
-   Kurs Kimlik sütununda tamsayı olmayan bir değer girin.  
  
-   Son tarih sütununa, başlangıç tarihinden önceki bir tarihi girin.  
  
-   Kurs kimliği, başlangıç tarihi veya bitiş tarihi değeri silin.  
  
-   Geçersiz bir hücre değerini geri hücreye geri imleci yerleştirin ve ESC tuşuna basın.  
  
-   Geçerli bir hücre düzenleme modunda olduğunda satırın tamamını değişiklikleri geri almak için ESC tuşuna iki kez basın.  
  
-   Bir doğrulama hatası oluştuğunda, ilişkili hata iletisini görmek için satır üst bilgisi göstergeyi fare işaretçinizi üzerine getirin.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Veri Bağlama](../data/data-binding-wpf.md)
- [Bağlama Doğrulaması Uygulama](../data/how-to-implement-binding-validation.md)
- [Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama](../data/how-to-implement-validation-logic-on-custom-objects.md)
