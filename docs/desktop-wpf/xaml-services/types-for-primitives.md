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
ms.openlocfilehash: ec0e2a29a191d5057ce66a5f3272d00e92b01bd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540035"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="ad737-102">Ortak XAML dil temelleri için yerleşik türler</span><span class="sxs-lookup"><span data-stu-id="ad737-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="ad737-103">XAML 2009, ortak dil çalışma zamanında (CLR) ve diğer programlama dillerinde sık kullanılan temel elemanlar olan çeşitli veri türleri için XAML dil düzeyinde destek sunar.</span><span class="sxs-lookup"><span data-stu-id="ad737-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="ad737-104">XAML 2009, bu temel öğeler için destek ekler: `x:Object` , `x:Boolean` ,, `x:Char` `x:String` , `x:Decimal` , `x:Single` , `x:Double` , `x:Int16` , `x:Int32` , `x:Int64` , `x:TimeSpan` , `x:Uri` , `x:Byte` ve `x:Array`</span><span class="sxs-lookup"><span data-stu-id="ad737-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="ad737-105">XAML biçimlendirmesinde dil temelleri için önceki teknikler</span><span class="sxs-lookup"><span data-stu-id="ad737-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="ad737-106">Önceki WPF sürümleri için XAML 'de, .NET Framework için bir CLR ilkel tanım sınıfı içeren derlemeyi ve ad alanını eşleyerek CLR dil temel temellerine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad737-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="ad737-107">Bunların çoğu mscorlib derlemesinde ve <xref:System> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad737-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="ad737-108">Örneğin, kullanmak için <xref:System.Int32> aşağıdaki eşlemeyi bildirebilirsiniz (bundan sonra bir örnek kullanım ile gösterilir):</span><span class="sxs-lookup"><span data-stu-id="ad737-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="ad737-109">XAML 2009 dil temelleri</span><span class="sxs-lookup"><span data-stu-id="ad737-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="ad737-110">Kurala göre, XAML için dil temelleri ve diğer XAML dil öğeleri, `x:` ön ek dahil gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="ad737-111">XAML dil öğeleri genellikle gerçek zamanlı biçimlendirmede kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad737-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="ad737-112">Bu kural, WPF 'de XAML için kavramsal belgelerde ve ayrıca XAML belirtiminde izlenir.</span><span class="sxs-lookup"><span data-stu-id="ad737-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="ad737-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="ad737-113">x:Object</span></span>

<span data-ttu-id="ad737-114">CLR yedeklemesi için, `x:Object` ilkel öğesine karşılık gelir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="ad737-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="ad737-115">Bu ilkel genellikle uygulama biçimlendirmesinde kullanılmaz, ancak bir XAML tür sisteminde atananlıya bilirlik gibi bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="ad737-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="ad737-116">x:Boolean</span></span>

<span data-ttu-id="ad737-117">CLR yedeklemesi için, `x:Boolean` ilkel öğesine karşılık gelir <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="ad737-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="ad737-118">XAML, `x:Boolean` büyük/küçük harfe duyarsız değerleri ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="ad737-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="ad737-119">`x:Bool`Kabul edilen bir alternatif değildir.</span><span class="sxs-lookup"><span data-stu-id="ad737-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="ad737-120">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.17 ve 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="ad737-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="ad737-121">x:Char</span></span>

<span data-ttu-id="ad737-122">CLR yedeklemesi için, `x:Char` ilkel öğesine karşılık gelir <xref:System.Char> .</span><span class="sxs-lookup"><span data-stu-id="ad737-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="ad737-123">Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="ad737-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="ad737-124">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.7 ve 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="ad737-125">x:String</span><span class="sxs-lookup"><span data-stu-id="ad737-125">x:String</span></span>

<span data-ttu-id="ad737-126">CLR yedeklemesi için, `x:String` ilkel öğesine karşılık gelir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="ad737-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="ad737-127">Dize ve karakter türlerinin, XML düzeyinde dosyanın genel kodlamasıyla etkileşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="ad737-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="ad737-128">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="ad737-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="ad737-129">x:Decimal</span></span>

<span data-ttu-id="ad737-130">CLR yedeklemesi için, `x:Decimal` ilkel öğesine karşılık gelir <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="ad737-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="ad737-131">XAML ayrıştırma, kültür altında kendiliğinden yapılır `en-US` .</span><span class="sxs-lookup"><span data-stu-id="ad737-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="ad737-132">`en-US`Kültür altında, bir Decimal bileşenleri için doğru ayırıcı, `.` geliştirme ortamının kültür ayarlarından ya da xaml 'nin çalışma zamanında yüklendiği son istemci hedefinde bağımsız olarak her zaman bir nokta () olur.</span><span class="sxs-lookup"><span data-stu-id="ad737-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="ad737-133">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.14 ve 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="ad737-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="ad737-134">x:Single</span></span>

<span data-ttu-id="ad737-135">CLR yedeklemesi için, `x:Single` ilkel öğesine karşılık gelir <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="ad737-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="ad737-136">Sayısal değerlere ek olarak, için de metin sözdizimi, `x:Single` ve belirteçlerine izin `Infinity` verir `-Infinity` `NaN` .</span><span class="sxs-lookup"><span data-stu-id="ad737-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="ad737-137">Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="ad737-138">`x:Single` metin sözdiziminde ilk karakter veya ise, bilimsel gösterim biçimindeki değerleri destekleyebilir `e` `E` .</span><span class="sxs-lookup"><span data-stu-id="ad737-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="ad737-139">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.8 ve 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="ad737-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="ad737-140">x:Double</span></span>

