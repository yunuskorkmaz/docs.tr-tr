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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c481b6889c1f10124465a4e851adfb25a1ba2eff
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890299"
---
# <a name="marshaling-classes-structures-and-unions"></a>Sınıflar, Yapılar ve Birleşimleri Hazırlama
.NET Framework sınıfları ve yapıları benzerdir. Hem alanlar, özellikler ve olaylar olabilir. Bunlar, ayrıca statik ve statik olmayan yöntemleri olabilir. Bir önemli fark, yapılar değer türüdür ve sınıflar, başvuru türleridir ' dir.  
  
 Aşağıdaki tabloda, sınıflar, yapılar ve birleşimleri hazırlama seçenekleri listeler. bunların kullanımını açıklar; ve gelen platformun sayfaya bağlantı verilmektedir örnek çağırır.  
  
|Tür|Açıklama|Örnek|  
|----------|-----------------|------------|  
|Değere göre sınıfı.|Tamsayı üyesi olan bir sınıf, yönetilen durumu gibi bir ın/Out parametresi olarak geçirir.|SysTime örneği|  
|Değer yapısı.|Parametreleri olduğu gibi yapıları geçirir.|Yapılar örneği|  
|Başvuruya göre yapısı.|Yapıları In/Out parametresi geçirir.|OSInfo örneği|  
|Yapı ile iç içe geçmiş yapılar (düzleştirilmiş).|Yönetilmeyen işlev içinde iç içe geçmiş yapılar yapısıyla temsil eden bir sınıf geçirir. Yapısı için büyük bir yönetilen prototip yapısında düzleştirilir.|FindFile örneği|  
|Başka bir yapıya bir işaretçi ile yapısı.|Bir üye olarak ikinci bir yapıya bir işaretçi içeren yapısı geçirir.|Yapılar Örneği|  
|Tamsayı değeriyle yapılarıyla dizisi.|Bir dizi yalnızca tamsayı içeren bir ın/Out parametresi olarak yapılarını geçirir. Dizi üyelerinin değiştirilebilir.|Diziler Örneği|  
|Tam sayılar ve dizeler başvuruya göre yapılarıyla dizisi.|Bir dizi tamsayılar ve dizelerin bir Out parametresi içeren yapılarını geçirir. Çağrılan işlev dizi için bellek ayırır.|OutArrayOfStructs Örneği|  
|Birleşimler ile değer türleri.|Değer türleri (Integer ve double) ile birleşimler geçirir.|Birleşimler örneği|  
|Birleşimler karma türlerine sahip.|Birleşimler (tamsayı ve dize) karma türleriyle geçirir.|Birleşimler örneği|  
|Null değerler yapısı.|Null bir başvuru geçirir (**hiçbir şey** Visual Basic'te) yerine bir değer türü referansı.|HandleRef örneği|  
  
## <a name="structures-sample"></a>Yapılar örneği  
 Bu örnek, ikinci bir yapısına işaret eden bir yapı geçirmek, katıştırılmış bir yapıya sahip bir yapı geçirin ve bir gömülü dizi yapısıyla geçirmek nasıl gösterir.  
  
 Yapılar örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestStructInStruct** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   **TestStructInStruct3** Pinvokelib.DLL'den dışarı.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   **TestArrayInStruct** Pinvokelib.DLL'den dışarı.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) uygulamaları için daha önce listelenen işlevlerin ve dört yapıları içeren özel bir yönetilmeyen kitaplıktır: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, ve **MYARRAYSTRUCT**. Bu yapılar aşağıdaki öğeleri içerir:  
  
```  
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
  
 Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`, ve `MyArrayStruct` yapılar aşağıdaki özellik vardır:  
  
-   `MyPerson` yalnızca dize üyeleri içerir. [CharSet](specifying-a-character-set.md) alan yönetilmeyen işleve geçirildiğinde ANSI biçim dizeleri ayarlar.  
  
-   `MyPerson2` içeren bir **IntPtr** için `MyPerson` yapısı. **IntPtr** türü .NET Framework uygulamaları kod işaretlenmediği sürece işaretçileri kullanmadığından yönetilmeyen yapısına orijinal işaretçiyle değiştirir **güvenli**.  
  
-   `MyPerson3` içeren `MyPerson` katıştırılmış bir yapı olarak. Başka bir yapı içinde katıştırılmış bir yapı ana yapısına doğrudan katıştırılmış yapısı öğelerini yerleştirerek düzleştirilebilir veya katıştırılmış bir yapısı olarak, bu örnekte olduğu gibi bırakılabilir.  
  
