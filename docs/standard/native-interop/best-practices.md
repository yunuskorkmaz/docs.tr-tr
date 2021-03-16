---
title: Yerel birlikte çalışabilirlik en iyi uygulamaları-.NET
description: .NET 'teki yerel bileşenlerle arabirimlendirme için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 7730241ba834d9fcafaaf13055da1a03d359aa1b
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479590"
---
# <a name="native-interoperability-best-practices"></a>Yerel birlikte çalışabilirlik en iyi uygulamaları

.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmek için kullanabileceğiniz çeşitli yollar sunar. Bu makale, Microsoft 'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği yönergeleri içerir.

## <a name="general-guidance"></a>Genel kılavuz

Bu bölümdeki kılavuz tüm birlikte çalışma senaryoları için geçerlidir.

- ✔️, yöntemlerinizi ve parametreleriniz için, çağırmak istediğiniz yerel yöntem olarak aynı adlandırma ve büyük harfleri kullanır.
- ✔️ sabit değerler için aynı adlandırma ve büyük harfleri kullanmayı düşünün.
- ✔️, yerel türe en yakın eşleme olan .NET türlerini kullanır. Örneğin, C# ' de, `uint` Yerel tür olduğunda kullanın `unsigned int` .
- ✔️ yalnızca, `[In]` `[Out]` istediğiniz davranış varsayılan davranıştan farklı olduğunda ve özniteliklerini kullanır.
- ✔️, <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> yerel dizi arabelleklerinizi havuza almak için KULLANMAYı düşünün.
- ✔️, P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfta sarmalamanızı düşünün.
  - Bu, `[DllImport]` özniteliklerinizin `nameof` Yerel kitaplığın adını geçirmek için C# dil özelliğini kullanmasını sağlar ve yerel kitaplığın adını yanlış yazmadığınızdan emin olun.

## <a name="dllimport-attribute-settings"></a>DllImport öznitelik ayarları

| Ayar | Varsayılan | Öneri | Ayrıntılar |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Varsayılanı tut  | Bu açık olarak yanlış olarak ayarlandığında, başarısız HRESULT dönüş değerleri özel durumlara açılır (ve tanımdaki dönüş değeri sonuç olarak null olur).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | API 'ye bağlıdır  | API GetLastError kullanıyorsa bunu true olarak ayarlayın ve değeri almak için Marshal. GetLastWin32Error kullanın. API bir hata olduğunu bildiren bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için başka çağrılar yapmadan önce hatayı alın.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, davranışa geri döner `CharSet.Ansi`  | `CharSet.Unicode` `CharSet.Ansi` Tanımda dizeler veya karakterler varsa, açıkça kullanın | Bu, dizelerin sıralama davranışını ve ne `ExactSpelling` zaman yapılacağını belirtir `false` . Bunun `CharSet.Ansi` aslında UNIX ÜZERINDE UTF8 olduğunu unutmayın. _Çoğu_ zaman Windows Unicode kullanır, ancak UNIX UTF8 kullanır. [Değiştirmeye belgeleri](./charset.md)hakkında daha fazla bilgi için bkz.. |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Bunu true olarak ayarlayın ve çalışma zamanı, ayarın değerine bağlı olarak bir "A" veya "W" sonekiyle `CharSet` (için "a" `CharSet.Ansi` ve "w") farklı işlev adlarını araymaz `CharSet.Unicode` . |

## <a name="string-parameters"></a>Dize parametreleri

Karakter kümesi Unicode olduğunda veya bağımsız değişken açıkça olarak işaretlenmişse `[MarshalAs(UnmanagedType.LPWSTR)]` _ve_ dize değer ile geçirildiğinde (değil `ref` `out` ), dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmaktansa).

`[DllImport]` `Charset.Unicode` DIZELERINIZIN ANSI düzeltmesini açıkça istemediğiniz sürece, işaretini işaretlemeyi unutmayın.

❌`[Out] string`Parametreleri kullanmayın. Değer tarafından özniteliği ile geçirilen dize parametreleri, `[Out]` dize bir dizilmiş dize ise çalışma zamanının kararlılığını bozabilir. İçin belgelerde dize oluşturma hakkında daha fazla bilgi görüntüleyin <xref:System.String.Intern%2A?displayProperty=nameWithType> .

❌`StringBuilder`PARAMETRELERDEN kaçının. `StringBuilder` hazırlama *her zaman* yerel bir arabellek kopyası oluşturur. Bu nedenle, son derece verimsiz olabilir. Bir dize alan bir Windows API 'SI çağırmanın tipik senaryosunu gerçekleştirin:

