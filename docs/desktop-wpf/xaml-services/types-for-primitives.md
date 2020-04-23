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
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071838"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="a3df9-102">Ortak XAML dil ilkelleri için yerleşik türleri</span><span class="sxs-lookup"><span data-stu-id="a3df9-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="a3df9-103">XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan çeşitli veri türleri için XAML dil düzeyinde destek sunar.</span><span class="sxs-lookup"><span data-stu-id="a3df9-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="a3df9-104">XAML 2009 bu ilkel için `x:Object` `x:Boolean`destek `x:Char` `x:String`ekler: `x:Single` `x:Double`, `x:Int16` `x:Int32` `x:Int64` `x:TimeSpan` `x:Uri` `x:Decimal`, , `x:Byte`, , , , , ,`x:Array`</span><span class="sxs-lookup"><span data-stu-id="a3df9-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="a3df9-105">XAML Biçimlendirmede Dil İlkelleri Için Önceki Teknikler</span><span class="sxs-lookup"><span data-stu-id="a3df9-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="a3df9-106">Önceki WPF sürümleri için XAML'de, .NET Framework için CLR ilkel tanım sınıfı içeren derleme ve ad alanını eşleyerek CLR dil ilkellerine başvuruda bulunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3df9-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="a3df9-107">Bunların çoğu mscorlib montaj ve <xref:System> ad alanı bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3df9-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="a3df9-108">Örneğin, kullanmak <xref:System.Int32>için, aşağıdaki eşleme (bundan sonra gösterilen bir örnek kullanımı ile) bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a3df9-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="a3df9-109">XAML 2009 Dil İlkel</span><span class="sxs-lookup"><span data-stu-id="a3df9-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="a3df9-110">Kural olarak, XAML ve diğer tüm XAML dil öğeleri için `x:` dil ilkel, önek de dahil olmak üzere gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="a3df9-111">XAML dil öğeleri genellikle gerçek dünya biçimlendirmesinde bu şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3df9-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="a3df9-112">Bu sözleşme, WPF'deki XAML kavramsal dokümantasyonlarında ve ayrıca XAML belirtiminde takip edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="a3df9-113">x:Nesne</span><span class="sxs-lookup"><span data-stu-id="a3df9-113">x:Object</span></span>

<span data-ttu-id="a3df9-114">CLR desteği `x:Object` için, <xref:System.Object>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="a3df9-115">Bu ilkel genellikle uygulama biçimlendirmesinde kullanılmaz, ancak XAML türü sistemde atabilmeyi denetleme gibi bazı senaryolar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="a3df9-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="a3df9-116">x:Boolean</span></span>

<span data-ttu-id="a3df9-117">CLR desteği `x:Boolean` için, <xref:System.Boolean>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="a3df9-118">XAML, değerleri `x:Boolean` karşıkonuolmayan durum olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="a3df9-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="a3df9-119">`x:Bool` Kabul edilen bir alternatif olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="a3df9-120">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.17 ve 5.4.11'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="a3df9-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="a3df9-121">x:Char</span></span>

<span data-ttu-id="a3df9-122">CLR desteği `x:Char` için, <xref:System.Char>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="a3df9-123">Dize ve char türleri, XML düzeyinde dosyanın genel kodlaması ile etkileşime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="a3df9-124">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölüm 5.2.7 ve 5.4.1'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="a3df9-125">x:Dize</span><span class="sxs-lookup"><span data-stu-id="a3df9-125">x:String</span></span>

