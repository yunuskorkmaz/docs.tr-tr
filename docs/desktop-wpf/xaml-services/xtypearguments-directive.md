---
title: x:TypeArguments Yönergesi
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543557"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="3eded-102">x:TypeArguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3eded-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="3eded-103">Bir genel öğesinin kısıtlayan tür bağımsız değişkenlerini genel türün oluşturucusuna geçirir.</span><span class="sxs-lookup"><span data-stu-id="3eded-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="3eded-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="3eded-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="3eded-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="3eded-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="3eded-106">Bir CLR genel türü tarafından desteklenen bir XAML türünün nesne öğesi bildirimi.</span><span class="sxs-lookup"><span data-stu-id="3eded-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="3eded-107">`object`Varsayılan xaml ad alanından olmayan BIR xaml türüne başvuruyorsa, varsa `object` xaml ad alanını belirtmek için bir ön ek gerektirir `object` .</span><span class="sxs-lookup"><span data-stu-id="3eded-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="3eded-108">CLR genel türü için tür bağımsız değişkenlerini sağlayan dizeler olarak bir veya daha fazla XAML tür adı bildiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3eded-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="3eded-109">Ek sözdizimi notları için bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="3eded-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3eded-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eded-110">Remarks</span></span>

<span data-ttu-id="3eded-111">Çoğu durumda, bir dizedeki bilgi öğesi olarak kullanılan XAML türlerinin `typeString` ön eki alınır.</span><span class="sxs-lookup"><span data-stu-id="3eded-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="3eded-112">CLR genel kısıtlamalarının tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String> ) clr temel sınıf kitaplıklarından gelir.</span><span class="sxs-lookup"><span data-stu-id="3eded-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="3eded-113">Bu kitaplıklar, çerçeveye özgü tipik varsayılan XAML ad alanları ile eşlenmedi ve bu nedenle XAML kullanımı için bir ön ek eşlemesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3eded-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="3eded-114">Bir virgül sınırlayıcısı kullanarak birden çok XAML türü adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3eded-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="3eded-115">Genel kısıtlamalar genel türler kullanıyorsa, iç içe geçmiş kısıtlama türü bağımsız değişkenleri parantez () ile yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="3eded-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="3eded-116">Bu tanımın `x:TypeArguments` .net xaml hizmetlerine özgü olduğunu ve clr yedeklemesini kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3eded-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="3eded-117">Bir dil düzeyi tanımı, [ \[ MS-xaml \] bölümünde 5.3.11](/previous-versions/msp-n-p/ff650760(v=pandp.10))bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3eded-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="3eded-118">Kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="3eded-118">Usage Examples</span></span>

<span data-ttu-id="3eded-119">Bu örnekler için aşağıdaki XAML ad alanı tanımlarının bildirildiği varsayılır:</span><span class="sxs-lookup"><span data-stu-id="3eded-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="3eded-120">Listele\<String></span><span class="sxs-lookup"><span data-stu-id="3eded-120">List\<String></span></span>

<span data-ttu-id="3eded-121">`<scg:List x:TypeArguments="sys:String" ...>` bir <xref:System.Collections.Generic.List%601> <xref:System.String> tür bağımsız değişkeniyle yeni bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3eded-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="3eded-122">Sözlük\<String,String></span><span class="sxs-lookup"><span data-stu-id="3eded-122">Dictionary\<String,String></span></span>

<span data-ttu-id="3eded-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`<xref:System.Collections.Generic.Dictionary%602>iki tür bağımsız değişkeni ile yeni bir oluşturur <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="3eded-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="3eded-124"><KeyValuePair kuyruğu\<String,String>></span><span class="sxs-lookup"><span data-stu-id="3eded-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="3eded-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlama türü bağımsız değişkenleri ve ile kısıtlaması olan yeni bir oluşturur <xref:System.String> <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="3eded-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="3eded-126">XAML 2006 ve WPF Genel XAML kullanımları</span><span class="sxs-lookup"><span data-stu-id="3eded-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="3eded-127">XAML 2006 kullanımı ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar `x:TypeArguments` ve genel olarak xaml 'den genel tür kullanımları vardır:</span><span class="sxs-lookup"><span data-stu-id="3eded-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="3eded-128">Yalnızca bir XAML dosyasının kök öğesi genel bir türe başvuran Genel XAML kullanımını destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3eded-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="3eded-129">Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türe eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3eded-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="3eded-130"><xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3eded-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="3eded-131">Sayfa işlevleri, WPF 'de XAML genel kullanım desteğinin birincil senaryosudur.</span><span class="sxs-lookup"><span data-stu-id="3eded-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="3eded-132">Genel için kök öğe XAML nesne öğesi, kullanarak kısmi bir sınıf de bildirmelidir `x:Class` .</span><span class="sxs-lookup"><span data-stu-id="3eded-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="3eded-133">Bu, WPF oluşturma eylemi tanımlansa bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3eded-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="3eded-134">`x:TypeArguments` iç içe geçmiş genel kısıtlamalara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="3eded-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="3eded-135">WPF 3,0 veya WPF 3,5 bağımlılığı olmayan XAML 2009 veya XAML 2006</span><span class="sxs-lookup"><span data-stu-id="3eded-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="3eded-136">XAML 2006 ya da XAML 2009 için .NET XAML hizmetlerinde, genel XAML kullanımı ile ilgili WPF ile ilgili kısıtlamalar gevşek olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="3eded-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="3eded-137">XAML biçimlendirmesinde, yedekleme türü sisteminin ve nesne modelinin destekleyebileceği herhangi bir konumda genel nesne öğesi örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3eded-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="3eded-138">Ortak dil temel öğeleri için XAML türleri almak üzere CLR temel türlerini eşlemek yerine XAML 2009 kullanıyorsanız, [ortak xaml dil temelleri Için yerleşik türleri](types-for-primitives.md) bir içinde bilgi öğeleri olarak kullanabilirsiniz `typeString` .</span><span class="sxs-lookup"><span data-stu-id="3eded-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="3eded-139">Örneğin, aşağıdaki bildirimi yapabilirsiniz (önek eşlemeleri gösterilmez, ancak x, XAML 2009 için XAML Language xaml ad alanıdır):</span><span class="sxs-lookup"><span data-stu-id="3eded-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="3eded-140">WPF 'de ve .NET Framework 4 veya .NET Core 3,0 (veya üzeri) hedeflenirken XAML 2009 özelliklerini `x:TypeArguments` yalnızca gevşek XAML (biçimlendirme derlenmiş olmayan XAML) ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3eded-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="3eded-141">WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="3eded-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="3eded-142">XAML 'yi derlemeyi işaretlemeyi gerekiyorsa, [xaml 2006 ve WPF genel xaml kullanımları](#xaml-2006-and-wpf-generic-xaml-usages) bölümünde belirtilen kısıtlamalar altında işlem yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eded-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="3eded-143">BAML yalnızca .NET Framework desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3eded-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="3eded-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eded-144">See also</span></span>

- [<span data-ttu-id="3eded-145">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3eded-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="3eded-146">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="3eded-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="3eded-147">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="3eded-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="3eded-148">XAML'deki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="3eded-148">Generics in XAML</span></span>](generics.md)
