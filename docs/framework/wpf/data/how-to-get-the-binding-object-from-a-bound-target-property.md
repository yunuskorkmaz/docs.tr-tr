---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453058"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="fae05-102">Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma</span><span class="sxs-lookup"><span data-stu-id="fae05-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="fae05-103">Bu örnek, bağlama nesnesinin bir veri bağlantılı hedef özelliğinden nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fae05-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="fae05-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fae05-104">Example</span></span>
 <span data-ttu-id="fae05-105"><xref:System.Windows.Data.Binding> nesnesini almak için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fae05-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="fae05-106">Hedef nesnenin birden fazla özelliğinin veri bağlamayı kullanıyor olması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliğini belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fae05-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="fae05-107">Alternatif olarak, <xref:System.Windows.Data.BindingExpression> alabilir ve sonra <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> özelliğinin değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae05-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="fae05-108">Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="fae05-108">For the complete example see [Binding Validation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>

> [!NOTE]
> <span data-ttu-id="fae05-109">Bağlamanız bir <xref:System.Windows.Data.MultiBinding>ise, <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="fae05-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fae05-110"><xref:System.Windows.Data.PriorityBinding>, <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="fae05-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fae05-111">Hedef özelliğin <xref:System.Windows.Data.Binding>, bir <xref:System.Windows.Data.MultiBinding>veya <xref:System.Windows.Data.PriorityBinding>kullanarak bağlanıp bağlanmadığından emin değilseniz, <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae05-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="fae05-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fae05-112">See also</span></span>

- [<span data-ttu-id="fae05-113">Kod İçinde Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fae05-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="fae05-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="fae05-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
