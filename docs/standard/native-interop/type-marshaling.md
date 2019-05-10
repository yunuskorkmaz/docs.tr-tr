---
title: Tür sıralama - .NET
description: .NET yerel gösterimine türlerinizi nasıl sürekliliğe devreder öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cb18a7607a3d99907401543b4d37995a956a3920
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065467"
---
# <a name="type-marshaling"></a><span data-ttu-id="3224b-103">Sıralama türü</span><span class="sxs-lookup"><span data-stu-id="3224b-103">Type marshaling</span></span>

<span data-ttu-id="3224b-104">**Hazırlama** yönetilen ve yerel kod arasında çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="3224b-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="3224b-105">Yönetilen ve yönetilmeyen kod türleri farklı olduğundan, hazırlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3224b-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="3224b-106">Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyleri yapacakları dener.</span><span class="sxs-lookup"><span data-stu-id="3224b-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="3224b-107">Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3224b-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="3224b-108">Dizeyi ANSI null ile sonlandırılmış dize olarak gönderilmesini istiyorsanız, örneğin, şöyle bunu:</span><span class="sxs-lookup"><span data-stu-id="3224b-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="3224b-109">Varsayılan kuralları ortak türlerini hazırlama</span><span class="sxs-lookup"><span data-stu-id="3224b-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="3224b-110">Çalışma zamanı genellikle "doğru şeyi" yaptığınızda dener iş sizden az miktarda gerektirecek şekilde hazırlama.</span><span class="sxs-lookup"><span data-stu-id="3224b-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="3224b-111">Aşağıdaki tablolar, bir parametre veya alanında kullanıldığında varsayılan olarak her tür nasıl sıralanmış açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3224b-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="3224b-112">C99 / C ++ 11 sabit genişlik tamsayı ve karakter türleri aşağıdaki tabloda tüm platformlar için doğru olduğundan emin olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3224b-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="3224b-113">Aynı hizalama ve bu türü olarak boyut gereksinimlerine sahip herhangi bir yerel tür kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3224b-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="3224b-114">Birinci tablo eşlemelerini kendisi için hazırlama P/Invoke ve hazırlama alanı için aynı çeşitli türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3224b-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="3224b-115">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3224b-115">.NET Type</span></span> | <span data-ttu-id="3224b-116">Yerel tür</span><span class="sxs-lookup"><span data-stu-id="3224b-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="3224b-117">Ya da `char` veya `char16_t` bağlı olarak `CharSet` P/Invoke veya yapının.</span><span class="sxs-lookup"><span data-stu-id="3224b-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="3224b-118">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="3224b-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="3224b-119">Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke veya yapının.</span><span class="sxs-lookup"><span data-stu-id="3224b-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="3224b-120">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="3224b-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="3224b-121">.NET işaretçi türleri (ör.</span><span class="sxs-lookup"><span data-stu-id="3224b-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="3224b-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="3224b-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="3224b-123">Türetilmiş türü `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="3224b-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="3224b-124">Türetilmiş türü `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="3224b-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="3224b-125">Win32 `BOOL` türü</span><span class="sxs-lookup"><span data-stu-id="3224b-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="3224b-126">COM `DECIMAL` yapısı</span><span class="sxs-lookup"><span data-stu-id="3224b-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="3224b-127">.NET temsilci</span><span class="sxs-lookup"><span data-stu-id="3224b-127">.NET Delegate</span></span> | <span data-ttu-id="3224b-128">Yerel işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="3224b-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="3224b-129">Win32 `DATE` türü</span><span class="sxs-lookup"><span data-stu-id="3224b-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="3224b-130">Win32 `GUID` türü</span><span class="sxs-lookup"><span data-stu-id="3224b-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="3224b-131">Hazırlama, birkaç kategoriden varsayılan değerleri farklı varsa bir parametre veya yapısı hazırlama.</span><span class="sxs-lookup"><span data-stu-id="3224b-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="3224b-132">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3224b-132">.NET Type</span></span> | <span data-ttu-id="3224b-133">Yerel türü (parametre)</span><span class="sxs-lookup"><span data-stu-id="3224b-133">Native Type (Parameter)</span></span> | <span data-ttu-id="3224b-134">Yerel bir tür (alan)</span><span class="sxs-lookup"><span data-stu-id="3224b-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="3224b-135">.NET dizisi</span><span class="sxs-lookup"><span data-stu-id="3224b-135">.NET array</span></span> | <span data-ttu-id="3224b-136">Dizi öğeleri yerel temsillerini bir dizi başlangıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3224b-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="3224b-137">Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="3224b-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="3224b-138">Bir sınıf ile bir `LayoutKind` , `Sequential` veya `Explicit`</span><span class="sxs-lookup"><span data-stu-id="3224b-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="3224b-139">Yerel gösterimine sınıfının işaretçisi</span><span class="sxs-lookup"><span data-stu-id="3224b-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="3224b-140">Yerel gösterimi sınıfı</span><span class="sxs-lookup"><span data-stu-id="3224b-140">The native representation of the class</span></span> |