-   `MyArrayStruct` tamsayı dizisi içerir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümeleri <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini **ByValArray**, dizideki öğelerin sayısını belirtmek için kullanılır.  
  
 Bu örnekte, tüm yapıları için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri uygulanır.  
  
 `LibWrap` Sınıfı için yönetilen prototipleri içeren `TestStructInStruct`, `TestStructInStruct3`, ve `TestArrayInStruct` çağıran yöntemleri `App` sınıfı. Her bir prototip gibi tek bir parametre bildirir:  
  
-   `TestStructInStruct` bir başvuru türüne bildirir `MyPerson2` parametre olarak.  
  
-   `TestStructInStruct3` tür bildirir `MyPerson3` parametre olarak ve parametre değeri geçirir.  
  
-   `TestArrayInStruct` bir başvuru türüne bildirir `MyArrayStruct` parametre olarak.  
  
 Parametre içermedikçe yöntemlerinin bağımsız değişkenleri değere göre geçirilir gibi yapıları **ref** (**ByRef** Visual Basic'te) anahtar sözcüğü. Örneğin, `TestStructInStruct` yöntemi (bir adresi değeri) başvuru türünde bir nesne geçirir `MyPerson2` yönetilmeyen kod için. Yapıyı işlemek için `MyPerson2` noktaları için örnek bir arabellek belirli bir boyuttaki oluşturur ve birleştirerek adresini döndürür <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemleri. Ardından, örnek içerik yönetilen yapısı yönetilmeyen arabelleğe kopyalar. Son olarak, örnek kullanır <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> sıralama verilerini bir yönteme bir yönetilen nesneye yönetilmeyen arabellekteki ve <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yönetilmeyen bellek bloğunu serbest bırakmak için yöntemi.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile örneği  
 Bu örnek yönetilmeyen bir işleve ikinci, katıştırılmış bir yapı içeren bir yapının nasıl geçirileceğini gösterir. Ayrıca nasıl kullanılacağını gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> yapısı içinde bir sabit uzunluklu diziyi bildirmek için özniteliği. Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir. Değil düzleştirilmiş katıştırılmış bir yapının bir örnek için bkz [yapılar örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).  
  
 FindFile örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **FindFirstFile** Kernel32.dll öğesinden dışa aktarılır.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:  
  
```  
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
  
 Bu örnekte `FindData` orijinal yapı ve katıştırılmış yapısı her öğesi için karşılık gelen bir veri üyesi sınıfı içerir. İki orijinal karakter arabelleği yerine sınıfı, dizeleri yerini alır. **MarshalAsAttribute** ayarlar <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesine **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunluklu karakteri diziler yönetilmeyen yapıları içinde görünür.  
  
 `LibWrap` Sınıfı içeren yönetilen bir prototipi `FindFirstFile` geçirir yöntemi `FindData` bir parametre olarak sınıf. Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreler geçirildiğinden öznitelikleri.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>Birleşimler örneği  
 Bu örnek yalnızca değer türleri içeren yapılara ve bir birleşim bekleniyor yönetilmeyen bir işlev için parametre olarak bir değer türü ve bir dize içeren yapıları nasıl gösterir. UNION iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.  
  
 Birleşimler örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **TestUnion** Pinvokelib.DLL'den dışarı.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) daha önce listelenen işlev ve iki birleşimler için bir uygulama içeren özel bir yönetilmeyen kitaplıktır **MYUNION** ve **MYUNION2**. Birleşimler aşağıdaki öğeleri içerir:  
  
```  
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
  
 Yönetilen kodda birleşimler yapı olarak tanımlanır. `MyUnion` Yapı üyeleri olarak iki değer türleri içeriyor: tamsayı ve bir çift. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, her veri üyesi kesin konumunu denetlemek için ayarlanır. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Özniteliği, yönetilmeyen temsili bir birleşim alanlarını fiziksel konumunu sağlar. Üyeleri aynı parça bellek bu sayede her iki üye aynı uzaklık değerleri sahip olduğunuzdan emin olun.  
  
 `MyUnion2_1` ve `MyUnion2_2` bir değer türü (tamsayı) ve bir dize içerir. Yönetilen kodda değer türleri ve başvuru türleri çakıştırmayı izin verilmez. Bu örnek iki türü de aynı yönetilmeyen işlev çağrılırken kullanılacak çağıran etkinleştirmek için aşırı yükleme yöntemini kullanır. Düzenini `MyUnion2_1` açık olduğunu ve kesin bir uzaklık değeri. Buna karşılık, `MyUnion2_2` açık düzenleri başvuru türleri için verilmeyen bir ardışık düzen sahip. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümeleri <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesine **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunluklu karakteri diziler yönetilmeyen gösterimini Birliği içinde görünür.  
  
 `LibWrap` Sınıfı içeren yönelik prototipleri `TestUnion` ve `TestUnion2` yöntemleri. `TestUnion2` bildirmek için aşırı yüklenmiş `MyUnion2_1` veya `MyUnion2_2` parametre olarak.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime örneği  
 Bu örnek, bir sınıf bir yapıya bir işaretçi bekliyor yönetilmeyen bir işleve işaretçi nasıl gösterir.  
  
 SysTime örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **GetSystemTime** Kernel32.dll öğesinden dışa aktarılır.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:  
  
```  
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
  
 Bu örnekte `SystemTime` sınıfı özgün yapısının sınıfı üyeleri olarak temsil edilen öğeleri içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri ayarlanır.  
  
 `LibWrap` Sınıfı içeren yönetilen bir prototipi `GetSystemTime` geçirir yöntemi `SystemTime` sınıfı olarak bir ın/Out parametresinin varsayılan olarak. Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreler geçirildiğinden öznitelikleri. Sonuçları almak çağırıcı için bunlar [yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanmalıdır. `App` Sınıfının yeni bir örneğini oluşturur `SystemTime` sınıfı ve veri alanlarını erişir.  
  
### <a name="code-samples"></a>Kod Örnekleri  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs örneği  
 Bu örnek, tamsayı ve dış parametrelerin yönetilmeyen bir işlev için dize olarak içeren bir dizi yapıların nasıl gösterir.  
  
 Bu örnek kullanarak yerel bir işlev çağırmayı göstermektedir <xref:System.Runtime.InteropServices.Marshal> sınıfı ve güvenli olmayan kod kullanarak.  
  
 Bu örnek bir sarmalayıcı işlevleri kullanır ve platform çağırır tanımlanan [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), da sağlanan kaynak dosyalarında. Kullandığı `TestOutArrayOfStructs` işlevi ve `MYSTRSTRUCT2` yapısı. Yapı aşağıdaki öğeleri içerir:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Sınıfı içeren bir dize nesnesi ANSI karakter. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Alanı ANSI biçimini belirtir. `MyUnsafeStruct`, bir yapı olduğunu içeren bir <xref:System.IntPtr> türü bir dize yerine.  
  
 `LibWrap` Sınıfı içeren Aşırı yüklenen `TestOutArrayOfStructs` prototip yöntemi. İle bir yöntem parametresi olarak bir işaretçiyi bildirir, sınıf işaretlenmelidir `unsafe` anahtar sözcüğü. Çünkü [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] güvenli olmayan kod, aşırı yüklenmiş yöntemin güvenli olmayan değiştirici kullanamazsınız ve `MyUnsafeStruct` yapısı gereksizdir.  
  
 `App` Sınıfının Implements `UsingMarshaling` dizi geçirmek için gerekli tüm görevleri gerçekleştiren yöntemi. Dizi ile işaretlenmiş `out` (`ByRef` Visual Basic'te) verileri göstermek için anahtar sözcüğü, çağırana çağrılan geçirir. Aşağıdaki uygulama kullanan <xref:System.Runtime.InteropServices.Marshal> sınıfı yöntemleri:  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> yönetilen bir nesnenin yönetilmeyen buffer'dan alınan verileri hazırlamak için.  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> yapısında dizeler için ayrılan belleği serbest bırakmak için.  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> dizi için ayrılmış belleği serbest bırakmak için.  
  
 Daha önce belirtildiği gibi C# güvenli olmayan koda izin verir ve [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] desteklemez. İçinde C# örneği `UsingUnsafePointer` işaretçileri yerine kullanan alternatif bir yöntem uygulamasıdır <xref:System.Runtime.InteropServices.Marshal> geçirmek için sınıfı yeniden diziyi içeren `MyUnsafeStruct` yapısı.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Platform Çağırma ile Veri Sıralama](marshaling-data-with-platform-invoke.md)
- [Dizeleri Hazırlama](marshaling-strings.md)
- [Farklı Dizi Türlerini Hazırlama](marshaling-different-types-of-arrays.md)