1. İstenen kapasiteyi (yönetilen kapasiteyi ayırır) bir SB oluşturun **{1}**
2. Çağır
   1. Yerel bir arabellek ayırır **{2}**
   2. `[In]` _(Bir `StringBuilder` parametre için varsayılan)_ içeriğini kopyalar
   3. Yerel arabelleği yeni ayrılmış bir yönetilen diziye `[Out]` **{3}** _(Ayrıca için varsayılan `StringBuilder` )_ kopyalar
3. `ToString()` henüz başka bir yönetilen diziyi ayırır **{4}**

Bu, *{4}* yerel koddan bir dizeyi almak için ayırmaların bir dizesidir. Bunu sınırlamak için en iyi yöntem, başka bir çağrıda öğesini yeniden kullanmak olacaktır `StringBuilder` ancak yalnızca *1* ayırmayı kaydeder. ' Den bir karakter arabelleğini kullanmak ve önbelleğe almak çok daha iyidir `ArrayPool` . daha sonra, sonraki çağrılar için yalnızca ayırmaya erişebilirsiniz `ToString()` .

İle ilgili diğer sorun, `StringBuilder` geri dönüş arabelleğini her zaman ilk null değere kopyasın. Geçilen geri dize sonlandırılmazsa veya çift null ile sonlandırılmış bir dize ise, P/Invoke uygulamanız en iyi şekilde yanlış olur.

*Kullanıyorsanız* `StringBuilder` , bir adet son Gotcha, kapasitenin birlikte çalışma içinde her zaman hesaba katılmış bir gizli null değer **içermemelidir** . Çoğu API 'nin, null değeri *de dahil olmak üzere* arabellek boyutunu istediği için bu, insanların bu yanlış alması yaygındır. Bu, harcanan/gereksiz ayırmalara neden olabilir. Ayrıca, bu Gotcha, çalışma zamanının `StringBuilder` kopyaları en aza indirmek için sıralama iyileştirmesine engel olur.

✔️ içinden ' i kullanmayı düşünün `char[]` `ArrayPool` .

Dize sıralaması hakkında daha fazla bilgi için bkz. [dizeler Için varsayılan sıralama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralamasını özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).

