---
title: Sınıflar, Yapılar ve Birleşimleri Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: d761d8ed7488e99f29d4844d061867915a624b96
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960010"
---
# <a name="marshaling-classes-structures-and-unions"></a>Sınıflar, Yapılar ve Birleşimleri Hazırlama

Sınıflar ve yapılar .NET Framework benzerdir. Her ikisinde de alanlar, Özellikler ve olaylar olabilir. Statik ve statik olmayan yöntemlere de sahip olabilirler. Bir önemli farkı, yapıların değer türleri ve sınıfların başvuru türleridir.

Aşağıdaki tablo sınıflar, yapılar ve birleşimler için sıralama seçeneklerini listeler; kullanımlarını açıklar; ve buna karşılık gelen platform çağırma örneğine bir bağlantı sağlar.

|Tür|Açıklama|Örnek|
|----------|-----------------|------------|
|Değere göre sınıf.|Tamsayı üyeleri olan bir sınıfı, yönetilen durum gibi bir ın/out parametresi olarak geçirir.|[SysTime örneği](#systime-sample)|
|Değere göre yapı.|Yapıları parametrelerde olduğu gibi geçirir.|[Yapılar örneği](#structures-sample)|
|Başvuruya göre yapı.|Yapıları ın/out parametreleri olarak geçirir.|[OSINFO örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|
|İç içe yapılar (düzleştirilmiş) ile yapı.|Yönetilmeyen işlevde iç içe yapılar içeren bir yapıyı temsil eden bir sınıf geçirir. Yapı, yönetilen prototipde bir büyük yapıya düzleştirilir.|[FindFile örneği](#findfile-sample)|
|Başka bir yapıya işaretçi içeren yapı.|İkinci bir yapıya bir işaretçi içeren bir yapıyı üye olarak geçirir.|[Yapılar örneği](#structures-sample)|
|Değere göre tamsayılar içeren yapıların dizisi.|Yalnızca tamsayı içeren bir yapı dizisini bir ın/out parametresi olarak geçirir. Dizi üyeleri değiştirilebilir.|[Diziler örneği](marshaling-different-types-of-arrays.md)|
|Başvuruya göre tamsayılar ve dizeler içeren yapıların dizisi.|Out parametresi olarak tamsayılar ve dizeler içeren bir yapı dizisini geçirir. Çağrılan işlev dizi için bellek ayırır.|[Outarrayofyapılar örneği](#outarrayofstructs-sample)|
|Değer türleri olan birleşimler.|Birleşimleri değer türleriyle geçirir (tamsayı ve çift).|[Birleşimler örneği](#unions-sample)|
|Karışık Türler içeren birleşimler.|Birleşimleri karışık türler (tamsayı ve dize) ile geçirir.|[Birleşimler örneği](#unions-sample)|
|Yapıda null değerler.|Değer türüne başvuru yerine bir null başvurusu (Visual Basic**hiçbir şey** ) geçirir.|[HandleRef örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))|

## <a name="structures-sample"></a>Yapılar örneği

Bu örnek, ikinci yapıya işaret eden bir yapının nasıl geçirileceğini, gömülü bir yapıya sahip bir yapının nasıl geçirileceğini ve bir yapının gömülü dizi ile nasıl geçirileceğini gösterir.  
  
Yapılar örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:

- **Teststructsöylemek** , PInvokeLib. dll dosyasından verildi.

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- **TestStructInStruct3** , PInvokeLib. dll dosyasından verildi.

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- **Testarraybildirmek** , PInvokeLib. dll dosyasından verildi.

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlevler ve dört yapı için uygulamalar içeren özel bir yönetilmeyen kitaplıktır: **MyPerson**, **MyPerson2**, **MyPerson3**ve **MyArrayStruct**. Bu yapılar, aşağıdaki öğeleri içerir:

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`ve `MyArrayStruct` yapıları aşağıdaki özelliklere sahiptir:

- `MyPerson` yalnızca dize üyeleri içerir. [Karakter kümesi](specifying-a-character-set.md) alanı yönetilmeyen işleve GEÇIRILDIĞINDE dizeleri ANSI biçimine ayarlar.

- `MyPerson2`, `MyPerson` yapısına bir **IntPtr** içerir. .NET Framework uygulamalar, kod **güvensiz**olarak işaretlenmedikçe işaretçileri kullanmadığı Için, **IntPtr** türü özgün işaretçinin yönetilmeyen yapıya göre yerini alır.

- `MyPerson3`, gömülü bir yapı olarak `MyPerson` içerir. Başka bir yapıda gömülü bir yapı, gömülü yapının öğeleri doğrudan ana yapıya girilerek düzleştirilir veya bu örnekte yapıldığı gibi gömülü bir yapı olarak bırakılabilir.

- `MyArrayStruct` bir tamsayılar dizisi içerir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizideki öğelerin sayısını göstermek için kullanılan <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini **ByValArray**olarak ayarlar.

Bu örnekteki tüm yapılar için, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği uygulanır.

`NativeMethods` sınıfı, `App` sınıfı tarafından çağrılan `TestStructInStruct`, `TestStructInStruct3`ve `TestArrayInStruct` yöntemleri için yönetilen prototürler içerir. Her prototip, aşağıdaki gibi tek bir parametre bildirir:

- `TestStructInStruct`, parametresi olarak `MyPerson2` yazmak için bir başvuru bildirir.

- `TestStructInStruct3`, parametre olarak `MyPerson3` türü bildirir ve parametreyi değere göre geçirir.

- `TestArrayInStruct`, parametresi olarak `MyArrayStruct` yazmak için bir başvuru bildirir.

Parametreler **ref** (Visual Basic içinde**ByRef** ) anahtar sözcüğü içermiyorsa, yöntemlere bağımsız değişken olarak geçirilen yapılar değere göre geçirilir. Örneğin `TestStructInStruct` yöntemi, yönetilmeyen koda `MyPerson2` türünde bir nesneye bir başvuru (bir adres değeri) geçirir. `MyPerson2`, işaret eden yapıyı değiştirmek için, örnek belirtilen boyutun bir arabelleğini oluşturur ve <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemlerini birleştirerek adresini döndürür. Ardından örnek, yönetilen yapının içeriğini yönetilmeyen arabelleğe kopyalar. Son olarak, örnek, yönetilmeyen arabellekteki verileri yönetilen bir nesneye ve yönetilmeyen bellek bloğunu serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yöntemine aktarmak üzere <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> yöntemini kullanır.

### <a name="declaring-prototypes"></a>Prototipleri Bildirme

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a>İşlevleri Çağırma

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a>FindFile örneği

Bu örnek, yönetilmeyen bir işleve ikinci, gömülü bir yapı içeren bir yapının nasıl geçirileceğini gösterir. Ayrıca, yapı içinde sabit uzunluklu bir dizi bildirmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğinin nasıl kullanılacağını gösterir. Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir. Düzleştirilmemiş gömülü bir yapının örneği için bkz. [yapılar örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).

FindFile örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:

- Kernel32. dll dosyasından bir **FindFirstFile** verildi.

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

Bu örnekte, `FindData` sınıfı özgün yapıdaki her öğe için karşılık gelen bir veri üyesini ve katıştırılmış yapıyı içerir. İki orijinal karakter arabelleği yerine, sınıf yerine dizeler koyar. **MarshalAsAttribute** <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmayı, yönetilmeyen yapılar içinde görünen satır içi, sabit uzunluklu karakter dizilerini belirlemek Için kullanılan **ByValTStr**olarak ayarlar.

`NativeMethods` sınıfı, `FindData` sınıfını bir parametre olarak geçiren `FindFirstFile` yönteminin yönetilen bir prototipini içerir. Parametre, başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirildiğinden <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleriyle bildirilmelidir.

### <a name="declaring-prototypes"></a>Prototipleri Bildirme

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a>İşlevleri Çağırma

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a>Birleşimler örneği

Bu örnek, yalnızca değer türlerini içeren yapıların ve bir değer türü içeren yapıların ve bir birleşim bekleyen yönetilmeyen bir işleve parametre olarak dize olarak nasıl geçirileceğini gösterir. Birleşim, iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.

Birleşimler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:

- **TestUnion** , PInvokeLib. dll dosyasından verildi.

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlev için bir uygulama ve **MyUnion** ve **MYUNION2**olmak üzere iki birleşim içeren özel bir yönetilmeyen kitaplıktır. Birleşimler aşağıdaki öğeleri içerir:

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

Yönetilen kodda birleşimler yapılar olarak tanımlanır. `MyUnion` yapısı, üyeleri olarak iki değer türü içerir: tamsayı ve çift. <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği her bir veri üyesinin kesin konumunu denetlemek üzere ayarlanır. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> özniteliği, bir birleşimin yönetilmeyen gösterimi içindeki alanların fiziksel konumunu sağlar. Her iki üyenin de aynı fark değerlerine sahip olduğuna dikkat edin, bu nedenle Üyeler aynı bellek parçasını tanımlayabilirler.

`MyUnion2_1` ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içerir. Yönetilen kodda, değer türleri ve başvuru türlerinin örtüşmesine izin verilmez. Bu örnek, çağıranın aynı yönetilmeyen işlevi çağırırken her iki türü de kullanmasını sağlamak için yöntem aşırı yüklemesini kullanır. `MyUnion2_1` düzeni açıktır ve kesin bir fark değeri içerir. Buna karşılık, `MyUnion2_2` sıralı bir düzene sahiptir, çünkü açık düzenlerine başvuru türleriyle izin verilmez. <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, birleşimin yönetilmeyen gösterimi içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek için kullanılan <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmayı **ByValTStr**olarak ayarlar.

`NativeMethods` sınıfı, `TestUnion` ve `TestUnion2` yöntemlerinin prototiptürlerini içerir. `TestUnion2`, `MyUnion2_1` veya `MyUnion2_2` parametre olarak bildirmek için aşırı yüklendi.

### <a name="declaring-prototypes"></a>Prototipleri Bildirme

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a>İşlevleri Çağırma

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="systime-sample"></a>SysTime örneği

Bu örnek, bir sınıfa işaretçi bekleyen yönetilmeyen bir işleve bir işaretçinin nasıl geçirileceğini gösterir.

SysTime örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:

- Kernel32. dll ' den bir **GetSystemTime** verildi.

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

Bu örnekte, `SystemTime` sınıfı sınıf üyeleri olarak temsil edilen orijinal yapının öğelerini içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği, üyelerin bellekte sıralı şekilde, gözüktükleri sırada düzenlenmesi sağlanacak şekilde ayarlanır.

`NativeMethods` sınıfı, varsayılan olarak `SystemTime` sınıfını bir ın/out parametresi olarak geçiren `GetSystemTime` yönteminin yönetilen bir prototipini içerir. Parametre, başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirildiğinden <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleriyle bildirilmelidir. Çağıranın sonuçları alması için, bu [yönlü özniteliklerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanması gerekir. `App` sınıfı, `SystemTime` sınıfının yeni bir örneğini oluşturur ve veri alanlarına erişir.

### <a name="code-samples"></a>Kod Örnekleri

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs örneği

Bu örnek, yönetilmeyen bir işleve tamsayı ve dizeler içeren bir yapı dizisinin nasıl geçirileceğini gösterir.

Bu örnek, <xref:System.Runtime.InteropServices.Marshal> sınıfını kullanarak ve güvenli olmayan kod kullanarak yerel bir işlevin nasıl çağrılacağını gösterir.

Bu örnek, bir sarmalayıcı işlevleri ve kaynak dosyalarında da sağlanmış olan [PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll)içinde tanımlanan platform çağırır kullanır. `TestOutArrayOfStructs` işlevini ve `MYSTRSTRUCT2` yapısını kullanır. Yapı aşağıdaki öğeleri içerir:

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

`MyStruct` sınıfı, ANSI karakterlerinden oluşan bir dize nesnesi içerir. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alanı ANSI biçimini belirtir. `MyUnsafeStruct`, bir dize yerine <xref:System.IntPtr> türü içeren bir yapıdır.

`NativeMethods` sınıfı, aşırı yüklenmiş `TestOutArrayOfStructs` prototip metodunu içerir. Bir yöntem parametre olarak bir işaretçi bildirirse, sınıf `unsafe` anahtar sözcüğüyle işaretlenmelidir. Visual Basic güvenli olmayan kod kullanamadığından, aşırı yüklenmiş yöntem, güvensiz değiştirici ve `MyUnsafeStruct` yapısı gereksizdir.

`App` sınıfı, diziyi iletmek için gereken tüm görevleri gerçekleştiren `UsingMarshaling` yöntemini uygular. Dizi, verilerin çağrıdan arayana geçerken`ByRef` `out` olduğunu göstermek için Visual Basic) anahtar sözcüğüyle işaretlenir. Uygulama aşağıdaki <xref:System.Runtime.InteropServices.Marshal> sınıf yöntemlerini kullanır:

- yönetilmeyen arabellekteki verileri yönetilen bir nesneye sıralama <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>.

- yapıdaki dizeler için ayrılan belleği serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>.

- dizi için ayrılan belleği serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>.

Daha önce belirtildiği gibi C# , güvenli olmayan koda izin verir ve Visual Basic. C# Örnekte `UsingUnsafePointer`, `MyUnsafeStruct` yapısını içeren diziyi geri geçirmek için <xref:System.Runtime.InteropServices.Marshal> sınıfı yerine işaretçiler kullanan alternatif bir yöntem uygulamasıdır.

### <a name="declaring-prototypes"></a>Prototipleri Bildirme

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a>İşlevleri Çağırma

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a>Ayrıca bkz.

- [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)
- [Dizeleri Hazırlama](marshaling-strings.md)
- [Farklı Dizi Türlerini Hazırlama](marshaling-different-types-of-arrays.md)