<span data-ttu-id="3224b-141">Aşağıdaki tablo, varsayılan sıralama kuralları içerir. yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="3224b-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="3224b-142">Windows dışı platformlarda, bu tür sıralanamıyor.</span><span class="sxs-lookup"><span data-stu-id="3224b-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="3224b-143">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3224b-143">.NET Type</span></span> | <span data-ttu-id="3224b-144">Yerel türü (parametre)</span><span class="sxs-lookup"><span data-stu-id="3224b-144">Native Type (Parameter)</span></span> | <span data-ttu-id="3224b-145">Yerel bir tür (alan)</span><span class="sxs-lookup"><span data-stu-id="3224b-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="3224b-146">COM arabirimi</span><span class="sxs-lookup"><span data-stu-id="3224b-146">COM interface</span></span> | <span data-ttu-id="3224b-147">Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="3224b-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="3224b-148">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="3224b-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="3224b-149">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="3224b-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="3224b-150">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="3224b-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="3224b-151">`int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden</span><span class="sxs-lookup"><span data-stu-id="3224b-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="3224b-152">`int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden</span><span class="sxs-lookup"><span data-stu-id="3224b-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="3224b-153">Bazı türleri parametre olarak ve alanlar olarak değil yalnızca sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="3224b-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="3224b-154">Bu tür aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3224b-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="3224b-155">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3224b-155">.NET Type</span></span> | <span data-ttu-id="3224b-156">Yerel bir tür (yalnızca parametresi)</span><span class="sxs-lookup"><span data-stu-id="3224b-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="3224b-157">Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="3224b-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="3224b-158">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="3224b-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="3224b-159">`va_list` (Windows x86/x64/arm64'te yalnızca)</span><span class="sxs-lookup"><span data-stu-id="3224b-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="3224b-160">Bu varsayılanlar, tam olarak aradığınız şeyi yapmazsanız, parametreleri nasıl sıralanmış özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3224b-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="3224b-161">[Parametreyi](customize-parameter-marshaling.md) makalesi Yürüyüşü nasıl farklı parametre türlerinin nasıl özelleştirildiği size hazırlanır.</span><span class="sxs-lookup"><span data-stu-id="3224b-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="3224b-162">Sınıfları ve yapıları sıralama</span><span class="sxs-lookup"><span data-stu-id="3224b-162">Marshaling classes and structs</span></span>

<span data-ttu-id="3224b-163">Sıralama türü başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür.</span><span class="sxs-lookup"><span data-stu-id="3224b-163">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="3224b-164">Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3224b-164">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="3224b-165">Bu gibi durumlarda, yönetilen bölümünde bir parametresi olarak kullanılabilmesi için dünyanın karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3224b-165">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="3224b-166">Ancak, yalnızca bir sınıf tanımlama yeterli değildir, ayrıca Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="3224b-166">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="3224b-167">Burada `StructLayout` özniteliği yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="3224b-167">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="3224b-168">Önceki kod çağırma basit bir örneğini gösterir `GetSystemTime()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3224b-168">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="3224b-169">4. satırda ilginç bitidir.</span><span class="sxs-lookup"><span data-stu-id="3224b-169">The interesting bit is on line 4.</span></span> <span data-ttu-id="3224b-170">Öznitelik sınıfı alanlarını (yönetilmeyen) diğer tarafında struct sırayla eşlenmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="3224b-170">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="3224b-171">Bu adlandırma alanlarını'aşağıdaki örnekte gösterilen yönetilmeyen yapının karşılık gerektiğinde yalnızca bunların sırası önemlidir, önemli olmadığı anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="3224b-171">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="3224b-172">Bazen, yapı için hazırlama varsayılan gerekenler yapmaz.</span><span class="sxs-lookup"><span data-stu-id="3224b-172">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="3224b-173">[Yapısı hazırlama özelleştirme](./customize-struct-marshaling.md) makale yapınızı nasıl sıralanır özelleştirme öğretir.</span><span class="sxs-lookup"><span data-stu-id="3224b-173">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
