---
title: "Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78846e2b6a1d73e011441b0ccb46b8aad365d5dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="65617-102">Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama</span><span class="sxs-lookup"><span data-stu-id="65617-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="65617-103"><xref:System.Windows.Controls.DataGrid> Denetimi hücre ve satır düzeyinde doğrulama gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="65617-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="65617-104">Bir kullanıcı bir değer güncelleştirdiğinde hücre düzeyi doğrulama ile ilişkili veri nesnesinin ayrı ayrı özellikler doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="65617-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="65617-105">Satır düzeyi doğrulama ile bir kullanıcı için bir satır değişiklikleri onayladığında tüm veri nesnelerini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="65617-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="65617-106">Ayrıca, doğrulama hataları için özelleştirilmiş görsel geribildirim sağlayabilir veya varsayılan görsel geribildirimi kullanabilirsiniz, <xref:System.Windows.Controls.DataGrid> denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="65617-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="65617-107">Aşağıdaki yordamlar doğrulama kurallarının uygulanacağı anlatılmaktadır <xref:System.Windows.Controls.DataGrid> bağlamaları ve görsel geribildirim özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65617-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="65617-108">Tek tek hücre değerlerini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="65617-108">To validate individual cell values</span></span>  
  
-   <span data-ttu-id="65617-109">Sütun ile kullanılan bağlama üzerinde bir veya daha fazla doğrulama kuralları belirtin.</span><span class="sxs-lookup"><span data-stu-id="65617-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="65617-110">Bu bölümünde açıklandığı gibi basit denetimler veri doğrulamaya benzer [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65617-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="65617-111">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.DataGrid> denetimi ile iş nesnesi farklı özelliklerine bağlı dört sütun.</span><span class="sxs-lookup"><span data-stu-id="65617-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="65617-112">Üç sütun belirtin <xref:System.Windows.Controls.ExceptionValidationRule> ayarlayarak <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="65617-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="65617-113">Bir kullanıcı (örneğin, bir tamsayı olmayan indirmelere kimliği sütun) geçersiz bir değer girdiğinde, hücre etrafında kırmızı bir sınır görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65617-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="65617-114">Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirimini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65617-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="65617-115">Hücre doğrulama geribildirimini özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="65617-115">To customize cell validation feedback</span></span>  
  
-   <span data-ttu-id="65617-116">Sütunun ayarlamak <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> stil özelliğine uygun sütun düzenleme denetimine kullanıcının için.</span><span class="sxs-lookup"><span data-stu-id="65617-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="65617-117">Düzenleme denetimleri çalışma zamanında oluşturduğundan kullanamazsınız <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ile basit denetimler gibi özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="65617-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="65617-118">Aşağıdaki örnek, önceki örnekte doğrulama kuralları ile üç sütun tarafından paylaşılan bir hata stili ekleyerek güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="65617-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="65617-119">Bir kullanıcı geçersiz bir değer girdiğinde, stil hücre arka plan rengi değişir ve araç ipucu ekler.</span><span class="sxs-lookup"><span data-stu-id="65617-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="65617-120">Bir doğrulama hatası olup olmadığını belirlemek için bir tetikleyici kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="65617-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="65617-121">Şu anda ayrılmış hiç hata şablonu hücreler için olduğundan, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="65617-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="65617-122">Değiştirerek daha kapsamlı özelleştirme uygulayabilirsiniz <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> sütun tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="65617-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="65617-123">Tek bir satır birden fazla değer doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="65617-123">To validate multiple values in a single row</span></span>  
  
