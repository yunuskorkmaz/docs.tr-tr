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
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400361"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="3023c-102">Nasıl yapılır: Bağımlılık Özelliği Uygulama</span><span class="sxs-lookup"><span data-stu-id="3023c-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="3023c-103">Bu örnek, bir ortak dil çalışma zamanı (CLR) özelliğinin bir <xref:System.Windows.DependencyProperty> alanla nasıl geri alınacağını gösterir ve bu nedenle bir bağımlılık özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3023c-103">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="3023c-104">Kendi özelliklerinizi tanımladığınızda ve stiller, veri bağlama, devralma, animasyon ve varsayılan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] değerler dahil olmak üzere işlevlerin birçok yönlerini desteklemek istiyorsanız, bunları bir bağımlılık özelliği olarak uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3023c-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3023c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3023c-105">Example</span></span>  
 <span data-ttu-id="3023c-106">Aşağıdaki örnek öncelikle <xref:System.Windows.DependencyProperty.Register%2A> yöntemini çağırarak bir bağımlılık özelliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3023c-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="3023c-107">Dependency özelliğinin adını ve özelliklerini depolamak için kullandığınız tanımlayıcı alanının adı, <xref:System.Windows.DependencyProperty.Name%2A> <xref:System.Windows.DependencyProperty.Register%2A> çağrının bir parçası olarak, değişmez dize `Property`tarafından eklenen bağımlılık özelliği için seçtiğiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3023c-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="3023c-108">Örneğin, ' a bir <xref:System.Windows.DependencyProperty.Name%2A> `Location`bağımlılık özelliği kaydettiğinizde, bağımlılık özelliği için tanımladığınız tanımlayıcı alanın adı `LocationProperty`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3023c-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="3023c-109">Bu örnekte, Dependency özelliğinin `State`adı ve clr erişimcisi ' dir; tanımlayıcı alanı, `StateProperty`özelliğin <xref:System.Boolean>türü ve bağımlılık özelliğini `MyStateControl`kaydeden tür olur.</span><span class="sxs-lookup"><span data-stu-id="3023c-109">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="3023c-110">Bu adlandırma modelini izlemeden, tasarımcılar özelliği doğru şekilde bildiremeyebilir ve özellik sistem stili uygulamasının belirli yönleri beklendiği gibi davranmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3023c-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="3023c-111">Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3023c-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="3023c-112">Bu örnek, `State` bağımlılık özelliğinin `false`varsayılan değerini olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3023c-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="3023c-113">Bir bağımlılık özelliğinin nasıl ve neden uygulanacağı hakkında daha fazla bilgi için, yalnızca bir CLR özelliğinin özel bir alanla yedeklenmesinin aksine, bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3023c-113">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3023c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3023c-114">See also</span></span>

- [<span data-ttu-id="3023c-115">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3023c-115">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="3023c-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3023c-116">How-to Topics</span></span>](properties-how-to-topics.md)
