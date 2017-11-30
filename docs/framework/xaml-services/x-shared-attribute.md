---
title: "x:Shared Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d6a9333b2267e82fc25b2a0ec4bf5dd14f644078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="83037-102">x:Shared Özniteliği</span><span class="sxs-lookup"><span data-stu-id="83037-102">x:Shared Attribute</span></span>
<span data-ttu-id="83037-103">Ayarlandığında `false`, böylece istekleri öznitelikli kaynak için tüm istekler için aynı örneği paylaşmak yerine her istek için yeni bir örnek oluşturmak WPF kaynak alma davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="83037-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="83037-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="83037-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="83037-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83037-105">Remarks</span></span>  
 <span data-ttu-id="83037-106">`x:Shared`XAML dil XAML ad alanına eşlenir ve geçerli bir XAML dil öğesi .NET Framework XAML hizmetlerinde ve XAML okuyucuları tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="83037-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="83037-107">Ancak, belirtilen özellikleri `x:Shared` yalnızca WPF XAML ayrıştırıcısı ve WPF uygulamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="83037-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="83037-108">WPF, `x:Shared` WPF içinde bulunan bir nesnenin uygulandığında yalnızca bir özniteliği olarak yararlıdır <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="83037-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="83037-109">Diğer kullanımlar ayrıştırma özel durumları veya diğer hatalar throw değil, ancak herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="83037-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="83037-110">Anlamını `x:Shared` XAML dil belirtimi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="83037-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="83037-111">.NET Framework XAML hizmetlerinde yapı olanlar gibi diğer XAML uygulamaları kaynak paylaşma destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="83037-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="83037-112">Bu tür XAML uygulamaları da kullanılan destekleyen Framework'te benzer Davranış sağlayabilir `x:Shared` değerleri.</span><span class="sxs-lookup"><span data-stu-id="83037-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="83037-113">WPF'de varsayılan `x:Shared` kaynaklar için koşul `true`.</span><span class="sxs-lookup"><span data-stu-id="83037-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="83037-114">Bu koşul herhangi belirli kaynak isteği her zaman aynı örneğini döndürür anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="83037-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="83037-115">Bir kaynak API gibi döndürülen nesneyi değiştirme <xref:System.Windows.FrameworkElement.FindResource%2A>, veya bir nesne doğrudan içinde değiştirerek bir <xref:System.Windows.ResourceDictionary>, özgün kaynak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="83037-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="83037-116">Bu kaynak başvurular dinamik kaynak başvuruları olsaydı, o kaynak tüketicileri değiştirilen kaynak alın.</span><span class="sxs-lookup"><span data-stu-id="83037-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="83037-117">Kaynak başvuruları statik kaynak başvuruları olsaydı, sonra kaynak değişikliklerini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işleme süresi ilgisiz.</span><span class="sxs-lookup"><span data-stu-id="83037-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="83037-118">Statik dinamik kaynak başvuruları karşılaştırması hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="83037-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="83037-119">Açıkça belirtilmesi `x:Shared="true"` , varsayılan zaten olduğundan nadiren, yapılır.</span><span class="sxs-lookup"><span data-stu-id="83037-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="83037-120">Doğrudan kod için eşdeğer `x:Shared` WPF içinde nesne modeli; yalnızca bir XAML kullanımı belirtilebilir ve varsayılan WPF davranışı tarafından veya bir ara XAML düğümü akışı yükleme yolunda .NET Framework XAML Se kullanarak işlenen işlenmesi gerekir rvices ve XAML okuyucuları.</span><span class="sxs-lookup"><span data-stu-id="83037-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="83037-121">Bir senaryo için `x:Shared="false"` tanımlarsanız, olan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf kaynak olarak ve ardından içerik modeline öğesi kaynak tanıtır.</span><span class="sxs-lookup"><span data-stu-id="83037-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="83037-122">`x:Shared="false"`birden çok kez aynı koleksiyonunda sunulması öğesi kaynak sağlar (gibi bir <xref:System.Windows.Controls.UIElementCollection>).</span><span class="sxs-lookup"><span data-stu-id="83037-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="83037-123">Olmadan `x:Shared="false"` koleksiyonu içeriğinin benzersizliğini zorladığından bu geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="83037-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="83037-124">Ancak, `x:Shared="false"` davranışı aynı örneğini döndüren yerine kaynak aynı başka bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83037-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="83037-125">Başka bir senaryo için `x:Shared="false"` kullanıyorsanız olan bir <xref:System.Windows.Freezable> kaynak animasyon değerlerini ancak animasyon başına temelinde kaynak değiştirmek istiyorum.</span><span class="sxs-lookup"><span data-stu-id="83037-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="83037-126">Dize işlenmesini `false` büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="83037-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="83037-127">WPF, `x:Shared` yalnızca aşağıdaki koşullar altında geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="83037-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="83037-128"><xref:System.Windows.ResourceDictionary> Öğeleri içeren `x:Shared` derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83037-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="83037-129"><xref:System.Windows.ResourceDictionary> Temaları kullanılan veya gevşek XAML içinde olamaz.</span><span class="sxs-lookup"><span data-stu-id="83037-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="83037-130"><xref:System.Windows.ResourceDictionary> Öğeleri içeren içinde başka bir iç içe gerekir değil <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="83037-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="83037-131">Örneğin, kullanamazsınız `x:Shared` öğe için bir <xref:System.Windows.ResourceDictionary> içinde olan bir <xref:System.Windows.Style> zaten olan bir <xref:System.Windows.ResourceDictionary> öğesi.</span><span class="sxs-lookup"><span data-stu-id="83037-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83037-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83037-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="83037-133">XAML kaynakları</span><span class="sxs-lookup"><span data-stu-id="83037-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="83037-134">Temel öğeler</span><span class="sxs-lookup"><span data-stu-id="83037-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
