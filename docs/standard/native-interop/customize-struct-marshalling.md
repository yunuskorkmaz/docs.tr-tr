---
title: Yapı özelleştirme taşıma - .NET
description: .NET yerel gösterimine, yapıları nasıl sürekliliğe devreder özelleştirmeyi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b07851a0d26f5bfe7edc2115d7276a8e96ba0917
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973564"
---
# <a name="customizing-structure-marshalling"></a><span data-ttu-id="18b44-103">Yapı taşıma özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-103">Customizing structure marshalling</span></span>

<span data-ttu-id="18b44-104">Bazen yapıları için varsayılan sıralama kuralları tam olarak ihtiyacınız olanları değil.</span><span class="sxs-lookup"><span data-stu-id="18b44-104">Sometimes the default marshalling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="18b44-105">.NET çalışma zamanları, yapının düzeni ve alanları nasıl sıralanmış özelleştirmeniz için birkaç uzantı noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b44-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="18b44-106">Yapı düzenini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-106">Customizing structure layout</span></span>

<span data-ttu-id="18b44-107">.NET sağlar <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> özniteliği ve <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> alanları bellekte nasıl yerleştirileceğini özelleştirmenize izin vermek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="18b44-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="18b44-108">Aşağıdaki yönergeler, sık karşılaşılan sorunları önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="18b44-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="18b44-109">**✔️ DÜŞÜNÜN** kullanarak `LayoutKind.Sequential` mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="18b44-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="18b44-110">**✔️ YAPMAK** yalnızca `LayoutKind.Explicit` içinde taşıma, yerel yapı ayrıca olduğunda bir birleşim gibi açık bir düzene sahip.</span><span class="sxs-lookup"><span data-stu-id="18b44-110">**✔️ DO** only use `LayoutKind.Explicit` in marshalling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="18b44-111">**❌ KAÇININ** kullanarak `LayoutKind.Explicit` Windows dışı platformlarda yapıları taşıma olduğunda.</span><span class="sxs-lookup"><span data-stu-id="18b44-111">**❌ AVOID** using `LayoutKind.Explicit` when marshalling structures on non-Windows platforms.</span></span> <span data-ttu-id="18b44-112">.NET Core çalışma zamanı açık yapıları değere göre yerel işlevleri için Intel ya da AMD 64 bit Windows olmayan sistemlerde geçirme desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="18b44-112">The .NET Core runtime doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="18b44-113">Ancak, çalışma zamanı, tüm platformlarda başvuruya göre geçirme açık yapıları destekler.</span><span class="sxs-lookup"><span data-stu-id="18b44-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshalling"></a><span data-ttu-id="18b44-114">Boole alanı taşıma özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-114">Customizing boolean field marshalling</span></span>

<span data-ttu-id="18b44-115">Yerel kod, birçok farklı Boole temsile sahiptir.</span><span class="sxs-lookup"><span data-stu-id="18b44-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="18b44-116">Tek başına Windows üzerinde boolean değerlerini temsil edecek şekilde üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="18b44-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="18b44-117">Çalışma zamanı yerel tanımı yapınızın bilmeniz, yapmak için en iyi şekilde bir boolean değerlerinizi hazırlama hakkında tahminde değil.</span><span class="sxs-lookup"><span data-stu-id="18b44-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="18b44-118">.NET çalışma zamanı nasıl hazırlanacağını boolean alan belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b44-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="18b44-119">Aşağıdaki örnekler nasıl hazırlanacağını .NET `bool` farklı yerel Boole türleri için.</span><span class="sxs-lookup"><span data-stu-id="18b44-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="18b44-120">Boole değerleri varsayılan yerel bir 4 baytlık Win32 taşıma için [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) aşağıdaki örnekte gösterildiği gibi değeri:</span><span class="sxs-lookup"><span data-stu-id="18b44-120">Boolean values default to marshalling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="18b44-121">Açık olmasını istiyorsanız, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> yukarıdakilerle aynı davranışı sağlamak için değer:</span><span class="sxs-lookup"><span data-stu-id="18b44-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="18b44-122">Kullanarak `UnmanagedType.U1` veya `UnmanagedType.I1` aşağıdaki değerleri, çalışma zamanının sıralamanız öğrenebilirsiniz `b` bir 1 baytlık yerel olarak alan `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="18b44-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="18b44-123">Windows üzerinde kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değeri, boolean değerine 2 baytlık hazırlamak için çalışma zamanı bildirmek için `VARIANT_BOOL` değeri:</span><span class="sxs-lookup"><span data-stu-id="18b44-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="18b44-124">`VARIANT_BOOL` Çoğu bool türleri, farklı `VARIANT_TRUE = -1` ve `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="18b44-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="18b44-125">Ayrıca, eşit olmayan tüm değerleri `VARIANT_TRUE` yanlış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="18b44-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshalling"></a><span data-ttu-id="18b44-126">Dizi alan taşıma özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-126">Customizing array field marshalling</span></span>

