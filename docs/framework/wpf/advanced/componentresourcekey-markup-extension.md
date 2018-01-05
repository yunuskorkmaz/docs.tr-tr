---
title: "ComponentResourceKey Biçimlendirme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bfaee35ba9f8cf60deb01c52a142433d08021c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="1f4e8-102">ComponentResourceKey Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="1f4e8-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="1f4e8-103">Tanımlar ve dış derlemelerden yüklenen kaynaklar tuşları başvurur.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="1f4e8-104">Bu, bir derlemeyi ya da bir sınıf bir açık kaynak sözlüğü yerine bir derlemeyi hedef türünü belirtmek bir kaynak arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="1f4e8-105">XAML öznitelik kullanımı (anahtar ayarlama, kısaltılmış)</span><span class="sxs-lookup"><span data-stu-id="1f4e8-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="1f4e8-106">XAML öznitelik (anahtar ayarlama, ayrıntılı) kullanımı</span><span class="sxs-lookup"><span data-stu-id="1f4e8-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="1f4e8-107">XAML öznitelik kullanımı (kaynak isteme, kısaltılmış)</span><span class="sxs-lookup"><span data-stu-id="1f4e8-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="1f4e8-108">XAML öznitelik kullanımı (kaynak isteme, ayrıntılı)</span><span class="sxs-lookup"><span data-stu-id="1f4e8-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1f4e8-109">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="1f4e8-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="1f4e8-110">Ortak ad [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kaynak derlemede tanımlanan türü.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="1f4e8-111">Kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-111">The key for the resource.</span></span> <span data-ttu-id="1f4e8-112">Kaynaklar, arandığı zaman `targetID` benzer olacaktır [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) kaynağının.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f4e8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f4e8-113">Remarks</span></span>  
 <span data-ttu-id="1f4e8-114">Yukarıdaki kullanımları görülen bir {`ComponentResourceKey`} biçimlendirme uzantısı kullanımı iki yerde bulundu:</span><span class="sxs-lookup"><span data-stu-id="1f4e8-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="1f4e8-115">Bir anahtar içerisinde bir denetim yazar tarafından sağlanan bir tema kaynak sözlüğü tanımı.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="1f4e8-116">Bir tema kaynak derlemeden erişme, ne zaman yeniden şablon oluşturma denetimi olan ancak denetimin temalar tarafından sağlanan kaynaklardan gelen özellik değerleri kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="1f4e8-117">Temalardan gelmesi bileşen kaynakları başvurmak için genellikle kullanmanız önerilir `{DynamicResource}` yerine `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="1f4e8-118">Bu kullanımları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-118">This is shown in the usages.</span></span> <span data-ttu-id="1f4e8-119">`{DynamicResource}`kullanıcı tarafından tema değiştirilebildiğinden önerilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="1f4e8-120">Bir tema desteklemek için denetim yazarının hedefi en yakından eşleşen bileşen kaynak isterseniz, bileşeni kaynak başvuru dinamik de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="1f4e8-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Kaynak gerçekte tanımlandığı hedef derlemesinde varolan bir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="1f4e8-122">A `ComponentResourceKey` tanımlanan ve tam olarak bilmeden bağımsız olarak kullanılan nerede <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandı ancak başvurulan derlemeler üzerinden türü çözümlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="1f4e8-123">Bir ortak kullanım <xref:System.Windows.ComponentResourceKey> bir sınıf bir üyesi olarak ardından sunulan anahtarları tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="1f4e8-124">Bu kullanım için kullandığınız <xref:System.Windows.ComponentResourceKey> sınıfı oluşturucusu, biçimlendirme uzantısını değil.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="1f4e8-125">Daha fazla bilgi için bkz: <xref:System.Windows.ComponentResourceKey>, veya "Tanımlama ve başvuran anahtarları için tema kaynaklar" bölümüne [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e8-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="1f4e8-126">Hem anahtarları oluşturma ve başvuru kaynakları anahtarlı için öznitelik sözdizimi için yaygın olarak kullanılır `ComponentResourceKey` biçimlendirme uzantısı.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="1f4e8-127">Kısaltılmış sözdizimi dayanan <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu imza ve biçimlendirme uzantısı konumsal parametre kullanımı.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="1f4e8-128">Hangi sırayla `targetTypeName` ve `targetID` verilir önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="1f4e8-129">Ayrıntılı sözdizimi dayanan <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> varsayılan oluşturucu ve kümelerini <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> nesne öğesindeki doğru öznitelik sözdizimine benzer şekilde.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="1f4e8-130">Ayrıntılı sözdizimi, hangi özellikler ayarlanır sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="1f4e8-131">İlişkileri ve bu iki alternatifleri (kısaltılmış ve ayrıntılı) mekanizmaları açıklanan konusunda daha fazla ayrıntı [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e8-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="1f4e8-132">Teknik olarak, değeri `targetID` bir dize olması gerekmez, herhangi bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="1f4e8-133">Ancak, en yaygın WPF'de hizalamak için kullanımdır `targetID` dizeleri olan ve olduğu gibi dizeleri geçerli forms değerle [XamlName Dilbilgisi](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e8-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="1f4e8-134">`ComponentResourceKey`nesne öğesi sözdiziminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="1f4e8-135">Bu durumda, her ikisi de değerini belirten <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> özellikleri uzantıyı düzgün başlatmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="1f4e8-136">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması işleme için bu biçimlendirme uzantısı tarafından tanımlanan <xref:System.Windows.ComponentResourceKey> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="1f4e8-137">`ComponentResourceKey`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="1f4e8-138">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="1f4e8-139">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="1f4e8-140">Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e8-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4e8-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f4e8-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1f4e8-142">Denetim Yazımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f4e8-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="1f4e8-143">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="1f4e8-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="1f4e8-144">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1f4e8-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
