---
title: "Nasıl yapılır: Bir Yönteme Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45f2a141b09c52085c13803b8d338fdc9eebf135
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="3104e-102">Nasıl yapılır: Bir Yönteme Bağlama</span><span class="sxs-lookup"><span data-stu-id="3104e-102">How to: Bind to a Method</span></span>
<span data-ttu-id="3104e-103">Aşağıdaki örnek, bir yöntemi kullanarak bağlamak gösterilmiştir <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="3104e-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3104e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3104e-104">Example</span></span>  
 <span data-ttu-id="3104e-105">Bu örnekte, `TemperatureScale` bir yönteme sahip bir sınıf `ConvertTemp`, iki parametreyi alır (birini `double` ve aşağıdakilerden birini `enum` türü `TempType)` ve verilen değer bir sıcaklık ölçeğinden diğerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3104e-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="3104e-106">Aşağıdaki örnekte, bir <xref:System.Windows.Data.ObjectDataProvider> örneği oluşturmak için kullanılan `TemperatureScale` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3104e-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="3104e-107">`ConvertTemp` Yöntemi iki belirtilen parametrelerle çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3104e-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="3104e-108">Bir kaynak olarak kullanılabilir bir yöntemdir, sonuçlarını bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3104e-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="3104e-109">Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> , <xref:System.Windows.Controls.ComboBox> yöntemi iki parametre için bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3104e-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="3104e-110">Bu, dönüştürmek için sıcaklık belirtmek için kullanıcıları ve dönüştürmek için sıcaklık ölçek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3104e-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="3104e-111">Unutmayın <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> ayarlanır `true` bağlama biz çünkü <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> özelliği <xref:System.Windows.Data.ObjectDataProvider> örneği ve özellikleri tarafından Sarmalanan nesnesinin <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` nesnesi).</span><span class="sxs-lookup"><span data-stu-id="3104e-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="3104e-112"><xref:System.Windows.Controls.ContentControl.Content%2A> Son <xref:System.Windows.Controls.Label> güncelleştirmeleri kullanıcı içeriğini değiştirdiğinde <xref:System.Windows.Controls.TextBox> ya da seçimini <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="3104e-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="3104e-113">Dönüştürücü `DoubleToString` double alır ve içindeki bir dizeye dönüştürür <xref:System.Windows.Data.IValueConverter.Convert%2A> yönünü (bağlama hedefi bağlama kaynağından olduğu <xref:System.Windows.Controls.TextBox.Text%2A> özelliği) ve dönüştüren bir `string` için bir `double` içinde <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yönü.</span><span class="sxs-lookup"><span data-stu-id="3104e-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="3104e-114">`InvalidationCharacterRule` Olan bir <xref:System.Windows.Controls.ValidationRule> geçersiz karakterler için denetler.</span><span class="sxs-lookup"><span data-stu-id="3104e-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="3104e-115">Kırmızı bir sınır olan varsayılan hata şablonu çevresinde <xref:System.Windows.Controls.TextBox>, giriş değeri double değeri olmadığında kullanıcıları bilgilendirmek için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3104e-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3104e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3104e-116">See Also</span></span>  
 [<span data-ttu-id="3104e-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3104e-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="3104e-118">Sabit Listesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="3104e-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