<span data-ttu-id="18b44-127">.NET, dizi taşıma özelleştirmek için birkaç yol da içerir.</span><span class="sxs-lookup"><span data-stu-id="18b44-127">.NET also includes a few ways to customize array marshalling.</span></span>

<span data-ttu-id="18b44-128">Varsayılan olarak, .NET dizileri için bitişik öğelerin listesini bir işaretçi olarak sürekliliğe devreder:</span><span class="sxs-lookup"><span data-stu-id="18b44-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="18b44-129">COM API'leri ile arabirim, dizileri olarak sıralamanız olabilir `SAFEARRAY*` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="18b44-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="18b44-130">Kullanabileceğiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> değeri olarak bir dizi hazırlamak için çalışma zamanı bildirmek için bir `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="18b44-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="18b44-131">Ne tür bir öğenin bulunduğu özelleştirmeniz gerekirse `SAFEARRAY`, kullanabileceğiniz sonra <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe özelleştirmek için alanları türü `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="18b44-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="18b44-132">Yerinde dizi sıralamanız gerekirse, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> yerinde dizi hazırlamak için sıralayıcıya bildirmek için değer.</span><span class="sxs-lookup"><span data-stu-id="18b44-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="18b44-133">Bu taşıma kullanırken da bir değer belirtmeniz gerekir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan çalışma zamanı yapısı için doğru yer ayırabilirsiniz şekilde dizideki öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="18b44-133">When you're using this marshalling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="18b44-134">.NET, C99 esnek dizi üyesi olarak bir değişken uzunluklu dizi alan taşıma desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="18b44-134">.NET doesn't support marshalling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshalling"></a><span data-ttu-id="18b44-135">Dize alanı taşıma özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-135">Customizing string field marshalling</span></span>

<span data-ttu-id="18b44-136">.NET çok çeşitli dize alanları taşıma için özelleştirmeler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b44-136">.NET also provides a wide variety of customizations for marshalling string fields.</span></span>

