---
title: "Sınıflar, Yapılar ve Birleşimleri Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dcfa2e60a9659db6d38e0561785ece5726989ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-classes-structures-and-unions"></a>Sınıflar, Yapılar ve Birleşimleri Hazırlama
.NET Framework sınıfları ve yapıları benzerdir. Her ikisi de alanları, özellikleri ve olayları olabilir. Ayrıca statik ve statik olmayan yöntemleri sahip olabilir. Bir dikkat çekici fark yapıları değer türleri ve başvuru türleri sınıflardır olduğundan ' dir.  
  
 Aşağıdaki tabloda, sınıflar, yapılar ve birleşimleri hazırlama seçeneklerini listeler. bunların kullanım açıklar; ve karşılık gelen platform için bir bağlantı sağlar örnek çağırma.  
  
|Tür|Açıklama|Örnek|  
|----------|-----------------|------------|  
|Sınıfı tarafından değeri.|Yönetilen servis talebi gibi bir giriş/çıkış parametresi olarak bir sınıf tamsayı üyeleriyle geçirir.|SysTime örneği|  
|Değere göre yapısı.|Yapıları parametreleri olduğu gibi geçirir.|Yapıları örnek|  
|Başvuruya göre yapısı.|Yapıları olarak In/Out parametreleri geçirir.|OSInfo örneği|  
|İç içe geçmiş yapılar (düzleştirilmiş) yapısıyla.|Yönetilmeyen işlevinde iç içe geçmiş yapılar yapısıyla temsil eden bir sınıf geçirir. Yönetilen prototip bir büyük yapısına yapısı düzleştirilmiş.|FindFile örneği|  
|Başka bir yapısına yönelik işaretçinin yapısıyla.|Bir üye olarak ikinci bir yapı için bir işaretçi içeren bir yapısı geçirir.|Yapılar Örneği|  
|Değere göre tamsayılı yapıları dizisi.|Bir giriş/çıkış parametresi olarak yalnızca tamsayı içeren yapılarını dizisi geçirir. Dizi üyelerinin değiştirilebilir.|Diziler Örneği|  
|Yapıları tamsayılar ve başvuruya göre dizeler dizisi.|Tamsayıları ve dizeleri bir çıkış parametresi olarak içeren yapılarını dizisi geçirir. Çağrılan işlev dizi için bellek ayırır.|OutArrayOfStructs Örneği|  
|Değer türleri ile birleşimler.|Değer türleri (tamsayı ve çift) ile birleşimler geçirir.|Birleşimler örneği|  
|Birleşimler karma türleriyle.|Birleşimler (tamsayı ve dize) karma türleriyle geçirir.|Birleşimler örneği|  
|Null değerler yapısındaki.|Bir null başvuru geçirir (**hiçbir şey** Visual Basic'te) yerine bir değer türü referansı.|HandleRef örneği|  
  
## <a name="structures-sample"></a>Yapıları örnek  
 Bu örnek, ikinci bir yapıya işaret eden bir yapı geçirmek için bir katıştırılmış yapısı yapısıyla geçip katıştırılmış bir dizi yapısıyla geçirmek gösterilmiştir.  
  
 Yapılar örnek kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestStructInStruct** PinvokeLib.dll dışarı.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   **TestStructInStruct3** PinvokeLib.dll dışarı.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   **TestArrayInStruct** PinvokeLib.dll dışarı.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) uygulamalar için daha önce listelenen işlevleri ve dört yapıları içeren özel bir yönetilmeyen kitaplığıdır: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, ve **MYARRAYSTRUCT**. Bu yapıları aşağıdaki öğeleri içerir:  
  
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
  
 Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`, ve `MyArrayStruct` yapılarına aşağıdaki özelliğe sahiptir:  
  
-   `MyPerson`yalnızca dize üyeler içerir. [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) alan yönetilmeyen işleve geçirildiğinde ANSI biçimine dizeleri ayarlar.  
  
-   `MyPerson2`içeren bir **IntPtr** için `MyPerson` yapısı. **IntPtr** türü değiştirir özgün işaretçiyi yönetilmeyen yapısı için .NET Framework uygulamaları kodu işaretlenmemişse işaretçileri kullanmadığından **güvensiz**.  
  
-   `MyPerson3`içeren `MyPerson` katıştırılmış yapısı olarak. Başka bir yapı içinde katıştırılmış bir yapı doğrudan ana yapısına katıştırılmış yapısı öğelerini koyarak düzleştirilmiş veya katıştırılmış bir yapısı olarak, bu örnekte gibi bırakılabilir.  
  
-   `MyArrayStruct`dizisi içerir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümelerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri **ByValArray**, dizideki öğelerin sayısını belirtmek için kullanılır.  
  
 Bu örnekteki tüm yapıları için <xref:System.Runtime.InteropServices.StructLayoutAttribute> öznitelik üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olmak için uygulanır.  
  
 `LibWrap` Sınıfı için yönetilen prototipleri içerir `TestStructInStruct`, `TestStructInStruct3`, ve `TestArrayInStruct` yöntemleri tarafından çağrılır `App` sınıfı. Her prototip gibi tek bir parametre bildirir:  
  
-   `TestStructInStruct`türü için bir başvuru bildirir `MyPerson2` , parametre olarak.  
  
-   `TestStructInStruct3`tür bildirir `MyPerson3` , parametre olarak ve parametre değerine göre geçirir.  
  
-   `TestArrayInStruct`türü için bir başvuru bildirir `MyArrayStruct` , parametre olarak.  
  
 Yapıları parametresi içermedikçe yöntemleri bağımsız değişkenleri değere göre geçirilen **ref** (**ByRef** Visual Basic'te) anahtar sözcüğü. Örneğin, `TestStructInStruct` yöntemi geçirir türünde bir nesneye başvuru (bir adresi değeri) `MyPerson2` yönetilmeyen kod için. Yapısını işlemek için `MyPerson2` noktaları için örnek belirtilen boyutta bir arabellek oluşturur ve birleştirerek adresini döndürür <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemleri. Ardından, örnek yönetilmeyen arabellek yönetilen yapısı içeriği kopyalar. Son olarak, örnek kullanır <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> yönetilen bir nesne için yönetilmeyen arabellek sıralama verilere yönteminden ve <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yöntemi yönetilmeyen bellek bloğu boş.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile örneği  
 Bu örnek, yönetilmeyen bir işleve ikinci, katıştırılmış bir yapı içeren bir yapısı geçirmek gösterilmiştir. Ayrıca nasıl kullanılacağı ortaya <xref:System.Runtime.InteropServices.MarshalAsAttribute> yapısı içinde bir sabit uzunluk dizisi bildirmek için öznitelik. Bu örnekte, katıştırılmış yapı öğeleri üst yapısına eklenir. Katıştırılmış yapısının değil düzleştirilmiş bir örnek için bkz: [yapıları örnek](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).  
  
 FindFile örnek özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **FindFirstFile** Kernel32.dll dışarı.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 İşleve özgün yapısı aşağıdaki öğeleri içerir:  
  
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
  
 Bu örnekte `FindData` sınıfı, karşılık gelen veri üyesi özgün yapısı ve katıştırılmış yapısı her öğe için içerir. İki özgün karakter arabellekleri yerine, sınıf dizelerini değiştirir. **MarshalAsAttribute** ayarlar <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunlukta karakter diziler yönetilmeyen yapılar içinde görüntülenir.  
  
 `LibWrap` Sınıfı içeren yönetilen prototipi `FindFirstFile` geçirir yöntemi `FindData` bir parametre olarak sınıfı. Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreleri geçirildiğinden öznitelikleri.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>Birleşimler örneği  
 Bu örnek yalnızca değer türleri içeren yapılar ve UNION bekleniyor bir yönetilmeyen işlevi için parametre olarak bir değer türü ve bir dize içeren yapıları geçirmek nasıl gösterir. UNION, iki veya daha fazla değişken tarafından paylaşılan bir bellek konumunu temsil eder.  
  
 Özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi, birleşimler örnek kullanır:  
  
-   **TestUnion** PinvokeLib.dll dışarı.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) daha önce listelenen işlevi ve iki birleşimler için bir uygulama içeren özel bir yönetilmeyen kitaplık **MYUNION** ve **MYUNION2**. Birleşimler aşağıdaki öğeleri içerir:  
  
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
  
 Yönetilen kodda birleşimler yapıları olarak tanımlanır. `MyUnion` Yapısı üye olarak iki değer türleri içerir: bir tamsayı ve bir double. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, her veri üyesi kesin konumunu denetlemek için ayarlanır. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Özniteliği, UNION yönetilmeyen gösterimini alanlarını fiziksel konumunu sağlar. Üyeleri aynı parça bellek tanımlayabilirsiniz böylece her iki üye aynı uzaklık değerleri sahip dikkat edin.  
  
 `MyUnion2_1`ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içermelidir. Yönetilen kodda değer türleri ve başvuru türleri çakışmasına izin verilmez. Bu örnek aynı yönetilmeyen işlevi çağrılırken hem türlerini kullanmak arayan etkinleştirmek için aşırı yükleme yöntemini kullanır. Düzenini `MyUnion2_1` açık olup kesin bir uzaklık değeri içerir. Buna karşılık, `MyUnion2_2` bir ardışık düzen sahip olduğundan açık düzenleri başvuru türleriyle izin verilmez. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümelerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunlukta karakter diziler UNION yönetilmeyen gösterimini içinde görüntülenir.  
  
 `LibWrap` Sınıfı için prototipleri içerir `TestUnion` ve `TestUnion2` yöntemleri. `TestUnion2`bildirmek için aşırı `MyUnion2_1` veya `MyUnion2_2` parametre olarak.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime örneği  
 Bu örnek, bir işaretçi bir sınıf bir yapısına yönelik işaretçinin bekliyor yönetilmeyen bir işleve geçirilecek gösterilmiştir.  
  
 SysTime örnek özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:  
  
-   **GetSystemTime** Kernel32.dll dışarı.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 İşleve özgün yapısı aşağıdaki öğeleri içerir:  
  
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
  
 Bu örnekte `SystemTime` sınıfı sınıf üyeleri gösterilen özgün yapısı öğelerini içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği ayarlanmış üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olun.  
  
 `LibWrap` Sınıfı içeren yönetilen prototipi `GetSystemTime` geçirir yöntemi `SystemTime` sınıfı olarak bir giriş/çıkış parametresi varsayılan olarak. Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreleri geçirildiğinden öznitelikleri. Çağıran sonuçlarını almak için bu [yön öznitelikleri](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) açıkça uygulanmış olması gerekir. `App` Sınıfının yeni bir örneğini oluşturur `SystemTime` sınıfı ve kendi veri alanları erişir.  
  
### <a name="code-samples"></a>Kod Örnekleri  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs örneği  
 Bu örnek nasıl tamsayılar ve Out parametreleri yönetilmeyen bir işleve dize olarak içeren bir dizi yapıların iletileceğini gösterir.  
  
 Bu örnek kullanarak yerel bir işleve nasıl çağırılacağını <xref:System.Runtime.InteropServices.Marshal> sınıfı ve güvenli olmayan kod kullanarak.  
  
 Bu örnek bir sarmalayıcı işlevleri kullanır ve platform çağırır tanımlanan [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), aynı zamanda sağlanan kaynak dosyalarında. Kullandığı `TestOutArrayOfStructs` işlevi ve `MYSTRSTRUCT2` yapısı. Yapısı aşağıdaki öğeleri içerir:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Sınıfı, bir dize nesnesi ANSI karakter içerir. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Alan ANSI biçimini belirtir. `MyUnsafeStruct`, bir yapı olduğundan içeren bir <xref:System.IntPtr> yerine bir dize türü.  
  
 `LibWrap` Sınıfı içeren aşırı yüklenmiş `TestOutArrayOfStructs` prototip yöntemi. İle bir yöntem bir işaretçi bir parametre olarak bildirirse, sınıf işaretlenmelidir `unsafe` anahtar sözcüğü. Çünkü [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] güvenli olmayan kod, aşırı yüklenmiş yöntemin güvensiz değiştiricisi kullanamazsınız ve `MyUnsafeStruct` yapısı gereksizdir.  
  
 `App` Uygulayan sınıf `UsingMarshaling` dizi geçirmek için gerekli görevleri gerçekleştiren yöntemi. Dizi işaretlenmiş `out` (`ByRef` Visual Basic'te) verileri belirtmek için anahtar sözcüğü Aranan çağırana iletir. Aşağıdaki uygulama kullanan <xref:System.Runtime.InteropServices.Marshal> sınıfı yöntemlerinin:  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>yönetilen bir nesnenin yönetilmeyen arabellek verilerini sıralamakta.  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>yapısında dizeler için ayrılan bellek serbest bırakmak için.  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>dizi için ayrılan bellek serbest bırakmak için.  
  
 Daha önce belirtildiği gibi C# güvenli olmayan kod verir ve [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] desteklemez. C# örneğinde, `UsingUnsafePointer` yerine işaretçileri kullanan alternatif bir yöntem uygulamasıdır <xref:System.Runtime.InteropServices.Marshal> geçirmek için sınıf geri dizi içeren `MyUnsafeStruct` yapısı.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [Platform çağırma veri türleri](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Dizeleri hazırlama](../../../docs/framework/interop/marshaling-strings.md)  
 [Türlerin dizileri sıralama](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)
