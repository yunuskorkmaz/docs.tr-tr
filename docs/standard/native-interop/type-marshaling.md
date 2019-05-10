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
# <a name="type-marshaling"></a>Sıralama türü

**Hazırlama** yönetilen ve yerel kod arasında çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.

Yönetilen ve yönetilmeyen kod türleri farklı olduğundan, hazırlama gereklidir. Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyleri yapacakları dener. Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği. Dizeyi ANSI null ile sonlandırılmış dize olarak gönderilmesini istiyorsanız, örneğin, şöyle bunu:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a>Varsayılan kuralları ortak türlerini hazırlama

Çalışma zamanı genellikle "doğru şeyi" yaptığınızda dener iş sizden az miktarda gerektirecek şekilde hazırlama. Aşağıdaki tablolar, bir parametre veya alanında kullanıldığında varsayılan olarak her tür nasıl sıralanmış açıklamaktadır. C99 / C ++ 11 sabit genişlik tamsayı ve karakter türleri aşağıdaki tabloda tüm platformlar için doğru olduğundan emin olmak için kullanılır. Aynı hizalama ve bu türü olarak boyut gereksinimlerine sahip herhangi bir yerel tür kullanabilirsiniz.

Birinci tablo eşlemelerini kendisi için hazırlama P/Invoke ve hazırlama alanı için aynı çeşitli türleri açıklanmaktadır.

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

Hazırlama, birkaç kategoriden varsayılan değerleri farklı varsa bir parametre veya yapısı hazırlama.

| .NET türü | Yerel türü (parametre) | Yerel bir tür (alan) |
|-----------|-------------------------|---------------------|
| .NET dizisi | Dizi öğeleri yerel temsillerini bir dizi başlangıcı için bir işaretçi. | Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği|
| Bir sınıf ile bir `LayoutKind` , `Sequential` veya `Explicit` | Yerel gösterimine sınıfının işaretçisi | Yerel gösterimi sınıfı |

Aşağıdaki tablo, varsayılan sıralama kuralları içerir. yalnızca Windows. Windows dışı platformlarda, bu tür sıralanamıyor.

| .NET türü | Yerel türü (parametre) | Yerel bir tür (alan) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | COM arabirimi | Olmadan izin verilmiyor bir `[MarshalAs]` özniteliği |
| `System.ArgIterator` | `va_list` | İzin verilmiyor |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | İzin verilmiyor |
| `System.Collections.IEnumerable` | `IDispatch*` | İzin verilmiyor |
| `System.DateTimeOffset` | `int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden || `int64_t` 1 Ocak 1601 gece yarısından tıklarının sayısını temsil eden |

Bazı türleri parametre olarak ve alanlar olarak değil yalnızca sıralanabilir. Bu tür aşağıdaki tabloda listelenmiştir:

| .NET türü | Yerel bir tür (yalnızca parametresi) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | Ya da `char*` veya `char16_t*` bağlı olarak `CharSet` P/Invoke.  Bkz: [charset belgeleri](charset.md). |
| `System.ArgIterator` | `va_list` (Windows x86/x64/arm64'te yalnızca) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Bu varsayılanlar, tam olarak aradığınız şeyi yapmazsanız, parametreleri nasıl sıralanmış özelleştirebilirsiniz. [Parametreyi](customize-parameter-marshaling.md) makalesi Yürüyüşü nasıl farklı parametre türlerinin nasıl özelleştirildiği size hazırlanır.

## <a name="marshaling-classes-and-structs"></a>Sınıfları ve yapıları sıralama

Sıralama türü başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür. Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir. Bu gibi durumlarda, yönetilen bölümünde bir parametresi olarak kullanılabilmesi için dünyanın karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir. Ancak, yalnızca bir sınıf tanımlama yeterli değildir, ayrıca Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek gerekir. Burada `StructLayout` özniteliği yararlı olur.

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

Bazen, yapı için hazırlama varsayılan gerekenler yapmaz. [Yapısı hazırlama özelleştirme](./customize-struct-marshaling.md) makale yapınızı nasıl sıralanır özelleştirme öğretir.
