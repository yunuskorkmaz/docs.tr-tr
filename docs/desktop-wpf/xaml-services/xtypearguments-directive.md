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
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071355"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="0e2fc-102">x:TypeArguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0e2fc-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="0e2fc-103">Genel bir jenerik türü bağımsız değişkenlerini genel türün oluşturucuya kısıtlayıcı tür bağımsız değişkenlerini geçer.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="0e2fc-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="0e2fc-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="0e2fc-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="0e2fc-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="0e2fc-106">CLR genel türü tarafından desteklenen XAML türünün nesne öğesi bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="0e2fc-107">Varsayılan `object` XAML ad alanından olmayan bir XAML türüne başvuruyorsa, `object` `object` var olan XAML ad alanını belirtmek için bir önek gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="0e2fc-108">CLR genel türü için tür bağımsız değişkenleri sağlayan bir veya daha fazla XAML türü adlarını dizeleri olarak bildiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="0e2fc-109">Ek sözdizimi notları için Açıklamalar'a bakın.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e2fc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e2fc-110">Remarks</span></span>

<span data-ttu-id="0e2fc-111">Çoğu durumda, bir `typeString` dize de bilgi öğesi olarak kullanılan XAML türleri önceden sabitlenir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="0e2fc-112">Tipik CLR genel kısıtlama türleri (örneğin <xref:System.String>ve) <xref:System.Int32> CLR taban sınıf kitaplıklarından gelir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="0e2fc-113">Bu kitaplıklar, tipik çerçeveye özgü varsayılan XAML ad alanlarına eşlenmez ve bu nedenle XAML kullanımı için bir önek eşleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="0e2fc-114">Virgül delimiter kullanarak birden fazla XAML türü adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="0e2fc-115">Genel kısıtlamaların kendileri genel türleri kullanıyorsa, iç içe geçmiş kısıtlama türü bağımsız değişkenleri parantez () tarafından bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="0e2fc-116">Bu tanımın `x:TypeArguments` .NET XAML Hizmetlerine özgü olduğunu ve CLR desteğini kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="0e2fc-117">[ \[MS-XAML\] Bölüm 5.3.11'de](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))dil düzeyi tanımı bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="0e2fc-118">Kullanım Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0e2fc-118">Usage Examples</span></span>

<span data-ttu-id="0e2fc-119">Bu örnekler için, aşağıdaki XAML ad alanı tanımlarının beyan edildiğine varyalım:</span><span class="sxs-lookup"><span data-stu-id="0e2fc-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="0e2fc-120">Liste\<Dize></span><span class="sxs-lookup"><span data-stu-id="0e2fc-120">List\<String></span></span>

<span data-ttu-id="0e2fc-121">`<scg:List x:TypeArguments="sys:String" ...>`bir tür bağımsız <xref:System.Collections.Generic.List%601> değişkeni <xref:System.String> ile yeni bir instantiates.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="0e2fc-122">Sözlük\<Dize, String></span><span class="sxs-lookup"><span data-stu-id="0e2fc-122">Dictionary\<String,String></span></span>

<span data-ttu-id="0e2fc-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`iki <xref:System.String> tür bağımsız <xref:System.Collections.Generic.Dictionary%602> değişkenlerle yeni bir instantiates.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="0e2fc-124">Sıra<KeyValuePair\<String, String>></span><span class="sxs-lookup"><span data-stu-id="0e2fc-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="0e2fc-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`iç kısıtlama türü <xref:System.Collections.Generic.Queue%601> bağımsız <xref:System.Collections.Generic.KeyValuePair%602> değişkenleri <xref:System.String> ile bir kısıtlama olan <xref:System.String>yeni bir instantiates ve .</span><span class="sxs-lookup"><span data-stu-id="0e2fc-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="0e2fc-126">XAML 2006 ve WPF Genel XAML Kullanımları</span><span class="sxs-lookup"><span data-stu-id="0e2fc-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="0e2fc-127">XAML 2006 kullanımı ve WPF uygulamaları için kullanılan XAML için `x:TypeArguments` genel olarak XAML'den genel tür kullanımları için aşağıdaki kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="0e2fc-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="0e2fc-128">Yalnızca bir XAML dosyasının kök öğesi, genel bir türe başvuran genel bir XAML kullanımını destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="0e2fc-129">Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türle eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="0e2fc-130"><xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="0e2fc-131">Sayfa işlevleri WPF'de XAML genel kullanım desteği için birincil senaryodur.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="0e2fc-132">Genel için kök öğesi XAML nesne öğesi de `x:Class`kullanarak kısmi bir sınıf beyan etmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="0e2fc-133">Bu, bir WPF oluşturma eylemi tanımlansa bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="0e2fc-134">`x:TypeArguments`iç içe geçmiş genel kısıtlamalara başvurulamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="0e2fc-135">WPF 3.0 veya WPF 3.5 Bağımlılık olmadan XAML 2009 veya XAML 2006</span><span class="sxs-lookup"><span data-stu-id="0e2fc-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="0e2fc-136">XAML 2006 veya XAML 2009 için .NET XAML Hizmetlerinde, genel XAML kullanımına ilişkin WPF ile ilgili kısıtlamalar gevşetilir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="0e2fc-137">Genel bir nesne öğe öğesini, destek türü sistemi ve nesne modelinin destekedebileceği XAML biçimlendirmesinde herhangi bir konumda anında atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="0e2fc-138">Ortak dil ilkelleri için XAML türleri elde etmek için CLR taban türlerini eşlemek yerine XAML 2009 kullanıyorsanız, [Ortak XAML Dil İlkelleri için Yerleşik Türleri](types-for-primitives.md) bir `typeString`.'de bilgi öğesi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="0e2fc-139">Örneğin, aşağıdakileri bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak x XAML 2009 için XAML dilixaml ad alanıdır):</span><span class="sxs-lookup"><span data-stu-id="0e2fc-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="0e2fc-140">WPF'de ve .NET Framework 4 veya .NET Core 3.0 (veya daha sonra) hedeflenirken, XAML 2009 özelliklerini ancak yalnızca gevşek XAML (biçimlendirme-derlenmemiş XAML) ile `x:TypeArguments` birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="0e2fc-141">WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="0e2fc-142">XAML'yi işaretlemeniz gerekiyorsa, [XAML 2006 ve WPF Generic XAML Kullanımları](#xaml-2006-and-wpf-generic-xaml-usages) bölümünde belirtilen kısıtlamalar altında çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="0e2fc-143">BAML yalnızca .NET Framework'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e2fc-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e2fc-144">See also</span></span>

- [<span data-ttu-id="0e2fc-145">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0e2fc-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="0e2fc-146">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="0e2fc-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="0e2fc-147">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="0e2fc-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="0e2fc-148">XAML'deki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="0e2fc-148">Generics in XAML</span></span>](generics.md)