<span data-ttu-id="18b44-137">Varsayılan olarak, .NET bir dize null ile sonlandırılmış dizeye bir işaretçi olarak sürekliliğe devreder.</span><span class="sxs-lookup"><span data-stu-id="18b44-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="18b44-138">Kodlama değerine bağlıdır <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanındaki <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b44-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b44-139">Kodlamada hiçbir öznitelik belirtilmezse, bir ANSI kodlaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18b44-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="18b44-140">Farklı kodlamaları için farklı alanları kullanın veya sadece gerekiyorsa, yapı Tanımınızda daha net olmanızı tercih, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> üzerinde değerleri bir <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="18b44-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="18b44-141">UTF-8 kodlaması kullanarak dizelerinizi hazırlamak istiyorsanız, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> değerini, <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="18b44-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="18b44-142">Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> ya da .NET Framework 4.7 (veya sonraki sürümler) gerektirir veya .NET Core 1.1 (veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="18b44-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="18b44-143">.NET Standard 2.0 içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="18b44-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="18b44-144">COM API'leri ile çalışıyorsanız, bir dize olarak sıralamanız gerekebilir bir `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="18b44-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="18b44-145">Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> değeri bir dize olarak hazırlamak bir `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="18b44-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="18b44-146">WinRT tabanlı bir API kullanırken, bir dize olarak sıralamanız gerekebilir bir `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="18b44-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="18b44-147">Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> değeri bir dize olarak hazırlamak bir `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="18b44-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="18b44-148">API'nizi yapısında yerinde dizesini geçirmenizi gerektiriyorsa, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="18b44-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="18b44-149">Kodlama için bir dize tarafından sıraya olduğunu unutmayın `ByValTStr` gelen belirlenir `CharSet` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="18b44-149">Do note that the encoding for a string marshalled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="18b44-150">Ayrıca, bir dize uzunluğu geçirilen gerektirir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan.</span><span class="sxs-lookup"><span data-stu-id="18b44-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshalling"></a><span data-ttu-id="18b44-151">Ondalık alan taşıma özelleştirme</span><span class="sxs-lookup"><span data-stu-id="18b44-151">Customizing decimal field marshalling</span></span>

<span data-ttu-id="18b44-152">Windows üzerinde çalışıyorsanız, yerel kullanan bazı API'leri karşılaşabileceğiniz [ `CY` veya `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) yapısı.</span><span class="sxs-lookup"><span data-stu-id="18b44-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/desktop/api/wtypes/ns-wtypes-tagcy) structure.</span></span> <span data-ttu-id="18b44-153">Varsayılan olarak, .NET `decimal` türü için yerel sıraladığında [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) yapısı.</span><span class="sxs-lookup"><span data-stu-id="18b44-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/desktop/api/wtypes/ns-wtypes-tagdec) structure.</span></span> <span data-ttu-id="18b44-154">Ancak, kullanabileceğiniz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> dönüştürmek için sıralayıcı istemek için değer bir `decimal` yerel bir değer `CY` değeri.</span><span class="sxs-lookup"><span data-stu-id="18b44-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshalling-systemobjects"></a><span data-ttu-id="18b44-155">Taşıma `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="18b44-155">Marshalling `System.Object`s</span></span>

<span data-ttu-id="18b44-156">Windows üzerinde sıralanmamaktadır `object`-yazılan yerel kod için alanlar.</span><span class="sxs-lookup"><span data-stu-id="18b44-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="18b44-157">Bu alanlar üç türlerden sıralanmamaktadır:</span><span class="sxs-lookup"><span data-stu-id="18b44-157">You can marshal these fields to one of three types:</span></span>
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="18b44-158">Varsayılan olarak, bir `object`-alanın yazılan sıraya için bir `IUnknown*` nesnesinin sonuna geldik.</span><span class="sxs-lookup"><span data-stu-id="18b44-158">By default, an `object`-typed field will be marshalled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="18b44-159">Bir nesne alanının için hazırlamak istiyorsanız bir `IDispatch*`, ekleme bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="18b44-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="18b44-160">Olarak hazırlamak istiyorsanız bir `VARIANT`, ekleme bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="18b44-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="18b44-161">Aşağıdaki tabloda farklı çalışma zamanı türlerini açıklar `obj` depolanan çeşitli türleri için alan haritası bir `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="18b44-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="18b44-162">.NET türü</span><span class="sxs-lookup"><span data-stu-id="18b44-162">.NET Type</span></span> | <span data-ttu-id="18b44-163">DEĞİŞKEN türü</span><span class="sxs-lookup"><span data-stu-id="18b44-163">VARIANT Type</span></span> | | <span data-ttu-id="18b44-164">.NET türü</span><span class="sxs-lookup"><span data-stu-id="18b44-164">.NET Type</span></span> | <span data-ttu-id="18b44-165">DEĞİŞKEN türü</span><span class="sxs-lookup"><span data-stu-id="18b44-165">VARIANT Type</span></span> |
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
