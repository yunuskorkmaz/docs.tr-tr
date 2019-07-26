---
title: 'Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401124"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="4269c-102">Nasıl yapılır: Bağımlılık Özelliği için Sahip Türü Ekleme</span><span class="sxs-lookup"><span data-stu-id="4269c-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="4269c-103">Bu örnek, farklı bir tür için kaydedilen Dependency özelliğinin sahibi olarak bir sınıfın nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4269c-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="4269c-104">Bunu yaptığınızda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu ve özellik sistemi, özelliğin ek sahibi olarak sınıfını tanıyabilecektir.</span><span class="sxs-lookup"><span data-stu-id="4269c-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="4269c-105">Sahip olarak eklemek, isteğe bağlı olarak türe özgü meta veriler sağlamak için sınıfın eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4269c-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="4269c-106">Aşağıdaki örnekte, `StateProperty` `MyStateControl` sınıfı tarafından kaydedilen bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="4269c-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="4269c-107">Sınıfı `UnrelatedStateControl` , özellikle, ekleme türü üzerinde olduğu gibi `StateProperty` bağımlılık özelliği için yeni meta verilere izin veren imzayı kullanarak kendisini kullanarak <xref:System.Windows.DependencyProperty.AddOwner%2A> kendi sahibi olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="4269c-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="4269c-108">Özellik için ortak dil çalışma zamanı (CLR) erişimcileri sağlamanız gerektiğine dikkat edin. bunun yanı sıra, sahip olarak eklenmekte [](how-to-implement-a-dependency-property.md) olan sınıfta bağımlılık özellik tanımlayıcısını yeniden kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4269c-108">Notice that you should provide common language runtime (CLR) accessors for the property similar to the example shown in the [Implement a Dependency Property](how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="4269c-109">Sarmalayıcılar olmadan, bağımlılık özelliği, veya <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>kullanılarak programlı erişim perspektifinden çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="4269c-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="4269c-110">Ancak, bu özellik sistem davranışının CLR özellik sarmalayıcılarıyla paralel olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4269c-110">But you typically want to parallel this property-system behavior with the CLR property wrappers.</span></span> <span data-ttu-id="4269c-111">Sarmalayıcılar, bağımlılık özelliğini programlı bir şekilde ayarlamayı kolaylaştırır ve özellikleri öznitelik olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayarlamayı mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4269c-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="4269c-112">Varsayılan meta verileri nasıl geçersiz kılabileceğinizi öğrenmek için bkz. [bir bağımlılık özelliği Için meta verileri geçersiz kılma](how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="4269c-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4269c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4269c-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="4269c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4269c-114">See also</span></span>

- [<span data-ttu-id="4269c-115">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4269c-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="4269c-116">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4269c-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
