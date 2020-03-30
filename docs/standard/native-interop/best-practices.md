---
title: Yerli birlikte çalışabilirlik en iyi uygulamalar - .NET
description: .NET'te yerel bileşenlerle etkileşim için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391227"
---
# <a name="native-interoperability-best-practices"></a>Yerel birlikte çalışabilirlik en iyi uygulamalar

.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmeniz için çeşitli yollar sunar. Bu makalede, Microsoft'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği kılavuz yer almaktadır.

## <a name="general-guidance"></a>Genel rehber

Bu bölümdeki kılavuz tüm interop senaryoları için geçerlidir.

- ✔️ DO, aramak istediğiniz yerel yöntemle yöntemleriniz ve parametreleriniz için aynı adlandırma ve büyük harf kullanır.
- ✔️ sabit değerler için aynı adlandırma ve büyük harf kullanmayı düşünün.
- ✔️ DO, yerel türe en yakın eşlenebilen .NET türlerini kullanır. Örneğin, C#'da, `uint` yerel tür `unsigned int`.
- ✔️ yalnızca `[In]` istediğiniz `[Out]` davranış varsayılan davranıştan farklı olduğunda kullanın ve öznitelik.
- ✔️ yerel <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> dizi arabelleklerinizi bir araya getirmek için kullanmayı düşünün.
- ✔️ P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfa sarmayı düşünün.
  - Bu, `[DllImport]` özniteliklerinizin yerel `nameof` kitaplığın adına geçmek ve yerel kitaplığın adını yanlış yazmadığınızdan emin olmak için C# dil özelliğini kullanmasına olanak tanır.

## <a name="dllimport-attribute-settings"></a>DllImport öznitelik ayarları

| Ayar | Varsayılan | Öneri | Ayrıntılar |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  varsayılan tutma  | Bu açıkça yanlış olarak ayarlandığında, başarısız HRESULT iade değerleri özel durumlara dönüştürülür (ve tanımdaki iade değeri sonuç olarak null olur).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | API bağlıdır  | API GetLastError kullanıyorsa bunu doğru olarak ayarlayın ve değeri almak için Marshal.GetLastWin32Error'ı kullanın. API bir hata olduğunu söyleyen bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için diğer aramaları yapmadan önce hatayı alın.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, davranışa `CharSet.Ansi` geri döner  | Tanımda `CharSet.Unicode` açıkça `CharSet.Ansi` veya dizeleri veya karakterleri mevcut olduğunda | Bu dizeleri mareşal davranışını `ExactSpelling` belirtir `false`ve ne zaman . Unix'te utf8 olduğunu `CharSet.Ansi` unutmayın. _Unix_ UTF8 kullanırken Çoğu zaman Windows Unicode kullanır. [Charsets üzerinde belgeler](./charset.md)hakkında daha fazla bilgi bakın. |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Çalışma zamanı `CharSet` ayarın değerine bağlı olarak "A" veya "W" soneki ("A" için `CharSet.Ansi` ve "W" için) ile alternatif işlev adları aramaz gibi bunu doğru ayarlayın ve hafif bir perf yararı elde edin. `CharSet.Unicode` |

## <a name="string-parameters"></a>Dize parametreleri

CharSet Unicode olduğunda veya bağımsız değişken açıkça `[MarshalAs(UnmanagedType.LPWSTR)]` olarak işaretlendiğinde _ve_ dize `out`değere göre geçirildiğinde (değil veya), `ref` dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmak yerine).

`[DllImport]` Dizelerinizin `Charset.Unicode` ANSI tedavisini açıkça istemediğiniz sürece işaretlemeyi unutmayın.

❌PARAMETRELERİ `[Out] string` KULLANMAYIN. Dize interned dize ise öznitelik ile `[Out]` değer tarafından geçirilen dize parametreleri çalışma süresini bozabilir. Için belgelerde dize stajı <xref:System.String.Intern%2A?displayProperty=nameWithType>hakkında daha fazla bilgi için bkz.

