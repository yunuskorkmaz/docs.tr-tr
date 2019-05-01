---
title: Yerel birlikte çalışabilirliği en iyi uygulamalar - .NET
description: . NET'te yerel bileşenleriyle arabirim için en iyi uygulamaları öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 6702d469abf317b3b1f545ce79b980e8581ab5f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973608"
---
# <a name="native-interoperability-best-practices"></a>Yerel birlikte çalışabilirliği en iyi uygulamalar

.NET yerel birlikte çalışabilirliği kodunuzu özelleştirmek için yol çeşitli sağlar. Bu makalede, Microsoft'un .NET ekipleri için yerel birlikte çalışabilirliği izleyin kılavuz içerir.

## <a name="general-guidance"></a>Genel rehber

Birlikte çalışma tüm senaryolarda bu bölümdeki yönergeler geçerlidir.

- **✔️ YAPMAK** yöntem ve parametreler için çağırmak istediğiniz yerel yöntemi olarak aynı adlandırma ve büyük/küçük harf kullanın.
- **✔️ DÜŞÜNÜN** aynı adlandırma ve büyük/küçük harf sabit değerleri için kullanma.
- **✔️ YAPMAK** yakın eşleme için yerel türü .NET türlerini kullanın. Örneğin, C#, kullanın `uint` yerel bir tür olduğunda `unsigned int`.
- **✔️ YAPMAK** yalnızca `[In]` ve `[Out]` istediğiniz davranışı varsayılan davranışı farklılık gösterdiğinde öznitelikleri.
- **✔️ DÜŞÜNÜN** kullanarak <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> , yerel bir dizi arabellek havuzu için.
- **✔️ DÜŞÜNÜN** , P/Invoke bildirimleri ile aynı ada ve büyük/küçük harf, yerel kitaplık olarak sınıfında kaydırma.
  - Böylece, `[DllImport]` öznitelikler C# `nameof` yerel kitaplık adını geçirin ve yerel kitaplık adını yazsanız yaramadı emin olmak için dil özelliğidir.

## <a name="dllimport-attribute-settings"></a>DllImport özniteliği ayarları

