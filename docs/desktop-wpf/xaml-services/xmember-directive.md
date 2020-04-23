---
title: x:Member Yönergesi
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071474"
---
# <a name="xmember-directive"></a><span data-ttu-id="dcb36-102">x:Member Yönergesi</span><span class="sxs-lookup"><span data-stu-id="dcb36-102">x:Member Directive</span></span>
<span data-ttu-id="dcb36-103">Biçimlendirmede bir XAML üyesi bildirir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="dcb36-104">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dcb36-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="dcb36-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="dcb36-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="dcb36-106">XAML üretimi için destek sınıfının veya kısmi sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="dcb36-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="dcb36-107">Tanımlanan özelliğin üye adı.</span><span class="sxs-lookup"><span data-stu-id="dcb36-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dcb36-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcb36-108">Remarks</span></span>

<span data-ttu-id="dcb36-109">.NET XAML Hizmetleri uygulamasında, .</span><span class="sxs-lookup"><span data-stu-id="dcb36-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="dcb36-110">`x:Member`doğrudan bir tür desteği yoktur, ancak <xref:System.Windows.Markup.MemberDefinition> sınıf tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="dcb36-111">XAML düğümü akışında, `x:Member` xaml dilinden xaml ad alanından bir öğe, xaml adı alan bir `Member`üye olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="dcb36-112">Üye, `Member` biçimlendirme tarafından beyan edildiği gibi öznitelikleri tutar.</span><span class="sxs-lookup"><span data-stu-id="dcb36-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="dcb36-113">.NET `Name` XAML Hizmetleri düzeyinde atanır ve `Type` atanır.</span><span class="sxs-lookup"><span data-stu-id="dcb36-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="dcb36-114">Bunlar, daha sonra belirli çerçeveler tarafından empoze edilebilir kurallar altında yorumlanacak, dize değerleri olarak ilk XAML düğüm akışında depolanır.</span><span class="sxs-lookup"><span data-stu-id="dcb36-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="dcb36-115">Anlam, xaml adı ve XAML türü anlamı ile hizalanabilir veya uygulamaya bağlı olarak yalnızca bir destek türü sisteminde geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="dcb36-116">Biçimlendirmede üye `x:Members` tanımlarını belirtmek için pratik bir kullanım sağlamak için, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="dcb36-117">Amaçlanan model, `x:Members` bir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="dcb36-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="dcb36-118">Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturma mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dcb36-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="dcb36-119">Bu, XAML'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçevelere bırakılır.</span><span class="sxs-lookup"><span data-stu-id="dcb36-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="dcb36-120">Tipik olarak, MSBUILD, XAML'yi biçimlendirmek ve kod arkası ile tümleştiren veya bu özelliği desteklemek için saf From-XAML derlemeleri üreten eylemler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dcb36-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="dcb36-121">x:Windows İş Akışı Temeli için özellik</span><span class="sxs-lookup"><span data-stu-id="dcb36-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="dcb36-122">Windows İş Akışı `x:Property` Temeli için, tamamen XAML veya XAML tanımlı dinamik üyeleri kod arkası olan bir etkinlik tasarımcısı için oluşturulan özel bir etkinliğin üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dcb36-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="dcb36-123">`x:Class`xaml üretiminin kök elemanı üzerinde de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="dcb36-124">Bu,.NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi MSBUILD yapı eylemleri tarafından yüklendiğinde özel etkinlikleri ve Genel olarak Windows İş Akışı Temeli XAML'yi destekleyen bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="dcb36-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="dcb36-125">Windows İş Akışı Temeli, öznitelik için `x:Property` `Type` amaçlanan değer olarak saf XAML türü adını kullanmaz ve bunun yerine burada belgelenmemiş bir kuralı kullanır.</span><span class="sxs-lookup"><span data-stu-id="dcb36-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="dcb36-126">Daha fazla bilgi için [Dinamik Etkinlik Oluşturma'ya](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="dcb36-126">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
