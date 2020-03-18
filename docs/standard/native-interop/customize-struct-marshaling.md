---
title: Yapı yı özelleştirme - .NET
description: .NET'in yapılarınızı yerel bir gösterime nasıl görebildiğini öğrenin.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400374"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="98daa-103">Yapı hazırlamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98daa-103">Customizing structure marshaling</span></span>

<span data-ttu-id="98daa-104">Bazen yapılar için varsayılan mareşalleme kuralları tam olarak ihtiyacınız olan şey değildir.</span><span class="sxs-lookup"><span data-stu-id="98daa-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="98daa-105">.NET çalışma saatleri, yapınızın düzenini ve alanların nasıl marshaled'ini özelleştirmeniz için birkaç uzantı noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="98daa-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="98daa-106">Yapı düzenini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98daa-106">Customizing structure layout</span></span>

<span data-ttu-id="98daa-107">.NET, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> alanların belleğe <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> nasıl yerleştirildiğini özelleştirmenize olanak tanıyan öznitelik ve numaralandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="98daa-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="98daa-108">Aşağıdaki kılavuz, sık karşılaşılan sorunları önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="98daa-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="98daa-109">✔️ mümkün `LayoutKind.Sequential` olduğunca kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="98daa-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="98daa-110">✔️ yalnızca `LayoutKind.Explicit` yerel yapınız da birleşim gibi açık bir düzene sahipse, mareşallikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="98daa-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="98daa-111">❌.NET `LayoutKind.Explicit` Core 3.0'dan önce çalışma sürelerini hedeflemeniz gerekiyorsa, Windows dışı platformlarda yapıları mareşallik yaparken kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="98daa-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="98daa-112">3.0'dan önceki .NET Core çalışma süresi, Intel veya AMD 64 bit Windows dışı sistemlerde açık yapıların yerel işlevlere değer olarak geçirilmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98daa-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="98daa-113">Ancak, çalışma zamanı tüm platformlarda başvuru ile açık yapıları geçen destekler.</span><span class="sxs-lookup"><span data-stu-id="98daa-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="98daa-114">Boolean mareşalözelleme</span><span class="sxs-lookup"><span data-stu-id="98daa-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="98daa-115">Yerel kod birçok farklı boolean gösterimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="98daa-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="98daa-116">Sadece Windows'da boolean değerlerini temsil etmenin üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="98daa-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="98daa-117">Çalışma zamanı yapınızın yerel tanımını bilmiyor, bu yüzden yapabileceği en iyi şey boolean değerlerinizi nasıl kareşalyapacağınız hakkında bir tahminde bulunmaktır.</span><span class="sxs-lookup"><span data-stu-id="98daa-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="98daa-118">.NET çalışma zamanı, boolean alanınızı nasıl mareşallik ediniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="98daa-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="98daa-119">Aşağıdaki örnekler , .NET'in `bool` farklı yerli boolean türlerine nasıl atandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98daa-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="98daa-120">Boolean değerleri varsayılan olarak aşağıdaki örnekte gösterildiği gibi [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) yerel 4 bayt lık win32 değeri olarak marshaling için:</span><span class="sxs-lookup"><span data-stu-id="98daa-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="98daa-121">Açık olmak istiyorsanız, yukarıdaki yle <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> aynı davranışı elde etmek için değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98daa-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="98daa-122">Aşağıdaki `UnmanagedType.U1` değerleri `UnmanagedType.I1` veya değerleri kullanarak, çalışma zamanını `b` alanı 1 baytlık `bool` yerel bir tür olarak mareşal olarak yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

<span data-ttu-id="98daa-123">Windows'da, boolean <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değerinizi 2 baytlık `VARIANT_BOOL` bir değere göre düzenlemeyi çalışma zamanı söylemek için değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98daa-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> <span data-ttu-id="98daa-124">`VARIANT_BOOL`bu `VARIANT_TRUE = -1` ve `VARIANT_FALSE = 0`en bool türleri farklıdır.</span><span class="sxs-lookup"><span data-stu-id="98daa-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="98daa-125">Ayrıca, eşit olmayan tüm değerler `VARIANT_TRUE` yanlış olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="98daa-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="98daa-126">Dizi mareşalcilik özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98daa-126">Customizing array field marshaling</span></span>

<span data-ttu-id="98daa-127">.NET ayrıca dizi mareşallik özelleştirmek için birkaç yol içerir.</span><span class="sxs-lookup"><span data-stu-id="98daa-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="98daa-128">Varsayılan olarak, .NET dizileri öğelerin bitişik listesine işaretçi olarak alır:</span><span class="sxs-lookup"><span data-stu-id="98daa-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

<span data-ttu-id="98daa-129">COM API'leri ile birlikte arıyorsanız, dizileri nesne `SAFEARRAY*` olarak sıralamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="98daa-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="98daa-130">Bir diziyi <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> şöyle <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> bir şekilde mareşalleştirmek için `SAFEARRAY*`çalışma saatini söylemek için ve değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98daa-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

