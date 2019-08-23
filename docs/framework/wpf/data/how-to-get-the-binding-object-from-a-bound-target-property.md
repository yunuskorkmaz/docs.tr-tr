---
title: 'Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965430"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="30c08-102">Nasıl yapılır: Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma</span><span class="sxs-lookup"><span data-stu-id="30c08-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="30c08-103">Bu örnek, bağlama nesnesinin bir veri bağlantılı hedef özelliğinden nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30c08-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30c08-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="30c08-104">Example</span></span>  
 <span data-ttu-id="30c08-105"><xref:System.Windows.Data.Binding> Nesneyi almak için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30c08-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> <span data-ttu-id="30c08-106">Hedef nesnenin birden fazla özelliğinin veri bağlamayı kullanıyor olması mümkün olduğundan, istediğiniz bağlama için bağımlılık özelliğini belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="30c08-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="30c08-107">Alternatif olarak, <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> ve daha sonra özelliğin değerini alabilir. <xref:System.Windows.Data.BindingExpression></span><span class="sxs-lookup"><span data-stu-id="30c08-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="30c08-108">Tüm örnek için bkz. [bağlama doğrulama örneği](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="30c08-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30c08-109">Bağlamanız bir <xref:System.Windows.Data.MultiBinding>ise, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>..</span><span class="sxs-lookup"><span data-stu-id="30c08-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="30c08-110">Bir <xref:System.Windows.Data.PriorityBinding>ise, kullanın <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>..</span><span class="sxs-lookup"><span data-stu-id="30c08-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="30c08-111"><xref:System.Windows.Data.Binding>Hedef özelliğin bir<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A> <xref:System.Windows.Data.BindingOperations>,, veya a <xref:System.Windows.Data.PriorityBinding>kullanarak bağlanıp bağlanmadığından emin değilseniz, kullanabilirsiniz... <xref:System.Windows.Data.MultiBinding></span><span class="sxs-lookup"><span data-stu-id="30c08-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c08-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c08-112">See also</span></span>

- [<span data-ttu-id="30c08-113">Kod İçinde Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="30c08-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="30c08-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="30c08-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
