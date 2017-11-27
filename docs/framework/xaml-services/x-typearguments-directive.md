---
title: "x:TypeArguments Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: "18"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a63a8080c71ad026664e2e14fc1762fcdd4bdb36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="cbc66-102">x:TypeArguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="cbc66-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="cbc66-103">Sınırlama geçişleri genel tür oluşturucuya genel bağımsız değişkenlerini yazın.</span><span class="sxs-lookup"><span data-stu-id="cbc66-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="cbc66-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="cbc66-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="cbc66-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="cbc66-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="cbc66-106">Bir nesne öğesi bildirimi CLR genel türü tarafından yedeklenen bir XAML türü.</span><span class="sxs-lookup"><span data-stu-id="cbc66-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="cbc66-107">Varsa `object` varsayılan XAML ad alanından değil bir XAML türü başvurduğu `object` XAML ad uzayı belirtmek için bir önek gerektirir nerede `object` bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbc66-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="cbc66-108">Bir veya daha fazla XAML bildiren bir dize türü adları dize olarak, tür bağımsız değişkenleri CLR genel tür için sağladığı.</span><span class="sxs-lookup"><span data-stu-id="cbc66-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="cbc66-109">Açıklamalar için ek sözdizimi notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="cbc66-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc66-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbc66-110">Remarks</span></span>  
 <span data-ttu-id="cbc66-111">Çoğu durumda, bir bilgi öğesi olarak kullanılan XAML türleri bir `typeString` dize öneki.</span><span class="sxs-lookup"><span data-stu-id="cbc66-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="cbc66-112">CLR genel kısıtlamalar tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String>) CLR temel sınıf kitaplıklarından gelir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="cbc66-113">Bu kitaplıklar eşlenmemiş tipik çerçeveye özel varsayılan XAML ad uzayları olup olmadığı ve bu nedenle, bir önek eşleştirme için XAML kullanımı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="cbc66-114">Bir virgül ayırıcısı kullanarak birden fazla XAML tür adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc66-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="cbc66-115">Genel türler genel kısıtlamalar kullanırsanız, iç içe geçmiş kısıtlaması tür bağımsız değişkenleri bulunabilir parantez (tarafından).</span><span class="sxs-lookup"><span data-stu-id="cbc66-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="cbc66-116">Unutmayın, bu tanımı `x:TypeArguments` .NET Framework XAML Hizmetleri için özeldir ve CLR yedekleme kullanma.</span><span class="sxs-lookup"><span data-stu-id="cbc66-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="cbc66-117">Bir dil düzeyi tanımı bulunabilir [ \[MS XAML\] bölüm 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="cbc66-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="cbc66-118">Kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="cbc66-118">Usage Examples</span></span>  
 <span data-ttu-id="cbc66-119">Bu örnekler için aşağıdaki XAML ad alanı tanımları bildirilir varsayın:</span><span class="sxs-lookup"><span data-stu-id="cbc66-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="cbc66-120">Liste\<dize ></span><span class="sxs-lookup"><span data-stu-id="cbc66-120">List\<String></span></span>  
 <span data-ttu-id="cbc66-121">`<scg:List x:TypeArguments="sys:String" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.List%601> ile bir <xref:System.String> bağımsız değişkeni yazın.</span><span class="sxs-lookup"><span data-stu-id="cbc66-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="cbc66-122">Sözlük\<dize, dize ></span><span class="sxs-lookup"><span data-stu-id="cbc66-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="cbc66-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Dictionary%602> iki <xref:System.String> tür bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="cbc66-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="cbc66-124">Sıra < KeyValuePair\<dize, dize >></span><span class="sxs-lookup"><span data-stu-id="cbc66-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="cbc66-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Queue%601> bir kısıtlaması olan <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlama tür bağımsız değişkenleri ile <xref:System.String> ve <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cbc66-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="cbc66-126">XAML 2006 ve WPF XAML genel kullanımları</span><span class="sxs-lookup"><span data-stu-id="cbc66-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="cbc66-127">XAML 2006 kullanım ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar mevcut `x:TypeArguments` ve genel olarak genel tür kullanımları XAML gelen:</span><span class="sxs-lookup"><span data-stu-id="cbc66-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="cbc66-128">XAML dosyasının kök öğesinin yalnızca genel bir tür başvuran genel bir XAML kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="cbc66-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="cbc66-129">Kök öğesi en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="cbc66-130">Örnek <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="cbc66-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="cbc66-131">WPF XAML genel kullanım desteği için birincil senaryo sayfa işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="cbc66-132">Genel için kök öğesi XAML object öğesi, ayrıca kullanarak bir parçalı sınıf bildirmelidir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="cbc66-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="cbc66-133">Bir WPF tanımlama yapı eylemi bile bu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="cbc66-134">`x:TypeArguments`iç içe geçmiş genel kısıtlamalar başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="cbc66-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="cbc66-135">XAML 2009 veya herhangi bir WPF 3.0 veya 3.5 WPF XAML 2006 bağımlılık</span><span class="sxs-lookup"><span data-stu-id="cbc66-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="cbc66-136">.NET Framework XAML Hizmetleri XAML 2006 ya da XAML 2009, genel XAML kullanımı WPF ile ilgili kısıtlamalar rahat.</span><span class="sxs-lookup"><span data-stu-id="cbc66-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="cbc66-137">Yedekleme türü sistem ve nesne modeli destekleyebilir XAML işaretleme herhangi bir konumda bir genel nesne öğesi örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc66-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="cbc66-138">XAML 2009 kullanırsanız, ortak dil temelleri için XAML türlerinin edinilir türleri temel CLR eşleme yerine, kullanabileceğiniz [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak bir `typeString`.</span><span class="sxs-lookup"><span data-stu-id="cbc66-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="cbc66-139">Örneğin, aşağıdaki bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak x olduğu XAML dili XAML ad uzayı XAML 2009 için):</span><span class="sxs-lookup"><span data-stu-id="cbc66-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="cbc66-140">WPF ve hedeflerken [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], XAML 2009 özellikleri ile birlikte kullanabileceğiniz `x:TypeArguments` ancak yalnızca gevşek XAML (işaretleme-derlenmemiş XAML).</span><span class="sxs-lookup"><span data-stu-id="cbc66-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="cbc66-141">XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.</span><span class="sxs-lookup"><span data-stu-id="cbc66-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="cbc66-142">XAML biçimlendirme derleme varsa, "XAML 2006 ve WPF genel XAML kullanımları" bölümünde belirtildiği kısıtlamaları altında çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbc66-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc66-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc66-143">See Also</span></span>  
 [<span data-ttu-id="cbc66-144">x: Class yönergesi</span><span class="sxs-lookup"><span data-stu-id="cbc66-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="cbc66-145">x: Type işaretleme uzantısı</span><span class="sxs-lookup"><span data-stu-id="cbc66-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="cbc66-146">XAML dili ortak temelleri için yerleşik türler</span><span class="sxs-lookup"><span data-stu-id="cbc66-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="cbc66-147">XAML'deki genel türler</span><span class="sxs-lookup"><span data-stu-id="cbc66-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
