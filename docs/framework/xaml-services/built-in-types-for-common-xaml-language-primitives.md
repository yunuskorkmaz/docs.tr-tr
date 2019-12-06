---
title: XAML Dili Ortak Temelleri İçin Yerleşik Türler
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837278"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="b2e86-102">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="b2e86-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="b2e86-103">XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan temel elemanlar olan çeşitli veri türleri için XAML dil düzeyinde destek sunar.</span><span class="sxs-lookup"><span data-stu-id="b2e86-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="b2e86-104">XAML 2009, bu temel öğeler için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`ve `x:Array`</span><span class="sxs-lookup"><span data-stu-id="b2e86-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="b2e86-105">XAML Biçimlendirmede Dil Temelleri için Önceki Teknikler</span><span class="sxs-lookup"><span data-stu-id="b2e86-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="b2e86-106">WPF önceki sürümleri için XAML içinde .NET Framework için CLR temel tanım sınıfı içeren bir derlemeyi ve ad boşluğunu eşleyerek CLR dil temellerine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2e86-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="b2e86-107">Bunların çoğu mscorlib derlemesi ve <xref:System> ad alanı içindedir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="b2e86-108">Örneğin, <xref:System.Int32> kullanmak için aşağıdaki eşlemeyi (bundan sonra örnek kullanım ile gösterilen) bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2e86-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="b2e86-109">XAML 2009 Dil Temelleri</span><span class="sxs-lookup"><span data-stu-id="b2e86-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="b2e86-110">Kural gereği, XAML dil temelleri ve diğer tüm XAML dil öğeleri `x:` öneki ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="b2e86-111">XAML dil öğeleri genellikle gerçek biçimlendirme içinde bu şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="b2e86-112">WPF'de XAML için kavramsal belgelerde ve ayrıca XAML belirtiminde bu kural izlenir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="b2e86-113">x:Nesne</span><span class="sxs-lookup"><span data-stu-id="b2e86-113">x:Object</span></span>  
 <span data-ttu-id="b2e86-114">CLR desteklemesi için `x:Object` temel öğesi <xref:System.Object> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="b2e86-115">Bu temel eleman uygulama biçimlendirme içinde genellikle kullanılmaz, ancak XAML türü bir sistemde atanabilirliği denetleme gibi bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="b2e86-116">x:Boole</span><span class="sxs-lookup"><span data-stu-id="b2e86-116">x:Boolean</span></span>  
 <span data-ttu-id="b2e86-117">CLR desteklemesi için `x:Boolean` temel öğesi <xref:System.Boolean> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="b2e86-118">XAML, değerleri `x:Boolean` için ayrıştırır; büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="b2e86-119">`x:Bool` kabul edilen bir alternatif olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b2e86-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="b2e86-120">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.17 ve 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="b2e86-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="b2e86-121">x:Char</span></span>  
 <span data-ttu-id="b2e86-122">CLR desteklemesi için `x:Char` temel öğesi <xref:System.Char> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="b2e86-123">Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="b2e86-124">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.7 ve 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="b2e86-125">x:Dize</span><span class="sxs-lookup"><span data-stu-id="b2e86-125">x:String</span></span>  
 <span data-ttu-id="b2e86-126">CLR desteklemesi için `x:String` temel öğesi <xref:System.String> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="b2e86-127">Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b2e86-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="b2e86-128">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="b2e86-129">x:Ondalık</span><span class="sxs-lookup"><span data-stu-id="b2e86-129">x:Decimal</span></span>  
 <span data-ttu-id="b2e86-130">CLR desteklemesi için `x:Decimal` temel öğesi <xref:System.Decimal> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="b2e86-131">XAML ayrıştırmanın `en-US` kültürü altında kendiliğinden yapıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b2e86-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="b2e86-132">`en-US` kültürü altında, ondalık sayı bileşenleri için doğru ayırıcı her zaman, geliştirme ortamının veya XAML'nin çalışma zamanında yüklendiği asıl son istemcinin kültür ayarları göz ardı edilerek her zaman bir noktadır (`.`) .</span><span class="sxs-lookup"><span data-stu-id="b2e86-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="b2e86-133">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.14 ve 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="b2e86-134">x:Tek</span><span class="sxs-lookup"><span data-stu-id="b2e86-134">x:Single</span></span>  
 <span data-ttu-id="b2e86-135">CLR desteklemesi için `x:Single` temel öğesi <xref:System.Single> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="b2e86-136">Sayısal değerlere ek olarak `x:Single` için metin sözdizimi `Infinity`, `-Infinity` ve `NaN` belirteçlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="b2e86-137">Bu belirteçlerin büyük/küçük harfe duyarlı olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="b2e86-138">`x:Single` metin sözdiziminin ilk karakteri `e` veya `E` ise değerleri bilimsel gösterim biçiminde destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="b2e86-139">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.8 ve 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="b2e86-140">x:Çift</span><span class="sxs-lookup"><span data-stu-id="b2e86-140">x:Double</span></span>  
 <span data-ttu-id="b2e86-141">CLR desteklemesi için `x:Double` temel öğesi <xref:System.Double> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="b2e86-142">Sayısal değerlere ek olarak `x:Double` için metin sözdizimi `Infinity`, `-Infinity` ve `NaN` belirteçlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="b2e86-143">Bu belirteçlerin büyük/küçük harfe duyarlı olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="b2e86-144">`x:Double` değerleri bilimsel gösterim biçiminde destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="b2e86-145">Üs bölümü tanıtmak için `e` veya `E` karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2e86-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="b2e86-146">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.9 ve 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="b2e86-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="b2e86-147">x:Int16</span></span>  
 <span data-ttu-id="b2e86-148">CLR yedekleme için `x:Int16` karşılık gelen temel <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="b2e86-149">XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b2e86-150">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.11 ve 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="b2e86-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="b2e86-151">x:Int32</span></span>  
 <span data-ttu-id="b2e86-152">CLR desteklemesi için `x:Int32` temel öğesi <xref:System.Int32> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="b2e86-153">`x:Int32` işaretlenmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="b2e86-154">XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b2e86-155">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.12 ve 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="b2e86-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="b2e86-156">x:Int64</span></span>  
 <span data-ttu-id="b2e86-157">CLR desteklemesi için `x:Int64` temel öğesi <xref:System.Int64> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="b2e86-158">`x:Int64` işaretlenmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="b2e86-159">XAML içinde metin sözdiziminde artı (`+`) işaretinin olmaması pozitif imzalı değer olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="b2e86-160">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.13 ve 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="b2e86-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b2e86-161">x:TimeSpan</span></span>  
 <span data-ttu-id="b2e86-162">CLR desteklemesi için `x:TimeSpan` temel öğesi <xref:System.TimeSpan> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="b2e86-163">Saat tarih biçimi için XAML ayrıştırmanın `en-US` kültürü altında kendiliğinden yapıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b2e86-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="b2e86-164">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.16 ve 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="b2e86-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="b2e86-165">x:Uri</span></span>  
 <span data-ttu-id="b2e86-166">CLR desteklemesi için `x:Uri` temel öğesi <xref:System.Uri> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="b2e86-167">Protokollerin denetimi, `x:Uri` için XAML tanımının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="b2e86-168">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.15 ve 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="b2e86-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="b2e86-169">x:Byte</span></span>  
 <span data-ttu-id="b2e86-170">CLR desteklemesi için `x:Byte` temel öğesi <xref:System.Byte> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="b2e86-171"><xref:System.Byte> / `x:Byte` imzasız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="b2e86-172">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.10 ve 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="b2e86-173">x:Dizi</span><span class="sxs-lookup"><span data-stu-id="b2e86-173">x:Array</span></span>  
 <span data-ttu-id="b2e86-174">CLR desteklemesi için `x:Array` temel öğesi <xref:System.Array> öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="b2e86-175">Bir diziyi, biçimlendirme uzantısı söz dizimini kullanarak XAML 2006 ' de tanımlayabilirsiniz; Ancak XAML 2009 sözdizimi, biçimlendirme uzantısına erişmeyi gerektirmeyen dil tanımlı bir temel dildir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="b2e86-176">XAML 2006 desteği hakkında daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="b2e86-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="b2e86-177">XAML dil belirtimi tanımı için bkz. [\[MS-XAML\] sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="b2e86-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="b2e86-178">WPF Desteği</span><span class="sxs-lookup"><span data-stu-id="b2e86-178">WPF Support</span></span>  
 <span data-ttu-id="b2e86-179">WPF 'de XAML 2009 özelliklerini, ancak yalnızca işaretleme ile derlenen XAML için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2e86-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="b2e86-180">WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="b2e86-181">XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsa ve bu XAML 'yi <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>bir WPF çalışma zamanına ve nesne grafiğine yüklerseniz.</span><span class="sxs-lookup"><span data-stu-id="b2e86-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2e86-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlReader.Load%2A>, XAML 2009 dil anahtar sözcüklerini ve özelliklerini geçerli bir nesne grafiği temsiline işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b2e86-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
