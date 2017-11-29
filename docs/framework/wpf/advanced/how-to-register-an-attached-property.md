---
title: "Nasıl yapılır: Ekli Özelliği Kaydetme"
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
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aecb5d2f35b8532ad2ae7558af1a93243b0fd6df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="c14e1-102">Nasıl yapılır: Ekli Özelliği Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c14e1-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="c14e1-103">Bu örnek, iliştirilmiş bir özellik kaydetmek ve böylece özelliği hem de kullanabilirsiniz ortak erişimciler sağlamak gösterilmiştir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.</span><span class="sxs-lookup"><span data-stu-id="c14e1-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="c14e1-104">Ekli özellikler tarafından tanımlanan bir sözdizimi kavramıdır olan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c14e1-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="c14e1-105">İçin çoğu iliştirilmiş özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri bağımlılık özellikleri olarak da uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c14e1-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="c14e1-106">Bağımlılık özellikleri herhangi kullanabilirsiniz <xref:System.Windows.DependencyObject> türleri.</span><span class="sxs-lookup"><span data-stu-id="c14e1-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c14e1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c14e1-107">Example</span></span>  
 <span data-ttu-id="c14e1-108">Aşağıdaki örnek, iliştirilmiş bir özellik kullanarak bağımlılık özelliği olarak kaydettirmek gösterilmiştir <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c14e1-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="c14e1-109">Sağlayıcı sınıf özelliği başka bir sınıf üzerinde kullanıldığında, o sınıfın meta verileri geçersiz kılmadıkça uygulanabilir özellik için varsayılan meta veri sağlama seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="c14e1-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="c14e1-110">Bu örnekte, varsayılan değeri `IsBubbleSource` özelliği ayarlanmış `false`.</span><span class="sxs-lookup"><span data-stu-id="c14e1-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="c14e1-111">Sağlayıcı sınıfı (bağımlılık özelliği olarak kaydedilmemiş olsa bile) iliştirilmiş bir özellik için statik alma ve adlandırma kuralını uyguladığınızdan set erişimcileri sağlamalıdır `Set` *[AttachedPropertyName]* ve `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="c14e1-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="c14e1-112">Bu erişimciler gereklidir şekilde hareket [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu bir öznitelik olarak özellik algılayabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve uygun türleri çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="c14e1-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="c14e1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c14e1-113">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="c14e1-114">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="c14e1-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="c14e1-115">Özel bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="c14e1-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="c14e1-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c14e1-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
