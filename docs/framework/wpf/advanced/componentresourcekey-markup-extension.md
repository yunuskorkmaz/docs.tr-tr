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
ms.openlocfilehash: 5f72d6c3273cfda4276383cfe72f90196e5d4340
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169760"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="f9d13-102">ComponentResourceKey Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="f9d13-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="f9d13-103">Tanımlar ve dış derlemelerden yüklü olan kaynaklar için anahtarları başvurur.</span><span class="sxs-lookup"><span data-stu-id="f9d13-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="f9d13-104">Bu, bir açık kaynak sözlüğü bir derlemede veya bir sınıf yerine bir derleme bir hedef türü belirtmek bir kaynak araması sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9d13-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="f9d13-105">XAML öznitelik kullanımı (anahtar ayarlama, compact)</span><span class="sxs-lookup"><span data-stu-id="f9d13-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="f9d13-106">XAML öznitelik kullanımı (anahtar ayarlama, ayrıntılı)</span><span class="sxs-lookup"><span data-stu-id="f9d13-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="f9d13-107">XAML öznitelik kullanımı (kaynak isteme, compact)</span><span class="sxs-lookup"><span data-stu-id="f9d13-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="f9d13-108">XAML öznitelik kullanımı (kaynak isteme, ayrıntılı)</span><span class="sxs-lookup"><span data-stu-id="f9d13-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f9d13-109">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="f9d13-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="f9d13-110">Ortak adını [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kaynak derlemesinde tanımlanan tür.</span><span class="sxs-lookup"><span data-stu-id="f9d13-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="f9d13-111">Kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f9d13-111">The key for the resource.</span></span> <span data-ttu-id="f9d13-112">Kaynakları, arandığı zaman `targetID` benzer olacaktır [x: Key yönergesi](../../xaml-services/x-key-directive.md) kaynak.</span><span class="sxs-lookup"><span data-stu-id="f9d13-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9d13-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9d13-113">Remarks</span></span>  
 <span data-ttu-id="f9d13-114">Yukarıdaki kullanımları görüldüğü gibi bir {`ComponentResourceKey`} biçimlendirme uzantısı kullanımı, iki yerde bulunur:</span><span class="sxs-lookup"><span data-stu-id="f9d13-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="f9d13-115">Denetim yazarı tarafından sağlanan bir tema kaynak sözlüğünün içinde bir anahtar tanımı.</span><span class="sxs-lookup"><span data-stu-id="f9d13-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="f9d13-116">Derlemeden bir tema kaynak erişimi ne zaman yeniden şablon oluşturma denetimi olan ancak denetimin temalar tarafından sağlanan kaynaklardan gelen özellik değerlerini kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f9d13-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="f9d13-117">Temalarından gelen bileşen kaynakları başvurmak için genellikle kullanmanız önerilir `{DynamicResource}` yerine `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="f9d13-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="f9d13-118">Bu kullanımları içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-118">This is shown in the usages.</span></span> `{DynamicResource}` <span data-ttu-id="f9d13-119">kullanıcı tarafından tema değiştirilebilmesi için nedeniyle önerilir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-119">is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="f9d13-120">Bir tema desteklemek için denetim yazarının hedefi en yakından eşleşen bileşen kaynak isterseniz, bileşeni kaynak başvurusu'de dinamik olarak etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="f9d13-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Burada kaynak gerçekten tanımlanmış hedef derlemede mevcut bir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9d13-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="f9d13-122">A `ComponentResourceKey` tanımlanabilir ve tam olarak bilerek bağımsız olarak kullanılan burada <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandı, ancak başvurulan derlemeler üzerinden türü çözümlemelidir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="f9d13-123">Bir ortak kullanım <xref:System.Windows.ComponentResourceKey> sonra sunulan anahtarları bir sınıfın üyeleri olarak tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f9d13-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="f9d13-124">Bu kullanım için kullandığınız <xref:System.Windows.ComponentResourceKey> sınıf oluşturucusu, işaretleme uzantısı değil.</span><span class="sxs-lookup"><span data-stu-id="f9d13-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="f9d13-125">Daha fazla bilgi için <xref:System.Windows.ComponentResourceKey>, veya "tanımlama ve başvurma anahtarları için tema kaynaklar" bölümünü konunun [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f9d13-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="f9d13-126">Hem anahtarları oluşturma ve başvuru kaynakları Anahtarlanan için öznitelik sözdizimi için yaygın olarak kullanılır `ComponentResourceKey` işaretleme uzantısı.</span><span class="sxs-lookup"><span data-stu-id="f9d13-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="f9d13-127">Kısaltılmış sözdizimi kullanır <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucu imzası ve bir işaretleme uzantısı konumsal parametresi kullanımı.</span><span class="sxs-lookup"><span data-stu-id="f9d13-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="f9d13-128">Bir sırayı `targetTypeName` ve `targetID` verilen önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="f9d13-129">Ayrıntılı sözdizimi kullanır <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> varsayılan oluşturucu ve kümelerini <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> bir nesne öğesi üzerinde doğru öznitelik sözdizimine benzer bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="f9d13-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="f9d13-130">Ayrıntılı söz dizimi içinde özelliklerini ayarlamak sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="f9d13-131">İlişkileri ve bu iki alternatifleri (kısa ve ayrıntılı) mekanizmaları konusunda daha ayrıntılı açıklanmıştır [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f9d13-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="f9d13-132">Teknik olarak, değeri `targetID` bir dize olması gerekmez, herhangi bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="f9d13-133">Ancak, en yaygın WPF hizalamak için kullanımdır `targetID` dizeleri olan ve burada gibi dizeleri geçerli forms değeriyle [XamlName Dilbilgisi](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="f9d13-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span>  
  
 `ComponentResourceKey` <span data-ttu-id="f9d13-134">nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-134">can be used in object element syntax.</span></span> <span data-ttu-id="f9d13-135">Bu durumda, her ikisi de değerini belirterek <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> özellikler uzantısı düzgün başlatmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="f9d13-136">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.ComponentResourceKey> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f9d13-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 `ComponentResourceKey` <span data-ttu-id="f9d13-137">bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="f9d13-137">is a markup extension.</span></span> <span data-ttu-id="f9d13-138">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f9d13-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f9d13-139">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9d13-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f9d13-140">Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f9d13-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d13-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9d13-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f9d13-142">Denetim Yazımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9d13-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="f9d13-143">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="f9d13-143">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="f9d13-144">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f9d13-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
