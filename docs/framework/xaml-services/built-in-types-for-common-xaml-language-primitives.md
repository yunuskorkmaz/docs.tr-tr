---
title: "XAML Dili Ortak Temelleri İçin Yerleşik Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 2b960e52d8d7dca590411f1c5f096a6942e1ade9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="c6910-102">XAML Dili Ortak Temelleri İçin Yerleşik Türler</span><span class="sxs-lookup"><span data-stu-id="c6910-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="c6910-103">XAML 2009 sık kullanılan temelleri ortak dil çalışma zamanı (CLR) ve diğer programlama dilleri olan çeşitli veri türleri için XAML dil düzeyi destek sunar.</span><span class="sxs-lookup"><span data-stu-id="c6910-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="c6910-104">XAML 2009 bu temelleri için destek ekler: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, ve`x:Array`</span><span class="sxs-lookup"><span data-stu-id="c6910-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="c6910-105">XAML biçimlendirme dil temelleri için önceki teknikleri</span><span class="sxs-lookup"><span data-stu-id="c6910-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="c6910-106">XAML'de önceki WPF sürümleri için derleme ve .NET Framework CLR ilkel tanımı sınıf bulunan ad alanını eşleyerek CLR dil temelleri başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="c6910-107">Bu çoğu mscorlib derlemede ve <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c6910-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="c6910-108">Örneğin, kullanılacak <xref:System.Int32>, aşağıdaki eşleme (Bundan sonra gösterilen kullanım örneği ile) bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6910-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="c6910-109">XAML 2009 dil temelleri</span><span class="sxs-lookup"><span data-stu-id="c6910-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="c6910-110">Kurala göre XAML ve diğer tüm XAML dil öğeleri için dil temelleri dahil olmak üzere gösterilir `x:` öneki.</span><span class="sxs-lookup"><span data-stu-id="c6910-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="c6910-111">XAML dil öğeleri genellikle kullanılan gerçek biçimlendirmede nasıl budur.</span><span class="sxs-lookup"><span data-stu-id="c6910-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="c6910-112">Bu kural, XAML WPF hem de XAML belirtimi kavramsal belgelerindeki izlenir.</span><span class="sxs-lookup"><span data-stu-id="c6910-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="c6910-113">x: nesne</span><span class="sxs-lookup"><span data-stu-id="c6910-113">x:Object</span></span>  
 <span data-ttu-id="c6910-114">CLR yedekleme için `x:Object` ilkel karşılık gelen <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c6910-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="c6910-115">Bu temel genellikle uygulama biçimlendirmede kullanılmaz, ancak bir XAML türü sisteminde assignability denetimi gibi bazı senaryolar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="c6910-116">x: Boolean</span><span class="sxs-lookup"><span data-stu-id="c6910-116">x:Boolean</span></span>  
 <span data-ttu-id="c6910-117">CLR yedekleme için `x:Boolean` ilkel karşılık gelen <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="c6910-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="c6910-118">XAML ayrıştırmak için değerleri `x:Boolean` olarak büyük küçük harfe duyarlı.</span><span class="sxs-lookup"><span data-stu-id="c6910-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="c6910-119">Unutmayın `x:Bool` kabul edilen alternatif değildir.</span><span class="sxs-lookup"><span data-stu-id="c6910-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="c6910-120">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.17 ve 5.4.11 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="c6910-121">x: Char</span><span class="sxs-lookup"><span data-stu-id="c6910-121">x:Char</span></span>  
 <span data-ttu-id="c6910-122">CLR yedekleme için `x:Char` ilkel karşılık gelen <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="c6910-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="c6910-123">Dize ve karakter türleri XML düzeyinde dosya genel kodlama ile etkileşim sahip.</span><span class="sxs-lookup"><span data-stu-id="c6910-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="c6910-124">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.7'ye ve 5.4.1 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="c6910-125">x: String</span><span class="sxs-lookup"><span data-stu-id="c6910-125">x:String</span></span>  
 <span data-ttu-id="c6910-126">CLR yedekleme için `x:String` ilkel karşılık gelen <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c6910-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="c6910-127">Dize ve karakter türleri XML düzeyinde dosya genel kodlama ile etkileşim sahip.</span><span class="sxs-lookup"><span data-stu-id="c6910-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="c6910-128">XAML dil belirtimi, bkz. [ \[MS XAML\] bölümleri 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="c6910-129">x: ondalık</span><span class="sxs-lookup"><span data-stu-id="c6910-129">x:Decimal</span></span>  
 <span data-ttu-id="c6910-130">CLR yedekleme için `x:Decimal` ilkel karşılık gelen <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="c6910-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="c6910-131">XAML ayrıştırma kendiliğinden altında yapıldığını unutmayın `en-US` kültür.</span><span class="sxs-lookup"><span data-stu-id="c6910-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="c6910-132">Altında `en-US` , ondalık bileşenleri için doğru ayırıcı kültürdür her zaman bir süre (`.`) geliştirme ortamı veya çalışma zamanında XAML yüklendiği nihai istemci hedef kültür ayarları ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="c6910-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="c6910-133">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.14 ve 5.4.8 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="c6910-134">x: Single</span><span class="sxs-lookup"><span data-stu-id="c6910-134">x:Single</span></span>  
 <span data-ttu-id="c6910-135">CLR yedekleme için `x:Single` ilkel karşılık gelen <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="c6910-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="c6910-136">Sayısal değerler için metin sözdizimi yanı sıra `x:Single` ayrıca belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c6910-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="c6910-137">Bu belirteçler olarak büyük küçük harfe duyarlı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="c6910-138">`x:Single`ilk karakter, metin sözdizimi ise değerleri bilimsel gösterim biçiminde destekleyebilir `e` veya `E`.</span><span class="sxs-lookup"><span data-stu-id="c6910-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="c6910-139">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.8 ve 5.4.2 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="c6910-140">x: Double</span><span class="sxs-lookup"><span data-stu-id="c6910-140">x:Double</span></span>  
 <span data-ttu-id="c6910-141">CLR yedekleme için `x:Double` ilkel karşılık gelen <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="c6910-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="c6910-142">Sayısal değerler için metin sözdizimi yanı sıra `x:Double` belirteçleri verir `Infinity`, `-Infinity`, ve `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c6910-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="c6910-143">Bu belirteçler olarak büyük küçük harfe duyarlı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="c6910-144">`x:Double`değerleri bilimsel gösterim biçiminde destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="c6910-145">Karakter kullanın `e` veya `E` üs bölümü tanıtmak için.</span><span class="sxs-lookup"><span data-stu-id="c6910-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="c6910-146">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.9 ve 5.4.3 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="c6910-147">x: Int16</span><span class="sxs-lookup"><span data-stu-id="c6910-147">x:Int16</span></span>  
 <span data-ttu-id="c6910-148">CLR yedekleme için `x:Int16` ilkel karşılık gelen <xref:System.Int16> ve `x:Int16` imzalanmış olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="c6910-149">XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.</span><span class="sxs-lookup"><span data-stu-id="c6910-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c6910-150">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.11 ve 5.4.5 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="c6910-151">x: Int32</span><span class="sxs-lookup"><span data-stu-id="c6910-151">x:Int32</span></span>  
 <span data-ttu-id="c6910-152">CLR yedekleme için `x:Int32` ilkel karşılık gelen <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="c6910-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="c6910-153">`x:Int32`imzalanmış olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="c6910-154">XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.</span><span class="sxs-lookup"><span data-stu-id="c6910-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c6910-155">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.12 ve 5.4.6 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="c6910-156">x: Int64</span><span class="sxs-lookup"><span data-stu-id="c6910-156">x:Int64</span></span>  
 <span data-ttu-id="c6910-157">CLR yedekleme için `x:Int64` ilkel karşılık gelen <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c6910-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="c6910-158">`x:Int64`imzalanmış olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="c6910-159">XAML'de artı yokluğu (`+`) metin sözdiziminde oturum olarak imzalanmış pozitif kapsanan.</span><span class="sxs-lookup"><span data-stu-id="c6910-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c6910-160">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.13 ve 5.4.7 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="c6910-161">x: TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c6910-161">x:TimeSpan</span></span>  
 <span data-ttu-id="c6910-162">CLR yedekleme için `x:TimeSpan` ilkel karşılık gelen <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c6910-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="c6910-163">Bu XAML ayrıştırma saat ve tarih biçimi kendiliğinden altında bitti için Not `en-US` kültür.</span><span class="sxs-lookup"><span data-stu-id="c6910-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="c6910-164">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.16 ve 5.4.10 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="c6910-165">x: Uri</span><span class="sxs-lookup"><span data-stu-id="c6910-165">x:Uri</span></span>  
 <span data-ttu-id="c6910-166">CLR yedekleme için `x:Uri` ilkel karşılık gelen <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="c6910-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="c6910-167">Protokolleri denetimi için XAML tanımının bir parçası değil `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="c6910-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="c6910-168">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.15 ve 5.4.9 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="c6910-169">x: Byte</span><span class="sxs-lookup"><span data-stu-id="c6910-169">x:Byte</span></span>  
 <span data-ttu-id="c6910-170">CLR yedekleme için `x:Byte` ilkel karşılık gelen <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="c6910-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="c6910-171">A <xref:System.Byte>  /  `x:Byte` davranılır olarak imzalanmamış.</span><span class="sxs-lookup"><span data-stu-id="c6910-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="c6910-172">XAML dil belirtimi, bkz. [ \[MS XAML\] 5.2.10 ve 5.4.4 bölümlerine](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="c6910-173">x: Array</span><span class="sxs-lookup"><span data-stu-id="c6910-173">x:Array</span></span>  
 <span data-ttu-id="c6910-174">CLR yedekleme için `x:Array` ilkel karşılık gelen <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="c6910-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="c6910-175">Biçimlendirme uzantısı sözdizimi kullanarak, bir dizi XAML 2006'tanımlayabilirsiniz; Ancak, XAML 2009 söz dizimi biçimlendirme uzantısı erişme gerektirmez dili tarafından tanımlanan bir ilkel olur.</span><span class="sxs-lookup"><span data-stu-id="c6910-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="c6910-176">XAML 2006 desteği hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c6910-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="c6910-177">XAML dil belirtimi, bkz. [ \[MS XAML\] bölümleri 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c6910-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="c6910-178">WPF desteği</span><span class="sxs-lookup"><span data-stu-id="c6910-178">WPF Support</span></span>  
 <span data-ttu-id="c6910-179">WPF'de, ancak yalnızca biçimlendirme-derlenmemiş XAML için XAML 2009 özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6910-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="c6910-180">XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.</span><span class="sxs-lookup"><span data-stu-id="c6910-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="c6910-181">Burada kullanabileceğiniz XAML 2009 özellikleri WPF ile birlikte bir gevşek XAML yazar ve ardından bir WPF çalışma zamanı ve Nesne grafiği içine bu XAML yükleyin senaryodur <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6910-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c6910-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve kendi <xref:System.Windows.Markup.XamlReader.Load%2A> XAML 2009 dil anahtar sözcükleri ve özellikleri geçerli nesne grafiği gösterimine işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c6910-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
