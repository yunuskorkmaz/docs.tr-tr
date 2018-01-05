---
title: "x:Property Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36e464f9a45d737317192b2588473e90ae44a456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xproperty-directive"></a><span data-ttu-id="07c2f-102">x:Property Yönergesi</span><span class="sxs-lookup"><span data-stu-id="07c2f-102">x:Property Directive</span></span>
<span data-ttu-id="07c2f-103">Biçimlendirme XAML özelliğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-103">Declares a XAML property in markup.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="07c2f-104">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="07c2f-104">XAML Object Element Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="07c2f-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="07c2f-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="07c2f-106">XAML üretim için yedekleme sınıfı ya da parçalı sınıf adıdır.</span><span class="sxs-lookup"><span data-stu-id="07c2f-106">Name of the backing class or partial class for the XAML production.</span></span>|  
|`propertyName`|<span data-ttu-id="07c2f-107">Tanımlanan özelliğinin üye adı.</span><span class="sxs-lookup"><span data-stu-id="07c2f-107">Member name of the property being defined.</span></span>|  
|`propertyType`|<span data-ttu-id="07c2f-108">Tür adı (veya diğer dize form çerçeveye özel), bu özelliğin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07c2f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07c2f-109">Remarks</span></span>  
 <span data-ttu-id="07c2f-110">.NET Framework XAML hizmetlerinde uygulamasında.</span><span class="sxs-lookup"><span data-stu-id="07c2f-110">In the .NET Framework XAML Services implementation, .</span></span> <span data-ttu-id="07c2f-111">`x:Property`Yedekleme doğrudan türüne sahip değil, ancak tarafından desteklenen <xref:System.Windows.Markup.PropertyDefinition> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="07c2f-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="07c2f-112">XAML düğümü akışı içinde bir `x:Property` öğesi adlı bir üye temsil edilir `Property`, XAML dili XAML ad.</span><span class="sxs-lookup"><span data-stu-id="07c2f-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="07c2f-113">Üye `Property` biçimlendirme tarafından bildirilen şekilde öznitelikleri tutun.</span><span class="sxs-lookup"><span data-stu-id="07c2f-113">The member `Property` hold attributes as declared by markup.</span></span>  
  
 <span data-ttu-id="07c2f-114">Anlamını `Name` ve `Type` .NET Framework XAML hizmetlerinde düzeyinde atanmaz.</span><span class="sxs-lookup"><span data-stu-id="07c2f-114">The meaning of `Name` and `Type` are not assigned at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="07c2f-115">Bunlar daha sonra belirli çerçeveleri tarafından uygulanan kuralları altında yorumlanan dize değerleri, ilk XAML düğüm akış içinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="07c2f-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="07c2f-116">Anlamı bir XAML ad ve XAML türü anlamı Hizala veya yalnızca uygulama bağlı olarak bir yedekleme türü sistemindeki geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>  
  
 <span data-ttu-id="07c2f-117">Pratik kullanımını desteklemek için `x:Members` üye tanımları biçimlendirmede belirtmek için bir yol üyeleri değiştirilebilir bir sınıf ile ilişkili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07c2f-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="07c2f-118">Hedeflenen modeli olan `x:Members` belirten bir türü bir üyesi olarak mevcut bir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="07c2f-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="07c2f-119">Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üyenin tanımları oluşturan mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="07c2f-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="07c2f-120">Bu üye tanımları XAML destek uygulama modelleri sahip tek tek çerçeveler bırakılır.</span><span class="sxs-lookup"><span data-stu-id="07c2f-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="07c2f-121">Genellikle, isteğe bağlı olarak işaretleme-XAML ve ya da derleme MSBUILD yapı eylemleri arka plan kodu ile tümleştirmek veya üretim XAML gelen saf derlemeler bu özelliği desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="07c2f-122">x: özellik Windows Workflow Foundation için</span><span class="sxs-lookup"><span data-stu-id="07c2f-122">x:Property for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="07c2f-123">Windows Workflow Foundation için `x:Property` tamamen XAML veya XAML oluşan özel bir aktivite üyelerini tanımlayan – dinamik üyeler arka plan kodu ile bir etkinlik Tasarımcısı için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="07c2f-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="07c2f-124">`x:Class`XAML üretim kök öğesinin de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="07c2f-125">Bu, .NET Framework XAML hizmetlerinde düzeyinde zorunlu değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklenen bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="07c2f-125">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="07c2f-126">Windows Workflow Foundation kullanmaz saf XAML tür adı için hedeflenen değeri olarak `x:Property` `Type` özniteliği ve bunun yerine belgelenmemiştir bir kuralı burada kullanır.</span><span class="sxs-lookup"><span data-stu-id="07c2f-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="07c2f-127">Daha fazla bilgi için bkz: [dinamik etkinlik oluşturma](http://msdn.microsoft.com/library/dd807392.aspx).</span><span class="sxs-lookup"><span data-stu-id="07c2f-127">For more information, see [Dynamic Activity Creation](http://msdn.microsoft.com/library/dd807392.aspx).</span></span>
