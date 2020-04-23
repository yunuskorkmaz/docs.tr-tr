---
title: x:Members Yönergesi
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071467"
---
# <a name="xmembers-directive"></a><span data-ttu-id="f5853-102">x:Members Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f5853-102">x:Members Directive</span></span>
<span data-ttu-id="f5853-103">Üst öğenin x:Sınıfı için geçerli olan biçimlendirmede tanımlanan bir üye kümesi tutar.</span><span class="sxs-lookup"><span data-stu-id="f5853-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="f5853-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f5853-104">XAML Attribute Usage</span></span>

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="f5853-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="f5853-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="f5853-106">XAML üretimi için destek sınıfının veya kısmi sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="f5853-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="f5853-107">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="f5853-107">See Remarks.</span></span>|
|`oneOrMoreMembers`|<span data-ttu-id="f5853-108">Üye tanımları temsil eden bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5853-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="f5853-109">Genellikle, bunlar `x:Property` nesne öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="f5853-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="f5853-110">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="f5853-110">See Remarks.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5853-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5853-111">Remarks</span></span>

<span data-ttu-id="f5853-112">.NET XAML Hizmetleri uygulamasında, `x:Members`..</span><span class="sxs-lookup"><span data-stu-id="f5853-112">In .NET XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="f5853-113">`x:Members`herhangi bir türde bir üye olarak var olabilir özel bir XAML üyesidir.</span><span class="sxs-lookup"><span data-stu-id="f5853-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="f5853-114">Bir XAML düğüm akışında, `x:Members` XAML `Members`dilinden XAML ad alanından bir üye olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f5853-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="f5853-115">Üye, `Members` `Member` yalnızca okunan genel nesneler listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5853-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="f5853-116">Tipik biçimlendirmede tek tek `x:Property` üyeler özellik öğeleri olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f5853-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="f5853-117">`x:Property`türleri özellikleri için özel olarak daha hassas bir `x:Member`türüdür ve atanabilir.</span><span class="sxs-lookup"><span data-stu-id="f5853-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="f5853-118">Daha fazla bilgi için [bkz: Özellik Yönergesi](xproperty-directive.md).</span><span class="sxs-lookup"><span data-stu-id="f5853-118">For more information, see [x:Property Directive](xproperty-directive.md).</span></span>

<span data-ttu-id="f5853-119">Biçimlendirmede üye `x:Members` tanımlarını belirtmek için pratik bir kullanım sağlamak için, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5853-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="f5853-120">Amaçlanan model, `x:Members` bir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f5853-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="f5853-121">Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturma mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f5853-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="f5853-122">Bu, XAML'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçevelere bırakılır.</span><span class="sxs-lookup"><span data-stu-id="f5853-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="f5853-123">Tipik olarak, MSBUILD, XAML'yi biçimlendirmek ve kod arkası ile tümleştiren veya bu özelliği desteklemek için saf From-XAML derlemeleri üreten eylemler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5853-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="f5853-124">x:Windows İş Akışı Vakfı üyeleri</span><span class="sxs-lookup"><span data-stu-id="f5853-124">x:Members for Windows Workflow Foundation</span></span>

<span data-ttu-id="f5853-125">Windows İş Akışı `x:Members` Temeli için, tamamen XAML veya XAML tanımlı dinamik üyeleri kod arkası olan bir etkinlik tasarımcısı için oluşturulmuş özel bir etkinliğin üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5853-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="f5853-126">`x:Class`xaml üretiminin kök elemanı üzerinde de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f5853-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="f5853-127">Bu,.NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi MSBUILD yapı eylemleri tarafından yüklendiğinde özel etkinlikleri ve Genel olarak Windows İş Akışı Temeli XAML'yi destekleyen bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="f5853-127">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="f5853-128">`x:Members`' yi bildiren nesne öğesinin biçimlendirmesindeki `x:Class`ilk alt öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5853-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