❌PARAMETRELERDEN KAÇıN. `StringBuilder` `StringBuilder`mareşallik *her zaman* yerel bir arabellek kopyası oluşturur. Bu nedenle, son derece verimsiz olabilir. Dize alan bir Windows API'yi arama nın tipik senaryosunu ele alalım:

1. İstenilen kapasitede bir SB oluşturma (yönetilen kapasiteyi tahsis eder)**{1}**
2. Çağır
   1. Yerel arabellek ayırır**{2}**
   2. Eğer içeriği `[In]` kopyalar _(parametre `StringBuilder` için varsayılan)_
   3. Yerel arabelleği yeni ayrılan yönetilen bir `[Out]` **{3}** diziye kopyalar _(ayrıca `StringBuilder`varsayılan)_
3. `ToString()`başka bir yönetilen dizi ayırır**{4}**

Bu, *{4}* yerel koddan bir dize çıkarmak için ayırmalar. Bunu sınırlamak için yapabileceğiniz en iyi şey `StringBuilder` başka bir aramayı yeniden kullanmaktır, ancak bu yine de yalnızca *1* ayırma kaydeder. Bir karakter arabelleğini kullanmak ve önbelleğe `ArrayPool`almak çok daha iyidir - daha `ToString()` sonra sonraki aramalariçin sadece tahsisata inebilirsiniz.

Diğer `StringBuilder` bir sorun ise, iade arabelleği her zaman ilk null'a kadar kopyalar. Geçirilen geri dize sonlandırılmazsa veya çift null-sonlandırılan dize ise, P/Invoke'ınız en iyi şekilde yanlıştır.

*Eğer* kullanırsanız `StringBuilder`, son bir gotcha kapasite her zaman interop için muhasebeleştirilmiş gizli bir null, **içermemelidir.** Çoğu API null *dahil* arabellek boyutunu istediğiniz gibi insanların bu yanlış almak için yaygındır. Bu, boşa/gereksiz ayırmalara neden olabilir. Ayrıca, bu gotcha kopyaları en aza `StringBuilder` indirmek için mareşal optimize çalışma zamanı engeller.

✔️ s `char[]`kullanarak `ArrayPool`DÜŞÜNÜN bir .

