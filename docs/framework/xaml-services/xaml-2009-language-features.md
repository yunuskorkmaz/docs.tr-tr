---
title: "XAML 2009 Dil Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447ba37330e8027d86fd24239a8aca2461dce8d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-2009-language-features"></a><span data-ttu-id="b9e6a-102">XAML 2009 Dil Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b9e6a-102">XAML 2009 Language Features</span></span>
<span data-ttu-id="b9e6a-103">XAML 2009 varolan XAML dil belirtimi genişleten yeni XAML dil özellikleri için toplu terimdir.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-103">XAML 2009 is the shorthand term for new XAML language features that extend the existing XAML language specification.</span></span> <span data-ttu-id="b9e6a-104">XAML 2009 birkaç yeni yönergeleri ve yapıları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-104">XAML 2009 introduces several new directives and constructs.</span></span> <span data-ttu-id="b9e6a-105">Bunlar[x: Arguments yönergesi](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference işaretleme uzantısı](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: TypeArguments yönergesi ](../../../docs/framework/xaml-services/x-typearguments-directive.md); ve ortak dil temelleri için yerleşik türleri (örneğin `x:Char`).</span><span class="sxs-lookup"><span data-stu-id="b9e6a-105">These include the[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md); the [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md); the [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md); the [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md); and built-in types for common language primitives (for example `x:Char`).</span></span>  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a><span data-ttu-id="b9e6a-106">WPF ve Visual Studio XAML 2009 desteği</span><span class="sxs-lookup"><span data-stu-id="b9e6a-106">XAML 2009 Support in WPF and Visual Studio</span></span>  
 <span data-ttu-id="b9e6a-107">WPF'de XAML 2009 özellikleri kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-107">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="b9e6a-108">XAML biçimlendirme derlenmiş ve XAML BAML form, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-108">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>  
  
 <span data-ttu-id="b9e6a-109">WPF gevşek XAML'de yüklenmesi için varolan teknikleri de biçimlendirme derlenmiş XAML için daha kısıtlayıcı daha CLR türlerine ve tür sistemi olası güvenlik ve erişim kısıtlamaları gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-109">Note that existing techniques for loading loose XAML in WPF also have possible security and access restrictions to CLR types and the type system that are more restrictive than for markup-compiled XAML.</span></span> <span data-ttu-id="b9e6a-110">Daha fazla bilgi için bkz: [güvenlik (WPF)](../../../docs/framework/wpf/security-wpf.md) veya [WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="b9e6a-110">For more information, see [Security (WPF)](../../../docs/framework/wpf/security-wpf.md) or [WPF Security Strategy - Platform Security](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
 <span data-ttu-id="b9e6a-111">XAML 2009 ya da önceki XAML 2006 değiştirme ek özellikler de sunar yapıları ya da temel biçimlendirme forms değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-111">XAML 2009 also introduces additional features that either modify the previous XAML 2006 constructs or that modify the basic markup forms.</span></span>  
  
### <a name="xkey-as-an-object-element"></a><span data-ttu-id="b9e6a-112">x: Key Object öğesi olarak</span><span class="sxs-lookup"><span data-stu-id="b9e6a-112">x:Key as an Object Element</span></span>  
 <span data-ttu-id="b9e6a-113">XAML 2009 destekleyebilmesi `x:Key` bir nesne (nesne öğesi değerine sahip bir özellik öğesi); ancak, XAML 2006 yalnızca desteklenen `x:Key` özniteliği olarak.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-113">XAML 2009 can support `x:Key` as an object (a property element that has object element value); however, XAML 2006 only supported `x:Key` as an attribute.</span></span> <span data-ttu-id="b9e6a-114">"XAML 2009" bölümüne bakın [x: Key yönergesi](../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="b9e6a-114">See the "XAML 2009" section of [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
### <a name="xmlns-on-property-elements"></a><span data-ttu-id="b9e6a-115">Özellik öğelerde xmlns</span><span class="sxs-lookup"><span data-stu-id="b9e6a-115">xmlns on Property Elements</span></span>  
 <span data-ttu-id="b9e6a-116">XAML 2009 XAML ad alanı (xmlns) tanımları özelliği öğelerde destekler; Ancak, XAML 2006 yalnızca nesne öğelerde xmlns tanımları destekler.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-116">XAML 2009 can support XAML namespace (xmlns) definitions on property elements; however, XAML 2006 only supports xmlns definitions on object elements.</span></span>  
  
### <a name="event-attributes"></a><span data-ttu-id="b9e6a-117">Olay öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b9e6a-117">Event Attributes</span></span>  
 <span data-ttu-id="b9e6a-118">Olaylar tarafından yedeklenen öznitelikleri için XAML 2006 biçimlendirmesi derleme karmaşıktır ve biçimlendirme derleme olaylara gönderdikten varsayar.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-118">For attributes that are backed by events, XAML 2006 presumes that markup compilation is involved and submits the events to markup compilation.</span></span> <span data-ttu-id="b9e6a-119">XAML 2009 olay kablolama çalıştırma ayrıştırma ve XAML yükleme kadar erteler biçimlendirme uzantısı benzer bir işaretleme biçimini destekler.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-119">XAML 2009 supports a markup form that resembles a markup extension, which defers the event wiring until run-time parsing and loading of the XAML.</span></span> <span data-ttu-id="b9e6a-120">Ancak, WPF uygulamaları ve XAML senaryoları WPF UI için bu özellik genellikle kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-120">However, WPF applications and XAML scenarios for WPF UI generally do not use this capability.</span></span> <span data-ttu-id="b9e6a-121">WPF ve XAML 2006 uygulaması için tanımlanan yönlendirilmiş olaylar için olay işleyicisi kablolama bileşimini kullanır <xref:System.Windows.UIElement> düzeyi ve biçimlendirme derleyici adım büyük bir olay özniteliği işlemesi için.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-121">WPF and its XAML 2006 implementation uses the combination of event handler wiring for routed events defined at the <xref:System.Windows.UIElement> level and its markup compiler step for much of its event attribute processing.</span></span> <span data-ttu-id="b9e6a-122">Biçimlendirme derleyici burada biçimlendirme derleyici kullanılır yapı eylemleri bildirmek XAML'de bulunan tüm olay öznitelikler de preprocesses.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-122">The markup compiler also preprocesses any event attributes found in XAML where the build actions declare that the markup compiler is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e6a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9e6a-123">See Also</span></span>  
 [<span data-ttu-id="b9e6a-124">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="b9e6a-124">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
