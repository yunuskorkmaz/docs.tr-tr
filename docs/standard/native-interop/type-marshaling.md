---
title: Tür sıralama - .NET
description: .NET yerel gösterimine türlerinizi nasıl sürekliliğe devreder öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2cb8898b52b4b4afba1184a886e16c9f7f68f03a
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041789"
---
# <a name="type-marshaling"></a><span data-ttu-id="a9ea5-103">Tür hazırlama</span><span class="sxs-lookup"><span data-stu-id="a9ea5-103">Type marshaling</span></span>

<span data-ttu-id="a9ea5-104">**Hazırlama** yönetilen ve yerel kod arasında çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="a9ea5-105">Yönetilen ve yönetilmeyen kod türleri farklı olduğundan, hazırlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="a9ea5-106">Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyleri yapacakları dener.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="a9ea5-107">Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="a9ea5-108">Dizeyi ANSI null ile sonlandırılmış dize olarak gönderilmesini istiyorsanız, örneğin, şöyle bunu:</span><span class="sxs-lookup"><span data-stu-id="a9ea5-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="a9ea5-109">Varsayılan kuralları ortak türlerini hazırlama</span><span class="sxs-lookup"><span data-stu-id="a9ea5-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="a9ea5-110">Çalışma zamanı genellikle "doğru şeyi" yaptığınızda dener iş sizden az miktarda gerektirecek şekilde hazırlama.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="a9ea5-111">Aşağıdaki tablolar, bir parametre veya alanında kullanıldığında varsayılan olarak her tür nasıl sıralanmış açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="a9ea5-112">C99 / C ++ 11 sabit genişlik tamsayı ve karakter türleri aşağıdaki tabloda tüm platformlar için doğru olduğundan emin olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="a9ea5-113">Aynı hizalama ve bu türü olarak boyut gereksinimlerine sahip herhangi bir yerel tür kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="a9ea5-114">Birinci tablo eşlemelerini kendisi için hazırlama P/Invoke ve hazırlama alanı için aynı çeşitli türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="a9ea5-115">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-115">.NET Type</span></span> | <span data-ttu-id="a9ea5-116">Yerel tür</span><span class="sxs-lookup"><span data-stu-id="a9ea5-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="a9ea5-117">Ya da `char` veya `char16_t` bağlı olarak `CharSet` P/Invoke veya yapının.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="a9ea5-118">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="a9ea5-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="a9ea5-119">Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke veya yapının.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="a9ea5-120">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="a9ea5-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="a9ea5-121">.NET işaretçi türleri (ör.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="a9ea5-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="a9ea5-123">Türetilmiş türü `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="a9ea5-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="a9ea5-124">Türetilmiş türü `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="a9ea5-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="a9ea5-125">Win32 `BOOL` türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="a9ea5-126">COM `DECIMAL` yapısı</span><span class="sxs-lookup"><span data-stu-id="a9ea5-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="a9ea5-127">.NET temsilci</span><span class="sxs-lookup"><span data-stu-id="a9ea5-127">.NET Delegate</span></span> | <span data-ttu-id="a9ea5-128">Yerel işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="a9ea5-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="a9ea5-129">Win32 `DATE` türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="a9ea5-130">Win32 `GUID` türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="a9ea5-131">Hazırlama, birkaç kategoriden varsayılan değerleri farklı varsa bir parametre veya yapısı hazırlama.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="a9ea5-132">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-132">.NET Type</span></span> | <span data-ttu-id="a9ea5-133">Yerel türü (parametre)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-133">Native Type (Parameter)</span></span> | <span data-ttu-id="a9ea5-134">Yerel bir tür (alan)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="a9ea5-135">.NET dizisi</span><span class="sxs-lookup"><span data-stu-id="a9ea5-135">.NET array</span></span> | <span data-ttu-id="a9ea5-136">Dizi öğeleri yerel temsillerini bir dizi başlangıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="a9ea5-137">Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="a9ea5-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="a9ea5-138">Bir sınıf ile bir `LayoutKind` , `Sequential` veya `Explicit`</span><span class="sxs-lookup"><span data-stu-id="a9ea5-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="a9ea5-139">Yerel gösterimine sınıfının işaretçisi</span><span class="sxs-lookup"><span data-stu-id="a9ea5-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="a9ea5-140">Yerel gösterimi sınıfı</span><span class="sxs-lookup"><span data-stu-id="a9ea5-140">The native representation of the class</span></span> |

<span data-ttu-id="a9ea5-141">Aşağıdaki tablo, varsayılan sıralama kuralları içerir. yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="a9ea5-142">Windows dışı platformlarda, bu tür sıralanamıyor.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="a9ea5-143">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-143">.NET Type</span></span> | <span data-ttu-id="a9ea5-144">Yerel türü (parametre)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-144">Native Type (Parameter)</span></span> | <span data-ttu-id="a9ea5-145">Yerel bir tür (alan)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="a9ea5-146">COM arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9ea5-146">COM interface</span></span> | <span data-ttu-id="a9ea5-147">Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği</span><span class="sxs-lookup"><span data-stu-id="a9ea5-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="a9ea5-148">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="a9ea5-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="a9ea5-149">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="a9ea5-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="a9ea5-150">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="a9ea5-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="a9ea5-151">`int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden</span><span class="sxs-lookup"><span data-stu-id="a9ea5-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="a9ea5-152">`int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden</span><span class="sxs-lookup"><span data-stu-id="a9ea5-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="a9ea5-153">Bazı türleri parametre olarak ve alanlar olarak değil yalnızca sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="a9ea5-154">Bu tür aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="a9ea5-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="a9ea5-155">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-155">.NET Type</span></span> | <span data-ttu-id="a9ea5-156">Yerel bir tür (yalnızca parametresi)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="a9ea5-157">Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="a9ea5-158">Bkz: [charset belgeleri](charset.md).</span><span class="sxs-lookup"><span data-stu-id="a9ea5-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="a9ea5-159">`va_list` (Windows x86/x64/arm64'te yalnızca)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="a9ea5-160">Bu varsayılanlar, tam olarak aradığınız şeyi yapmazsanız, parametreleri nasıl sıralanmış özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="a9ea5-161">[Parametreyi](customize-parameter-marshaling.md) makalesi Yürüyüşü nasıl farklı parametre türlerinin nasıl özelleştirildiği size hazırlanır.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="a9ea5-162">Varsayılan COM senaryolarda hazırlama</span><span class="sxs-lookup"><span data-stu-id="a9ea5-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="a9ea5-163">. NET'te COM nesnelerinde yöntemleri çağırarak, .NET çalışma zamanı ortak COM semantiği eşleştirilecek kuralları hazırlama varsayılan değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="a9ea5-164">Aşağıdaki tablo, .NET çalışma zamanları COM senaryolarda kullandığı kurallarını listeler:</span><span class="sxs-lookup"><span data-stu-id="a9ea5-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="a9ea5-165">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a9ea5-165">.NET Type</span></span> | <span data-ttu-id="a9ea5-166">Yerel bir tür (COM yöntem çağrıları)</span><span class="sxs-lookup"><span data-stu-id="a9ea5-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="a9ea5-167">Temsilci türleri</span><span class="sxs-lookup"><span data-stu-id="a9ea5-167">Delegate types</span></span> | <span data-ttu-id="a9ea5-168">`_Delegate*` .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="a9ea5-169">' De .NET Core izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="a9ea5-170">.NET dizisi</span><span class="sxs-lookup"><span data-stu-id="a9ea5-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="a9ea5-171">`SAFEARRAY` ' ın `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="a9ea5-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="a9ea5-172">Sınıfları ve yapıları sıralama</span><span class="sxs-lookup"><span data-stu-id="a9ea5-172">Marshaling classes and structs</span></span>

<span data-ttu-id="a9ea5-173">Sıralama türü başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="a9ea5-174">Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="a9ea5-175">Bu gibi durumlarda, yönetilen bölümünde bir parametresi olarak kullanılabilmesi için dünyanın karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="a9ea5-176">Ancak, yalnızca bir sınıf tanımlama yeterli değildir, ayrıca Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="a9ea5-177">Burada `StructLayout` özniteliği yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-177">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="a9ea5-178">Önceki kod çağırma basit bir örneğini gösterir `GetSystemTime()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="a9ea5-179">4\. satırda ilginç bitidir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="a9ea5-180">Öznitelik sınıfı alanlarını (yönetilmeyen) diğer tarafında struct sırayla eşlenmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="a9ea5-181">Bu adlandırma alanlarını'aşağıdaki örnekte gösterilen yönetilmeyen yapının karşılık gerektiğinde yalnızca bunların sırası önemlidir, önemli olmadığı anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="a9ea5-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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

<span data-ttu-id="a9ea5-182">Bazen, yapı için hazırlama varsayılan gerekenler yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="a9ea5-183">[Yapısı hazırlama özelleştirme](./customize-struct-marshaling.md) makale yapınızı nasıl sıralanır özelleştirme öğretir.</span><span class="sxs-lookup"><span data-stu-id="a9ea5-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
