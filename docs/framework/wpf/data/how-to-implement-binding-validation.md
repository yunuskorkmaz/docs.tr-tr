---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 245b05d9cfa7ca66dec310bd9a5291def0101d19
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459113"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="f0ff8-102">Nasıl yapılır: Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="f0ff8-102">How to: Implement Binding Validation</span></span>

<span data-ttu-id="f0ff8-103">Bu örnek, bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve stil tetikleyicisinin bir özel doğrulama kuralına göre geçersiz bir değer girildiğinde kullanıcıya bilgilendirmek için görsel geribildirim sağlamak üzere nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="f0ff8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0ff8-104">Example</span></span>

<span data-ttu-id="f0ff8-105">Aşağıdaki örnekteki <xref:System.Windows.Controls.TextBox> metin içeriği, `ods`adlı bir bağlama kaynak nesnesinin `Age` özelliğine (int türünde) bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="f0ff8-106">Bağlama, Kullanıcı sayısal olmayan karakterler veya 130 21 ' den daha küçük bir değer girerse `AgeRangeRule` adlı bir doğrulama kuralı kullanmak üzere ayarlanır; Bu durumda, metin kutusunun yanında kırmızı bir ünlem işareti görünür ve hata iletisi  Kullanıcı fareyi metin kutusunun üzerine taşıdıkça.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="f0ff8-107">Aşağıdaki örnek, <xref:System.Windows.Controls.ValidationRule> devralan `AgeRangeRule`uygulamasını gösterir ve <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="f0ff8-108">`Int32.Parse` yöntemi, geçersiz karakter içermediğinden emin olmak için değer üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-108">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="f0ff8-109"><xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi, değerin ayrıştırma sırasında yakalanıp yakalanmadığını ve yaş değerinin alt ve üst sınırların dışında olup olmadığına bağlı olarak değerin geçerli olup olmadığını belirten bir <xref:System.Windows.Controls.ValidationResult> döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="f0ff8-110">Aşağıdaki örnek, kullanıcıya doğrulama hatası bildirmek için kırmızı bir ünlem işareti oluşturan özel <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="f0ff8-111">Denetim şablonları, bir denetimin görünümünü yeniden tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-111">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="f0ff8-112">Aşağıdaki örnekte gösterildiği gibi, hata iletisini gösteren <xref:System.Windows.Controls.ToolTip> `textBoxInError`adlı stil kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="f0ff8-113"><xref:System.Windows.Controls.Validation.HasError%2A> değeri `true`, tetikleyici geçerli <xref:System.Windows.Controls.TextBox> araç ipucunu ilk doğrulama hatasına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="f0ff8-114"><xref:System.Windows.Data.Binding.RelativeSource%2A>, geçerli öğeye başvuran <xref:System.Windows.Data.RelativeSourceMode.Self>olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="f0ff8-115">Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="f0ff8-115">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="f0ff8-116">Özel bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> sağlamazsanız, doğrulama hatası olduğunda kullanıcıya görsel geri bildirim sağlamak için varsayılan hata şablonunun göründüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="f0ff8-117">Daha fazla bilgi için [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-117">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="f0ff8-118">Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları yakalayan yerleşik bir doğrulama kuralı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="f0ff8-119">Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0ff8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0ff8-120">See also</span></span>

- [<span data-ttu-id="f0ff8-121">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f0ff8-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f0ff8-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f0ff8-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
