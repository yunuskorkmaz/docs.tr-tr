---
title: 'Nasıl yapılır: Bağımlılık Özelliği Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757462"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="0b0df-102">Nasıl yapılır: Bağımlılık Özelliği Uygulama</span><span class="sxs-lookup"><span data-stu-id="0b0df-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="0b0df-103">Bu örnek nasıl yedekleneceği gösterir bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliğiyle bir <xref:System.Windows.DependencyProperty> alan, bu nedenle bir bağımlılık özelliği tanımlama.</span><span class="sxs-lookup"><span data-stu-id="0b0df-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="0b0df-104">Ne zaman kendi özelliklerini tanımlayın ve bunların birçok yönden desteklemek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stilleri, veri bağlama, devralma, animasyon ve varsayılan değerleri dahil işlevleri, bir bağımlılık özelliği olarak uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b0df-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b0df-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b0df-105">Example</span></span>  
 <span data-ttu-id="0b0df-106">Bağımlılık özelliği ilk kaydeder çağırarak aşağıdaki örnekte <xref:System.Windows.DependencyProperty.Register%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b0df-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="0b0df-107">Adı depolamak için kullandığınız ve bağımlılık özelliği özelliklerini olmalıdır tanımlayıcı alanı adını <xref:System.Windows.DependencyProperty.Name%2A> parçası olarak bağımlılık özelliği için seçtiğiniz <xref:System.Windows.DependencyProperty.Register%2A> çağrı, eklenen dizesiyle `Property`.</span><span class="sxs-lookup"><span data-stu-id="0b0df-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="0b0df-108">Örneğin, bir bağımlılık özelliği ile kaydederseniz bir <xref:System.Windows.DependencyProperty.Name%2A> , `Location`, bağımlılık özelliği için tanımladığınız tanımlayıcı alanı adlandırılmalıdır `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="0b0df-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="0b0df-109">Bu örnekte, bağımlılık özelliği adı ve kendi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişimcisi `State`; tanımlayıcı alanı `StateProperty`; özellik türü <xref:System.Boolean>; ve bağımlılık özelliği kaydeden türü `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="0b0df-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="0b0df-110">Şu adlandırma desenini izler yapamazsanız, tasarımcılar, özelliği doğru şekilde rapor edemeyebilir ve bazı yönlerini özelliği sistem stil uygulama beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0b0df-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="0b0df-111">Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0df-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="0b0df-112">Bu örnekte varsayılan değerini kaydeder `State` bağımlılık özellik `false`.</span><span class="sxs-lookup"><span data-stu-id="0b0df-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="0b0df-113">Hakkında daha fazla bilgi ve neden yalnızca yedekleme aksine, bir bağımlılık özelliği uygulama için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özel bir alan özelliğine bakın [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0b0df-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0df-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b0df-114">See also</span></span>

- [<span data-ttu-id="0b0df-115">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0b0df-115">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="0b0df-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0b0df-116">How-to Topics</span></span>](properties-how-to-topics.md)
