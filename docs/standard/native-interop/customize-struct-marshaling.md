---
title: Yapı sıralamasını özelleştirme-.NET
description: .NET 'in yapılarınızı yerel bir gösterimde nasıl sıraladığında nasıl özelleştireceğinizi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 6e3dcaeb71ae32812d3b022fff2bdc4e3e0691bf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040148"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="e1c95-103">Yapı hazırlamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-103">Customizing structure marshaling</span></span>

<span data-ttu-id="e1c95-104">Bazen yapılar için varsayılan sıralama kuralları, ihtiyacınız olan tam değildir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="e1c95-105">.NET çalışma zamanları, yapınızın yerleşimini ve alanların nasıl sıralanmayı özelleştirmeniz için birkaç uzantı noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="e1c95-106">Yapı mizanpajını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-106">Customizing structure layout</span></span>

<span data-ttu-id="e1c95-107">.Net, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> alanların belleğe nasıl yerleştirileceğini <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> özelleştirmenizi sağlayacak özniteliği ve sabit listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="e1c95-108">Aşağıdaki kılavuz yaygın sorunlardan kaçınmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e1c95-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="e1c95-109">mümkün olan **her durumda kullanmayı ✔️** `LayoutKind.Sequential` .</span><span class="sxs-lookup"><span data-stu-id="e1c95-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="e1c95-110">**✔️** yalnızca, yerel `LayoutKind.Explicit` yapının birleşim gibi açık bir düzeni de olduğunda, hazırlama sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-110">**✔️ DO** only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="e1c95-111">Windows dışı platformlarda `LayoutKind.Explicit` yapıları hazırlama sırasında **kullanmaktan kaçının ❌** .</span><span class="sxs-lookup"><span data-stu-id="e1c95-111">**❌ AVOID** using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms.</span></span> <span data-ttu-id="e1c95-112">.NET Core çalışma zamanı, Intel veya AMD 64-bit Windows dışı sistemlerdeki yerel işlevlere değere göre açık yapıların geçirilmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e1c95-112">The .NET Core runtime doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="e1c95-113">Ancak çalışma zamanı, tüm platformlarda başvuruya göre açık yapıların geçirilmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="e1c95-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="e1c95-114">Boole alan sıralamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="e1c95-115">Yerel kodun birçok farklı Boolean temsili vardır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="e1c95-116">Windows tek başına, Boole değerlerini göstermenin üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="e1c95-117">Çalışma zamanı, yapınızın yerel tanımını bilmez, bu yüzden en iyi yöntem, Boolean değerlerinizi nasıl sıraleyeceğinizi tahmin edebilir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="e1c95-118">.NET çalışma zamanı, Boolean alanınızı nasıl sıralamadığını göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="e1c95-119">Aşağıdaki örneklerde, .net `bool` 'in farklı yerel Boole türlerine nasıl sıralaması yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="e1c95-120">Aşağıdaki örnekte gösterildiği gibi, yerel 4 baytlık bir Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) değeri olarak sıralama varsayılan Boole değerleri:</span><span class="sxs-lookup"><span data-stu-id="e1c95-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="e1c95-121">Açık olmasını istiyorsanız, yukarıdaki gibi aynı davranışı almak için <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1c95-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="e1c95-122">`b` `bool` Aşağıdaki veya değerlerini`UnmanagedType.I1` kullanarak çalışma zamanına, alanı 1 baytlık yerel bir tür olarak sıralayamaz. `UnmanagedType.U1`</span><span class="sxs-lookup"><span data-stu-id="e1c95-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="e1c95-123">Windows 'ta, çalışma zamanına, Boole <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değerini 2 baytlık `VARIANT_BOOL` bir değere göre sıralayamaz şekilde söylemek için bu değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1c95-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="e1c95-124">`VARIANT_BOOL`, `VARIANT_TRUE = -1` ve`VARIANT_FALSE = 0`' deki en bool türlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="e1c95-125">Ayrıca, eşit `VARIANT_TRUE` olmayan tüm değerler false olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="e1c95-126">Dizi alanı sıralamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-126">Customizing array field marshaling</span></span>

<span data-ttu-id="e1c95-127">.NET ayrıca dizi sıralamasını özelleştirmenin birkaç yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="e1c95-128">Varsayılan olarak, .NET, dizileri öğelerin bitişik listesine bir işaretçi olarak sıralar:</span><span class="sxs-lookup"><span data-stu-id="e1c95-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="e1c95-129">COM API 'leri ile arabirimleriniz varsa, dizileri nesneler olarak `SAFEARRAY*` sıralama yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="e1c95-130">Çalışma zamanına bir diziyi <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> bir `SAFEARRAY*`diziyi <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> sıralayamaz söylemek için ve değerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1c95-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="e1c95-131">İçinde `SAFEARRAY`ne tür bir öğe olduğunu özelleştirmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve öğelerinin tam öğe türünü özelleştirmek `SAFEARRAY`için ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> alanlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="e1c95-132">Diziyi yerinde sıralamakta ihtiyacınız varsa, sıralayıcıya diziyi yerinde sıralayamaz söylemek için <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> değerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="e1c95-133">Bu sıralama 'yı kullanırken, çalışma zamanının yapıya doğru bir şekilde alan ayırabilmesi için <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> dizideki öğe sayısı için alana bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="e1c95-134">.NET, bir değişken uzunluklu dizi alanının C99 esnek dizi üyesi olarak sıralamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e1c95-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="e1c95-135">Dize alanı sıralamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-135">Customizing string field marshaling</span></span>