<span data-ttu-id="ad737-141">CLR yedeklemesi için, `x:Double` ilkel öğesine karşılık gelir <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="ad737-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="ad737-142">Sayısal değerlere ek olarak, için metin sözdizimi, `x:Double` ve belirteçlerine izin `Infinity` verir `-Infinity` `NaN` .</span><span class="sxs-lookup"><span data-stu-id="ad737-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="ad737-143">Bu belirteçler büyük/küçük harfe duyarlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="ad737-144">`x:Double` , bilimsel gösterim biçimindeki değerleri destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="ad737-145">`e` `E` Üs kısmını tanıtmak için veya karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad737-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="ad737-146">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.9 ve 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="ad737-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="ad737-147">x:Int16</span></span>

<span data-ttu-id="ad737-148">CLR yedeklemesi için, `x:Int16` ilkel öğesine karşılık gelir <xref:System.Int16> ve `x:Int16` imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="ad737-149">XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.</span><span class="sxs-lookup"><span data-stu-id="ad737-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="ad737-150">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.11 ve 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="ad737-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="ad737-151">x:Int32</span></span>

<span data-ttu-id="ad737-152">CLR yedeklemesi için, `x:Int32` ilkel öğesine karşılık gelir <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="ad737-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="ad737-153">`x:Int32` imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="ad737-154">XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.</span><span class="sxs-lookup"><span data-stu-id="ad737-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="ad737-155">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.12 ve 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="ad737-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="ad737-156">x:Int64</span></span>

<span data-ttu-id="ad737-157">CLR yedeklemesi için, `x:Int64` ilkel öğesine karşılık gelir <xref:System.Int64> .</span><span class="sxs-lookup"><span data-stu-id="ad737-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="ad737-158">`x:Int64` imzalı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="ad737-159">XAML 'de, artı ( `+` ) işareti metin sözdiziminde devamsızlık pozitif bir işaretli değer olarak kapsanır.</span><span class="sxs-lookup"><span data-stu-id="ad737-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="ad737-160">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.13 ve 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="ad737-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ad737-161">x:TimeSpan</span></span>

<span data-ttu-id="ad737-162">CLR yedeklemesi için, `x:TimeSpan` ilkel öğesine karşılık gelir <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="ad737-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="ad737-163">Zaman tarih biçimi için XAML ayrıştırma, kültür altında kendiliğinden yapılır `en-US` .</span><span class="sxs-lookup"><span data-stu-id="ad737-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="ad737-164">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.16 ve 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="ad737-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="ad737-165">x:Uri</span></span>

<span data-ttu-id="ad737-166">CLR yedeklemesi için, `x:Uri` ilkel öğesine karşılık gelir <xref:System.Uri> .</span><span class="sxs-lookup"><span data-stu-id="ad737-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="ad737-167">Protokollerin denetlenmesi için XAML tanımının bir parçası değildir `x:Uri` .</span><span class="sxs-lookup"><span data-stu-id="ad737-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="ad737-168">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.15 ve 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="ad737-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="ad737-169">x:Byte</span></span>

<span data-ttu-id="ad737-170">CLR yedeklemesi için, `x:Byte` ilkel öğesine karşılık gelir <xref:System.Byte> .</span><span class="sxs-lookup"><span data-stu-id="ad737-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="ad737-171"><xref:System.Byte>  /  `x:Byte` , İmzasız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="ad737-172">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.10 ve 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="ad737-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="ad737-173">x:Array</span></span>

<span data-ttu-id="ad737-174">CLR yedeklemesi için, `x:Array` ilkel öğesine karşılık gelir <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="ad737-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="ad737-175">Bir diziyi, biçimlendirme uzantısı söz dizimini kullanarak XAML 2006 ' de tanımlayabilirsiniz; Ancak XAML 2009 sözdizimi, biçimlendirme uzantısına erişmeyi gerektirmeyen dil tanımlı bir temel dildir.</span><span class="sxs-lookup"><span data-stu-id="ad737-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="ad737-176">XAML 2006 desteği hakkında daha fazla bilgi için bkz. [X:Array Işaretleme uzantısı](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="ad737-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="ad737-177">XAML dil belirtimi tanımı için bkz. [ \[ MS-xaml \] sections 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ad737-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="ad737-178">WPF desteği</span><span class="sxs-lookup"><span data-stu-id="ad737-178">WPF Support</span></span>

<span data-ttu-id="ad737-179">WPF 'de XAML 2009 özelliklerini, ancak yalnızca işaretleme ile derlenen XAML için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad737-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="ad737-180">WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="ad737-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="ad737-181">XAML 2009 özelliklerini WPF ile birlikte kullanabileceğiniz bir senaryo, gevşek XAML yazarsa ve bu XAML 'yi ile bir WPF çalışma zamanına ve nesne grafiğine yüklerseniz <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ad737-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad737-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve, <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcüklerini ve özelliklerini geçerli bir nesne grafiği temsiline işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ad737-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