| Ayar | Varsayılan | Öneri | Ayrıntılar |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Varsayılan koruyun  | Bu açıkça false, başarısız HRESULT dönüş değerine ayarlandığında, özel durumları kapatılacak (ve sonuç olarak tanımındaki dönüş değeri null olur).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | API'ye bağlıdır  | Bunu Marshal.GetLastWin32Error değerini almak için kullanın ve API GetLastError kullanıyorsa true olarak ayarlayın. API hata var olmadığını belirten bir koşul ayarlar, yanlışlıkla üzerine zorunda kalmamak için diğer aramaları yapmadan önce hata alırsınız.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, hangi gördükleri `CharSet.Ansi` davranışı  | Açıkça kullanın `CharSet.Unicode` veya `CharSet.Ansi` dize ve karakter olduğunda tanımında mevcut | Bu dizeler ve hangi sıralama davranışını belirtir `ExactSpelling` ne zaman mu `false`. Unutmayın `CharSet.Ansi` gerçekten UNIX üzerinde UTF8'dir. _Çoğu_ UNIX UTF8 kullanırken saati Unicode Windows kullanır. Daha fazla bilgi görmek [charsets belgelerine](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Doğru ve çalışma zamanı değerine bağlı olarak bir "A" veya "W" soneki ile alternatif işlev adlarını aramaz gibi küçük bir performans kazancı elde etmek için bunu ayarlayın `CharSet` ayarı ("A" `CharSet.Ansi` ve "W" `CharSet.Unicode`). |

## <a name="string-parameters"></a>Dizesi parametreleri

Ne zaman karakter Unicode veya bağımsız değişken olarak açıkça işaretlenmiş `[MarshalAs(UnmanagedType.LPWSTR)]` _ve_ dizeyi değere göre geçirilir (değil `ref` veya `out`), dize sabitlenebilir ve doğrudan yerel kod tarafından kullanılan (yerine kopyalandı).

İşaretlenecek unutmayın `[DllImport]` olarak `Charset.Unicode` , dizeleri ANSI işleme açıkça istemediğiniz sürece.

**❌ SAĞLAMADIĞI** kullanın `[Out] string` parametreleri. Dize değeri ile tarafından geçirilen parametreler `[Out]` dize interned bir dize ise, öznitelik çalışma zamanı kararlılığını. Belgelerindeki dize kopyası kullanımı hakkında daha fazla bilgi <xref:System.String.Intern%2A?displayProperty=nameWithType>.

**❌ KAÇININ** `StringBuilder` parametreleri. `StringBuilder` taşıma *her zaman* yerel arabellek kopyasını oluşturur. Bu nedenle, son derece verimsiz olabilir. Bir dize alır bir Windows API'si çağırma tipik bir senaryo uygulayın:

1. Bir SB (yönetilen kapasite ayırır) istenen kapasite oluşturma **{1}**
2. Çağır
   1. Yerel bir arabelleği ayırır **{2}**  
   2. İçeriği kopyalar `[In]` _(için varsayılan bir `StringBuilder` parametresi)_  
   3. Yerel arabellek yönetilen yeni ayrılan bir diziye kopyalar `[Out]` **{3}** _(aynı zamanda varsayılan `StringBuilder`)_  
3. `ToString()` henüz başka yönetilen diziye ayırır **{4}**

Diğer bir deyişle *{4}* yerel kodunun dışında bir dizesini almak için ayırma. Yeniden kullanmak için bunu sınırlandırmak için yapabileceğiniz en iyi olduğu `StringBuilder` başka bir çağrı ancak yine de yalnızca kazandırır *1* ayırma. Karakter arabellek önbellek ve kullanmak çok daha iyi `ArrayPool`-ardından ayırma için ulaşmak için `ToString()` arka arkaya çağrı.

Diğer sorun `StringBuilder` olduğundan, her zaman ilk null kadar geri dönüş arabelleğine kopyalar. Geçirilen geri dizeyi sonlandırılmış değil veya çift null ile sonlandırılmış bir dize ise, P/Invoke en iyi şekilde doğru değil.

Varsa, *yapmak* kullanın `StringBuilder`, bir son sorunu olan kapasite uğramadığını **değil** her zaman için birlikte çalışabilirlik alındığından bir gizli null içerir. Arabellek boyutu çoğu API'ler istediğiniz gibi yanlış bu kişiler için ortak olan *dahil olmak üzere* null. Bu boşa/gereksiz ayırmaları sonuçlanabilir. Ayrıca, bu sorunu en iyi duruma getirmesini çalışma zamanı engeller `StringBuilder` kopyaları en aza indirmek için hazırlama.

**✔️ DÜŞÜNÜN** kullanarak `char[]`s bir `ArrayPool`.

Dize taşıma hakkında daha fazla bilgi için bkz: [dizeler için varsayılan taşıma](../../framework/interop/default-marshaling-for-strings.md) ve [dize taşıma özelleştirme](customize-parameter-marshalling.md#customizing-string-parameters).

> __Windows özel__  
> İçin `[Out]` CLR dizeleri kullanacağı `CoTaskMemFree` boş dizeler için varsayılan veya `SysStringFree` olarak işaretlenmiş dizeler `UnmanagedType.BSTR`.  
**Bir çıkış dizesi arabelleği ile çoğu API'ler için:**  
> Geçirilen null karakter sayısı içermesi gerekir. Döndürülen değer geçirilen küçükse karakter sayısına çağrısı başarılı oldu ve karakter sayısını değerdir *olmadan* sondaki null. Aksi takdirde sayısı gerekli arabellek boyutu: *dahil olmak üzere* null karakteri.  
> - 5'te geçmek için 4 alın: 4 dizedir ile uzun sondaki null karakter.
> - 5'te geçmek için 6 alın: Bir dizedir 5 karakter uzunluğunda olmalı, boş tutmak için 6 karakter arabelleği gerekir.  
> [Windows veri türleri için dizeleri](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boole parametreler ve alanlar

Boole değerlerini uğraşmanız kolaydır. Varsayılan olarak, bir .NET `bool` için bir Windows sıraya `BOOL`, bir 4 baytlık değer olduğu. Ancak, `_Bool`, ve `bool` türleri C ve C++'ta bir *tek* bayt. Bu sabit yarı dönüş değeri, hangi yalnızca atılacak olarak hataları izlemek için açabilir *potansiyel olarak* sonucu değiştirin. .NET taşıma hakkında bilgi için daha fazla bilgi için `bool` C veya C++ değerlere `bool` türleri, şirket belgelerine bakın [Boole alanı taşıma özelleştirme](customize-struct-marshalling.md#customizing-boolean-field-marshalling).

## <a name="guids"></a>GUID'ler

GUID'ler, dosyalardaki imzaları doğrudan kullanılabilir. Birçok Windows apı'lerinizle `GUID&` tür diğer adları gibi `REFIID`. Başvuru tarafından geçirilen, bunlar ya da geçirilebilir `ref` veya `[MarshalAs(UnmanagedType.LPStruct)]` özniteliği.

| GUID | Başvuru tarafından GUID |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**❌ SAĞLAMADIĞI** kullanım `[MarshalAs(UnmanagedType.LPStruct)]` dışındaki her şey için `ref` GUID parametreleri.

## <a name="blittable-types"></a>Blok halinde kopyalanabilir türler

Blittable türleri aynı bit düzeyinde gösterimine sahip yönetilen ve yerel kodda türleridir. Bu nedenle bunlar için ve yerel koddan sıraya için başka bir biçime dönüştürülüp gerekmez ve bu performansı artırmak amacıyla, tercih edilen olmalıdır.

**Blittable türleri:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- iç içe olmayan tek boyutlu diziler blittable türleri (örneğin, `int[]`)
- yapıları ve sınıfları sabit düzen ile yalnızca blittable değere sahip türleri örneği için alanları
  - Sabit Düzen gerektirir `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`
  - Yapı birimleridir `LayoutKind.Sequential` varsayılan olarak, sınıflardır. `LayoutKind.Auto`

**Blittable değil:**

- `bool`

**BAZEN blittable:**

- `char`, `string`

Blittable türleri başvuruya göre geçirildiğinde, bunlar yalnızca bir ara arabelleğe kopyalanan yerine marshaller tarafından sabitlenmiş. (Sınıflar kendiliğinden başvuruya göre geçirilen, yapılar ile kullanıldığında başvuruyla geçirilir `ref` veya `out`.)

`char` Blittable bir tek boyutlu dizisi olan **veya** parçası ise onu içeren bir türe açıkça ile işaretlenmiş `[StructLayout]` ile `CharSet = CharSet.Unicode`.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` Blittable başka bir tür içinde yer alan değildir ve bu ile işaretlenmiş bir bağımsız değişken olarak Geçirilmekte olan `[MarshalAs(UnmanagedType.LPWStr)]` veya `[DllImport]` sahip `CharSet = CharSet.Unicode` ayarlayın.

Sabitlenmiş oluşturulmaya çalışılırken tarafından bir türü blok halinde kopyalanabilir olup olmadığını görebilirsiniz `GCHandle`. Türü bir dize değilse veya kabul blittable, `GCHandle.Alloc` oluşturmaz bir `ArgumentException`.

**✔️ YAPMAK** mümkün olduğunda, yapıları blittable olun.

Daha fazla bilgi için bkz.:

- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../framework/interop/blittable-and-non-blittable-types.md)  
- [Türü taşıma](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a>Canlı tutma yönetilen nesneler

`GC.KeepAlive()` KeepAlive yöntemi isabet kadar nesne kapsam içinde kalır sağlayacaktır.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) bir nesne bir P/Invoke süresi boyunca Canlı tutmak marshaller sağlar. Yerine kullanılabilir `IntPtr` yöntem imzaları içinde. `SafeHandle` etkili bir şekilde bu sınıfı değiştirir ve bunun yerine kullanılmalıdır.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) yönetilen bir nesnenin sabitleme ve yerel işaretçi kendisine alma sağlar. Temel modelidir:  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

İçin varsayılan olmayan sabitleme `GCHandle`. Diğer önemli bir başvuru yerel kod aracılığıyla yönetilen bir nesne ve genellikle bir geri çağırma ile yönetilen kod için geri geçirmek için modelidir. Bu düzen aşağıdaki gibidir:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Gerektiğini unutmayın `GCHandle` bellek sızıntılarını önlemek için açıkça boşaltılması gerekiyor.

## <a name="common-windows-data-types"></a>Ortak Windows veri türleri

İşte sık kullanılan Windows API'leri ve hangi veri türlerinin bir listesi C# Windows koda çağrılırken kullanılacak türleri.

Aynı boyutta adlarını rağmen 32-bit ve 64-bit Windows üzerinde türleridir.

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

İşaretçisi olan aşağıdaki türleri, platform genişliğini izleyin. Kullanım `IntPtr` / `UIntPtr` bu.

| İşaretçi türleri imzalı (kullanın `IntPtr`) | İşaretsiz işaretçi türleri (kullanın `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Bir Windows `PVOID` C olduğu `void*` olarak sıralanabilir `IntPtr` veya `UIntPtr`, ancak tercih `void*` mümkün olduğunda.

[Windows veri türleri](/windows/desktop/WinProg/windows-data-types)

[Veri Türü Aralıkları](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Yapılar

Yönetilen yapıları yığında oluşturulur ve yöntem dönene kadar kaldırılmaz. Ardından tanımı gereği, bunlar "Sabitlenen" (atık toplama tarafından taşınması gerekmez). Yerel kod geçerli yönteminin sonuna işaretçiyi kullanmaz, blok içinde güvenli olmayan kod adresi kısaca alabilir.

Blok halinde kopyalanabilir, yalnızca doğrudan düzenleme katmanı tarafından kullanılabilmesi için çok daha yüksek performanslı birimleridir. Yapılar blittable yapmayı denerseniz (örneğin, kaçının `bool`). Daha fazla bilgi için [türlerse](#blittable-types) bölümü.

*Varsa* blittable struct, kullanın `sizeof()` yerine `Marshal.SizeOf<MyStruct>()` daha iyi performans için. Yukarıda belirtildiği gibi bir sabitlenmiş oluşturulmaya çalışılırken tarafından türü blittable olduğunu doğrulayabilirsiniz `GCHandle`. Türü bir dize değilse veya kabul blittable, `GCHandle.Alloc` oluşturmaz bir `ArgumentException`.

Yapılar tanımlarında işaretçileri ya da geçirilmelidir `ref` veya `unsafe` ve `*`.

**✔️ YAPMAK** yönetilen yapı şekil ve resmi platformu belgeleri veya üstbilgi kullanılan adları için mümkün olduğunca aynı.

**✔️ YAPMAK** kullanın C# `sizeof()` yerine `Marshal.SizeOf<MyStruct>()` performansını artırmak blittable yapıları için.

Bir dizi ister `INT_PTR Reserved1[2]` iki olarak sıralanması gereken `IntPtr` alanları `Reserved1a` ve `Reserved1b`. Yerel bir dizi temel bir tür olduğunda, kullanabiliriz `fixed` biraz daha temiz bir şekilde yazmak için anahtar sözcüğü. Örneğin, `SYSTEM_PROCESS_INFORMATION` şöyle görünür yerel başlığı:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

İçinde C#, şöyle yazabiliriz:

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

Ancak, bazı tuzakları sabit arabellekler ile vardır. Yerinde dizi kullanıma birden çok ayrı ayrı alanlara genişletilmesi gerekir kopyalanamaz türler, sabit arabellekleri doğru sıraya gerekmez. Bir sabit arabellek alanı içeren bir yapı kopyalanamaz yapı birimi içinde iç içe ek olarak, .NET Framework ve .NET Core 3.0 önce sabit arabellek alanı doğru yerel kod için sıraya gerekmez.
