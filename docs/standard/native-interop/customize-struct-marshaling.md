---
title: Yapı sıralamasını özelleştirme-.NET
description: .NET 'in yapılarınızı yerel bir gösterimde nasıl sıraladığında nasıl özelleştireceğinizi öğrenin.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 8248ca589f41967a9112ba61c09599b337814de7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003899"
---
# <a name="customizing-structure-marshaling"></a>Yapı hazırlamayı özelleştirme

Bazen yapılar için varsayılan sıralama kuralları, ihtiyacınız olan tam değildir. .NET çalışma zamanları, yapınızın yerleşimini ve alanların nasıl sıralanmayı özelleştirmeniz için birkaç uzantı noktası sağlar.

## <a name="customizing-structure-layout"></a>Yapı mizanpajını özelleştirme

.NET, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> alanların belleğe nasıl yerleştirileceğini özelleştirmenizi sağlayacak özniteliği ve sabit listesini sağlar. Aşağıdaki kılavuz yaygın sorunlardan kaçınmanıza yardımcı olur.

`LayoutKind.Sequential`mümkün olan her durumda kullanmayı ✔️.

✔️ yalnızca `LayoutKind.Explicit` , yerel yapı yerinizde birleşim gibi açık bir düzen varsa, hazırlama sırasında kullanılır.

❌`LayoutKind.Explicit`.NET Core 3,0 ' den önce çalışma zamanlarını hedeflemek gerekirse, Windows dışı platformlarda yapıları hazırlama sırasında kullanmaktan kaçının. 3,0 öncesi .NET Core çalışma zamanı, Intel veya AMD 64-bit Windows dışı sistemlerdeki yerel işlevlere değere göre açık yapıların geçirilmesini desteklemez. Ancak çalışma zamanı, tüm platformlarda başvuruya göre açık yapıların geçirilmesini destekler.

## <a name="customizing-boolean-field-marshaling"></a>Boole alan sıralamasını özelleştirme

Yerel kodun birçok farklı Boolean temsili vardır. Windows tek başına, Boole değerlerini göstermenin üç yolu vardır. Çalışma zamanı, yapınızın yerel tanımını bilmez, bu yüzden en iyi yöntem, Boolean değerlerinizi nasıl sıraleyeceğinizi tahmin edebilir. .NET çalışma zamanı, Boolean alanınızı nasıl sıralamadığını göstermek için bir yol sağlar. Aşağıdaki örneklerde, .NET `bool` 'in farklı yerel Boole türlerine nasıl sıralaması yapılacağı gösterilmektedir.

Aşağıdaki örnekte gösterildiği gibi, yerel 4 baytlık bir Win32 değeri olarak sıralama varsayılan Boole değerleri [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) :

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

Açık olmasını istiyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> yukarıdaki gibi aynı davranışı almak için değeri kullanabilirsiniz:

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

`UnmanagedType.U1` `UnmanagedType.I1` Aşağıdaki veya değerlerini kullanarak çalışma zamanına, `b` alanı 1 baytlık yerel bir tür olarak sıralayamaz `bool` .

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

Windows 'ta, <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> çalışma zamanına, Boole değerini 2 baytlık bir değere göre sıralayamaz şekilde söylemek için bu değeri kullanabilirsiniz `VARIANT_BOOL` :

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
> `VARIANT_BOOL`, ve ' deki en bool türlerden farklıdır `VARIANT_TRUE = -1` `VARIANT_FALSE = 0` . Ayrıca, eşit olmayan tüm değerler `VARIANT_TRUE` false olarak değerlendirilir.

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

COM API 'Leri ile arabirimleriniz varsa, dizileri nesneler olarak sıralama yapmanız gerekebilir `SAFEARRAY*` . <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> Çalışma zamanına bir diziyi bir diziyi sıralayamaz söylemek için ve değerini kullanabilirsiniz `SAFEARRAY*` :

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

İçinde ne tür bir öğe olduğunu özelleştirmeniz gerekiyorsa, `SAFEARRAY` <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve öğelerinin <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe türünü özelleştirmek için ve alanlarını kullanabilirsiniz `SAFEARRAY` .

Diziyi yerinde sıralamakta ihtiyacınız varsa, <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> sıralayıcıya diziyi yerinde sıralayamaz söylemek için değerini kullanabilirsiniz. Bu sıralama 'yı kullanırken, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> çalışma zamanının yapıya doğru bir şekilde alan ayırabilmesi için dizideki öğe sayısı için alana bir değer sağlamanız gerekir.

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

Varsayılan olarak, .NET, bir dizeyi null ile sonlandırılmış bir dizenin işaretçisi olarak sıraar. Kodlama <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> , içindeki alanın değerine bağlıdır <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> . Hiçbir öznitelik belirtilmemişse, kodlama varsayılan olarak bir ANSI kodlaması olur.

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

Farklı alanlar için farklı kodlamalar kullanmanız veya yapı tanımınızda daha açık olmasını tercih etmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> değerlerini bir öznitelik üzerinde kullanabilirsiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> .

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

Dizelerinizi UTF-8 kodlaması kullanarak sıralamak isterseniz, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> içindeki değeri kullanabilirsiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute> .

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

COM API 'Leri ile çalışıyorsanız bir dizeyi bir olarak sıralıyoruz `BSTR` . Değerini kullanarak bir <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> dizeyi bir olarak sıraaktarabilirsiniz `BSTR` .

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

WinRT tabanlı bir API kullanırken bir dizeyi bir olarak sıralamakta gerek olabilir `HSTRING` .  Değerini kullanarak bir <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> dizeyi bir olarak sıraaktarabilirsiniz `HSTRING` .

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

API 'niz dizeyi yapıya yerinde geçirmeniz gerekiyorsa, bu <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> değeri kullanabilirsiniz. Tarafından sıralanan bir dizenin kodlamasının `ByValTStr` `CharSet` öznitelikten belirlendiğini unutmayın. Ayrıca, alan tarafından bir dize uzunluğunun geçirilmesini gerektirir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> .

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

Windows üzerinde çalışıyorsanız, yerel [ `CY` veya `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) yapıyı kullanan bazı API 'lerle karşılaşabilirsiniz. Varsayılan olarak, .NET `decimal` türü yerel yapıya göre sıralar [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) . Bununla birlikte, bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> değeri yerel bir değere dönüştürmek üzere Sıralayıcı 'yı yönlendirmek için değeriyle birlikte kullanabilirsiniz `decimal` `CY` .

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

Windows 'ta, `object` yerel koda göre türsüz alanları sıraaktarabilirsiniz. Bu alanları üç türden birine göre sıraaktarabilirsiniz:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Varsayılan olarak, bir `object` türü olan bir alan, nesneyi sarmalayan bir öğesine sıralanacaktır `IUnknown*` .

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

Bir nesne alanını bir öğesine sıralamak istiyorsanız `IDispatch*` <xref:System.Runtime.InteropServices.MarshalAsAttribute> değeri ile bir ekleyin <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> .

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

Bunu bir olarak sıralamak istiyorsanız `VARIANT` <xref:System.Runtime.InteropServices.MarshalAsAttribute> değeri ile bir ekleyin <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> .

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

Aşağıdaki tabloda, alanın farklı çalışma zamanı türlerinin `obj` ' de depolanan çeşitli türlere nasıl eşlendiğini açıklanmaktadır `VARIANT` :

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
