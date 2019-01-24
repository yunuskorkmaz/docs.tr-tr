---
title: Diziler için Varsayılan Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a7b4cb29dcf2c799f17bb7f3a02c300c5f0d36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555407"
---
# <a name="default-marshaling-for-arrays"></a>Diziler için Varsayılan Hazırlama
Tamamen yönetilen kod oluşan bir uygulamada, ortak dil çalışma zamanı dizi türleri olarak In/Out parametresi geçirir. Buna karşılık, birlikte çalışma sıralayıcısı parametreleri olduğu gibi bir dizi varsayılan olarak geçirir.  
  
 İle [sabitleme iyileştirme](copying-and-pinning.md), bir blok halinde kopyalanabilir dizisi olarak bir ın/Out parametresi aynı grup nesneleri ile etkileşim kurulurken çalışılacak görünebilir. Ancak, daha sonra kod çapraz makine proxy oluşturmak için kullanılan bir tür kitaplığı verme ve bu kitaplık çağrılarınızı apartmanlar arasında hazırlamak için kullanılan, parametre davranış true çağrıları döndürebilirsiniz.  
  
 Diziler, doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki farklılıklar garanti diğer kopyalanamaz türler daha fazla bilgi. Bu konu, sıralama dizileri aşağıdaki bilgileri sağlar:  
  
