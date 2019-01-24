---
title: 'Nasıl yapılır: Ekli Özelliği Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 71b516a1d181c409fef397b7c959860d47d05b37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608566"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="c9832-102">Nasıl yapılır: Ekli Özelliği Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c9832-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="c9832-103">Bu örnekte, ekli özelliği kaydetme ve böylece özelliği hem de kullanabilirsiniz, ortak erişimciler sağlamak gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.</span><span class="sxs-lookup"><span data-stu-id="c9832-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="c9832-104">Ekli özellikler tarafından tanımlanan bir söz dizimi kavram olan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9832-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="c9832-105">Çoğu iliştirilmiş özellik için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri de bağımlılık özellikleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c9832-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="c9832-106">Bağımlılık özellikleri kullanabilirsiniz herhangi <xref:System.Windows.DependencyObject> türleri.</span><span class="sxs-lookup"><span data-stu-id="c9832-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9832-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9832-107">Example</span></span>  
 <span data-ttu-id="c9832-108">Aşağıdaki örneği kullanarak, bir bağımlılık özelliği ekli özelliği kaydetme işlemi gösterilmektedir <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c9832-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="c9832-109">Sağlayıcı sınıfı özelliği başka bir sınıf üzerinde kullanıldığında, bu sınıfın meta veriler geçersiz kılmadıkça geçerli özelliği için varsayılan meta veri sağlama seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="c9832-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="c9832-110">Bu örnekte, varsayılan değerini `IsBubbleSource` özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="c9832-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="c9832-111">Ekli özelliği (bir bağımlılık özelliği olarak kaydedilmemiş olsa bile) için sağlayıcı sınıfı statik get ve set erişimcileri, adlandırma kuralını uyguladığınızdan sağlamalıdır `Set` *[AttachedPropertyName]* ve `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="c9832-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="c9832-112">Bunlar gerekli şekilde acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu özniteliği olarak özelliği algılayabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve uygun türleri çözümlemek.</span><span class="sxs-lookup"><span data-stu-id="c9832-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="c9832-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9832-113">See also</span></span>
- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="c9832-114">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c9832-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="c9832-115">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c9832-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [<span data-ttu-id="c9832-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c9832-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
