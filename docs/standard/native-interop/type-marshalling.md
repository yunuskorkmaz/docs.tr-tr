---
title: Türü taşıma - .NET
description: .NET yerel gösterimine türlerinizi nasıl sürekliliğe devreder öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b4846f2e6cd945a25ec6a747c9038d48fe115559
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185421"
---
# <a name="type-marshalling"></a>Türü taşıma

**Taşıma** yönetilen ve yerel kod arasında çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.

Yönetilen ve yönetilmeyen kod türleri farklı olduğundan taşıma gereklidir. Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyleri yapacakları dener. Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği. Dizeyi ANSI null ile sonlandırılmış dize olarak gönderilmesini istiyorsanız, örneğin, şöyle bunu:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshalling-common-types"></a>Genel türleri taşıma için varsayılan kurallar

Çalışma zamanı genellikle "doğru şeyi" yaptığınızda dener iş sizden az miktarda gerektirecek şekilde hazırlama. Aşağıdaki tablolar, bir parametre veya alanında kullanıldığında varsayılan olarak her tür nasıl sıraya açıklamaktadır. C99 / C ++ 11 sabit genişlik tamsayı ve karakter türleri aşağıdaki tabloda tüm platformlar için doğru olduğundan emin olmak için kullanılır. Aynı hizalama ve bu türü olarak boyut gereksinimlerine sahip herhangi bir yerel tür kullanabilirsiniz.

Birinci tablo eşlemelerini kendisi için taşıma P/Invoke ve alan taşıma için aynı çeşitli türleri açıklanmaktadır.

| .NET türü | Yerel tür  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | Ya da `char` veya `char16_t` bağlı olarak `CharSet` P/Invoke veya yapının. Bkz: [charset belgeleri](charset.md). |
| `string`  | Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke veya yapının. Bkz: [charset belgeleri](charset.md). |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| .NET işaretçi türleri (ör. `void*`)  | `void*` |
| Türetilmiş türü `System.Runtime.InteropServices.SafeHandle` | `void*` |
| Türetilmiş türü `System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Win32 `BOOL` türü       |
| `decimal` | COM `DECIMAL` yapısı |
| .NET temsilci | Yerel işlev işaretçisi |
| `System.DateTime` | Win32 `DATE` türü |
| `System.Guid` | Win32 `GUID` türü |

Bir parametre veya yapısı taşıma, taşıma, birkaç kategoriden farklı varsayılanlara sahiptir.

| .NET türü | Yerel türü (parametre) | Yerel bir tür (alan) |
|-----------|-------------------------|---------------------|
| .NET dizisi | Dizi öğeleri yerel temsillerini bir dizi başlangıcı için bir işaretçi. | Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği|
| Bir sınıf ile bir `LayoutKind` , `Sequential` veya `Explicit` | Yerel gösterimine sınıfının işaretçisi | Yerel gösterimi sınıfı |

Aşağıdaki tablo, taşıma kuralları varsayılan içerir. yalnızca Windows. Windows dışı platformlarda, bu tür sıralanamıyor.

| .NET türü | Yerel türü (parametre) | Yerel bir tür (alan) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | COM arabirimi | Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği |
| `System.ArgIterator` | `va_list` | İzin verilmiyor |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | İzin verilmiyor |
| `System.Collections.IEnumerable` | `IDispatch*` | İzin verilmiyor |
| `System.DateTimeOffset` | `int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden || `int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden |

Bazı türleri yalnızca alanları değil de, parametre olarak sıraya. Bu tür aşağıdaki tabloda listelenmiştir:

| .NET türü | Yerel bir tür (yalnızca parametresi) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke.  Bkz: [charset belgeleri](charset.md). |
| `System.ArgIterator` | `va_list` (Windows x86/x64/arm64'te yalnızca) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Bu varsayılanlar, tam olarak aradığınız şeyi yapmazsanız, parametreleri nasıl sıraya özelleştirebilirsiniz. [Parametresi taşıma](customize-parameter-marshalling.md) nasıl farklı parametre türlerinin nasıl özelleştirildiği size sıraya Yürüyüşü makalesi.

## <a name="marshalling-classes-and-structs"></a>Sınıfları ve yapıları taşıma

Taşıma türü, başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür. Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir. Bu gibi durumlarda, yönetilen bölümünde bir parametresi olarak kullanılabilmesi için dünyanın karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir. Ancak, yalnızca bir sınıf tanımlama yeterli değildir, ayrıca Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek gerekir. Burada `StructLayout` özniteliği yararlı olur.

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

Önceki kod çağırma basit bir örneğini gösterir `GetSystemTime()` işlevi. 4. satırda ilginç bitidir. Öznitelik sınıfı alanlarını (yönetilmeyen) diğer tarafında struct sırayla eşlenmelidir belirtir. Bu adlandırma alanlarını'aşağıdaki örnekte gösterilen yönetilmeyen yapının karşılık gerektiğinde yalnızca bunların sırası önemlidir, önemli olmadığı anlamına gelir:

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

Bazen, yapı için taşıma varsayılan gerekenler yapmaz. [Yapısı taşıma özelleştirme](./customize-struct-marshalling.md) makale yapınızı nasıl sıralanır özelleştirme öğretir.
