---
title: x:Subclass Yönergesi
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540725"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="6a4e6-102">x:Subclass Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6a4e6-102">x:Subclass Directive</span></span>

<span data-ttu-id="6a4e6-103">Ayrıca sağlandığında XAML biçimlendirme derleme davranışını değiştirir `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="6a4e6-104">' I temel alan kısmi bir sınıf oluşturmak yerine, `x:Class` belirtilen `x:Class` bir ara sınıf olarak oluşturulur ve ardından, sağlanmış türetilmiş sınıfınızın temel olması beklenir `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="6a4e6-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6a4e6-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="6a4e6-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="6a4e6-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="6a4e6-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-107">Optional.</span></span> <span data-ttu-id="6a4e6-108">İçeren bir CLR ad alanı belirtir `classname` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="6a4e6-109">`namespace`Belirtilmişse, nokta (.) `namespace` ve ayırır `classname` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="6a4e6-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-110">Required.</span></span> <span data-ttu-id="6a4e6-111">Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="6a4e6-112">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="6a4e6-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-113">Optional.</span></span> <span data-ttu-id="6a4e6-114">, `namespace` Her bir ad alanı diğerini çözümleyebiliyorsanız, öğesinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="6a4e6-115">İçeren bir CLR ad alanı belirtir `subclassName` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="6a4e6-116">`subclassName`Belirtilmişse, nokta (.) `subclassNamespace` ve ayırır `subclassName` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="6a4e6-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-117">Required.</span></span> <span data-ttu-id="6a4e6-118">Alt sınıfın CLR adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="6a4e6-119">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="6a4e6-119">Dependencies</span></span>

<span data-ttu-id="6a4e6-120">[X:Class yönergesi](xclass-directive.md) aynı nesne üzerinde de sağlanmalıdır ve bu nesnenin xaml üretiminin kök öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a4e6-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a4e6-121">Remarks</span></span>

<span data-ttu-id="6a4e6-122">`x:Subclass` Kullanım öncelikle kısmi sınıf bildirimlerini desteklemeyen diller için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="6a4e6-123">Olarak kullanılan sınıfı, `x:Subclass` iç içe geçmiş bir sınıf olamaz ve `x:Subclass` "bağımlılıklar" bölümünde açıklandığı gibi kök nesnesine başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="6a4e6-124">Aksi takdirde, kavramsal anlamı `x:Subclass` .net xaml Hizmetleri uygulamasıyla tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="6a4e6-125">Bunun nedeni, .NET XAML Hizmetleri davranışının XAML biçimlendirme ve yedekleme kodunun bağlı olduğu genel programlama modelini belirtmemesi nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="6a4e6-126">Ve ile ilgili başka kavramların `x:Class` Uygulamaları `x:Subclass` , XAML biçimlendirme, derlenmiş BIÇIMLENDIRME ve clr tabanlı arka plan kod bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="6a4e6-127">Her çerçeve, bazı davranışlarının veya yapı ortamına dahil olması gereken belirli bileşenlerin bir kısmını etkinleştiren kendi derleme eylemlerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="6a4e6-128">Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="6a4e6-129">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="6a4e6-129">WPF Usage Notes</span></span>

<span data-ttu-id="6a4e6-130">`x:Subclass` , zaten sahip olan uygulama tanımındaki bir sayfa kökü veya kök üzerinde olabilir <xref:System.Windows.Application> `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="6a4e6-131">`x:Subclass`Bir sayfa veya uygulama kökü dışında herhangi bir öğe üzerinde bildirme ya da bunu yok olarak belirleme `x:Class` , derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="6a4e6-132">Senaryo için doğru şekilde çalışan türetilmiş sınıfların oluşturulması `x:Subclass` oldukça karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="6a4e6-133">Ara dosyaları (. xaml dosya adlarını içeren adlarla biçimlendirme derlemesi tarafından, projenizin obj klasöründe oluşturulan. g dosyaları) incelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="6a4e6-134">Bu ara dosyalar, derlenmiş uygulamadaki birleştirilmiş kısmi sınıflarda belirli programlama yapılarının kaynağını belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="6a4e6-135">Türetilmiş sınıftaki olay işleyicileri `internal override` `Friend Overrides` , derleme sırasında ara sınıfta oluşturulan işleyicilerle ilgili saplamaları geçersiz kılmak Için (Microsoft Visual Basic) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="6a4e6-136">Aksi halde, türetilmiş sınıf uygulamaları gizle (gölge) ara sınıf uygulaması ve ara sınıf işleyicileri çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="6a4e6-137">Hem hem de tanımladığınızda `x:Class` `x:Subclass` , tarafından başvurulan sınıf için herhangi bir uygulama sağlamanız gerekmez `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="6a4e6-138">`x:Class`Derleyicinin ara dosyalarda oluşturduğu sınıfa yönelik bir kılavuza sahip olması için yalnızca özniteliği aracılığıyla bir ad vermeniz gerekir (derleyici bu durumda varsayılan bir ad seçmez).</span><span class="sxs-lookup"><span data-stu-id="6a4e6-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="6a4e6-139">`x:Class`Sınıfına bir uygulama verebilirsiniz; ancak, bu, hem hem de kullanımı için tipik bir senaryo değildir `x:Class` `x:Subclass` .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a4e6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-140">See also</span></span>

- [<span data-ttu-id="6a4e6-141">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6a4e6-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="6a4e6-142">WPF için XAML ve Özel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6a4e6-142">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
