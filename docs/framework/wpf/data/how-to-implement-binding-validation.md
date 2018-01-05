---
title: "Nasıl yapılır: Bağlama Doğrulaması Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d57fb099fa364d34b7df5c5fce792eb42079a31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="c8927-102">Nasıl yapılır: Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="c8927-102">How to: Implement Binding Validation</span></span>
<span data-ttu-id="c8927-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve geçersiz bir değer girdiğinizde kullanıcıyı bilgilendirmek üzere görsel geribildirim sağlamak için bir stil tetikleyici dayalı özel bir doğrulama kuralı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c8927-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8927-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8927-104">Example</span></span>  
 <span data-ttu-id="c8927-105">Metin içeriği <xref:System.Windows.Controls.TextBox> aşağıdaki örnekte bağlı `Age` adlı bağlama kaynak nesnesi (int türü) özelliğinin `ods`.</span><span class="sxs-lookup"><span data-stu-id="c8927-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="c8927-106">Adlı bir doğrulama kuralı kullanmak için bağlamayı ayarlamak `AgeRangeRule` böylece kullanıcı sayısal olmayan karakterler veya 21'den küçük veya 130'dan büyük bir değer girerse metin kutusunun yanında kırmızı bir ünlem işareti görünür ve Microsoft hata iletisiyle bir araç ipucu görünür n kullanıcı fare metin kutusunun üzerine taşır.</span><span class="sxs-lookup"><span data-stu-id="c8927-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="c8927-107">Aşağıdaki örnek uygulamasını gösterir `AgeRangeRule`, devralan <xref:System.Windows.Controls.ValidationRule> ve geçersiz kılmalar <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c8927-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="c8927-108">Int32.Parse() yöntemi değeri geçersiz karakterler içermediğinden emin olmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c8927-108">The Int32.Parse() method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="c8927-109"><xref:System.Windows.Controls.ValidationRule.Validate%2A> Yöntemi döndürür bir <xref:System.Windows.Controls.ValidationResult> özel bir durum Ayrıştırma sırasında olup olmadığını belirledi ve geçerlilik değerinin alt ve üst sınırların dışında olup göre değerinin geçerli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8927-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 <span data-ttu-id="c8927-110">Aşağıdaki örnek, özel gösterir <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` bir doğrulama hatası kullanıcıya bildirmek için kırmızı bir ünlem işareti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8927-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="c8927-111">Denetim şablonları, denetimin görünümünü yeniden tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8927-111">Control templates are used to redefine the appearance of a control.</span></span>  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 <span data-ttu-id="c8927-112">Aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Controls.ToolTip> gösteren hata iletisi adlı stil kullanılarak oluşturulan `textBoxInError`.</span><span class="sxs-lookup"><span data-stu-id="c8927-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="c8927-113">Varsa değerini <xref:System.Windows.Controls.Validation.HasError%2A> olan `true`, araç ipucu geçerli tetikleyici ayarlar <xref:System.Windows.Controls.TextBox> için ilk doğrulama hatası.</span><span class="sxs-lookup"><span data-stu-id="c8927-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="c8927-114"><xref:System.Windows.Data.Binding.RelativeSource%2A> Ayarlanır <xref:System.Windows.Data.RelativeSourceMode.Self>geçerli öğe başvuran.</span><span class="sxs-lookup"><span data-stu-id="c8927-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 <span data-ttu-id="c8927-115">Tam bir örnek için bkz: [bağlama doğrulama örnek](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="c8927-115">For the complete example, see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
 <span data-ttu-id="c8927-116">Özel bir sağlamazsanız unutmayın <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bir doğrulama hatası olduğunda kullanıcıya görsel geribildirim sağlamak için varsayılan hata şablonu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c8927-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="c8927-117">"Veri doğrulama" bölümüne bakın [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c8927-117">See "Data Validation" in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="c8927-118">Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynak özelliği güncelleştirme sırasında oluşturulan özel durumları yakalar yerleşik doğrulama kuralı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8927-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="c8927-119">Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="c8927-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8927-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8927-120">See Also</span></span>  
 [<span data-ttu-id="c8927-121">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c8927-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c8927-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c8927-122">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
