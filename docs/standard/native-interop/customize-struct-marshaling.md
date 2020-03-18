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
# <a name="customizing-structure-marshaling"></a>Yapı hazırlamayı özelleştirme

Bazen yapılar için varsayılan mareşalleme kuralları tam olarak ihtiyacınız olan şey değildir. .NET çalışma saatleri, yapınızın düzenini ve alanların nasıl marshaled'ini özelleştirmeniz için birkaç uzantı noktası sağlar.

## <a name="customizing-structure-layout"></a>Yapı düzenini özelleştirme

.NET, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> alanların belleğe <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> nasıl yerleştirildiğini özelleştirmenize olanak tanıyan öznitelik ve numaralandırma sağlar. Aşağıdaki kılavuz, sık karşılaşılan sorunları önlemenize yardımcı olur.

✔️ mümkün `LayoutKind.Sequential` olduğunca kullanmayı düşünün.

✔️ yalnızca `LayoutKind.Explicit` yerel yapınız da birleşim gibi açık bir düzene sahipse, mareşallikte kullanın.

❌.NET `LayoutKind.Explicit` Core 3.0'dan önce çalışma sürelerini hedeflemeniz gerekiyorsa, Windows dışı platformlarda yapıları mareşallik yaparken kullanmaktan kaçının. 3.0'dan önceki .NET Core çalışma süresi, Intel veya AMD 64 bit Windows dışı sistemlerde açık yapıların yerel işlevlere değer olarak geçirilmesini desteklemez. Ancak, çalışma zamanı tüm platformlarda başvuru ile açık yapıları geçen destekler.

## <a name="customizing-boolean-field-marshaling"></a>Boolean mareşalözelleme

Yerel kod birçok farklı boolean gösterimleri vardır. Sadece Windows'da boolean değerlerini temsil etmenin üç yolu vardır. Çalışma zamanı yapınızın yerel tanımını bilmiyor, bu yüzden yapabileceği en iyi şey boolean değerlerinizi nasıl kareşalyapacağınız hakkında bir tahminde bulunmaktır. .NET çalışma zamanı, boolean alanınızı nasıl mareşallik ediniz gösterir. Aşağıdaki örnekler , .NET'in `bool` farklı yerli boolean türlerine nasıl atandığını gösterir.

Boolean değerleri varsayılan olarak aşağıdaki örnekte gösterildiği gibi [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) yerel 4 bayt lık win32 değeri olarak marshaling için:

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

Açık olmak istiyorsanız, yukarıdaki yle <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> aynı davranışı elde etmek için değeri kullanabilirsiniz:

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

Aşağıdaki `UnmanagedType.U1` değerleri `UnmanagedType.I1` veya değerleri kullanarak, çalışma zamanını `b` alanı 1 baytlık `bool` yerel bir tür olarak mareşal olarak yazabilirsiniz.

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

Windows'da, boolean <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değerinizi 2 baytlık `VARIANT_BOOL` bir değere göre düzenlemeyi çalışma zamanı söylemek için değeri kullanabilirsiniz:

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
> `VARIANT_BOOL`bu `VARIANT_TRUE = -1` ve `VARIANT_FALSE = 0`en bool türleri farklıdır. Ayrıca, eşit olmayan tüm değerler `VARIANT_TRUE` yanlış olarak kabul edilir.

## <a name="customizing-array-field-marshaling"></a>Dizi mareşalcilik özelleştirme

.NET ayrıca dizi mareşallik özelleştirmek için birkaç yol içerir.

Varsayılan olarak, .NET dizileri öğelerin bitişik listesine işaretçi olarak alır:

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

COM API'leri ile birlikte arıyorsanız, dizileri nesne `SAFEARRAY*` olarak sıralamanız gerekebilir. Bir diziyi <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> şöyle <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> bir şekilde mareşalleştirmek için `SAFEARRAY*`çalışma saatini söylemek için ve değeri kullanabilirsiniz:

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

Eğer öğe nin ne tür özelleştirmek `SAFEARRAY`gerekiyorsa, o zaman <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe türünü özelleştirmek için `SAFEARRAY`ve alanları kullanabilirsiniz .

