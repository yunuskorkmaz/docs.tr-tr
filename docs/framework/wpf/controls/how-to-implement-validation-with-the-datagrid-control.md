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
ms.openlocfilehash: 20fcc8ebafb25e4e4f176447972e7637aaa5cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama
<xref:System.Windows.Controls.DataGrid> Denetimi hücre ve satır düzeyinde doğrulama gerçekleştirmenizi sağlar. Bir kullanıcı bir değer güncelleştirdiğinde hücre düzeyi doğrulama ile ilişkili veri nesnesinin ayrı ayrı özellikler doğrulayın. Satır düzeyi doğrulama ile bir kullanıcı için bir satır değişiklikleri onayladığında tüm veri nesnelerini doğrulayın. Ayrıca, doğrulama hataları için özelleştirilmiş görsel geribildirim sağlayabilir veya varsayılan görsel geribildirimi kullanabilirsiniz, <xref:System.Windows.Controls.DataGrid> denetim sağlar.  
  
 Aşağıdaki yordamlar doğrulama kurallarının uygulanacağı anlatılmaktadır <xref:System.Windows.Controls.DataGrid> bağlamaları ve görsel geribildirim özelleştirebilirsiniz.  
  
### <a name="to-validate-individual-cell-values"></a>Tek tek hücre değerlerini doğrulamak için  
  
-   Sütun ile kullanılan bağlama üzerinde bir veya daha fazla doğrulama kuralları belirtin. Bu bölümünde açıklandığı gibi basit denetimler veri doğrulamaya benzer [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
     Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.DataGrid> denetimi ile iş nesnesi farklı özelliklerine bağlı dört sütun. Üç sütun belirtin <xref:System.Windows.Controls.ExceptionValidationRule> ayarlayarak <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğine `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Bir kullanıcı (örneğin, bir tamsayı olmayan indirmelere kimliği sütun) geçersiz bir değer girdiğinde, hücre etrafında kırmızı bir sınır görüntülenir. Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirimini değiştirebilirsiniz.  
  
### <a name="to-customize-cell-validation-feedback"></a>Hücre doğrulama geribildirimini özelleştirmek için  
  
-   Sütunun ayarlamak <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> stil özelliğine uygun sütun düzenleme denetimine kullanıcının için. Düzenleme denetimleri çalışma zamanında oluşturduğundan kullanamazsınız <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ile basit denetimler gibi özelliği eklenmiş.  
  
     Aşağıdaki örnek, önceki örnekte doğrulama kuralları ile üç sütun tarafından paylaşılan bir hata stili ekleyerek güncelleştirir. Bir kullanıcı geçersiz bir değer girdiğinde, stil hücre arka plan rengi değişir ve araç ipucu ekler. Bir doğrulama hatası olup olmadığını belirlemek için bir tetikleyici kullanımına dikkat edin. Şu anda ayrılmış hiç hata şablonu hücreler için olduğundan, bu gereklidir.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Değiştirerek daha kapsamlı özelleştirme uygulayabilirsiniz <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> sütun tarafından kullanılan.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Tek bir satır birden fazla değer doğrulamak için  
  
1.  Uygulama bir <xref:System.Windows.Controls.ValidationRule> bağlanan veri nesnesi birden çok özellikleri denetleyen bir alt kümesi. İçinde <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntem uygulaması cast `value` parametre değerini bir <xref:System.Windows.Data.BindingGroup> örneği. Ardından veri nesnesi aracılığıyla erişebilir <xref:System.Windows.Data.BindingGroup.Items%2A> özelliği.  
  
     Aşağıdaki örnek doğrulamak için bu işlemi gösterir olup olmadığını `StartDate` için özellik değeri bir `Course` nesnesidir öncesi kendi `EndDate` özellik değeri.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Doğrulama kuralı ekleme <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> koleksiyonu. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Özelliği doğrudan erişim sağlar <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> özelliği bir <xref:System.Windows.Data.BindingGroup> denetimi tarafından kullanılan tüm bağlamaları grupları örneği.  
  
     Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML'de özelliği. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.ValidationStep.UpdatedValue> böylece yalnızca bağlanan veri nesnesi güncelleştirildikten sonra doğrulama oluşur.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Bir kullanıcı bir bitiş tarihi başlangıç tarihinden önce belirttiğinde, kırmızı bir ünlem işareti (!) satır başlığında görüntülenir. Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirimini değiştirebilirsiniz.  
  
### <a name="to-customize-row-validation-feedback"></a>Satır doğrulama geribildirimini özelleştirmek için  
  
-   Ayarlama <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği. Bu özellik için tek tek satır doğrulama geribildirimini özelleştirmenize olanak tanıyan <xref:System.Windows.Controls.DataGrid> kontrol eder. Ayarlamak için dolaylı satır stili kullanarak birden çok denetim etkileyebilir <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği.  
  
     Aşağıdaki örnek, varsayılan satır doğrulama geribildirimini daha görünür bir gösterge ile değiştirir. Bir kullanıcı geçersiz bir değer girdiğinde, beyaz ünlem işareti bulunan kırmızı bir daire satır başlığında görüntülenir. Bu, satır ve hücre doğrulama hataları için oluşur. Bir araç ipucunda ilişkili hata iletisi görüntülenir.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hücre ve satır doğrulama için tam bir örnek sağlar. `Course` SAX uygulayan örnek bir veri nesnesi <xref:System.ComponentModel.IEditableObject> işlemleri desteklemek için. <xref:System.Windows.Controls.DataGrid> Denetim etkileşime <xref:System.ComponentModel.IEditableObject> ESC tuşuna basarak değişiklikleri geri almak kullanıcıların sağlamak için.  
  
> [!NOTE]
>  Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="DataGridValidation.MainWindow"` ile `x:Class="MainWindow"`.  
  
 Doğrulama testi için aşağıdakileri deneyin:  
  
-   İndirmelere Kimlik sütununda tamsayı olmayan değerler girin.  
  
-   Bitiş tarihi sütununa başlangıç tarihinden daha erken bir tarih girin.  
  
-   İndirmelere kimliği, başlangıç tarihi veya bitiş tarihi değeri silin.  
  
-   Geçersiz bir hücre değerini geri almak için imleci hücreye geri getirme ve ESC tuşuna basın.  
  
-   Geçerli hücre düzenleme modunda olduğunda tüm satır değişiklikleri geri almak için ESC tuşuna iki kez basın.  
  
-   Bir doğrulama hatası oluştuğunda, fare işaretçisini ilişkili hata iletisini görmek için Satır üstbilgisi gösterge üzerine taşıyın.  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [Bağlama Doğrulaması Uygulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
