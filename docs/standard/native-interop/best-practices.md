---
title: Yerel birlikte çalışabilirlik en iyi uygulamaları-.NET
description: .NET 'teki yerel bileşenlerle arabirimlendirme için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 9486256b815856c0c283f5fe231be3d35d6e8f00
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742756"
---
# <a name="native-interoperability-best-practices"></a>Yerel birlikte çalışabilirlik en iyi uygulamaları

.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmek için kullanabileceğiniz çeşitli yollar sunar. Bu makale, Microsoft 'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği yönergeleri içerir.

## <a name="general-guidance"></a>Genel rehber

Bu bölümdeki kılavuz tüm birlikte çalışma senaryoları için geçerlidir.

- ✔️, yöntemlerinizi ve parametreleriniz için, çağırmak istediğiniz yerel yöntem olarak aynı adlandırma ve büyük harfleri kullanır.
- ✔️ sabit değerler için aynı adlandırma ve büyük harfleri kullanmayı düşünün.
- ✔️, yerel türe en yakın eşleme olan .NET türlerini kullanır. Örneğin, ' de C#, yerel tür `unsigned int`olduğunda `uint` kullanın.
- ✔️ yalnızca `[In]` ve `[Out]` özniteliklerini kullanarak istediğiniz davranış varsayılan davranıştan farklıdır.
- ✔️, yerel dizi arabelleklerinizi havuza almak için <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> kullanmayı düşünün.
- ✔️, P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfta sarmalamanızı düşünün.
  - Bu, `[DllImport]` niteliklerinin yerel kitaplığın adını geçirmek C# için `nameof` dil özelliğini kullanmasını sağlar ve yerel kitaplığın adını yanlış yazmadığınızdan emin olun.

## <a name="dllimport-attribute-settings"></a>DllImport öznitelik ayarları

| Ayar | Varsayılan | Öneri | Ayrıntılar |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Varsayılanı tut  | Bu açık olarak yanlış olarak ayarlandığında, başarısız HRESULT dönüş değerleri özel durumlara açılır (ve tanımdaki dönüş değeri sonuç olarak null olur).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | API 'ye bağlıdır  | API GetLastError kullanıyorsa bunu true olarak ayarlayın ve değeri almak için Marshal. GetLastWin32Error kullanın. API bir hata olduğunu bildiren bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için başka çağrılar yapmadan önce hatayı alın.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, `CharSet.Ansi` davranışa geri döner  | Tanımlarda dizeler veya karakterler bulunduğunda `CharSet.Unicode` veya `CharSet.Ansi` açıkça kullanın | Bu, dizelerin sıralama davranışını ve `false`ne `ExactSpelling` ne yaptığını belirler. `CharSet.Ansi` aslında UNIX üzerinde UTF8 olduğunu unutmayın. _Çoğu_ zaman Windows Unicode kullanır, ancak UNIX UTF8 kullanır. [Değiştirmeye belgeleri](./charset.md)hakkında daha fazla bilgi için bkz. |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Bunu true olarak ayarlayın ve küçük bir performans avantajı elde edin. çalışma zamanı, `CharSet` ayarının değerine bağlı olarak bir "A" veya "W" sonekiyle (`CharSet.Unicode`için "bir" `CharSet.Ansi` ve "W") birine göre alternatif işlev adları aramaz. |

## <a name="string-parameters"></a>Dize parametreleri

Karakter kümesi Unicode olduğunda veya bağımsız değişken açıkça `[MarshalAs(UnmanagedType.LPWSTR)]` olarak işaretlenmişse _ve_ dize değer ile geçirildiğinde (`ref` veya `out`), dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmaktansa).

Dizelerinizin ANSI düzeltmesini açıkça istemediğiniz sürece `[DllImport]` `Charset.Unicode` olarak işaretleyeceğini unutmayın.

❌ `[Out] string` parametrelerini kullanmaz. Değer tarafından `[Out]` özniteliği ile geçirilen dize parametreleri, dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. <xref:System.String.Intern%2A?displayProperty=nameWithType>belgelerde dize oluşturma hakkında daha fazla bilgi görüntüleyin.

❌ `StringBuilder` parametrelerden KAÇıNıN. `StringBuilder` sıralaması *her zaman* yerel bir arabellek kopyası oluşturur. Bu nedenle, son derece verimsiz olabilir. Bir dize alan bir Windows API 'SI çağırmanın tipik senaryosunu gerçekleştirin:

1. İstenen kapasiteyi (yönetilen kapasiteyi ayırır) bir SB oluşturun **{1}**
2. Çağır
   1. Yerel bir arabellek ayırır **{2}**
   2. `[In]` _(`StringBuilder` parametresi için varsayılan)_ içeriğini kopyalar
   3. `[Out]` **{3}** _(Ayrıca `StringBuilder`için varsayılan)_ , yerel arabelleği yeni ayrılmış bir yönetilen diziye kopyalar
3. `ToString()`, henüz başka bir yönetilen diziyi ayırır **{4}**

