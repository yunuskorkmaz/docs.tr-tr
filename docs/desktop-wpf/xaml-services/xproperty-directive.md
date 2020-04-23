---
title: x:Property Yönergesi
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071411"
---
# <a name="xproperty-directive"></a><span data-ttu-id="6a2fa-102">x:Property Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6a2fa-102">x:Property Directive</span></span>

<span data-ttu-id="6a2fa-103">Biçimlendirmede bir XAML özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="6a2fa-104">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6a2fa-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="6a2fa-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="6a2fa-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="6a2fa-106">XAML üretimi için destek sınıfının veya kısmi sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="6a2fa-107">Tanımlanan özelliğin üye adı.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="6a2fa-108">Bu özelliğin türünü belirten tür adı (veya diğer dize formu, çerçeveye özgü).</span><span class="sxs-lookup"><span data-stu-id="6a2fa-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a2fa-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a2fa-109">Remarks</span></span>

<span data-ttu-id="6a2fa-110">.NET XAML Hizmetleri uygulamasında, .</span><span class="sxs-lookup"><span data-stu-id="6a2fa-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="6a2fa-111">`x:Property`doğrudan bir tür desteği yoktur, ancak <xref:System.Windows.Markup.PropertyDefinition> sınıf tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="6a2fa-112">XAML düğümü akışında, `x:Property` xaml dilinden xaml ad alanından bir öğe, xaml adı alan bir `Property`üye olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="6a2fa-113">Üye, `Property` biçimlendirme tarafından beyan edildiği gibi öznitelikleri tutun.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="6a2fa-114">.NET `Name` XAML Hizmetleri düzeyinde atanır ve `Type` atanır.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="6a2fa-115">Bunlar, daha sonra belirli çerçeveler tarafından empoze edilebilir kurallar altında yorumlanacak, dize değerleri olarak ilk XAML düğüm akışında depolanır.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="6a2fa-116">Anlam, xaml adı ve XAML türü anlamı ile hizalanabilir veya uygulamaya bağlı olarak yalnızca bir destek türü sisteminde geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="6a2fa-117">Biçimlendirmede üye `x:Members` tanımlarını belirtmek için pratik bir kullanım sağlamak için, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="6a2fa-118">Amaçlanan model, `x:Members` bir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="6a2fa-119">Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturma mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="6a2fa-120">Bu, XAML'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçevelere bırakılır.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="6a2fa-121">Tipik olarak, MSBUILD, XAML'yi biçimlendirmek ve kod arkası ile tümleştiren veya bu özelliği desteklemek için saf From-XAML derlemeleri üreten eylemler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="6a2fa-122">x:Windows İş Akışı Temeli için özellik</span><span class="sxs-lookup"><span data-stu-id="6a2fa-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="6a2fa-123">Windows İş Akışı `x:Property` Temeli için, tamamen XAML veya XAML tanımlı dinamik üyeleri kod arkası olan bir etkinlik tasarımcısı için oluşturulan özel bir etkinliğin üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="6a2fa-124">`x:Class`xaml üretiminin kök elemanı üzerinde de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="6a2fa-125">Bu,.NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi MSBUILD yapı eylemleri tarafından yüklendiğinde özel etkinlikleri ve Genel olarak Windows İş Akışı Temeli XAML'yi destekleyen bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="6a2fa-126">Windows İş Akışı Temeli, öznitelik için `x:Property` `Type` amaçlanan değer olarak saf XAML türü adını kullanmaz ve bunun yerine burada belgelenmemiş bir kuralı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="6a2fa-127">Daha fazla bilgi için [Dinamik Etkinlik Oluşturma'ya](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="6a2fa-127">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
