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
ms.openlocfilehash: 0d3edf6c7a16fc206832d8d6deff9d4ac2f69ba3
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58043266"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="4df3c-102">x:TypeArguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="4df3c-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="4df3c-103">Sınırlama geçişleri bir genel oluşturucuya genel tür bağımsız değişkenlerini yazın.</span><span class="sxs-lookup"><span data-stu-id="4df3c-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4df3c-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4df3c-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4df3c-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="4df3c-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="4df3c-106">Bir CLR genel türü tarafından desteklenen bir XAML türündeki bir nesne öğe bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4df3c-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="4df3c-107">Varsa `object` varsayılan XAML ad alanından değil bir XAML türü başvurduğu `object` XAML ad alanı belirtmek için bir önek gerektirir burada `object` bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4df3c-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="4df3c-108">Bir veya daha fazla XAML bildiren bir dize tür adları dize olarak hangi CLR genel tür için tür bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4df3c-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="4df3c-109">Açıklamalar için ek söz dizimi notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="4df3c-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df3c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4df3c-110">Remarks</span></span>  
 <span data-ttu-id="4df3c-111">Çoğu durumda, bir bilgi öğesi olarak kullanılan XAML türleri bir `typeString` dize ön eki bulunur.</span><span class="sxs-lookup"><span data-stu-id="4df3c-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="4df3c-112">CLR genel kısıtlamalara tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String>) CLR temel sınıf kitaplıklarını gelir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="4df3c-113">Bu kitaplıklar eşlenmemiş tipik çerçeveye özgü varsayılan XAML ad alanları değildir ve bu nedenle, XAML kullanım için bir önek eşleştirme gerektiren.</span><span class="sxs-lookup"><span data-stu-id="4df3c-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="4df3c-114">Bir virgül olan sınırlayıcıyı kullanarak birden fazla XAML türü adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4df3c-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="4df3c-115">Genel sınırlamalar genel türleri kullanıyorsanız, iç içe geçmiş kısıtlaması tür bağımsız değişkenlerini bulunabilir parantezleri () tarafından.</span><span class="sxs-lookup"><span data-stu-id="4df3c-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="4df3c-116">Unutmayın, bu tanımı `x:TypeArguments` için .NET Framework XAML hizmetlerinde özeldir ve CLR yedekleme kullanma.</span><span class="sxs-lookup"><span data-stu-id="4df3c-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="4df3c-117">Dil düzeyi tanımı bulunabilir [ \[MS-XAML\] bölümü 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="4df3c-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="4df3c-118">Kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="4df3c-118">Usage Examples</span></span>  
 <span data-ttu-id="4df3c-119">Bu örnekler için aşağıdaki XAML ad alanı tanımları bildirilir varsayın:</span><span class="sxs-lookup"><span data-stu-id="4df3c-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="4df3c-120">Liste\<dizesi ></span><span class="sxs-lookup"><span data-stu-id="4df3c-120">List\<String></span></span>  
 <span data-ttu-id="4df3c-121">`<scg:List x:TypeArguments="sys:String" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.List%601> ile bir <xref:System.String> tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4df3c-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="4df3c-122">Sözlük\<String, String ></span><span class="sxs-lookup"><span data-stu-id="4df3c-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="4df3c-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Dictionary%602> iki <xref:System.String> tür bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="4df3c-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="4df3c-124">Kuyruk < KeyValuePair\<dize, dize >></span><span class="sxs-lookup"><span data-stu-id="4df3c-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="4df3c-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Queue%601> kısıtlaması, olan <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlaması tür bağımsız değişkenleri ile <xref:System.String> ve <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4df3c-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="4df3c-126">XAML 2006 ve WPF'de XAML genel kullanımları</span><span class="sxs-lookup"><span data-stu-id="4df3c-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="4df3c-127">XAML 2006 kullanım ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar için mevcut `x:TypeArguments` ve genel XAML gelen genel tür kullanımları:</span><span class="sxs-lookup"><span data-stu-id="4df3c-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="4df3c-128">Yalnızca bir XAML dosyasının kök öğesini bir genel türe başvuran genel bir XAML kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="4df3c-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="4df3c-129">Kök öğe en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="4df3c-130"><xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="4df3c-131">WPF XAML genel kullanım desteği için birincil senaryosu sayfasında işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="4df3c-132">Genel için kök öğesi XAML nesne öğesi de kullanarak bir parçalı sınıf bildirmeniz gerekir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="4df3c-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="4df3c-133">Bir WPF tanımlama derleme eylemi bile bu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="4df3c-134">`x:TypeArguments` iç içe geçmiş genel kısıtlamalara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="4df3c-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="4df3c-135">XAML 2009 ya da WPF 3.0 veya 3.5 WPF XAML 2006 bağımlılık</span><span class="sxs-lookup"><span data-stu-id="4df3c-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="4df3c-136">.NET Framework XAML hizmetlerinde XAML 2006 ya da XAML 2009, WPF ile ilgili sınırlamalar genel XAML kullanım esnek.</span><span class="sxs-lookup"><span data-stu-id="4df3c-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="4df3c-137">Yedekleme türü sistem ve nesne modelini desteklemek XAML biçimlendirmesi içinde herhangi bir konumda bir genel nesne öğesi örneği oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="4df3c-138">XAML 2009 kullanıyorsanız, CLR eşleme yerine temel türleri XAML dili ortak temelleri için elde etmek için türler, kullanabileceğiniz [XAML dili ortak temelleri için yerleşik türler](built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak bir `typeString`.</span><span class="sxs-lookup"><span data-stu-id="4df3c-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="4df3c-139">Örneğin, aşağıdaki bildirebilirsiniz (önek eşletirmeleri gösterilmez, ancak x olan XAML dil XAML ad alanı için XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="4df3c-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="4df3c-140">WPF ve hedeflenirken [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], XAML 2009 özelliklerini ile birlikte kullanabileceğiniz `x:TypeArguments` ancak yalnızca gevşek XAML (biçimlendirme yapılmayan XAML).</span><span class="sxs-lookup"><span data-stu-id="4df3c-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="4df3c-141">WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="4df3c-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="4df3c-142">XAML biçimlendirme için derlerseniz, "XAML 2006 ve WPF genel XAML kullanım" bölümünde belirtildiği kısıtlamaları'nın altında çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4df3c-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df3c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df3c-143">See also</span></span>
- [<span data-ttu-id="4df3c-144">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="4df3c-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="4df3c-145">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="4df3c-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="4df3c-146">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="4df3c-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="4df3c-147">XAML'deki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="4df3c-147">Generics in XAML</span></span>](generics-in-xaml.md)