> __Windows 'A özgü__ `[Out]` Clr 'nin `CoTaskMemFree` Varsayılan olarak boş dizeler veya `SysStringFree` olarak işaretlenen dizeler için kullanacağı dizeler `UnmanagedType.BSTR` .
> **Çıkış dizesi arabelleğine sahip çoğu API için:** Geçirilen karakter sayısı null içermelidir. Döndürülen değer geçilen karakter sayısından küçükse, çağrı başarılı olur ve değer sondaki null *olmayan* karakter sayısıdır. Aksi takdirde, sayı null karakter *dahil olmak üzere* arabelleğin gerekli boyutudur.
>
> - 5 ' te geçiş yapın, 4 ' ü alın: dize sonunda null olan 4 karakter uzunluğundadır.
> - 5 ' te geçiş yapın, 6: dize 5 karakter uzunluğundadır, null tutmak için 6 karakterlik bir arabellek gerekir.
> [Dizeler için Windows veri türleri](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boole parametreleri ve alanları

Boole değerleri daha kolay. Varsayılan olarak, .NET, `bool` `BOOL` 4 baytlık bir değer olan bir Windows için sıralanır. Ancak, `_Bool` ve `bool` C ve C++ içindeki türler *tek* bir bayttır. Bu, dönüş değerinin atıldığı ve yalnızca *büyük olasılıkla* sonucu değiştirecek olan hataları takip etmek zor olabilir. .NET `bool` değerlerini C veya C++ türlerine hazırlama hakkında daha fazla bilgi için `bool` , [Boole alanı sıralamasını özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling)hakkındaki belgelere bakın.

## <a name="guids"></a>Yapılamıyor

GUID 'Ler doğrudan imzalarda kullanılabilir. Birçok Windows API 'si, `GUID&` gibi tür diğer adlarını alır `REFIID` . Ref tarafından geçirildiğinde, `ref` ya da `[MarshalAs(UnmanagedType.LPStruct)]` özniteliğiyle geçirilebilir.

| GUID | -Başvuru GUID 'SI |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌`[MarshalAs(UnmanagedType.LPStruct)]`GUID parametrelerinden başka bir şey Için kullanmayın `ref` .

## <a name="blittable-types"></a>Blittable türleri

Blittable türleri, yönetilen ve yerel kodda aynı bit düzeyi gösterimine sahip olan türlerdir. Bu şekilde, yerel koda ve yerel koddan sıralanmaları için başka bir biçime dönüştürülmesi gerekmez ve bu da performansı artırdığı için tercih edilmelidir. Bazı türler blittable değildir ancak blittable içeriğini içerecek şekilde bilinir. Bu türler, blittable türleri gibi benzer iyileştirmelere sahiptir, ancak yapı alanları veya amaçları için blittable olarak değerlendirilmez [`UnmanagedCallersOnlyAttribute`](xref:System.Runtime.InteropServices.UnmanagedCallersOnlyAttribute) .

**Blittable türleri:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip yapılar
  - Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`
  - yapılar `LayoutKind.Sequential` Varsayılan olarak

**Blittable içeriği olan türler:**

- blittable ilkel türlerin iç içe olmayan, tek boyutlu dizileri (örneğin, `int[]` )
- örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip sınıflar
  - Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`
  - sınıflar `LayoutKind.Auto` Varsayılan olarak

**Blittable DEĞIL:**

- `bool`

**Bazen blittable:**

- `char`

**Bazen blittable içeriğe sahip türler:**

- `string`

Blittable türler,, veya ile başvuru ile `in` geçirildiğinde `ref` `out` veya blittable içeriði olan türler değere göre geçirildiğinde, bir ara belleğe kopyalamak yerine yalnızca hazırlayıcısı tarafından sabitlenmiştir.

`char` tek boyutlu bir dizide **veya** ile birlikte açık olarak işaretlenen bir türün parçasıysa blittable `[StructLayout]` `CharSet = CharSet.Unicode` .

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` , başka bir türde yoksa ve ile işaretlenmiş bir bağımsız değişken olarak geçiriliyorsa, blittable içeriğini içerir `[MarshalAs(UnmanagedType.LPWStr)]` `[DllImport]` `CharSet = CharSet.Unicode` .

Bir türün blittable olup olmadığını veya bir sabitlenmiş bir oluşturma girişiminde blittable içeriği içerip içerdiğini görebilirsiniz `GCHandle` . Tür bir dize değilse veya blittable olarak kabul edilir `GCHandle.Alloc` `ArgumentException` .

✔️ yapılarınızı mümkün olduğunca blittable yapın.

Daha fazla bilgi için bkz.

- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../framework/interop/blittable-and-non-blittable-types.md)
- [Tür sıralaması](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Yönetilen nesneleri canlı tutma

`GC.KeepAlive()` bir nesnenin, KeepAlive yöntemi vurana kadar kapsamda kalmasını güvence altına alınır.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) hazırlayıcısı 'in bir P/Invoke süresince bir nesneyi canlı tutmaya izin verir. Yöntemi, yöntem imzaları yerine kullanılabilir `IntPtr` . `SafeHandle` Bu sınıfın yerini etkin bir şekilde değiştirir ve bunun yerine kullanılmalıdır.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) yönetilen bir nesnenin sabitlenmesini ve yerel işaretçisine alınmasını sağlar. Temel model:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Sabitleme için varsayılan değer değildir `GCHandle` . Diğer büyük model, yerel kod aracılığıyla yönetilen bir nesneye başvuru geçirmek ve genellikle bir geri çağırma ile yönetilen koda geri dönmek içindir. Bu, şu şekildedir:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

`GCHandle`Bellek sızıntılarını önlemek için açıkça serbest bırakılmış olması gerektiğini unutmayın.

## <a name="common-windows-data-types"></a>Ortak Windows veri türleri

Aşağıda, Windows API 'Lerinde yaygın olarak kullanılan ve Windows koduna çağrılırken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi verilmiştir.

Aşağıdaki türler, adlarına rağmen 32-bit ve 64-bit Windows üzerinde aynı boyutlardır.

| Width | Windows          | C (Windows)          | C#       | Yapıyı                          |
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

Aşağıdaki türler, işaretçiler olması, platformun genişliğini izler. `IntPtr` / `UIntPtr` Bunlar için kullanın.

| İmzalı Işaretçi türleri (kullanım `IntPtr` ) | İşaretsiz Işaretçi türleri (kullanım `UIntPtr` ) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

`PVOID`C olan bir Windows `void*` ya da olarak sıralanabilir `IntPtr` `UIntPtr` , ancak `void*` mümkün olduğunda tercih edilebilir.

[Windows veri türleri](/windows/desktop/WinProg/windows-data-types)

[Veri türü aralıkları](/cpp/cpp/data-type-ranges)

### <a name="formerly-built-in-supported-types"></a>Önceden oluşturulmuş desteklenen türler

Bir tür için yerleşik desteğin kaldırıldığı nadir örnekler vardır.

[`UnmanagedType.HString`](xref:System.Runtime.InteropServices.UnmanagedType)Yerleşik sıralama desteği .NET 5 sürümünde kaldırılmıştır. Bu sıralama türünü kullanan ve önceki bir çerçeveyi hedefleyen ikili dosyaları yeniden derlemeniz gerekir. Bu tür sıralaması devam edebilir, ancak aşağıdaki kod örneğinde gösterildiği gibi bunu el ile sıralamamalısınız. Bu kod, ileriye dönük ve önceki çerçevelerle de uyumlu olacak şekilde çalışır.

```csharp
static class HSTRING
{
    public static IntPtr FromString(string s)
    {
        Marshal.ThrowExceptionForHR(WindowsCreateString(s, s.Length, out IntPtr h));
        return h;
    }

    public static void Delete(IntPtr s)
    {
        Marshal.ThrowExceptionForHR(WindowsDeleteString(s));
    }

    [DllImport("api-ms-win-core-winrt-string-l1-1-0.dll", CallingConvention = CallingConvention.StdCall, ExactSpelling = true)]
    private static extern int WindowsCreateString(
        [MarshalAs(UnmanagedType.LPWStr)] string sourceString, int length, out IntPtr hstring);

    [DllImport("api-ms-win-core-winrt-string-l1-1-0.dll", CallingConvention = CallingConvention.StdCall, ExactSpelling = true)]
    private static extern int WindowsDeleteString(IntPtr hstring);
}

// Usage example
IntPtr hstring = HSTRING.FromString("HSTRING from .NET to WinRT API");
try
{
    // Pass hstring to WinRT or Win32 API.
}
finally
{
    HSTRING.Delete(hstring);
}
```

## <a name="structs"></a>Yapılar

Yönetilen yapılar yığında oluşturulur ve Yöntem dönene kadar kaldırılmaz. Daha sonra, tanım olarak "sabitlenmiş" olur (GC tarafından taşınmaz). Ayrıca, yerel kod geçerli yöntemin sonundan sonra işaretçiyi kullanmayacaksa, güvenli olmayan kod bloklarıyla adresi de alabilirsiniz.

Blittable yapılar, doğrudan hazırlama katmanı tarafından yalnızca kullanılabilecek şekilde daha fazla performanızdır. Yapıları blittable yapmayı deneyin (örneğin, kullanmaktan kaçının `bool` ). Daha fazla bilgi için [blittable Types](#blittable-types) bölümüne bakın.

Yapı *blittable ise,* `sizeof()` `Marshal.SizeOf<MyStruct>()` daha iyi performans için yerine kullanın. Yukarıda da belirtildiği gibi, sabitlenmiş bir sabitlenmiş oluşturma girişiminde, türün blittable olduğunu doğrulayabilirsiniz `GCHandle` . Tür bir dize değilse veya blittable olarak kabul edilir, `GCHandle.Alloc` bir oluşturur `ArgumentException` .

Tanımlarda yapıların işaretçilerine ya da ile geçirilmesi gerekir `ref` `unsafe` `*` .

✔️, resmi platform belgelerinde veya üstbilgisinde kullanılan şekle ve adlara göre, yönetilen yapı ile mümkün olduğunca yakından eşleşir.

✔️ `sizeof()` `Marshal.SizeOf<MyStruct>()` performansı artırmak için blittable yapıları yerine C# kullanın.

❌`System.Delegate` `System.MulticastDelegate` Yapılardaki işlev işaretçisi alanlarını temsil etmek için veya alanlarını kullanmaktan kaçının.

<xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> Gerekli bir imzaya sahip olmadığından, geçirilen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti etmez. Ayrıca, .NET Framework ve .NET Core ' da, yerel `System.Delegate` `System.MulticastDelegate` temsilindeki alanın değeri yönetilen bir temsilciyi sarmalayan bir işlev işaretçisi değilse, bir veya yerel gösteriminden yönetilen bir nesne içeren bir yapının sıralaması çalışma zamanının kararlılığını bozabilir. .NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alanını yerel gösterimden yönetilen bir nesneye sıralama desteklenmez. Veya yerine belirli bir temsilci türü kullanın `System.Delegate` `System.MulticastDelegate` .

### <a name="fixed-buffers"></a>Sabit arabellekler

Benzer bir dizi `INT_PTR Reserved1[2]` iki alan için sıralanmalıdır `IntPtr` `Reserved1a` ve `Reserved1b` . Yerel dizi basit bir tür olduğunda, `fixed` anahtar sözcüğünü kullanarak biraz daha düzgün bir şekilde yazabilirsiniz. Örneğin, `SYSTEM_PROCESS_INFORMATION` Yerel üst bilgisinde şöyle görünür:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

C# ' de, bunu şöyle yazalım:

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

Ancak, sabit arabelleklerle bazı tuzakları vardır. Blittable olmayan türlerin sabit arabellekleri doğru sıralanmayacak, bu nedenle yerinde dizinin birden çok ayrı alana genişletilmesi gerekir. Ayrıca, .NET Framework ve .NET Core 'da 3,0 öncesinde, sabit bir arabellek alanı içeren bir struct, blittable olmayan bir yapı içinde iç içe geçmişse, sabit arabellek alanı yerel koda doğru şekilde sıralanmayacaktır.