<span data-ttu-id="98daa-131">Eğer öğe nin ne tür özelleştirmek `SAFEARRAY`gerekiyorsa, o zaman <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe türünü özelleştirmek için `SAFEARRAY`ve alanları kullanabilirsiniz .</span><span class="sxs-lookup"><span data-stu-id="98daa-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="98daa-132">Diziyi yerinde yerleştirmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> mareşale diziyi yerinde mareşallik etmesini söylemek için değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="98daa-133">Bu mareşalliği kullanırken, çalışma zamanının yapı <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> için doğru bir alan ayırabilmesi için dizideki öğe sayısı için alana bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="98daa-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> <span data-ttu-id="98daa-134">.NET, c99 Esnek Dizi Üyesi olarak değişken uzunlukta bir dizi alanının marshaling desteklemez.</span><span class="sxs-lookup"><span data-stu-id="98daa-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="98daa-135">Dize mareşalleme özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98daa-135">Customizing string field marshaling</span></span>

<span data-ttu-id="98daa-136">.NET ayrıca dize alanlarını mareşallik için çok çeşitli özelleştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="98daa-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="98daa-137">Varsayılan olarak, .NET bir dizeyi null-sonlandırılan dize için işaretçi olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="98daa-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="98daa-138">Kodlama, <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanın değerine <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="98daa-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="98daa-139">Öznitelik belirtilmemişse, kodlama varsayılan olarak bir ANSI kodlamasına gelir.</span><span class="sxs-lookup"><span data-stu-id="98daa-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="98daa-140">Farklı alanlar için farklı kodlamalar kullanmanız veya yapı tanımınızda daha açık olmayı tercih ederseniz, <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> öznitelik <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> üzerinde veya değerleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="98daa-141">UTF-8 kodlamasını kullanarak dizelerinizi mareşalleştirmek istiyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> ''deki <xref:System.Runtime.InteropServices.MarshalAsAttribute>değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> <span data-ttu-id="98daa-142">Kullanmak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> için .NET Framework 4.7 (veya sonraki sürümler) veya .NET Core 1.1 (veya daha sonraki sürümler) gerekir.</span><span class="sxs-lookup"><span data-stu-id="98daa-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="98daa-143">.NET Standart 2.0'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98daa-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="98daa-144">COM API'leri ile çalışıyorsanız, bir dizeyi `BSTR`bir .</span><span class="sxs-lookup"><span data-stu-id="98daa-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="98daa-145"><xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> Değeri kullanarak, bir dizeyi `BSTR`'' olarak sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

<span data-ttu-id="98daa-146">WinRT tabanlı BIR API kullanırken, bir dizeyi `HSTRING`'' olarak bağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="98daa-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="98daa-147"><xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> Değeri kullanarak, bir dizeyi `HSTRING`'' olarak sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

<span data-ttu-id="98daa-148">API'niz dizeyi yapıdaki yerine geçirmenizi gerektiriyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="98daa-149">Bir `ByValTStr` dize için kodlama nın öznitelikten `CharSet` belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="98daa-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="98daa-150">Ayrıca, bir dize uzunluğu <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan tarafından geçirilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="98daa-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="98daa-151">Ondalık alan mareşalcilik özelleştirme</span><span class="sxs-lookup"><span data-stu-id="98daa-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="98daa-152">Windows üzerinde çalışıyorsanız, yerel [ `CY` veya `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) yapıyı kullanan bazı API'larla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="98daa-153">Varsayılan olarak, .NET `decimal` türü yerel [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) yapıya marshals.</span><span class="sxs-lookup"><span data-stu-id="98daa-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="98daa-154">Ancak, <xref:System.Runtime.InteropServices.MarshalAsAttribute> bir <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> değeri yerel `decimal` `CY` değere dönüştürmesi için mareşaltalimat değeri ile a kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a><span data-ttu-id="98daa-155">Mareşallik `System.Object`</span><span class="sxs-lookup"><span data-stu-id="98daa-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="98daa-156">Windows'da, yazılan `object`alanları yerel koda göre yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98daa-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="98daa-157">Bu alanları üç türden birine göre mareşallik yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98daa-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="98daa-158">Varsayılan olarak, `object`türü yazılmı yapılan bir `IUnknown*` alan nesneyi saran bir alana marshaled olacaktır.</span><span class="sxs-lookup"><span data-stu-id="98daa-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

<span data-ttu-id="98daa-159">Bir nesne alanını bir `IDispatch*`nesneye göre <xref:System.Runtime.InteropServices.MarshalAsAttribute> mareşallemek istiyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri ile a ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98daa-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

<span data-ttu-id="98daa-160">Eğer bir `VARIANT`olarak mareşal istiyorsanız <xref:System.Runtime.InteropServices.MarshalAsAttribute> , <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri ile bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98daa-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

<span data-ttu-id="98daa-161">Aşağıdaki tabloda, `obj` alan eşleminin farklı çalışma zamanı türlerinin, bir `VARIANT`tabloda depolanan çeşitli türlere ne kadar farklı olduğu açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="98daa-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="98daa-162">.NET Türü</span><span class="sxs-lookup"><span data-stu-id="98daa-162">.NET Type</span></span> | <span data-ttu-id="98daa-163">VARYANT Türü</span><span class="sxs-lookup"><span data-stu-id="98daa-163">VARIANT Type</span></span> | | <span data-ttu-id="98daa-164">.NET Türü</span><span class="sxs-lookup"><span data-stu-id="98daa-164">.NET Type</span></span> | <span data-ttu-id="98daa-165">VARYANT Türü</span><span class="sxs-lookup"><span data-stu-id="98daa-165">VARIANT Type</span></span> |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