-   [Yönetilen diziler](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Yönetilmeyen diziler](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [.NET kodu için dizi parametreleri geçirme](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [COM dizileri geçirme](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a>Yönetilen diziler  
 Dizi türleri değişebilir yönetilen; Ancak, <xref:System.Array?displayProperty=nameWithType> tüm dizi türleri temel sınıfı. **System.Array** sınıfı derece, uzunluğu, alt ve üst sınırları erişme, sıralama, arama, kopyalama ve diziler oluşturma yöntemleri yanı sıra, bir dizi belirlemek için özelliklere sahiptir.  
  
 Bu dizi türleri dinamiktir ve temel sınıf kitaplığı'nda tanımlanan karşılık gelen statik türü yok. Her öğe türü ve boyut birleşimi farklı bir tür dizisi düşünmek uygundur. Bu nedenle, tek boyutlu bir tamsayı dizisi çift türlerinin tek boyutlu dizi değerinden farklı bir türü var. Benzer şekilde tamsayı iki boyutlu bir dizi tek boyutlu bir tamsayı dizi farklıdır. Dizi sınırları türleri karşılaştırırken dikkate alınmaz.  
  
 Aşağıdaki tabloda gösterildiği gibi yönetilen bir diziyi herhangi bir örneği bir özel öğe türü, boyut ve alt sınırı olmalıdır.  
  
|Yönetilen dizi türü|Öğe türü|boyut sayısı|Alt sınır|İmza gösterimi|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Türü tarafından belirtilen.|Boyut sayısı tarafından belirtilen.|İsteğe bağlı olarak sınır tarafından belirtilen.|*type* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Bilinmiyor|Bilinmiyor|Bilinmiyor|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|Türü tarafından belirtilen.|1.|0|*tür* **[** *n* **]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a>Yönetilmeyen diziler  
 COM Stili güvenli dizilere veya sabit veya değişken uzunluğu ile C stili diziler bunun yönetilmeyen dizilerdir. Güvenli dizilere türü, boyut ve sınırları ilişkili dizi veri taşıyan bir dizi kendini açıklayan özelliktedir. C stili, tek boyutlu bir türü belirlenmiş diziler sabit alt sınırı 0 ile dizilerdir. Hazırlama hizmet, her iki türde diziler için destek sınırlıdır.  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a>.NET kodu için dizi parametreleri geçirme  
 Hem C stili diziler hem de güvenli dizilere .NET kodu için yönetilmeyen koddan güvenli bir dizi veya bir C tarzı dizi olarak geçirilebilir. Aşağıdaki tabloda, yönetilmeyen tür ve içeri aktarılan türü gösterilmektedir.  
  
|Yönetilmeyen tür|İçeri aktarılan türü|  
|--------------------|-------------------|  
|**SafeArray (** *türü* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Boyut alt sınırı 1 = 0 =. Boyutu, yalnızca yönetilen imzasında sağlanırsa, adı verilir. Derece olmayan güvenli dizilere = 1 ya da alt sınır = 0 olamaz sıralanmış olarak **SZARRAY**.|  
|*Tür***]** |**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Boyut alt sınırı 1 = 0 =. Boyutu, yalnızca yönetilen imzasında sağlanırsa, adı verilir.|  
  
### <a name="safe-arrays"></a>Güvenli diziler  
 Güvenli bir dizi için bir .NET derlemesi bir tür kitaplığından içeri aktarıldığında, dizi tek boyutlu bir dizi için bir bilinen türü dönüştürülür (gibi **int**). Parametreleri için geçerli tür dönüştürme kurallarını dizi öğeleri için de geçerlidir. Örneğin, güvenli bir dizi **BSTR** türleri, yönetilen bir dize dizisi haline gelir ve güvenli bir dizisi bir yönetilen nesneler dizisi haline gelir. **SAFEARRAY'i** öğe türü tür kitaplığından yakalanır ve kaydedilen **SAFEARRAY'i** değerini <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi.  
  
 Tür kitaplığından boyut sayısı ve güvenli dizi sınırları belirlenemediğinden boyut eşit 1 olarak kabul edilir ve alt sınırı eşit 0 olarak varsayılır. Boyut sayısı ve sınırları tarafından üretilen yönetilen imzayı tanımlanmalıdır [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Çalışma zamanında yönteme boyut farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> oluşturulur. Dizi türünü çalışma zamanında aktarılırsa farklıdır, bir <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> oluşturulur. Aşağıdaki örnek, yönetilen ve yönetilmeyen kod içinde güvenli dizilere gösterir.  
  
 **Yönetilmeyen imzası**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Yönetilen imzası**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 Çok boyutlu veya sıfır olmayan sınır güvenli dizilere sıralanmış yönetilen koda Tlbimp.exe tarafından üretilen yöntem imzası bir öğe türü belirtmek için değiştirilirse **ELEMENT_TYPE_ARRAY** yerine **ELEMENT_ TYPE_SZARRAY**. Alternatif olarak, **/sysarray** tüm dizileri olarak içeri aktarmak için Tlbimp.exe anahtarı <xref:System.Array?displayProperty=nameWithType> nesneleri. Geçirilen dizi çok boyutlu olduğu bilinen durumlarda, Tlbimp.exe Microsoft Ara dil (MSIL) kodu üretilen düzenleyebilir ve yeniden derleyin. MSIL kodu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).  
  
### <a name="c-style-arrays"></a>C stili diziler  
 Bir C tarzı dizi için bir .NET derlemesi bir tür kitaplığından içeri aktarıldığında, diziye dönüştürülen **ELEMENT_TYPE_SZARRAY**.  
  
 Typ prvku pole tür kitaplığından belirledi ve içeri aktarma sırasında korunur. Parametreleri uygulanan aynı dönüştürme kuralları, dizi öğeleri için de geçerlidir. Örneğin, bir dizi **LPStr** türleri dizisi haline gelir **dize** türleri. Tlbimp.exe typ prvku pole yakalar ve geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği için parametre.  
  
 Dizi boyut sayısı 1'e eşit kabul edilir. Boyut sayısı 1'den büyükse, bir dizi sütun öncelikli bir sırada tek boyutlu bir dizi olarak sıralanır. Her zaman alt sınırı 0'a eşit.  
  
 Tür kitaplıkları, sabit veya değişken uzunlukta diziler içerebilir. Tür kitaplıkları değişken uzunlukta diziler hazırlamak için gereken bilgileri bulunmadığından Tlbimp.exe tür kitaplıklarından yalnızca sabit uzunluklu dizi içeri aktarabilirsiniz. Sabit uzunluklu dizilerle boyutu tür kitaplığından içeri aktarıldı ve yakalanan **MarshalAsAttribute** parametresi uygulanır.  
  
 Değişken uzunlukta diziler içeren tür kitaplıkları, aşağıdaki örnekte gösterildiği gibi el ile tanımlamalısınız.  
  
 **Yönetilmeyen imzası**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Yönetilen imzası**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 Uygulayabilirsiniz ancak **size_is** veya **length_is** bir dizi boyutu bir istemci, Microsoft arabirim tanımı dili (MIDL) iletmek için arabirim tanımlama dili (IDL) kaynak öznitelikleri Derleyici, tür kitaplığı için bu bilgileri dağıtılmaz. Hizmet hazırlama birlikte çalışma boyutu bilmeden dizi öğeleri sıralanamıyor. Sonuç olarak, değişken uzunlukta diziler, başvuru bağımsız değişkenleri içeri aktarılır. Örneğin:  
  
 **Yönetilmeyen imzası**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Yönetilen imzası**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 Microsoft Tlbimp.exe tarafından üretilen Ara dil (MSIL) kodu düzenleme ve ardından yeniden derlemeden, Sıralayıcı dizi boyutu ile sağlayabilirsiniz. MSIL kodu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)). Dizideki öğelerin sayısını belirtmek için uygulama <xref:System.Runtime.InteropServices.MarshalAsAttribute> yönetilen yöntem tanımında aşağıdaki yollardan biriyle dizi parametre türü:  
  
-   Dizideki öğelerin sayısını içeren başka bir parametre tanımlayın. Parametreleri, sayı olarak 0 ile ilk parametre başlangıç konuma göre tanımlanır.     
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   Dizinin boyutu sabit olarak tanımlayın. Örneğin:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Sıralama dizileri, yönetilmeyen koddan yönetilen koda, Sıralayıcı denetler **MarshalAsAttribute** dizi boyutu belirlemek için parametre ile ilişkili. Dizi boyutu belirtilmezse, yalnızca bir öğe sıralanır.  
  
> [!NOTE]
>  **MarshalAsAttribute** hazırlama üzerinde hiçbir etkisi diziler yönetilmeyen kod için yönetilen sahiptir. Bu yönde dizi boyutu inceleme tarafından belirlenir. Yönetilen dizi kümesini hazırlamak için hiçbir yolu yoktur.  
  
 Birlikte çalışma Sıralayıcısı'nı kullanan **CoTaskMemAlloc** ve **CoTaskMemFree** ayırma ve bellek almak için yöntemleri. Bellek ayırma yönetilmeyen kodu tarafından gerçekleştirilen bu yöntemleri de kullanmanız gerekir.  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a>COM dizileri geçirme  
 Tüm yönetilen dizi türleri, yönetilen koddan yönetilmeyen koda geçirilebilir. Yönetilen tür ve uygulanan öznitelikleri bağlı olarak, dizi güvenli bir dize veya bir C tarzı dizi olarak aşağıdaki tabloda gösterildiği gibi erişilebilir.  
  
|Yönetilen dizi türü|Olarak dışarı|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY** **\<** *türü* **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *türü* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Türü imzada sağlanır. Boyut her zaman 1, alt sınır her zaman 0. Boyut her zaman zamanında olarak bilinir.|  
|**ELEMENT_TYPE_ARRAY** **\<** *türü* **>** **\<** *derece* **>**[**\<** *sınırları* **>**]|**UnmanagedType.SafeArray (** *türü* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Sıralama, sınır türü imzada sağlanır. Boyut her zaman zamanında olarak bilinir.|  
|**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray (** *türü* **)**<br /><br /> Tür, boyut, sınırları ve boyutu her zaman zamanında bilinir.|  
  
 OLE Otomasyonu'ndaki LPSTR, LPWSTR içeren yapı dizileri için ilgili bir sınırlama yoktur.  Bu nedenle, **dize** alanları olarak sıralanması gereken **UnmanagedType.BSTR**. Aksi takdirde, bir özel durum oluşturulur.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 Bir yöntemi içeren bir **ELEMENT_TYPE_SZARRAY** parametre (tek boyutlu dizi) için bir tür kitaplığı bir .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **SAFEARRAY'i** belirli bir türde. Dizi öğesi türleri için aynı dönüştürme kurallarını uygulayın. Yönetilen dizi içeriğini otomatik olarak yönetilen belleğe kopyalanır **SAFEARRAY'i**. Örneğin:  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Güvenli dizilere boyut her zaman 1'dir ve alt sınırı her zaman 0. Boyutu çalışma zamanında geçirilen yönetilen dizi boyutu tarafından belirlenir.  
  
 Diziye ayrıca bir C tarzı dizi olarak kullanarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Örneğin:  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Sıralayıcı dizi hazırlamak için gereken uzunluk bilgileri olsa da, uzunluğu genellikle uzunluğu çağrılanın iletmek için ayrı bir bağımsız değişken olarak geçirilir.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 Bir yöntemi içeren bir **ELEMENT_TYPE_ARRAY** parametresi için bir tür kitaplığı bir .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **SAFEARRAY'i** belirli bir türde. Yönetilen dizi içeriğini otomatik olarak yönetilen belleğe kopyalanır **SAFEARRAY'i**. Örneğin:  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Boyut sayısı, boyutu ve güvenli dizilere sınırları çalışma zamanında yönetilen dizi özellikleri tarafından belirlenir.  
  
 Diziye ayrıca bir C tarzı dizi olarak uygulayarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Örneğin:  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 İç içe geçen diziler sıralanamaz. Örneğin, aşağıdaki imzası ile verildiğinde bir hata oluşturur [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array>  
 Bir yöntemi içeren bir <xref:System.Array?displayProperty=nameWithType> parametresi için bir tür kitaplığı bir .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **_dizisi** arabirimi. Yönetilen dizi içeriğini yalnızca yöntemleri ve özellikleri erişilebilen **_dizisi** arabirimi. **System.Array** olarak sıralanabilir bir **SAFEARRAY'i** kullanarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Güvenli bir dizi olarak sıralanmış, dizi öğelerinin çeşitleri sıralanmış. Örneğin:  
  
#### <a name="managed-signature"></a>Yönetilen imzası  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Yapıları içindeki diziler  
 Yönetilmeyen yapıları katıştırılmış dizileri içerebilir. Varsayılan olarak, bu katıştırılmış dize alanları bir SAFEARRAY'i hazırlanırlar. Aşağıdaki örnekte, `s1` doğrudan yapısında kendisine ayrılan katıştırılmış bir dizidir.  
  
#### <a name="unmanaged-representation"></a>Yönetilmeyen gösterimi  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Diziler sıralanmış olarak <xref:System.Runtime.InteropServices.UnmanagedType>, ayarlamanızı gerektiren <xref:System.Runtime.InteropServices.MarshalAsAttribute> alan. Boyut yalnızca bir sabit olarak ayarlanabilir. Aşağıdaki kod, karşılık gelen yönetilen tanımını göstermektedir `MyStruct`.  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yönlü öznitelikler](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
