---
title: "x:FieldModifier Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ed50dd2aff1702543789f06939f7c2bc4b3dd83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="152ac-102">x:FieldModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="152ac-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="152ac-103">Böylece adlandırılmış nesne başvuruları için alanları ile tanımlanmış XAML derleme davranışını değiştiren <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> yerine erişim <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranışı.</span><span class="sxs-lookup"><span data-stu-id="152ac-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="152ac-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="152ac-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="152ac-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="152ac-105">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="152ac-106">*Public*</span><span class="sxs-lookup"><span data-stu-id="152ac-106">*Public*</span></span>|<span data-ttu-id="152ac-107">Geçirdiğiniz belirtmek için tam dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> karşı <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullanılan arka plan kodu programlama dili bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="152ac-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="152ac-108">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="152ac-108">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="152ac-109">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="152ac-109">Dependencies</span></span>  
 <span data-ttu-id="152ac-110">XAML üretim kullanıyorsa `x:FieldModifier` herhangi bir yere, o XAML üretim kök öğesinin bildirmelidir bir [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md).</span><span class="sxs-lookup"><span data-stu-id="152ac-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="152ac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="152ac-111">Remarks</span></span>  
 <span data-ttu-id="152ac-112">`x:FieldModifier`bir sınıf veya üyelerine genel erişim düzeyini bildirmek için ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="152ac-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="152ac-113">XAML üretim parçası olan belirli bir XAML nesne işlenir ve bir uygulama nesne grafiğinde potansiyel olarak erişilebilen bir nesne olursa yalnızca XAML işleme davranışı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="152ac-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="152ac-114">Varsayılan olarak, böyle bir nesnenin alan başvurusu denetim tüketicileri Nesne grafiği doğrudan değiştirmesini engeller özel tutulur.</span><span class="sxs-lookup"><span data-stu-id="152ac-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="152ac-115">Bunun yerine, Denetim tüketicileri programlama modelleri tarafından gibi düzeni kök, alt öğe koleksiyonları, ayrılmış ortak özellikleri elde ederek etkinleştirilen standart desenler kullanılarak nesne grafiği değiştirmek için beklenen ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="152ac-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>  
  
 <span data-ttu-id="152ac-116">Değeri `x:FieldModifier` öznitelik programlama diline göre değişir ve amacı içinde belirli çerçeve değişebilir.</span><span class="sxs-lookup"><span data-stu-id="152ac-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="152ac-117">Her bir dilin nasıl uyguladığını kullanılacak dizesi bağlıdır, <xref:System.CodeDom.Compiler.CodeDomProvider> ve döndürür anlamı tanımlamak için tür dönüştürücüleri <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, ve bu dil büyük küçük harfe duyarlı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="152ac-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="152ac-118">İçin [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], atamak iletilecek dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olan `public`.</span><span class="sxs-lookup"><span data-stu-id="152ac-118">For [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>  
  
-   <span data-ttu-id="152ac-119">İçin [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], atamak iletilecek dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olan `Public`.</span><span class="sxs-lookup"><span data-stu-id="152ac-119">For [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>  
  
-   <span data-ttu-id="152ac-120">İçin [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], XAML için hiçbir hedef zaten var; Bu nedenle, iletilecek dizeyi tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="152ac-120">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>  
  
 <span data-ttu-id="152ac-121">De belirtebilirsiniz <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` içinde [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` içinde [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) ancak belirten <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olağandışıdır çünkü `NotPublic` davranışı zaten varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="152ac-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>  
  
 <span data-ttu-id="152ac-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>XAML derlenmiş derleme dışına kod XAML oluşturulan öğesine erişmesi gereken sık olduğundan varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="152ac-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="152ac-123">WPF XAML derleme davranışı ile birlikte güvenlik mimarisi değil bildirme öğesi örnekleri genel olarak, depolama alanları özellikle ayarlanmadığı sürece `x:FieldModifier` genel erişime izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="152ac-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>  
  
 <span data-ttu-id="152ac-124">`x:FieldModifier`yalnızca öğeleriyle için uygun olan bir [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md) bu ad alanı ortak sonra başvurmak için kullanıldığından.</span><span class="sxs-lookup"><span data-stu-id="152ac-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md) because that name is used to reference the field after it is public.</span></span>  
  
 <span data-ttu-id="152ac-125">Varsayılan olarak, kök öğe için parçalı sınıf ortak; Ancak, bunu kullanarak ortak olmayan bir duruma getirebilirsiniz [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span><span class="sxs-lookup"><span data-stu-id="152ac-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span> <span data-ttu-id="152ac-126">[X: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md) kök öğe sınıfı örneğini erişim düzeyini de etkiler.</span><span class="sxs-lookup"><span data-stu-id="152ac-126">The [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="152ac-127">Her ikisi de koyabilirsiniz `x:Name` ve `x:FieldModifier` kök öğesi, ancak bu yalnızca yapar tarafından denetlenen bir ortak alan kopyasını kök öğe, doğru kök öğe sınıfı erişim düzeyi hala [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span><span class="sxs-lookup"><span data-stu-id="152ac-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152ac-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="152ac-128">See Also</span></span>  
 [<span data-ttu-id="152ac-129">WPF için XAML ve Özel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="152ac-129">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [<span data-ttu-id="152ac-130">Arka Plan Kod ve WPF İçindeki XAML</span><span class="sxs-lookup"><span data-stu-id="152ac-130">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="152ac-131">x:Name Yönergesi</span><span class="sxs-lookup"><span data-stu-id="152ac-131">x:Name Directive</span></span>](../../../docs/framework/xaml-services/x-name-directive.md)  
 [<span data-ttu-id="152ac-132">WPF uygulaması (WPF) oluşturma</span><span class="sxs-lookup"><span data-stu-id="152ac-132">Building a WPF Application (WPF)</span></span>](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="152ac-133">x:ClassModifier Yönergesi</span><span class="sxs-lookup"><span data-stu-id="152ac-133">x:ClassModifier Directive</span></span>](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
