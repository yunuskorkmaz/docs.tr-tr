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
# <a name="customizing-structure-marshaling"></a>Yapı hazırlamayı özelleştirme

Bazen yapılar için varsayılan sıralama kuralları, ihtiyacınız olan tam değildir. .NET çalışma zamanları, yapınızın yerleşimini ve alanların nasıl sıralanmayı özelleştirmeniz için birkaç uzantı noktası sağlar.

## <a name="customizing-structure-layout"></a>Yapı mizanpajını özelleştirme

.Net, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> alanların belleğe nasıl yerleştirileceğini <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> özelleştirmenizi sağlayacak özniteliği ve sabit listesini sağlar. Aşağıdaki kılavuz yaygın sorunlardan kaçınmanıza yardımcı olur.

mümkün olan **her durumda kullanmayı ✔️** `LayoutKind.Sequential` .

**✔️** yalnızca, yerel `LayoutKind.Explicit` yapının birleşim gibi açık bir düzeni de olduğunda, hazırlama sırasında kullanılır.

Windows dışı platformlarda `LayoutKind.Explicit` yapıları hazırlama sırasında **kullanmaktan kaçının ❌** . .NET Core çalışma zamanı, Intel veya AMD 64-bit Windows dışı sistemlerdeki yerel işlevlere değere göre açık yapıların geçirilmesini desteklemez. Ancak çalışma zamanı, tüm platformlarda başvuruya göre açık yapıların geçirilmesini destekler.

## <a name="customizing-boolean-field-marshaling"></a>Boole alan sıralamasını özelleştirme

Yerel kodun birçok farklı Boolean temsili vardır. Windows tek başına, Boole değerlerini göstermenin üç yolu vardır. Çalışma zamanı, yapınızın yerel tanımını bilmez, bu yüzden en iyi yöntem, Boolean değerlerinizi nasıl sıraleyeceğinizi tahmin edebilir. .NET çalışma zamanı, Boolean alanınızı nasıl sıralamadığını göstermek için bir yol sağlar. Aşağıdaki örneklerde, .net `bool` 'in farklı yerel Boole türlerine nasıl sıralaması yapılacağı gösterilmektedir.

Aşağıdaki örnekte gösterildiği gibi, yerel 4 baytlık bir Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) değeri olarak sıralama varsayılan Boole değerleri:

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

Açık olmasını istiyorsanız, yukarıdaki gibi aynı davranışı almak için <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> değeri kullanabilirsiniz:

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

`b` `bool` Aşağıdaki veya değerlerini`UnmanagedType.I1` kullanarak çalışma zamanına, alanı 1 baytlık yerel bir tür olarak sıralayamaz. `UnmanagedType.U1`

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

Windows 'ta, çalışma zamanına, Boole <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> değerini 2 baytlık `VARIANT_BOOL` bir değere göre sıralayamaz şekilde söylemek için bu değeri kullanabilirsiniz:

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
> `VARIANT_BOOL`, `VARIANT_TRUE = -1` ve`VARIANT_FALSE = 0`' deki en bool türlerden farklıdır. Ayrıca, eşit `VARIANT_TRUE` olmayan tüm değerler false olarak değerlendirilir.

## <a name="customizing-array-field-marshaling"></a>Dizi alanı sıralamasını özelleştirme

.NET ayrıca dizi sıralamasını özelleştirmenin birkaç yolunu içerir.

Varsayılan olarak, .NET, dizileri öğelerin bitişik listesine bir işaretçi olarak sıralar:

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

COM API 'leri ile arabirimleriniz varsa, dizileri nesneler olarak `SAFEARRAY*` sıralama yapmanız gerekebilir. Çalışma zamanına bir diziyi <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> bir `SAFEARRAY*`diziyi <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> sıralayamaz söylemek için ve değerini kullanabilirsiniz:

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

İçinde `SAFEARRAY`ne tür bir öğe olduğunu özelleştirmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve öğelerinin tam öğe türünü özelleştirmek `SAFEARRAY`için ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> alanlarını kullanabilirsiniz.

