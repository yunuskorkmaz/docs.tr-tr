---
title: ComponentResourceKey Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243368"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="e1acc-102">ComponentResourceKey Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="e1acc-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="e1acc-103">Dış derlemelerden yüklenen kaynaklar için anahtarları tanımlar ve başvurur.</span><span class="sxs-lookup"><span data-stu-id="e1acc-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="e1acc-104">Bu, bir aygıtta veya sınıfta açık bir kaynak sözlüğü yerine, bir derlemede hedef türü belirtmek için kaynak araması sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1acc-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="e1acc-105">XAML Öznitelik Kullanımı (ayar tuşu, kompakt)</span><span class="sxs-lookup"><span data-stu-id="e1acc-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="e1acc-106">XAML Öznitelik Kullanımı (ayar tuşu, ayrıntılı)</span><span class="sxs-lookup"><span data-stu-id="e1acc-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="e1acc-107">XAML Öznitelik Kullanımı (kaynak isteyen, kompakt)</span><span class="sxs-lookup"><span data-stu-id="e1acc-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="e1acc-108">XAML Öznitelik Kullanımı (kaynak isteyen, ayrıntılı)</span><span class="sxs-lookup"><span data-stu-id="e1acc-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e1acc-109">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="e1acc-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="e1acc-110">Kaynak derlemesinde tanımlanan ortak ortak dil çalışma zamanı (CLR) türünün adı.</span><span class="sxs-lookup"><span data-stu-id="e1acc-110">The name of the public common language runtime (CLR) type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="e1acc-111">Kaynak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="e1acc-111">The key for the resource.</span></span> <span data-ttu-id="e1acc-112">Kaynaklar arandığında, `targetID` kaynağın [x:Anahtar Yönergesi'ne](../../../desktop-wpf/xaml-services/xkey-directive.md) benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1acc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1acc-113">Remarks</span></span>  
 <span data-ttu-id="e1acc-114">Yukarıdaki kullanımlarda görüldüğü gibi,`ComponentResourceKey`{ } biçimlendirme uzantısı kullanımı iki yerde bulunur:</span><span class="sxs-lookup"><span data-stu-id="e1acc-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
- <span data-ttu-id="e1acc-115">Bir denetim yazarı tarafından sağlanan tema kaynağı sözlüğündeki anahtarın tanımı.</span><span class="sxs-lookup"><span data-stu-id="e1acc-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
- <span data-ttu-id="e1acc-116">Denetimi yeniden ayarladığınız, ancak denetimin temaları tarafından sağlanan kaynaklardan gelen özellik değerlerini kullanmak istediğinizde, derlemeden bir tema kaynağına erişmek.</span><span class="sxs-lookup"><span data-stu-id="e1acc-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="e1acc-117">Temalardan gelen bileşen kaynaklarına başvurmak için genellikle `{DynamicResource}` . `{StaticResource}`</span><span class="sxs-lookup"><span data-stu-id="e1acc-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="e1acc-118">Bu kullanımlarda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-118">This is shown in the usages.</span></span> <span data-ttu-id="e1acc-119">`{DynamicResource}`temanın kendisi kullanıcı tarafından değiştirilebildiği için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="e1acc-120">Denetim yazarının bir temayı destekleme amacıyla en yakından eşleşen bileşen kaynağını istiyorsanız, bileşen kaynak başvurunuzun da dinamik olmasını sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="e1acc-121">Kaynak <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> gerçekte tanımlandığı hedef derlemede var olan bir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1acc-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="e1acc-122">A `ComponentResourceKey` tanımlanabilir ve tam olarak nerede <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandığını bilerek bağımsız olarak kullanılabilir, ancak sonunda başvurulan derlemeler aracılığıyla türü çözmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="e1acc-123">Bunun için <xref:System.Windows.ComponentResourceKey> yaygın bir kullanım, daha sonra bir sınıfın üyeleri olarak ortaya çıkarılan anahtarları tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="e1acc-124">Bu kullanım için biçimlendirme uzantısını <xref:System.Windows.ComponentResourceKey> değil, sınıf oluşturucuyu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e1acc-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="e1acc-125">Daha fazla bilgi <xref:System.Windows.ComponentResourceKey>için, bkz, veya konu Denetim Yazma Genel Bakış "Tema Kaynakları için Tanımlama ve Başvuru Tuşları" bölümüne [bakın.](../controls/control-authoring-overview.md)</span><span class="sxs-lookup"><span data-stu-id="e1acc-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="e1acc-126">Hem anahtar oluşturma hem de anahtarlı kaynaklara başvurma için, öznitelik sözdizimi genellikle `ComponentResourceKey` biçimlendirme uzantısı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="e1acc-127">Gösterilen kompakt sözdizimi, <xref:System.Windows.ComponentResourceKey.%23ctor%2A> biçimlendirme uzantısının oluşturucu imzasını ve konumsal parametre kullanımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="e1acc-128">Verilen `targetTypeName` ve `targetID` verilen sıra önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="e1acc-129">Ayrıntılı sözdizimi <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parametresiz oluşturucuya dayanır ve sonra <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> nesne <xref:System.Windows.ComponentResourceKey.ResourceId%2A> öğesiüzerindeki gerçek öznitelik sözdizimine benzer bir şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1acc-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parameterless constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="e1acc-130">Ayrıntılı sözdiziminde, özelliklerin ayarlandığı sıra önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="e1acc-131">İlişki ve bu iki alternatif mekanizmaları (kompakt ve ayrıntılı) konu [Markup Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="e1acc-132">Teknik olarak, değer `targetID` herhangi bir nesne olabilir, bir dize olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="e1acc-133">Ancak, WPF'de en yaygın `targetID` kullanım, değeri dizeleri olan ve [xamlName Grammar'da](../../../desktop-wpf/xaml-services/xamlname-grammar.md)bu dizeleri geçerli olan formlarla hizalamaktır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="e1acc-134">`ComponentResourceKey`nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="e1acc-135">Bu durumda, uzantıyı düzgün <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> bir <xref:System.Windows.ComponentResourceKey.ResourceId%2A> şekilde başlatmanın hem hem de özelliklerin değerini belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1acc-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="e1acc-136">Okuyucu uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.ComponentResourceKey> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1acc-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="e1acc-137">`ComponentResourceKey`biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="e1acc-138">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="e1acc-139">Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır.</span><span class="sxs-lookup"><span data-stu-id="e1acc-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="e1acc-140">Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)</span><span class="sxs-lookup"><span data-stu-id="e1acc-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1acc-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1acc-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e1acc-142">Denetim Yazımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1acc-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="e1acc-143">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="e1acc-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="e1acc-144">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="e1acc-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
