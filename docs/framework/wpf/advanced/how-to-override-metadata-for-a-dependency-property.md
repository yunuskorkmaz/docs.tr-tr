---
title: "Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma"
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
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78d90414d86d06040065ad8ae18a037412723ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a><span data-ttu-id="b5f0f-102">Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="b5f0f-102">How to: Override Metadata for a Dependency Property</span></span>
<span data-ttu-id="b5f0f-103">Bu örnek çağırarak devralınan bir sınıftan gelen varsayılan bağımlılık özelliği meta verileri geçersiz kılmak nasıl gösterir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemi ve türe özgü meta veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-103">This example shows how to override default dependency property metadata that comes from an inherited class, by calling the <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> method and providing type-specific metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f0f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5f0f-104">Example</span></span>  
 <span data-ttu-id="b5f0f-105">Tanımlayarak kendi <xref:System.Windows.PropertyMetadata>, bir sınıf kendi varsayılan değeri ve özellik sistem geri aramaları gibi bağımlılık özelliği davranışlarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-105">By defining its <xref:System.Windows.PropertyMetadata>, a class can define the dependency property's behaviors, such as its default value and property system callbacks.</span></span> <span data-ttu-id="b5f0f-106">Pek çok bağımlılık özelliği sınıfları kendi kayıt işleminin bir parçası belirlenen varsayılan meta verilere zaten var.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-106">Many dependency property classes already have default metadata established as part of their registration process.</span></span> <span data-ttu-id="b5f0f-107">Bu parçası olan bağımlılık özellikleri içerir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f0f-107">This includes the dependency properties that are part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span></span> <span data-ttu-id="b5f0f-108">Böylece meta veriler üzerinden değiştirilebilir özelliği özelliklerini herhangi bir alt kümesi özgü gereksinimler ile eşleşir, sınıf devralma üzerinden bağımlılık özelliğini devralan bir sınıf orijinal meta verileri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-108">A class that inherits the dependency property through its class inheritance can override the original metadata so that the characteristics of the property that can be altered through metadata will match any subclass-specific requirements.</span></span>  
  
 <span data-ttu-id="b5f0f-109">Bağımlılık özelliği üzerinde meta verileri geçersiz kılma (özelliği kaydeden nesnelerin belirli örneklerini örneklenen süre karşılık gelir) özellik sistemi tarafından kullanımda yerleştirilmiş o özellik önce yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-109">Overriding metadata on a dependency property must be done prior to that property being placed in use by the property system (this equates to the time that specific instances of objects that register the property are instantiated).</span></span> <span data-ttu-id="b5f0f-110">Çağrılar <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> olarak kendisini sağlar türü statik oluşturucular içinde gerçekleştirilmelidir `forType` parametresinin <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-110">Calls to <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> must be performed within the static constructors of the type that provides itself as the `forType` parameter of <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span></span> <span data-ttu-id="b5f0f-111">Sahibi türünün örneklerini mevcut sonra meta verileri değiştirmeye çalışırsa, bu özel durumları oluşturmaz, ancak özellik sistemi içinde tutarsız davranışlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-111">If you attempt to change metadata once instances of the owner type exist, this will not raise exceptions, but will result in inconsistent behaviors in the property system.</span></span> <span data-ttu-id="b5f0f-112">Ayrıca, meta veriler yalnızca bir kez başına türü geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-112">Also, metadata can only be overridden once per type.</span></span> <span data-ttu-id="b5f0f-113">Aynı türde meta verilerini geçersiz kılmak için sonraki denemeler bir özel durum oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-113">Subsequent attempts to override metadata on the same type will raise an exception.</span></span>  
  
 <span data-ttu-id="b5f0f-114">Aşağıdaki örnekte, özel bir sınıf `MyAdvancedStateControl` için sağlanan meta verileri geçersiz kılar `StateProperty` tarafından `MyAdvancedStateControl` yeni özellik meta verileri ile.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-114">In the following example, the custom class `MyAdvancedStateControl` overrides the metadata provided for `StateProperty` by `MyAdvancedStateControl` with new property metadata.</span></span> <span data-ttu-id="b5f0f-115">Örneği için varsayılan değeri `StateProperty` artık `true` özelliği sorgulanan zaman yeni oluşturulan üzerinde `MyAdvancedStateControl` örneği.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-115">For instance, the default value of the `StateProperty` is now `true` when the property is queried on a newly constructed `MyAdvancedStateControl` instance.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="b5f0f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f0f-116">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="b5f0f-117">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b5f0f-117">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="b5f0f-118">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b5f0f-118">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="b5f0f-119">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b5f0f-119">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