<span data-ttu-id="e1c95-136">.NET ayrıca, dize alanlarını hazırlama için çok çeşitli özelleştirmeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="e1c95-137">Varsayılan olarak, .NET, bir dizeyi null ile sonlandırılmış bir dizenin işaretçisi olarak sıraar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="e1c95-138">Kodlama, <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>içindeki alanın değerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1c95-139">Hiçbir öznitelik belirtilmemişse, kodlama varsayılan olarak bir ANSI kodlaması olur.</span><span class="sxs-lookup"><span data-stu-id="e1c95-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="e1c95-140">Farklı alanlar için farklı kodlamalar kullanmanız veya yapı tanımınızda daha açık olmasını tercih etmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> değerlerini bir <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> öznitelik üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="e1c95-141">Dizelerinizi UTF-8 kodlaması kullanarak sıralamak isterseniz, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute>içindeki değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="e1c95-142">Kullanmak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> .NET Framework 4,7 (veya sonraki sürümler) veya .NET Core 1,1 (ya da sonraki sürümler) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="e1c95-143">.NET Standard 2,0 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="e1c95-144">COM API 'Leri ile çalışıyorsanız bir dizeyi bir `BSTR`olarak sıralıyoruz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="e1c95-145">Değerini kullanarak bir dizeyi bir `BSTR`olarak sıraaktarabilirsiniz. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1c95-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="e1c95-146">WinRT tabanlı bir API kullanırken bir dizeyi bir `HSTRING`olarak sıralamakta gerek olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="e1c95-147">Değerini kullanarak bir dizeyi bir `HSTRING`olarak sıraaktarabilirsiniz. <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1c95-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="e1c95-148">API 'niz dizeyi yapıya yerinde geçirmeniz gerekiyorsa, bu <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="e1c95-149">Tarafından `ByValTStr` sıralanan bir dizenin kodlamasının `CharSet` öznitelikten belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1c95-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="e1c95-150">Ayrıca, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan tarafından bir dize uzunluğunun geçirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1c95-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="e1c95-151">Ondalık alan sıralamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1c95-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="e1c95-152">Windows üzerinde çalışıyorsanız, yerel [ `CY` veya `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) yapıyı kullanan bazı API 'lerle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="e1c95-153">Varsayılan olarak, .net `decimal` türü yerel [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) yapıya göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="e1c95-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="e1c95-154">Bununla birlikte <xref:System.Runtime.InteropServices.MarshalAsAttribute> , bir `decimal` değeri yerel <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> `CY` bir değere dönüştürmek üzere Sıralayıcı 'yı yönlendirmek için değeriyle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="e1c95-155">Sıralama `System.Object`</span><span class="sxs-lookup"><span data-stu-id="e1c95-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="e1c95-156">Windows 'ta, yerel koda göre `object`türsüz alanları sıraaktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c95-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="e1c95-157">Bu alanları üç türden birine göre sıraaktarabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1c95-157">You can marshal these fields to one of three types:</span></span>
- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="e1c95-158">Varsayılan olarak, bir `object`türü olan bir alan, nesneyi sarmalayan `IUnknown*` bir öğesine sıralanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1c95-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="e1c95-159">Bir nesne alanını bir `IDispatch*`öğesine sıralamak istiyorsanız <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri ile bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1c95-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="e1c95-160">Bunu bir `VARIANT`olarak sıralamak istiyorsanız <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri ile bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1c95-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="e1c95-161">Aşağıdaki tabloda, `obj` alanın farklı çalışma zamanı türlerinin `VARIANT`' de depolanan çeşitli türlere nasıl eşlendiğini açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e1c95-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="e1c95-162">.NET türü</span><span class="sxs-lookup"><span data-stu-id="e1c95-162">.NET Type</span></span> | <span data-ttu-id="e1c95-163">DEĞIŞKEN türü</span><span class="sxs-lookup"><span data-stu-id="e1c95-163">VARIANT Type</span></span> | | <span data-ttu-id="e1c95-164">.NET türü</span><span class="sxs-lookup"><span data-stu-id="e1c95-164">.NET Type</span></span> | <span data-ttu-id="e1c95-165">DEĞIŞKEN türü</span><span class="sxs-lookup"><span data-stu-id="e1c95-165">VARIANT Type</span></span> |
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