<span data-ttu-id="a3df9-126">CLR desteği `x:String` için, <xref:System.String>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="a3df9-127">Dize ve char türleri, XML düzeyinde dosyanın genel kodlaması ile etkileşime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="a3df9-128">XAML dil belirtimi tanımı için [ \[MS-XAML\] Bölümleri 5.2.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="a3df9-129">x:Ondalık</span><span class="sxs-lookup"><span data-stu-id="a3df9-129">x:Decimal</span></span>

<span data-ttu-id="a3df9-130">CLR desteği `x:Decimal` için, <xref:System.Decimal>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="a3df9-131">XAML ayrıştırma doğal `en-US` olarak kültür altında yapılır.</span><span class="sxs-lookup"><span data-stu-id="a3df9-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="a3df9-132">Kültür `en-US` altında, ondalık bileşenler için doğru ayırıcı her`.`zaman bir dönemdir ( ) geliştirme ortamının kültür ayarları ne olursa olsun, ya da XAML çalışma zamanında yüklenir nihai istemci hedefi.</span><span class="sxs-lookup"><span data-stu-id="a3df9-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="a3df9-133">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.14 ve 5.4.8'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="a3df9-134">x:Tek</span><span class="sxs-lookup"><span data-stu-id="a3df9-134">x:Single</span></span>

<span data-ttu-id="a3df9-135">CLR desteği `x:Single` için, <xref:System.Single>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="a3df9-136">Sayısal değerlere ek olarak, metin `x:Single` sözdizimi de belirteçleri `Infinity`, ve `-Infinity` `NaN`.</span><span class="sxs-lookup"><span data-stu-id="a3df9-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="a3df9-137">Bu belirteçler duruma duyarlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="a3df9-138">`x:Single`metin sözdiziminde ilk karakter `e` veya `E`.</span><span class="sxs-lookup"><span data-stu-id="a3df9-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="a3df9-139">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölüm 5.2.8 ve 5.4.2'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="a3df9-140">x:Çift</span><span class="sxs-lookup"><span data-stu-id="a3df9-140">x:Double</span></span>

<span data-ttu-id="a3df9-141">CLR desteği `x:Double` için, <xref:System.Double>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="a3df9-142">`x:Double` Sayısal değerlere ek olarak, belirteçlere `Infinity`izin vermek için `-Infinity`metin `NaN`sözdizimi , ve .</span><span class="sxs-lookup"><span data-stu-id="a3df9-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="a3df9-143">Bu belirteçler duruma duyarlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="a3df9-144">`x:Double`değerleri bilimsel gösterim biçiminde destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="a3df9-145">Karakteri `e` kullanın `E` veya üs kısmını tanıtmak için.</span><span class="sxs-lookup"><span data-stu-id="a3df9-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="a3df9-146">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.9 ve 5.4.3'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="a3df9-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="a3df9-147">x:Int16</span></span>

<span data-ttu-id="a3df9-148">CLR desteği için, `x:Int16` <xref:System.Int16> ilkel karşılık `x:Int16` gelir ve imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="a3df9-149">XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="a3df9-150">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.11 ve 5.4.5'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="a3df9-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="a3df9-151">x:Int32</span></span>

<span data-ttu-id="a3df9-152">CLR desteği `x:Int32` için, <xref:System.Int32>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="a3df9-153">`x:Int32`imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="a3df9-154">XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="a3df9-155">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.12 ve 5.4.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="a3df9-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="a3df9-156">x:Int64</span></span>

<span data-ttu-id="a3df9-157">CLR desteği `x:Int64` için, <xref:System.Int64>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="a3df9-158">`x:Int64`imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="a3df9-159">XAML'de, metin sözdiziminde artı ( )`+`işaretinin olmaması pozitif imzalı değer olarak ima edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="a3df9-160">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.13 ve 5.4.7'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="a3df9-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="a3df9-161">x:TimeSpan</span></span>

<span data-ttu-id="a3df9-162">CLR desteği `x:TimeSpan` için, <xref:System.TimeSpan>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="a3df9-163">XAML zaman-tarih biçimi için ayrıştırma `en-US` doğal olarak kültür altında yapılır.</span><span class="sxs-lookup"><span data-stu-id="a3df9-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="a3df9-164">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.16 ve 5.4.10'a](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="a3df9-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="a3df9-165">x:Uri</span></span>

<span data-ttu-id="a3df9-166">CLR desteği `x:Uri` için, <xref:System.Uri>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="a3df9-167">Protokolleri denetlemek `x:Uri`XAML tanımının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="a3df9-168">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.15 ve 5.4.9'a](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="a3df9-169">x:Bayt</span><span class="sxs-lookup"><span data-stu-id="a3df9-169">x:Byte</span></span>

<span data-ttu-id="a3df9-170">CLR desteği `x:Byte` için, <xref:System.Byte>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="a3df9-171"><xref:System.Byte>  /  A `x:Byte` imzasız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="a3df9-172">XAML dil belirtimi tanımı için [ \[\] MS-XAML Bölümleri 5.2.10 ve 5.4.4'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="a3df9-173">x:Dizi</span><span class="sxs-lookup"><span data-stu-id="a3df9-173">x:Array</span></span>

<span data-ttu-id="a3df9-174">CLR desteği `x:Array` için, <xref:System.Array>ilkel karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="a3df9-175">XAML 2006'da bir dizi biçimlendirme uzantısı sözdizimini kullanarak tanımlayabilirsiniz; ancak, XAML 2009 sözdizimi bir biçimlendirme uzantısı erişim gerektirmeyen bir dil tanımlı ilkel.</span><span class="sxs-lookup"><span data-stu-id="a3df9-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="a3df9-176">XAML 2006 desteği hakkında daha fazla bilgi için [bkz: x:Array Markup Extension](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="a3df9-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="a3df9-177">XAML dil belirtimi tanımı için [ \[MS-XAML\] Bölümleri 5.2.18'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="a3df9-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="a3df9-178">WPF Desteği</span><span class="sxs-lookup"><span data-stu-id="a3df9-178">WPF Support</span></span>

<span data-ttu-id="a3df9-179">WPF'de XAML 2009 özelliklerini ancak yalnızca biçimlendirmeyle derlenen XAML için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3df9-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="a3df9-180">WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a3df9-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="a3df9-181">XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsanız ve bu XAML'yi <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>WPF çalışma süresi ve nesne grafiğine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a3df9-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a3df9-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlReader.Load%2A> onun XAML 2009 dil anahtar kelimeleri ve özellikleri geçerli bir nesne grafik gösterimi içine işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a3df9-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