1.  <span data-ttu-id="65617-124">Uygulama bir <xref:System.Windows.Controls.ValidationRule> bağlanan veri nesnesi birden çok özellikleri denetleyen bir alt kümesi.</span><span class="sxs-lookup"><span data-stu-id="65617-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="65617-125">İçinde <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntem uygulaması cast `value` parametre değerini bir <xref:System.Windows.Data.BindingGroup> örneği.</span><span class="sxs-lookup"><span data-stu-id="65617-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="65617-126">Ardından veri nesnesi aracılığıyla erişebilir <xref:System.Windows.Data.BindingGroup.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="65617-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="65617-127">Aşağıdaki örnek doğrulamak için bu işlemi gösterir olup olmadığını `StartDate` için özellik değeri bir `Course` nesnesidir öncesi kendi `EndDate` özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="65617-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <span data-ttu-id="65617-128">Doğrulama kuralı ekleme <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="65617-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="65617-129"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Özelliği doğrudan erişim sağlar <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> özelliği bir <xref:System.Windows.Data.BindingGroup> denetimi tarafından kullanılan tüm bağlamaları grupları örneği.</span><span class="sxs-lookup"><span data-stu-id="65617-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="65617-130">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML'de özelliği.</span><span class="sxs-lookup"><span data-stu-id="65617-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="65617-131"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.ValidationStep.UpdatedValue> böylece yalnızca bağlanan veri nesnesi güncelleştirildikten sonra doğrulama oluşur.</span><span class="sxs-lookup"><span data-stu-id="65617-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="65617-132">Bir kullanıcı bir bitiş tarihi başlangıç tarihinden önce belirttiğinde, kırmızı bir ünlem işareti (!) satır başlığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65617-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="65617-133">Aşağıdaki yordamda açıklandığı gibi bu varsayılan doğrulama geribildirimini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65617-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="65617-134">Satır doğrulama geribildirimini özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="65617-134">To customize row validation feedback</span></span>  
  
-   <span data-ttu-id="65617-135">Ayarlama <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="65617-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="65617-136">Bu özellik için tek tek satır doğrulama geribildirimini özelleştirmenize olanak tanıyan <xref:System.Windows.Controls.DataGrid> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="65617-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="65617-137">Ayarlamak için dolaylı satır stili kullanarak birden çok denetim etkileyebilir <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="65617-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="65617-138">Aşağıdaki örnek, varsayılan satır doğrulama geribildirimini daha görünür bir gösterge ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="65617-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="65617-139">Bir kullanıcı geçersiz bir değer girdiğinde, beyaz ünlem işareti bulunan kırmızı bir daire satır başlığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65617-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="65617-140">Bu, satır ve hücre doğrulama hataları için oluşur.</span><span class="sxs-lookup"><span data-stu-id="65617-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="65617-141">Bir araç ipucunda ilişkili hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65617-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="65617-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="65617-142">Example</span></span>  
 <span data-ttu-id="65617-143">Aşağıdaki örnek, hücre ve satır doğrulama için tam bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="65617-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="65617-144">`Course` SAX uygulayan örnek bir veri nesnesi <xref:System.ComponentModel.IEditableObject> işlemleri desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="65617-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="65617-145"><xref:System.Windows.Controls.DataGrid> Denetim etkileşime <xref:System.ComponentModel.IEditableObject> ESC tuşuna basarak değişiklikleri geri almak kullanıcıların sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="65617-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65617-146">Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="DataGridValidation.MainWindow"` ile `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="65617-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="65617-147">Doğrulama testi için aşağıdakileri deneyin:</span><span class="sxs-lookup"><span data-stu-id="65617-147">To test the validation, try the following:</span></span>  
  
-   <span data-ttu-id="65617-148">İndirmelere Kimlik sütununda tamsayı olmayan değerler girin.</span><span class="sxs-lookup"><span data-stu-id="65617-148">In the Course ID column, enter a non-integer value.</span></span>  
  
-   <span data-ttu-id="65617-149">Bitiş tarihi sütununa başlangıç tarihinden daha erken bir tarih girin.</span><span class="sxs-lookup"><span data-stu-id="65617-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
-   <span data-ttu-id="65617-150">İndirmelere kimliği, başlangıç tarihi veya bitiş tarihi değeri silin.</span><span class="sxs-lookup"><span data-stu-id="65617-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
-   <span data-ttu-id="65617-151">Geçersiz bir hücre değerini geri almak için imleci hücreye geri getirme ve ESC tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65617-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
-   <span data-ttu-id="65617-152">Geçerli hücre düzenleme modunda olduğunda tüm satır değişiklikleri geri almak için ESC tuşuna iki kez basın.</span><span class="sxs-lookup"><span data-stu-id="65617-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
-   <span data-ttu-id="65617-153">Bir doğrulama hatası oluştuğunda, fare işaretçisini ilişkili hata iletisini görmek için Satır üstbilgisi gösterge üzerine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="65617-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="65617-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65617-154">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="65617-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="65617-155">DataGrid</span></span>](../../../../docs/framework/wpf/controls/datagrid.md)  
 [<span data-ttu-id="65617-156">Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="65617-156">Data Binding</span></span>](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [<span data-ttu-id="65617-157">Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="65617-157">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="65617-158">Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama</span><span class="sxs-lookup"><span data-stu-id="65617-158">Implement Validation Logic on Custom Objects</span></span>](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