Diziyi yerinde yerleştirmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> mareşale diziyi yerinde mareşallik etmesini söylemek için değeri kullanabilirsiniz. Bu mareşalliği kullanırken, çalışma zamanının yapı <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> için doğru bir alan ayırabilmesi için dizideki öğe sayısı için alana bir değer sağlamanız gerekir.

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
> .NET, c99 Esnek Dizi Üyesi olarak değişken uzunlukta bir dizi alanının marshaling desteklemez.

## <a name="customizing-string-field-marshaling"></a>Dize mareşalleme özelleştirme

.NET ayrıca dize alanlarını mareşallik için çok çeşitli özelleştirmeler sağlar.

Varsayılan olarak, .NET bir dizeyi null-sonlandırılan dize için işaretçi olarak sıralar. Kodlama, <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> alanın değerine <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>bağlıdır. Öznitelik belirtilmemişse, kodlama varsayılan olarak bir ANSI kodlamasına gelir.

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

Farklı alanlar için farklı kodlamalar kullanmanız veya yapı tanımınızda daha açık olmayı tercih ederseniz, <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> öznitelik <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> üzerinde veya değerleri kullanabilirsiniz.

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

UTF-8 kodlamasını kullanarak dizelerinizi mareşalleştirmek istiyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> ''deki <xref:System.Runtime.InteropServices.MarshalAsAttribute>değeri kullanabilirsiniz.

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
> Kullanmak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> için .NET Framework 4.7 (veya sonraki sürümler) veya .NET Core 1.1 (veya daha sonraki sürümler) gerekir. .NET Standart 2.0'da kullanılamaz.

COM API'leri ile çalışıyorsanız, bir dizeyi `BSTR`bir . <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> Değeri kullanarak, bir dizeyi `BSTR`'' olarak sıralayabilirsiniz.

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

WinRT tabanlı BIR API kullanırken, bir dizeyi `HSTRING`'' olarak bağlamanız gerekebilir.  <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> Değeri kullanarak, bir dizeyi `HSTRING`'' olarak sıralayabilirsiniz.

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

API'niz dizeyi yapıdaki yerine geçirmenizi gerektiriyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri kullanabilirsiniz. Bir `ByValTStr` dize için kodlama nın öznitelikten `CharSet` belirlendiğini unutmayın. Ayrıca, bir dize uzunluğu <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan tarafından geçirilir gerektirir.

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

## <a name="customizing-decimal-field-marshaling"></a>Ondalık alan mareşalcilik özelleştirme

Windows üzerinde çalışıyorsanız, yerel [ `CY` veya `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) yapıyı kullanan bazı API'larla karşılaşabilirsiniz. Varsayılan olarak, .NET `decimal` türü yerel [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) yapıya marshals. Ancak, <xref:System.Runtime.InteropServices.MarshalAsAttribute> bir <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> değeri yerel `decimal` `CY` değere dönüştürmesi için mareşaltalimat değeri ile a kullanabilirsiniz.

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

## <a name="marshaling-systemobjects"></a>Mareşallik `System.Object`

Windows'da, yazılan `object`alanları yerel koda göre yazabilirsiniz. Bu alanları üç türden birine göre mareşallik yapabilirsiniz:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Varsayılan olarak, `object`türü yazılmı yapılan bir `IUnknown*` alan nesneyi saran bir alana marshaled olacaktır.

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

Bir nesne alanını bir `IDispatch*`nesneye göre <xref:System.Runtime.InteropServices.MarshalAsAttribute> mareşallemek istiyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri ile a ekleyin.

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

Eğer bir `VARIANT`olarak mareşal istiyorsanız <xref:System.Runtime.InteropServices.MarshalAsAttribute> , <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri ile bir ekleyin.

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

Aşağıdaki tabloda, `obj` alan eşleminin farklı çalışma zamanı türlerinin, bir `VARIANT`tabloda depolanan çeşitli türlere ne kadar farklı olduğu açıklanmaktadır:

| .NET Türü | VARYANT Türü | | .NET Türü | VARYANT Türü |
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
