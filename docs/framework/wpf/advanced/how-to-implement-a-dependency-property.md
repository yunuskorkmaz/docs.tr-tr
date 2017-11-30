---
title: "Nasıl yapılır: Bağımlılık Özelliği Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bc4dee8f0b2eef76e5769ae7da3a13edf7c3300
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="96fb5-102">Nasıl yapılır: Bağımlılık Özelliği Uygulama</span><span class="sxs-lookup"><span data-stu-id="96fb5-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="96fb5-103">Bu örnek nasıl yedekleneceği gösterir bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği ile bir <xref:System.Windows.DependencyProperty> alan, bu nedenle bir bağımlılık özelliği tanımlama.</span><span class="sxs-lookup"><span data-stu-id="96fb5-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="96fb5-104">Ne zaman kendi özelliklerinizi tanımlayın ve bunları pek çok görünüşünün desteklemek için istediğiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] işlevselliği, stiller, veri bağlama, devralma, animasyon ve varsayılan değerleri dahil olmak üzere bir bağımlılık özelliği olarak uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96fb5-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96fb5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="96fb5-105">Example</span></span>  
 <span data-ttu-id="96fb5-106">Bağımlılık özelliği ilk kaydeder çağırarak aşağıdaki örnek <xref:System.Windows.DependencyProperty.Register%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96fb5-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="96fb5-107">Adı depolamak için kullandığınız ve bağımlılık özelliği özelliklerini olmalıdır tanımlayıcı alanı adını <xref:System.Windows.DependencyProperty.Name%2A> bağımlılık özelliği için bir parçası olarak seçtiğiniz <xref:System.Windows.DependencyProperty.Register%2A> dizesiyle eklenmiş çağrı `Property`.</span><span class="sxs-lookup"><span data-stu-id="96fb5-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="96fb5-108">Örneğin, bir bağımlılık özelliği ile kaydederseniz bir <xref:System.Windows.DependencyProperty.Name%2A> , `Location`, bağımlılık özelliği için tanımladığınız tanımlayıcı alanı adlandırılmalıdır `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="96fb5-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="96fb5-109">Bu örnekte, bir bağımlılık özelliğinin adı ve kendi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişen `State`; tanımlayıcı alanı `StateProperty`; özellik türü <xref:System.Boolean>; ve bağımlılık özelliği kaydeder tür `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="96fb5-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="96fb5-110">Bu adlandırma deseni izlemenizi başarısız olursa, tasarımcılar özelliğinizi doğru şekilde rapor edemeyebilir ve özellik sistem stil uygulamasının belirli yönlerini beklendiği gibi davranabilir değil.</span><span class="sxs-lookup"><span data-stu-id="96fb5-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="96fb5-111">Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96fb5-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="96fb5-112">Bu örnek varsayılan değerini kaydeder `State` bağımlılık özellik `false`.</span><span class="sxs-lookup"><span data-stu-id="96fb5-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="96fb5-113">Hakkında daha fazla bilgi ve yalnızca yedekleme aksine, bir bağımlılık özelliği uygulamak neden bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özel bir alanla özelliğine bakın [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96fb5-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96fb5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96fb5-114">See Also</span></span>  
 [<span data-ttu-id="96fb5-115">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="96fb5-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="96fb5-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="96fb5-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