Bu, yerel koddan bir dizeyi almak için ayırmaların *{4}* . Bunu, başka bir çağrıda `StringBuilder` yeniden kullanmak için en iyi yöntem, ancak yalnızca *1* ayırmayı kaydetmeye devam edebilir. `ArrayPool`bir karakter arabelleğini kullanmak ve önbelleğe almak çok daha iyidir. daha sonra, sonraki çağrılarda yalnızca `ToString()` ayırmaya erişebilirsiniz.

`StringBuilder` diğer sorun, her zaman geri dönüş arabelleğini ilk null 'a kopyasın. Geçilen geri dize sonlandırılmazsa veya çift null ile sonlandırılmış bir dize ise, P/Invoke uygulamanız en iyi şekilde yanlış olur.

`StringBuilder`kullanırsanız *,* son Gotcha, kapasitenin birlikte çalışma içinde her zaman hesaba katılmış olan gizli bir **null içermediği anlamına** gelir. Çoğu API 'nin, null değeri *de dahil olmak üzere* arabellek boyutunu istediği için bu, insanların bu yanlış alması yaygındır. Bu, harcanan/gereksiz ayırmalara neden olabilir. Ayrıca, bu Gotcha, çalışma zamanının kopyaları en aza indirmek için `StringBuilder` sıralamasını iyileştirmesine engel olur.

✔️ `ArrayPool``char[]`s kullanmayı göz önünde bulundurun.

Dize sıralaması hakkında daha fazla bilgi için bkz. [dizeler Için varsayılan sıralama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralamasını özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).

