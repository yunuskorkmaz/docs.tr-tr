---
title: Yapı özelleştirme sıralama - .NET
description: .NET yerel gösterimine, yapıları nasıl sürekliliğe devreder özelleştirmeyi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: da36f2a703fe817c171e192b9c94e473c93447a3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065473"
---
# <a name="customizing-structure-marshaling"></a>Yapı hazırlama özelleştirme

Bazen yapıları için varsayılan sıralama kuralları tam olarak ihtiyacınız olanları değil. .NET çalışma zamanları, yapının düzeni ve alanları nasıl sıralanmış özelleştirmeniz için birkaç uzantı noktaları sağlar.

## <a name="customizing-structure-layout"></a>Yapı düzenini özelleştirme

.NET sağlar <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> özniteliği ve <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> alanları bellekte nasıl yerleştirileceğini özelleştirmenize izin vermek için sabit listesi. Aşağıdaki yönergeler, sık karşılaşılan sorunları önlemenize yardımcı olur.

**✔️ DÜŞÜNÜN** kullanarak `LayoutKind.Sequential` mümkün olduğunda.

**✔️ YAPMAK** yalnızca `LayoutKind.Explicit` hazırlama yerel yapınızı ayrıca olduğunda bir birleşim gibi açık bir düzene sahip.

**❌ KAÇININ** kullanarak `LayoutKind.Explicit` yapıları Windows dışı platformlarda sıralarken. .NET Core çalışma zamanı açık yapıları değere göre yerel işlevleri için Intel ya da AMD 64 bit Windows olmayan sistemlerde geçirme desteklemiyor. Ancak, çalışma zamanı, tüm platformlarda başvuruya göre geçirme açık yapıları destekler.

## <a name="customizing-boolean-field-marshaling"></a>Boole alanı hazırlama özelleştirme

Yerel kod, birçok farklı Boole temsile sahiptir. Tek başına Windows üzerinde boolean değerlerini temsil edecek şekilde üç yolu vardır. Çalışma zamanı yerel tanımı yapınızın bilmeniz, yapmak için en iyi şekilde bir boolean değerlerinizi hazırlama hakkında tahminde değil. .NET çalışma zamanı nasıl hazırlanacağını boolean alan belirtmek için bir yol sağlar. Aşağıdaki örnekler nasıl hazırlanacağını .NET `bool` farklı yerel Boole türleri için.

Boole değerleri varsayılan yerel bir 4 baytlık Win32 sıralaması [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) aşağıdaki örnekte gösterildiği gibi değeri:

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

Açık olmasını istiyorsanız, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> yukarıdakilerle aynı davranışı sağlamak için değer:

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

Kullanarak `UnmanagedType.U1` veya `UnmanagedType.I1` aşağıdaki değerleri, çalışma zamanının sıralamanız öğrenebilirsiniz `b` bir 1 baytlık yerel olarak alan `bool` türü.

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

Windows üzerinde kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değeri, boolean değerine 2 baytlık hazırlamak için çalışma zamanı bildirmek için `VARIANT_BOOL` değeri:

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
> `VARIANT_BOOL` Çoğu bool türleri, farklı `VARIANT_TRUE = -1` ve `VARIANT_FALSE = 0`. Ayrıca, eşit olmayan tüm değerleri `VARIANT_TRUE` yanlış olarak değerlendirilir.

## <a name="customizing-array-field-marshaling"></a>Dizi alan hazırlama özelleştirme

.NET da dizi sıralaması özelleştirmek için birkaç yol içerir.

Varsayılan olarak, .NET dizileri için bitişik öğelerin listesini bir işaretçi olarak sürekliliğe devreder:

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

COM API'leri ile arabirim, dizileri olarak sıralamanız olabilir `SAFEARRAY*` nesneleri. Kullanabileceğiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> değeri olarak bir dizi hazırlamak için çalışma zamanı bildirmek için bir `SAFEARRAY*`:

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

Ne tür bir öğenin bulunduğu özelleştirmeniz gerekirse `SAFEARRAY`, kullanabileceğiniz sonra <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe özelleştirmek için alanları türü `SAFEARRAY`.

Yerinde dizi sıralamanız gerekirse, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> yerinde dizi hazırlamak için sıralayıcıya bildirmek için değer. Bu sıralama kullanırken da bir değer belirtmeniz gerekir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan çalışma zamanı yapısı için doğru yer ayırabilirsiniz şekilde dizideki öğelerin sayısı.

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
> .NET, C99 esnek dizi üyesi olarak bir değişken uzunluklu dizi alan hazırlama desteklemiyor.

## <a name="customizing-string-field-marshaling"></a>Dize alanı hazırlama özelleştirme

.NET çok çeşitli dize alanları hazırlama için özelleştirmeler de sağlar.

Varsayılan olarak, .NET bir dize null ile sonlandırılmış dizeye bir işaretçi olarak sürekliliğe devreder. Kodlama değerine bağlıdır <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanındaki <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>. Kodlamada hiçbir öznitelik belirtilmezse, bir ANSI kodlaması için kullanılır.

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

Farklı kodlamaları için farklı alanları kullanın veya sadece gerekiyorsa, yapı Tanımınızda daha net olmanızı tercih, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> üzerinde değerleri bir <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> özniteliği.

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

UTF-8 kodlaması kullanarak dizelerinizi hazırlamak istiyorsanız, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> değerini, <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

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
> Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> ya da .NET Framework 4.7 (veya sonraki sürümler) gerektirir veya .NET Core 1.1 (veya sonraki sürümler). .NET Standard 2.0 içinde kullanılamaz.

COM API'leri ile çalışıyorsanız, bir dize olarak sıralamanız gerekebilir bir `BSTR`. Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> değeri bir dize olarak hazırlamak bir `BSTR`.

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

WinRT tabanlı bir API kullanırken, bir dize olarak sıralamanız gerekebilir bir `HSTRING`.  Kullanarak <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> değeri bir dize olarak hazırlamak bir `HSTRING`.

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

API'nizi yapısında yerinde dizesini geçirmenizi gerektiriyorsa, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri. Bir dize için kodlama başvuruya göre olduğunu unutmayın `ByValTStr` gelen belirlenir `CharSet` özniteliği. Ayrıca, bir dize uzunluğu geçirilen gerektirir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan.

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

## <a name="customizing-decimal-field-marshaling"></a>Ondalık alan hazırlama özelleştirme

Windows üzerinde çalışıyorsanız, yerel kullanan bazı API'leri karşılaşabileceğiniz [ `CY` veya `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) yapısı. Varsayılan olarak, .NET `decimal` türü için yerel sıraladığında [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) yapısı. Ancak, kullanabileceğiniz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> dönüştürmek için sıralayıcı istemek için değer bir `decimal` yerel bir değer `CY` değeri.

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

## <a name="marshaling-systemobjects"></a>Hazırlama `System.Object`s

Windows üzerinde sıralanmamaktadır `object`-yazılan yerel kod için alanlar. Bu alanlar üç türlerden sıralanmamaktadır:
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Varsayılan olarak, bir `object`-alanın yazılan sıralanmış için bir `IUnknown*` nesnesinin sonuna geldik.

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

Bir nesne alanının için hazırlamak istiyorsanız bir `IDispatch*`, ekleme bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri.

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

Olarak hazırlamak istiyorsanız bir `VARIANT`, ekleme bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ile <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri.

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

Aşağıdaki tabloda farklı çalışma zamanı türlerini açıklar `obj` depolanan çeşitli türleri için alan haritası bir `VARIANT`:

| .NET türü | DEĞİŞKEN türü | | .NET türü | DEĞİŞKEN türü |
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
