---
title: 'Nasıl yapılır: Bağımlılık Özelliği Uygulama'
description: Bir DependencyProperty alanı ile ortak dil çalışma zamanı özelliğini yedekleyerek Windows Presentation Foundation ' de bir bağımlılık özelliği tanımlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165089"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="d9a13-103">Nasıl yapılır: Bağımlılık Özelliği Uygulama</span><span class="sxs-lookup"><span data-stu-id="d9a13-103">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="d9a13-104">Bu örnek, bir ortak dil çalışma zamanı (CLR) özelliğinin bir alanla nasıl geri alınacağını gösterir <xref:System.Windows.DependencyProperty> ve bu nedenle bir bağımlılık özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9a13-104">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="d9a13-105">Kendi özelliklerinizi tanımladığınızda ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Stiller, veri bağlama, devralma, animasyon ve varsayılan değerler dahil olmak üzere işlevlerin birçok yönlerini desteklemek istiyorsanız, bunları bir bağımlılık özelliği olarak uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d9a13-105">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9a13-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9a13-106">Example</span></span>  
 <span data-ttu-id="d9a13-107">Aşağıdaki örnek öncelikle yöntemini çağırarak bir bağımlılık özelliği kaydeder <xref:System.Windows.DependencyProperty.Register%2A> .</span><span class="sxs-lookup"><span data-stu-id="d9a13-107">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="d9a13-108">Dependency özelliğinin adını ve özelliklerini depolamak için kullandığınız tanımlayıcı alanının adı, <xref:System.Windows.DependencyProperty.Name%2A> çağrının bir parçası olarak <xref:System.Windows.DependencyProperty.Register%2A> , değişmez dize tarafından eklenen bağımlılık özelliği için seçtiğiniz olmalıdır `Property` .</span><span class="sxs-lookup"><span data-stu-id="d9a13-108">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="d9a13-109">Örneğin, ' a bir bağımlılık özelliği kaydettiğinizde <xref:System.Windows.DependencyProperty.Name%2A> `Location` , bağımlılık özelliği için tanımladığınız tanımlayıcı alanın adı olmalıdır `LocationProperty` .</span><span class="sxs-lookup"><span data-stu-id="d9a13-109">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="d9a13-110">Bu örnekte, Dependency özelliğinin adı ve CLR erişimcisi ' dir `State` ; tanımlayıcı alanı, `StateProperty` özelliğin türü <xref:System.Boolean> ve bağımlılık özelliğini kaydeden tür olur `MyStateControl` .</span><span class="sxs-lookup"><span data-stu-id="d9a13-110">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="d9a13-111">Bu adlandırma modelini izlemeden, tasarımcılar özelliği doğru şekilde bildiremeyebilir ve özellik sistem stili uygulamasının belirli yönleri beklendiği gibi davranmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d9a13-111">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="d9a13-112">Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9a13-112">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="d9a13-113">Bu örnek, bağımlılık özelliğinin varsayılan değerini olarak kaydeder `State` `false` .</span><span class="sxs-lookup"><span data-stu-id="d9a13-113">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="d9a13-114">Bir bağımlılık özelliğinin nasıl ve neden uygulanacağı hakkında daha fazla bilgi için, yalnızca bir CLR özelliğinin özel bir alanla yedeklenmesinin aksine, bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9a13-114">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a13-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9a13-115">See also</span></span>

- [<span data-ttu-id="d9a13-116">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9a13-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="d9a13-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d9a13-117">How-to Topics</span></span>](properties-how-to-topics.md)
