---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
description: Windows Presentation Foundation (WPF) içinde geçersiz bir değer girildiğinde kullanıcıya görsel geri bildirim sağlamak için bağlama doğrulaması kullanmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617888"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="5c985-103">Nasıl yapılır: Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="5c985-103">How to: Implement Binding Validation</span></span>

<span data-ttu-id="5c985-104">Bu örnek <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> , bir özel doğrulama kuralına bağlı olarak geçersiz bir değer girildiğinde kullanıcıya bilgilendirmek için görsel geribildirim sağlamak üzere bir ve stil tetikleyicisinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c985-104">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="5c985-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c985-105">Example</span></span>

<span data-ttu-id="5c985-106">Aşağıdaki örnekteki öğesinin metin içeriği <xref:System.Windows.Controls.TextBox> `Age` adlı bir bağlama kaynak nesnesinin özelliğine (int türünde) bağlanır `ods` .</span><span class="sxs-lookup"><span data-stu-id="5c985-106">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="5c985-107">Bağlama, `AgeRangeRule` Kullanıcı sayısal olmayan karakterler veya 21 ' den daha küçük bir değer girerse veya 130 ' den büyük bir değer girerse, metin kutusunun yanında kırmızı bir ünlem işareti ve Kullanıcı fareyi metin kutusunun üzerine taşırken hata iletisiyle birlikte bir araç ipucu görünür.</span><span class="sxs-lookup"><span data-stu-id="5c985-107">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="5c985-108">Aşağıdaki örnek `AgeRangeRule` , öğesinden devralan <xref:System.Windows.Controls.ValidationRule> ve geçersiz kılacak öğesinin uygulamasını gösterir <xref:System.Windows.Controls.ValidationRule.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="5c985-108">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="5c985-109">`Int32.Parse`Yöntemi, geçersiz karakter içermediğinden emin olmak için değer üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5c985-109">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="5c985-110"><xref:System.Windows.Controls.ValidationRule.Validate%2A>Yöntemi, bir <xref:System.Windows.Controls.ValidationResult> özel durumun ayrıştırma sırasında yakalanıp yakalanmadığını ve yaş değerinin alt ve üst sınırların dışında olup olmadığına bağlı olarak değerin geçerli olup olmadığını belirten bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c985-110">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="5c985-111">Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` kullanıcıya doğrulama hatası bildirmek için kırmızı bir ünlem işareti oluşturan özel bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c985-111">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="5c985-112">Denetim şablonları, bir denetimin görünümünü yeniden tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c985-112">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="5c985-113">Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Controls.ToolTip> hata iletisini gösteren adlı stil kullanılarak oluşturulur `textBoxInError` .</span><span class="sxs-lookup"><span data-stu-id="5c985-113">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="5c985-114">Değeri <xref:System.Windows.Controls.Validation.HasError%2A> ise `true` , tetikleyici geçerli olan araç ipucunu <xref:System.Windows.Controls.TextBox> ilk doğrulama hatasına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5c985-114">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="5c985-115">, <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.RelativeSourceMode.Self> Geçerli öğeye başvuran olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c985-115">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="5c985-116">Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="5c985-116">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="5c985-117">Özel bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> doğrulama hatası olduğunda kullanıcıya görsel geri bildirim sağlamak için, özel bir hata şablonu sunmayacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c985-117">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="5c985-118">Daha fazla bilgi için [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5c985-118">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="5c985-119">Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları yakalayan yerleşik bir doğrulama kuralı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c985-119">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="5c985-120">Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="5c985-120">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c985-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c985-121">See also</span></span>

- [<span data-ttu-id="5c985-122">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5c985-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5c985-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5c985-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
