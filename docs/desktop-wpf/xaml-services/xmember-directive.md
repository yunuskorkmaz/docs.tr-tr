---
title: x:Member Yönergesi
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 1c5b26b405e574290af54b29b22fb5e19e4b6b95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548253"
---
# <a name="xmember-directive"></a><span data-ttu-id="639b0-102">x:Member Yönergesi</span><span class="sxs-lookup"><span data-stu-id="639b0-102">x:Member Directive</span></span>
<span data-ttu-id="639b0-103">İşaretlemede bir XAML üyesi bildirir.</span><span class="sxs-lookup"><span data-stu-id="639b0-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="639b0-104">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="639b0-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="639b0-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="639b0-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="639b0-106">XAML üretimi için yedekleme sınıfının veya kısmi sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="639b0-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="639b0-107">Tanımlanan özelliğin üye adı.</span><span class="sxs-lookup"><span data-stu-id="639b0-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="639b0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="639b0-108">Remarks</span></span>

<span data-ttu-id="639b0-109">.NET XAML Hizmetleri uygulamasında,.</span><span class="sxs-lookup"><span data-stu-id="639b0-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="639b0-110">`x:Member` doğrudan bir tür yedeklemesi yoktur, ancak sınıfı tarafından desteklenir <xref:System.Windows.Markup.MemberDefinition> .</span><span class="sxs-lookup"><span data-stu-id="639b0-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="639b0-111">XAML düğüm akışında, bir `x:Member` Öğesı `Member` XAML Language xaml ad alanından adlı bir üye olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="639b0-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="639b0-112">Üye, `Member` biçimlendirme tarafından belirtilen öznitelikleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="639b0-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="639b0-113">`Name`Ve ' nin anlamı `Type` .net xaml Hizmetleri düzeyinde atanmaz.</span><span class="sxs-lookup"><span data-stu-id="639b0-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="639b0-114">Bunlar, daha sonra belirli çerçeveler tarafından uygulanabilir kuralların altında yorumlanmak üzere, ilk XAML düğüm akışında dize değerleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="639b0-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="639b0-115">Anlamı bir XAML adı ve XAML türü anlamını gösterebilir veya uygulamaya bağlı olarak yalnızca bir yedekleme türü sisteminde geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="639b0-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="639b0-116">' Nin pratik kullanımını, `x:Members` İşaretlemede üye tanımlarının belirtilmesi için bir yol olarak desteklemek amacıyla, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="639b0-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="639b0-117">Hedeflenen model, `x:Members` bir türü belirten bir üye olarak mevcuttur `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="639b0-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="639b0-118">Ancak, türlerin ve üyelerin ilişkilendirilmesi veya dinamik üye tanımlarının üretilme mekanizması .NET XAML Hizmetleri düzeyinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="639b0-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="639b0-119">Bu, XAML 'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçeveler için bırakılır.</span><span class="sxs-lookup"><span data-stu-id="639b0-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="639b0-120">Genellikle, XAML 'yi biçimlendirme-derleme ve bu özelliği desteklemeye yönelik saf from-XAML derlemeleri ile tümleştirme sağlayan MSBUILD derleme eylemleri.</span><span class="sxs-lookup"><span data-stu-id="639b0-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="639b0-121">Windows Workflow Foundation için x:Property</span><span class="sxs-lookup"><span data-stu-id="639b0-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="639b0-122">Windows Workflow Foundation için, `x:Property` tamamen XAML 'de oluşturulan özel bir etkinliğin üyelerini ya da arka plan kod içeren bir etkinlik TASARıMCıSıNıN xaml tanımlı dinamik üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="639b0-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="639b0-123">`x:Class` Ayrıca XAML üretiminin kök öğesinde de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="639b0-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="639b0-124">Bu, .NET XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi özel etkinlikleri destekleyen MSBUILD derleme eylemleri ve genel olarak XAML Windows Workflow Foundation yüklendiğinde bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="639b0-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="639b0-125">Windows Workflow Foundation, saf XAML tür adını özniteliği için amaçlanan değeri olarak kullanmaz `x:Property` `Type` ve bunun yerine burada belgelenmeyen bir kural kullanır.</span><span class="sxs-lookup"><span data-stu-id="639b0-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="639b0-126">Daha fazla bilgi için bkz. [DynamicActivity oluşturma](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="639b0-126">For more information, see [DynamicActivity Creation](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