Dize mareşalliği hakkında daha fazla bilgi için, [Strings için Varsayılan Mareşalve](../../framework/interop/default-marshaling-for-strings.md) [Özelleştirstring mareşalleme](customize-parameter-marshaling.md#customizing-string-parameters)bakın.

> __Windows'a Özel__ `[Out]` Dizeleri için CLR `CoTaskMemFree` varsayılan olarak serbest dizeleri veya `SysStringFree` olarak `UnmanagedType.BSTR`işaretlenmiş dizeleri için kullanır.
> **Çıktı dize arabelleği olan çoğu API için:** Karakter sayısında geçen null içermelidir. Döndürülen değer karakter sayısında geçirilenden daha azsa, çağrı başarılı oldu ve değer, azalan null *olmayan* karakter sayısıdır. Aksi takdirde sayım, null karakteri *de dahil olmak üzere* arabelleğe gereken boyuttur.
>
> - 5 pass, 4 olsun: dize bir iz null ile 4 karakter uzunluğundadır.
> - Pass 5, 6 olsun: dize 5 karakter uzunluğunda, null tutmak için 6 karakter arabellek gerekir.
> [Dizeleri için Windows Veri Türleri](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boolean parametreleri ve alanları

Booleans berbat etmek kolaydır. Varsayılan olarak, bir `bool` .NET, 4 `BOOL`bayt değerinde olan bir Windows'a marshaled. Ancak, `_Bool`C `bool` ve C++'daki , ve türleri *tek* bir baytdır. Bu, geri dönüş değerinin yarısı atıldığından hataların izlenmesi zor olabilir ve bu da sonucu *yalnızca değiştirebilir.* .NET `bool` değerlerini C veya C++ `bool` türlerine göre mareşalleme hakkında daha fazla bilgi için [boolean mareşallemesini özelleştirmeyle](customize-struct-marshaling.md#customizing-boolean-field-marshaling)ilgili belgelere bakın.

## <a name="guids"></a>Guıd

GUID'ler doğrudan imzalarda kullanılabilir. Birçok Windows API's i `REFIID`gibi `GUID&` tür takma alır. Ref tarafından geçirildiğinde, onlar ya `ref` tarafından `[MarshalAs(UnmanagedType.LPStruct)]` geçirilebilir ya da özniteliği ile.

| GUID | By-ref GUID |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌GUID parametreleri dışında `[MarshalAs(UnmanagedType.LPStruct)]` `ref` başka bir şey için KULLANMAYIN.

## <a name="blittable-types"></a>Blittable türleri

Blittable türleri yönetilen ve yerel kod aynı bit düzeyi gösterimi olan türleridir. Bu nedenle, yerel koda ve yerel koddan mareşalolmak üzere başka bir biçime dönüştürülmelerine gerek yoktur ve bu performansı artırdığı için tercih edilmelidir.

**Blittable türleri:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- blittable türleri iç içe olmayan tek boyutlu diziler `int[]`(örneğin, )
- örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip yapı ve sınıflar
  - sabit düzen `[StructLayout(LayoutKind.Sequential)]` gerektirir veya`[StructLayout(LayoutKind.Explicit)]`
  - structs `LayoutKind.Sequential` varsayılan olarak, sınıflar`LayoutKind.Auto`

**NOT blittable:**

- `bool`

**BAZEN blittable:**

- `char`, `string`

Blittable türleri başvuru ile geçirildiğinde, bir ara arabelleğe kopyalanmak yerine yalnızca marshaller tarafından sabitlenirler. (Sınıflar doğal olarak referans la geçirilir, structs `ref` ile `out`kullanıldığında referans tarafından geçirilir veya .)

`char`tek boyutlu bir **dizide** veya açıkça 'ile `[StructLayout]` `CharSet = CharSet.Unicode`işaretlenmiş içeren bir türün parçası ise blittable.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`başka bir türde içermiyorsa ve işaretli `[MarshalAs(UnmanagedType.LPWStr)]` veya `[DllImport]` ayarlanmış `CharSet = CharSet.Unicode` bir bağımsız değişken olarak geçiriliyorsa blittable olur.

Sabitlenmiş `GCHandle`bir tür oluşturmaya çalışarak bir türün blittable olup olmadığını görebilirsiniz. Tür bir dize değilse veya blittable `GCHandle.Alloc` olarak `ArgumentException`kabul edilirse, bir .

✔️ yapılarınızı mümkün olduğunda blittable olun.

Daha fazla bilgi için bkz.

- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../framework/interop/blittable-and-non-blittable-types.md)
- [Tip Mareşallik](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Yönetilen nesneleri canlı tutma

`GC.KeepAlive()`KeepAlive yöntemi vuruluna kadar bir nesnenin kapsamda kalmasını sağlar.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)marshaller'ın bir nesneyi P/Invoke süresince canlı tutmasını sağlar. Yöntem imzaları yerine `IntPtr` kullanılabilir. `SafeHandle`bu sınıfın yerini alır ve bunun yerine kullanılmalıdır.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)yönetilen bir nesneyi sabitlemeye ve yerel işaretçinin ona yerlemesine izin verir. Temel desen:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Sabitleme için varsayılan `GCHandle`değildir. Diğer önemli desen, yönetilen bir nesneye yerel kod üzerinden başvuru aktarmak ve genellikle geri arama ile yönetilen koda geri dönmek içindir. İşte desen:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Bellek sızıntılarını `GCHandle` önlemek için açıkça serbest bırakılmaları gerektiğini unutmayın.

## <a name="common-windows-data-types"></a>Ortak Windows veri türleri

Windows API'larında yaygın olarak kullanılan ve Windows koduna ararken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi aşağıda verilmiştir.

Aşağıdaki türler, adlarına rağmen 32 bit ve 64 bit Windows'da aynı boyuttadır.

| Genişlik | Windows          | C (Windows)          | C#       | Alternatif                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |

İşaretçiler olmak üzere aşağıdaki türler platformun genişliğini izler. Bunları `IntPtr` / `UIntPtr` kullan.

| İmzalı İşaretçi `IntPtr`Türleri (kullanım) | İmzasız İşaretçi `UIntPtr`Türleri (kullanım) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

`PVOID` C `void*` olan bir Windows ya da `IntPtr` `UIntPtr`, ancak `void*` mümkün olduğunca tercih olarak marshaled olabilir.

[Windows Veri Türleri](/windows/desktop/WinProg/windows-data-types)

[Veri Türü Aralıkları](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Yapılar

Yönetilen structs yığın üzerinde oluşturulur ve yöntem döndürür kadar kaldırılmaz. Tanım olarak o zaman, onlar "sabitlenmiş" (GC tarafından taşınmış almazsınız). Yerel kod işaretçiyi geçerli yöntemin sonundan sonra kullanmıyorsa, adresi güvenli olmayan kod bloklarında da alabilirsiniz.

Blittable structs sadece doğrudan mareşal tabaka tarafından kullanılabilir gibi çok daha performant vardır. Structs blittable yapmaya çalışın (örneğin, kaçının). `bool` Daha fazla bilgi için [Blittable Türleri](#blittable-types) bölümüne bakın.

*If* Yapı blittable ise, daha `sizeof()` iyi `Marshal.SizeOf<MyStruct>()` performans yerine kullanın. Yukarıda belirtildiği gibi, sabitlenmiş `GCHandle`bir oluşturmak için deneyerek türünün blittable olduğunu doğrulayabilirsiniz. Tür bir dize değilse veya blittable olarak kabul edilirse, `GCHandle.Alloc` bir `ArgumentException`.

Tanımlardaki yapı işaretçileri ya geçilmeli `ref` ya da `unsafe` `*`kullanılmalıdır ve .

✔️ DO, yönetilen yapıyla resmi platform belgelerinde veya üstbilgide kullanılan şekil ve adlarla mümkün olduğunca yakından eşleşir.

✔️ DO, performansı `sizeof()` artırmak `Marshal.SizeOf<MyStruct>()` için blittable yapılar yerine C# kullanın.

❌Yapılardaki `System.Delegate` `System.MulticastDelegate` işlev işaretçisi alanlarını temsil etmek için kullanmaktan veya alanlardan kaçının.

Gerekli <xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> bir imzaya sahip olmadıklarından ve gerekli imzaya sahip olmadıklarından, geçen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti etmezler. Ayrıca, .NET Framework ve .NET Core'da, yerel `System.Delegate` gösterimini içeren bir yapıyı veya `System.MulticastDelegate` yerel temsilini içeren bir yapıyı yönetilen bir nesneye iliştirmek, yerel gösterimdeki alanın değeri yönetilen bir temsilciyi saran bir işlev işaretçisi değilse çalışma süresini bozabilir. .NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alan yerel gösterimden yönetilen bir nesneye marshaling desteklenmez. Veya `System.Delegate` `System.MulticastDelegate`' yerine belirli bir temsilci türü kullanın

### <a name="fixed-buffers"></a>Sabit Arabellekler

Bunun gibi `INT_PTR Reserved1[2]` bir dizi iki `IntPtr` alana `Reserved1a` marshaled gerekir ve `Reserved1b`. Yerel dizi ilkel bir tür olduğunda, `fixed` anahtar kelimeyi biraz daha temiz yazmak için kullanabiliriz. Örneğin, `SYSTEM_PROCESS_INFORMATION` yerel üstbilgide şu na benzer:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

C#'da şöyle yazabiliriz:

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

Ancak, sabit arabellekleri ile bazı gotchas vardır. Blittable olmayan türlerin sabit arabellekleri doğru şekilde marshaled olmaz, bu nedenle yerinde dizi birden çok ayrı alanlara genişletilmesi gerekir. Ayrıca, .NET Framework ve .NET Core'da 3.0'dan önce, sabit arabellek alanı içeren bir yapı, blittable olmayan bir yapıiçinde iç içe geçikarsa, sabit arabellek alanı yerel koda doğru şekilde marshaled olmaz.