Diziyi yerinde sıralamakta ihtiyacınız varsa, sıralayıcıya diziyi yerinde sıralayamaz söylemek için <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> değerini kullanabilirsiniz. Bu sıralama 'yı kullanırken, çalışma zamanının yapıya doğru bir şekilde alan ayırabilmesi için <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> dizideki öğe sayısı için alana bir değer sağlamanız gerekir.

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
> .NET, bir değişken uzunluklu dizi alanının C99 esnek dizi üyesi olarak sıralamasını desteklemez.

## <a name="customizing-string-field-marshaling"></a>Dize alanı sıralamasını özelleştirme

.NET ayrıca, dize alanlarını hazırlama için çok çeşitli özelleştirmeler de sağlar.

Varsayılan olarak, .NET, bir dizeyi null ile sonlandırılmış bir dizenin işaretçisi olarak sıraar. Kodlama, <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>içindeki alanın değerine bağlıdır. Hiçbir öznitelik belirtilmemişse, kodlama varsayılan olarak bir ANSI kodlaması olur.

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

Farklı alanlar için farklı kodlamalar kullanmanız veya yapı tanımınızda daha açık olmasını tercih etmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> değerlerini bir <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> öznitelik üzerinde kullanabilirsiniz.

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

Dizelerinizi UTF-8 kodlaması kullanarak sıralamak isterseniz, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute>içindeki değeri kullanabilirsiniz.

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
> Kullanmak <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> .NET Framework 4,7 (veya sonraki sürümler) veya .NET Core 1,1 (ya da sonraki sürümler) gerektirir. .NET Standard 2,0 ' de kullanılamaz.

COM API 'Leri ile çalışıyorsanız bir dizeyi bir `BSTR`olarak sıralıyoruz. Değerini kullanarak bir dizeyi bir `BSTR`olarak sıraaktarabilirsiniz. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>

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

WinRT tabanlı bir API kullanırken bir dizeyi bir `HSTRING`olarak sıralamakta gerek olabilir.  Değerini kullanarak bir dizeyi bir `HSTRING`olarak sıraaktarabilirsiniz. <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>

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

API 'niz dizeyi yapıya yerinde geçirmeniz gerekiyorsa, bu <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri kullanabilirsiniz. Tarafından `ByValTStr` sıralanan bir dizenin kodlamasının `CharSet` öznitelikten belirlendiğini unutmayın. Ayrıca, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> alan tarafından bir dize uzunluğunun geçirilmesini gerektirir.

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

## <a name="customizing-decimal-field-marshaling"></a>Ondalık alan sıralamasını özelleştirme

Windows üzerinde çalışıyorsanız, yerel [ `CY` veya `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) yapıyı kullanan bazı API 'lerle karşılaşabilirsiniz. Varsayılan olarak, .net `decimal` türü yerel [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) yapıya göre sıralar. Bununla birlikte <xref:System.Runtime.InteropServices.MarshalAsAttribute> , bir `decimal` değeri yerel <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> `CY` bir değere dönüştürmek üzere Sıralayıcı 'yı yönlendirmek için değeriyle birlikte kullanabilirsiniz.

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

## <a name="marshaling-systemobjects"></a>Sıralama `System.Object`

Windows 'ta, yerel koda göre `object`türsüz alanları sıraaktarabilirsiniz. Bu alanları üç türden birine göre sıraaktarabilirsiniz:
- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Varsayılan olarak, bir `object`türü olan bir alan, nesneyi sarmalayan `IUnknown*` bir öğesine sıralanacaktır.

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

Bir nesne alanını bir `IDispatch*`öğesine sıralamak istiyorsanız <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> değeri ile bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ekleyin.

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

Bunu bir `VARIANT`olarak sıralamak istiyorsanız <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> değeri ile bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> ekleyin.

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

Aşağıdaki tabloda, `obj` alanın farklı çalışma zamanı türlerinin `VARIANT`' de depolanan çeşitli türlere nasıl eşlendiğini açıklanmaktadır:

| .NET türü | DEĞIŞKEN türü | | .NET türü | DEĞIŞKEN türü |
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
