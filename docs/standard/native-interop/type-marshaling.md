---
title: Tür sıralama-.NET
description: .NET 'in türlerinizi yerel bir gösterimde nasıl sıraladığında öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 91b8f3d6cb53fd7a0adea7ea9669e7459e81445f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706272"
---
# <a name="type-marshaling"></a><span data-ttu-id="13247-103">Tür hazırlama</span><span class="sxs-lookup"><span data-stu-id="13247-103">Type marshaling</span></span>

<span data-ttu-id="13247-104">**Sıralama** , yönetilen ve yerel kod arasında çapraz geçiş olmaları gerektiğinde türleri dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="13247-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="13247-105">Yönetilen ve yönetilmeyen koddaki türler farklı olduğundan sıralama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13247-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="13247-106">Yönetilen kodda, örneğin, `String`yönetilmeyen Uluslararası dizeler Unicode ("geniş"), Unicode olmayan, null ile SONLANDıRıLMıŞ, ASCII vb. olabilir. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyi gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="13247-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="13247-107">Ancak, ek denetime ihtiyacınız olan bu durumlar için, yönetilmeyen tarafta beklenen türü ne olduğunu belirtmek üzere [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13247-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="13247-108">Örneğin, dizenin null ile sonlandırılmış bir ANSI dizesi olarak gönderilmesini istiyorsanız bunu şöyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13247-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="13247-109">Ortak türleri hazırlama için varsayılan kurallar</span><span class="sxs-lookup"><span data-stu-id="13247-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="13247-110">Genellikle, çalışma zamanı, sizin için en az iş miktarını gerektirecek şekilde sıralama yaparken "doğru şeyi" gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="13247-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="13247-111">Aşağıdaki tablolarda, her türün bir parametre veya alanda kullanıldığında varsayılan olarak nasıl sıralandığına ilişkin bir açıklama verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13247-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="13247-112">Aşağıdaki tablonun tüm platformlar için doğru olduğundan emin olmak için C99/C++ 11 sabit genişlikli tamsayı ve karakter türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13247-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="13247-113">Aynı hizalama ve Boyut gereksinimlerine sahip herhangi bir yerel türü bu türlerle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13247-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="13247-114">Bu ilk tabloda, hem P/Invoke hem de alan sıralaması için, sıralama için aynı olan çeşitli türler için eşlemeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13247-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="13247-115">.NET türü</span><span class="sxs-lookup"><span data-stu-id="13247-115">.NET Type</span></span> | <span data-ttu-id="13247-116">Yerel tür</span><span class="sxs-lookup"><span data-stu-id="13247-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="13247-117">Ya `char` da `char16_t` P/Invoke `CharSet` ya da yapısına bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="13247-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="13247-118">[Karakter kümesi belgelerine](charset.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13247-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="13247-119">Ya `char*` da `char16_t*` P/Invoke `CharSet` ya da yapısına bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="13247-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="13247-120">[Karakter kümesi belgelerine](charset.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13247-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="13247-121">.NET Işaretçi türleri (örn.</span><span class="sxs-lookup"><span data-stu-id="13247-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="13247-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="13247-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="13247-123">Türetilmiş tür`System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="13247-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="13247-124">Türetilmiş tür`System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="13247-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="13247-125">Win32 `BOOL` türü</span><span class="sxs-lookup"><span data-stu-id="13247-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="13247-126">COM `DECIMAL` yapısı</span><span class="sxs-lookup"><span data-stu-id="13247-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="13247-127">.NET temsilcisi</span><span class="sxs-lookup"><span data-stu-id="13247-127">.NET Delegate</span></span> | <span data-ttu-id="13247-128">Yerel işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="13247-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="13247-129">Win32 `DATE` türü</span><span class="sxs-lookup"><span data-stu-id="13247-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="13247-130">Win32 `GUID` türü</span><span class="sxs-lookup"><span data-stu-id="13247-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="13247-131">Bir parametre veya yapı olarak sıralama yapıyorsanız, birkaç sıralama kategorisi farklı değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="13247-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="13247-132">.NET türü</span><span class="sxs-lookup"><span data-stu-id="13247-132">.NET Type</span></span> | <span data-ttu-id="13247-133">Yerel tür (parametre)</span><span class="sxs-lookup"><span data-stu-id="13247-133">Native Type (Parameter)</span></span> | <span data-ttu-id="13247-134">Yerel tür (alan)</span><span class="sxs-lookup"><span data-stu-id="13247-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="13247-135">.NET dizisi</span><span class="sxs-lookup"><span data-stu-id="13247-135">.NET array</span></span> | <span data-ttu-id="13247-136">Dizi öğelerinin yerel gösterimlerine ait bir dizi başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13247-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="13247-137">`[MarshalAs]` Özniteliği olmadan izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="13247-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="13247-138">`Sequential` Veya içeren `LayoutKind` bir sınıf`Explicit`</span><span class="sxs-lookup"><span data-stu-id="13247-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="13247-139">Sınıfın yerel gösterimine yönelik bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="13247-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="13247-140">Sınıfın yerel temsili</span><span class="sxs-lookup"><span data-stu-id="13247-140">The native representation of the class</span></span> |

<span data-ttu-id="13247-141">Aşağıdaki tablo, yalnızca Windows 'un varsayılan sıralama kurallarını içerir.</span><span class="sxs-lookup"><span data-stu-id="13247-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="13247-142">Windows dışı platformlarda bu türleri sıralayamaz.</span><span class="sxs-lookup"><span data-stu-id="13247-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="13247-143">.NET türü</span><span class="sxs-lookup"><span data-stu-id="13247-143">.NET Type</span></span> | <span data-ttu-id="13247-144">Yerel tür (parametre)</span><span class="sxs-lookup"><span data-stu-id="13247-144">Native Type (Parameter)</span></span> | <span data-ttu-id="13247-145">Yerel tür (alan)</span><span class="sxs-lookup"><span data-stu-id="13247-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="13247-146">COM arabirimi</span><span class="sxs-lookup"><span data-stu-id="13247-146">COM interface</span></span> | <span data-ttu-id="13247-147">`[MarshalAs]` Özniteliği olmadan izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="13247-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="13247-148">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="13247-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="13247-149">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="13247-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="13247-150">İzin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="13247-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="13247-151">`int64_t`1 Ocak 1601 ' de gece yarısından beri geçen onay işareti sayısını temsil etme</span><span class="sxs-lookup"><span data-stu-id="13247-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="13247-152">`int64_t`1 Ocak 1601 ' de gece yarısından beri geçen onay işareti sayısını temsil etme</span><span class="sxs-lookup"><span data-stu-id="13247-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="13247-153">Bazı türler, alan olarak değil yalnızca parametre olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="13247-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="13247-154">Bu türler aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="13247-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="13247-155">.NET türü</span><span class="sxs-lookup"><span data-stu-id="13247-155">.NET Type</span></span> | <span data-ttu-id="13247-156">Yerel tür (yalnızca parametre)</span><span class="sxs-lookup"><span data-stu-id="13247-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="13247-157">Ya `char*` da `char16_t*` P/Invoke `CharSet` öğesine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="13247-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="13247-158">[Karakter kümesi belgelerine](charset.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13247-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="13247-159">`va_list`(yalnızca Windows x86/x64/arm64 üzerinde)</span><span class="sxs-lookup"><span data-stu-id="13247-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="13247-160">Bu varsayılanlar tam olarak istediğiniz şekilde yapamazsa, parametrelerin nasıl sıralanmasını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13247-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="13247-161">[Parametre sıralama](customize-parameter-marshaling.md) makalesi, farklı parametre türlerinin nasıl sıralanmasını nasıl özelleştireceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="13247-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="13247-162">COM senaryolarında varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="13247-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="13247-163">.NET ' te COM nesnelerine Yöntemler çağırırken .NET çalışma zamanı, varsayılan sıralama kurallarını ortak COM semantiklerine uyacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="13247-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="13247-164">Aşağıdaki tabloda, .NET çalışma zamanlarının COM senaryolarında kullandığı kurallar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="13247-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="13247-165">.NET türü</span><span class="sxs-lookup"><span data-stu-id="13247-165">.NET Type</span></span> | <span data-ttu-id="13247-166">Yerel tür (COM Yöntem çağrıları)</span><span class="sxs-lookup"><span data-stu-id="13247-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="13247-167">Temsilci türleri</span><span class="sxs-lookup"><span data-stu-id="13247-167">Delegate types</span></span> | <span data-ttu-id="13247-168">`_Delegate*`.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13247-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="13247-169">.NET Core 'da izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="13247-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="13247-170">.NET dizisi</span><span class="sxs-lookup"><span data-stu-id="13247-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="13247-171">`SAFEARRAY`/ `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="13247-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="13247-172">Sınıfları ve yapıları hazırlama</span><span class="sxs-lookup"><span data-stu-id="13247-172">Marshaling classes and structs</span></span>

<span data-ttu-id="13247-173">Bir yapının tür sıralaması, yönetilmeyen bir yönteme nasıl geçmektir.</span><span class="sxs-lookup"><span data-stu-id="13247-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="13247-174">Örneğin, yönetilmeyen yöntemlerin bazıları parametre olarak bir yapı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="13247-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="13247-175">Bu durumlarda, bir parametre olarak kullanmak için, dünyanın yönetilen bölümünde karşılık gelen bir yapı veya bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13247-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="13247-176">Ancak, sınıfı tanımlamak yeterli değildir, Ayrıca, sınıf içindeki alanların yönetilmeyen yapıya nasıl eşlenmediğini de belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="13247-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="13247-177">Burada `StructLayout` öznitelik faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="13247-177">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="13247-178">Önceki kod, `GetSystemTime()` işlevine çağırmanın basit bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13247-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="13247-179">İlginç bit 4. satırda.</span><span class="sxs-lookup"><span data-stu-id="13247-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="13247-180">Özniteliği, sınıfın alanlarının diğer (yönetilmeyen) taraftaki yapıya sırayla eşlenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13247-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="13247-181">Bu, alanların adlandırılmasının önemli olmadığı, yönetilmeyen yapısına karşılık gelmesi gerektiğinden, aşağıdaki örnekte gösterildiği gibi, yalnızca kendi sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="13247-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="13247-182">Bazen yapınızın varsayılan sıralaması, ihtiyacınız olan şeyi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="13247-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="13247-183">[Yapı sıralamasını özelleştirme](./customize-struct-marshaling.md) makalesi, yapınızın nasıl sıralanmasını nasıl özelleştireceğinizi öğretir.</span><span class="sxs-lookup"><span data-stu-id="13247-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