> __Windows 'A özgü__ `[Out]` dizeleri için, CLR varsayılan olarak, `UnmanagedType.BSTR`olarak işaretlenen dizeler için `CoTaskMemFree` veya `SysStringFree` boş dizeler için kullanır.
> **Çıkış dizesi arabelleğine sahip çoğu API için:** Geçirilen karakter sayısı null içermelidir. Döndürülen değer geçilen karakter sayısından küçükse, çağrı başarılı olur ve değer sondaki null *olmayan* karakter sayısıdır. Aksi takdirde, sayı null karakter *dahil olmak üzere* arabelleğin gerekli boyutudur.
>
> - 5 ' te geçiş yapın, 4 ' ü alın: dize sonunda null olan 4 karakter uzunluğundadır.
> - 5 ' te geçiş yapın, 6: dize 5 karakter uzunluğundadır, null tutmak için 6 karakterlik bir arabellek gerekir.
> [Dizeler için Windows veri türleri](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boole parametreleri ve alanları

Boole değerleri daha kolay. Varsayılan olarak, bir .NET `bool`, bir Windows `BOOL`sıralanır ve burada 4 baytlık bir değerdir. Ancak, `_Bool`ve `bool` türleri C++ ve *tek* bir bayttır. Bu, dönüş değerinin atıldığı ve yalnızca *büyük olasılıkla* sonucu değiştirecek olan hataları takip etmek zor olabilir. .NET `bool` değerlerini C veya C++ `bool` türlerine hazırlama hakkında daha fazla bilgi için, [Boole alanı sıralamasını özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling)hakkındaki belgelere bakın.

## <a name="guids"></a>Yapılamıyor

GUID 'Ler doğrudan imzalarda kullanılabilir. Birçok Windows API 'si `REFIID`gibi `GUID&` tür diğer adlarını alır. Ref tarafından geçirildiğinde, `ref` ya da `[MarshalAs(UnmanagedType.LPStruct)]` özniteliğiyle geçirilebilir.

| GUID | -Başvuru GUID 'SI |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌ `ref` GUID parametrelerinden başka bir şey için `[MarshalAs(UnmanagedType.LPStruct)]` kullanmayın.

## <a name="blittable-types"></a>Blittable türleri

Blittable türleri, yönetilen ve yerel kodda aynı bit düzeyi gösterimine sahip olan türlerdir. Bu şekilde, yerel koda ve yerel koddan sıralanmaları için başka bir biçime dönüştürülmesi gerekmez ve bu da performansı artırdığı için tercih edilmelidir.

**Blittable türleri:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- blittable türlerin iç içe olmayan tek boyutlu dizileri (örneğin, `int[]`)
- örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzenine sahip yapılar ve sınıflar
  - Sabit düzen `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]` gerektiriyor
  - yapılar varsayılan olarak `LayoutKind.Sequential`, sınıflar `LayoutKind.Auto`

**Blittable DEĞIL:**

- `bool`

**Bazen blittable:**

- `char`, `string`

Blittable türleri başvuru ile geçirildiğinde, bir ara belleğe kopyalamak yerine yalnızca hazırlayıcısı tarafından sabitlenmiştir. (Sınıflar kendiliğinden başvuruya göre geçirilir, yapılar `ref` veya `out`kullanıldığında başvuruya göre geçirilir.)

`char`, tek boyutlu bir dizide **veya** `CharSet = CharSet.Unicode`ile `[StructLayout]` birlikte açıkça işaretlendikleri bir türün parçasıysa vardır.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`, başka bir türde yoksa ve `[MarshalAs(UnmanagedType.LPWStr)]` veya `[DllImport]` `CharSet = CharSet.Unicode` ayarlanmış bir bağımsız değişken olarak geçiriliyorsa.

Sabitlenmiş bir `GCHandle`oluşturmaya çalışan bir türün blittable olup olmadığını görebilirsiniz. Tür bir dize değilse veya blittable olarak kabul edilir `GCHandle.Alloc`, bir `ArgumentException`oluşturur.

✔️ yapılarınızı mümkün olduğunca blittable yapın.

Daha fazla bilgi için bkz.:

- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../framework/interop/blittable-and-non-blittable-types.md)
- [Tür sıralaması](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Yönetilen nesneleri canlı tutma

`GC.KeepAlive()`, KeepAlive yöntemi vurana kadar bir nesnenin kapsamda kalmasını sağlayacaktır.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) , hazırlayıcısı 'In bir P/Invoke süresince bir nesneyi canlı tutmaya izin verir. Yöntem imzalarında `IntPtr` yerine kullanılabilir. `SafeHandle` bu sınıfın yerini etkin bir şekilde değiştirir ve bunun yerine kullanılmalıdır.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) yönetilen bir nesnenin sabitlenmesini ve yerel işaretçinin alınmasını sağlar. Temel model:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Sabitleme, `GCHandle`için varsayılan değer değildir. Diğer büyük model, yerel kod aracılığıyla yönetilen bir nesneye başvuru geçirmek ve genellikle bir geri çağırma ile yönetilen koda geri dönmek içindir. Bu, şu şekildedir:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Bellek sızıntılarını önlemek için `GCHandle` açıkça serbest bırakılmış olması gerektiğini unutmayın.

## <a name="common-windows-data-types"></a>Ortak Windows veri türleri

Windows API 'Lerinde yaygın olarak kullanılan ve Windows koduna çağrı yaparken kullanılacak türleri içeren C# bir veri türleri listesi aşağıda verilmiştir.

Aşağıdaki türler, adlarına rağmen 32-bit ve 64-bit Windows üzerinde aynı boyutlardır.

| Genişlik | Windows          | C (Windows)          | C#       | Yapıyı                          |
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

Aşağıdaki türler, işaretçiler olması, platformun genişliğini izler. Bunlar için `IntPtr`/`UIntPtr` kullanın.

| İmzalı Işaretçi türleri (`IntPtr`kullanın) | İşaretsiz Işaretçi türleri (`UIntPtr`kullanın) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

C `void*` olan bir Windows `PVOID`, `IntPtr` veya `UIntPtr`olarak sıralanabilir, ancak mümkün olduğunda `void*` tercih edebilir.

[Windows veri türleri](/windows/desktop/WinProg/windows-data-types)

[Veri Türü Aralıkları](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Yapılar

Yönetilen yapılar yığında oluşturulur ve Yöntem dönene kadar kaldırılmaz. Daha sonra, tanım olarak "sabitlenmiş" olur (GC tarafından taşınmaz). Ayrıca, yerel kod geçerli yöntemin sonundan sonra işaretçiyi kullanmayacaksa, güvenli olmayan kod bloklarıyla adresi de alabilirsiniz.

Blittable yapılar, doğrudan hazırlama katmanı tarafından yalnızca kullanılabilecek şekilde daha fazla performanızdır. Yapıları blittable yapmayı deneyin (örneğin, `bool`önleyin). Daha fazla bilgi için [blittable Types](#blittable-types) bölümüne bakın.

Yapı *blittable ise,* daha iyi performans için `Marshal.SizeOf<MyStruct>()` yerine `sizeof()` kullanın. Yukarıda belirtildiği gibi, sabitlenmiş bir `GCHandle`oluşturmaya çalışan türün blittable olduğunu doğrulayabilirsiniz. Tür bir dize değilse veya blittable olarak kabul edildiğinde `GCHandle.Alloc` bir `ArgumentException`oluşturur.

Tanımlarda yapıların işaretçilerine `ref` ya da `unsafe` ve `*`kullanılması gerekir.

✔️, resmi platform belgelerinde veya üstbilgisinde kullanılan şekle ve adlara göre, yönetilen yapı ile mümkün olduğunca yakından eşleşir.

✔️, C# performansı artırmak için blittable yapıları `Marshal.SizeOf<MyStruct>()` yerine `sizeof()` kullanın.

`INT_PTR Reserved1[2]` gibi bir dizi iki `IntPtr` alanı `Reserved1a` ve `Reserved1b`olarak sıralanmalıdır. Yerel dizi basit bir tür olduğunda, `fixed` anahtar sözcüğünü kullanarak biraz daha düzgün bir şekilde yazabilirsiniz. Örneğin, `SYSTEM_PROCESS_INFORMATION` yerel üst bilgide şöyle görünür:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

' C#De, bunu şöyle yazalım:

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
