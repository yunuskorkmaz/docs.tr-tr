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
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181458"
---
# <a name="default-marshaling-for-arrays"></a>Diziler için Varsayılan Sıralama
Tamamen yönetilen koddan oluşan bir uygulamada, ortak dil çalışma süresi dizi türlerini Giriş/Çıkış parametreleri olarak geçirir. Buna karşılık, interop mareşal varsayılan olarak parametrelerolarak bir dizi geçer.  
  
 [Sabitleme optimizasyonu](copying-and-pinning.md)ile, aynı dairedeki nesnelerle etkileşimde bulunan bir blittable dizi, In/Out parametresi olarak çalışıyor gibi görünebilir. Ancak, daha sonra kodu makineler arası proxy oluşturmak için kullanılan bir tür kitaplığına dışa aktarırsanız ve bu kitaplık çağrılarınızı daireler arasında mareşallik etmek için kullanılırsa, aramalar parametre davranışında doğru ya da doğru ya da gerçek olarak geri döndürülebilir.  
  
 Diziler doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki ayrımlar diğer blittable olmayan türlere göre daha fazla bilgi garanti eder.  
  
## <a name="managed-arrays"></a>Yönetilen Diziler  
 Yönetilen dizi türleri değişebilir; ancak, <xref:System.Array?displayProperty=nameWithType> sınıf tüm dizi türlerinin taban sınıfıdır. **System.Array** sınıfı, bir dizinin derecesini, uzunluğunu ve alt ve üst sınırlarını belirleyen özelliklerin yanı sıra dizilere erişme, sıralama, arama, kopyalama ve oluşturma yöntemlerine sahiptir.  
  
 Bu dizi türleri dinamiktir ve taban sınıf kitaplığında tanımlanan karşılık gelen statik türü yoktur. Bu dizi farklı bir tür olarak öğe türü ve sıralama her kombinasyonu düşünmek uygundur. Bu nedenle, tek boyutlu bir tamsayı dizisi, çift tiplerden oluşan tek boyutlu bir diziden farklı bir türdedir. Benzer şekilde, iki boyutlu bir tamsayı dizisi, tek boyutlu bir tamsayı dizisinden farklıdır. Türleri karşılaştırırken dizinin sınırları dikkate alınmaz.  
  
 Aşağıdaki tabloda görüldüğü gibi, yönetilen dizinin herhangi bir örneğinin belirli bir öğe türü, rütbe ve alt sınır olması gerekir.  
  
|Yönetilen dizi türü|Eleman türü|Derece|Alt sınır|İmza gösterimi|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Türüne göre belirtilir.|Rütbeye göre belirtilir.|İsteğe bağlı olarak sınırlara göre belirtilir.|*yazın* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Bilinmiyor|Bilinmiyor|Bilinmiyor|**Array**|  
|**ELEMENT_TYPE_SZARRAY**|Türüne göre belirtilir.|1|0|*yazın* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Yönetilmeyen Diziler  
 Yönetilmeyen diziler, COM tarzı güvenli diziler veya sabit veya değişken uzunlukta C tarzı dizilerdir. Güvenli diziler, ilişkili dizi verilerinin türünü, sıralamasını ve sınırlarını taşıyan kendi kendini açıklayan dizilerdir. C stili diziler, sabit alt sınırı 0 olan tek boyutlu daktisol dizilerdir. Mareşallik hizmeti, her iki dizi türü için de sınırlı bir desteğe sahiptir.  
  
## <a name="passing-array-parameters-to-net-code"></a>Dizi Parametrelerinin .NET Koduna Geçirilmesi  
 Hem C stili diziler hem de güvenli diziler ,güvenli bir dizi veya C stili dizi olarak yönetilmeyen koddan .NET koduna geçirilebilir. Aşağıdaki tabloyönetilmeyen türü değerini ve alınan türü gösterir.  
  
|Yönetilmeyen tür|Alınan tür|  
|--------------------|-------------------|  
|**SafeArray (** *Türü* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType***>**<br /><br /> Sıralama = 1, alt sınır = 0. Boyut yalnızca yönetilen imzada sağlanırsa bilinir. Rank = 1 veya alt bound = 0 olmayan güvenli diziler **SZARRAY**olarak marshaled olamaz.|  
|*Türü*  **[]**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType***>**<br /><br /> Sıralama = 1, alt sınır = 0. Boyut yalnızca yönetilen imzada sağlanırsa bilinir.|  
  
### <a name="safe-arrays"></a>Güvenli Diziler  
 Güvenli bir dizi bir tür kitaplığından bir .NET derlemesine aktarıldığında, dizi bilinen bir türün tek boyutlu dizisine **(int**gibi) dönüştürülür. Parametreler için geçerli olan aynı tür dönüştürme kuralları dizi öğeleri için de geçerlidir. Örneğin, güvenli bir **BSTR** türü dizisi yönetilen bir dize dizisi ne de güvenli bir türdizi yönetilen bir nesne dizisi olur. **SAFEARRAY** öğe türü tür kitaplığından yakalanır ve numaralandırmanın <xref:System.Runtime.InteropServices.UnmanagedType> **SAFEARRAY** değerine kaydedilir.  
  
 Güvenli dizinin sıralaması ve sınırları tür kitaplığından belirlenemediğinden, sıralama 1'e eşit, alt sınır ise 0'a eşit olarak kabul edilir. Sıralama ve [sınırlar, Tip Kitaplığı İthalatçısı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından üretilen yönetilen imzada tanımlanmalıdır. Çalışma zamanında yönteme geçirilen sıralama farklıysa, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> bir atılır. Çalışma zamanında geçirilen dizi türü farklıysa, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> bir atılır. Aşağıdaki örnek, yönetilen ve yönetilmeyen koddaki güvenli dizileri gösterir.  
  
 **Yönetilmeyen imza**  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Yönetilen imza**  
  
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
  
 Tlbimp.exe tarafından üretilen yöntem imzası **ELEMENT_TYPE_SZARRAY**yerine **bir ELEMENT_TYPE_ARRAY** öğe türünü belirtmek üzere değiştirilirse, çok boyutlu veya sıfıra bağlı olmayan güvenli diziler yönetilen koda dönüştürülebilir. Alternatif olarak, tüm dizileri nesne olarak <xref:System.Array?displayProperty=nameWithType> almak için Tlbimp.exe ile **/sysarray** anahtarını kullanabilirsiniz. Geçirilen dizinin çok boyutlu olduğu bilinen durumlarda, Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyebilir ve yeniden derleyebilirsiniz. MSIL kodunu niçin değiştireceğimiz hakkında ayrıntılı bilgi için [Runtime Çağrılı Paketleyicilerini Özelleştirme'ye](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))bakın.  
  
### <a name="c-style-arrays"></a>C-Style Diziler  
 C stili bir dizi bir tür kitaplığından .NET derlemesine aktarıldığında, dizi **ELEMENT_TYPE_SZARRAY**dönüştürülür.  
  
 Dizi öğesi türü tür kitaplığından belirlenir ve alma sırasında korunur. Parametreler için geçerli olan aynı dönüştürme kuralları dizi öğeleri için de geçerlidir. Örneğin, bir dizi **LPD** türü String **türleri** dizisi olur. Tlbimp.exe dizi öğesi türünü yakalar ve <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametreöze özniteliği uygular.  
  
 Dizi sıralaması 1'e eşit olarak kabul edilir. Sıralama 1'den büyükse, dizi sütun-ana sırada tek boyutlu bir dizi olarak sıralanır. Alt sınır her zaman 0'a eşittir.  
  
 Tür kitaplıkları sabit veya değişken uzunlukta diziler içerebilir. Tür kitaplıkları değişken uzunluktaki dizileri mareşallemek için gereken bilgilerden yoksun olduğundan, Tlbimp.exe tür kitaplıklarından yalnızca sabit uzunlukta diziler içe aktarabilir. Sabit uzunluktadizilerle boyut, tür kitaplığından alınır ve parametreye uygulanan **MarshalAsÖz'de** yakalanır.  
  
 Aşağıdaki örnekte gösterildiği gibi, değişken uzunlukta diziler içeren tür kitaplıklarını el ile tanımlamanız gerekir.  
  
 **Yönetilmeyen imza**  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Yönetilen imza**  
  
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
  
 **Boyutu** istemciye iletmek için Size_is veya **length_is** özniteliklerini Arabirim Tanımı Dili (IDL) kaynağındaki bir diziye uygulayabilirsiniz, ancak Microsoft Arabirim Tanım Dili (MIDL) derleyicisi bu bilgileri tür kitaplığına yaymaz. Boyutunu bilmeden, interop mareşallik hizmeti dizi öğelerini karemleyemez. Sonuç olarak, değişken uzunluktaki diziler başvuru bağımsız değişkenleri olarak içe aktarılır. Örnek:  
  
 **Yönetilmeyen imza**  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Yönetilen imza**  
  
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
  
 Tlbimp.exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyip yeniden derleyerek mareşale dizi boyutunu sağlayabilirsiniz. MSIL kodunu niçin değiştireceğimiz hakkında ayrıntılı bilgi için [Runtime Çağrılı Paketleyicilerini Özelleştirme'ye](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))bakın. Dizideki öğe sayısını belirtmek için, <xref:System.Runtime.InteropServices.MarshalAsAttribute> türü yönetilen yöntem tanımının dizi parametresine aşağıdaki yollardan biriyle uygulayın:  
  
- Dizideki öğe sayısını içeren başka bir parametre tanımlayın. Parametreler, ilk parametre den başlayarak 0 sayısı olarak konumlandırılır.
  
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
  
- Dizinin boyutunu sabit olarak tanımlayın. Örnek:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Dizileri yönetilmeyen koddan yönetilen koda göre sıralarken, mareşal dizi boyutunu belirlemek için parametreyle ilişkili **MarshalAsÖzniteliğini** denetler. Dizi boyutu belirtilmemişse, yalnızca bir öğe marshaled.  
  
> [!NOTE]
> **MarshalAsAttribute** yönetilen dizileri yönetilmeyen kodiçin mareşal üzerinde hiçbir etkisi yoktur. Bu doğrultuda, dizi boyutu inceleyerek belirlenir. Yönetilen bir dizinin bir alt kümesini mareşallemek için bir yol yoktur.  
  
 Interop marshaler ayırmak ve bellek almak için **CoTaskMemAlloc** ve **CoTaskMemFree** yöntemleri kullanır. Yönetilmeyen kod tarafından gerçekleştirilen bellek ayırma da bu yöntemleri kullanmanız gerekir.  
  
## <a name="passing-arrays-to-com"></a>Dizileri COM'a Geçirme  
 Yönetilen tüm dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir. Yönetilen türe ve uygulanan özniteliklere bağlı olarak, diziaşağıdaki tabloda gösterildiği gibi güvenli bir dizi veya C stili dizi olarak erişilebilir.  
  
|Yönetilen dizi türü|Dışa aktarılan|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY** **\<** *türü***>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *türü)* **)**<br /><br /> **YönetilmeyenType.LPArray**<br /><br /> Yazı imzada sağlanır. Rütbe her zaman 1, alt sınır her zaman 0'dır. Boyut her zaman çalışma zamanında bilinir.|  
|**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** türü**\<** *sıralama* *bounds* **>**[ sınırlar ] **>**|**YönetilmeyenType.SafeArray(** *türü)* **)**<br /><br /> **YönetilmeyenType.LPArray**<br /><br /> Yazı, rütbe, sınırlar imzada verilmiştir. Boyut her zaman çalışma zamanında bilinir.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **YönetilmeyenType.SafeArray(** *türü)* **)**<br /><br /> Türü, sıralaması, sınırları ve boyutu her zaman çalışma zamanında bilinir.|  
  
 OLE Otomasyonu'nda LPSTR veya LPWSTR içeren yapı dizileri ile ilgili bir sınırlama vardır.  Bu nedenle, **String** alanları **UnmanagedType.BSTR**olarak marshaled olması gerekir. Aksi takdirde, bir özel durum atılır.  
  
### <a name="element_type_szarray"></a>ELEMENT_TYPE_SZARRAY  
 **ELEMENT_TYPE_SZARRAY** parametresi (tek boyutlu dizi) içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY'ine** dönüştürülür. Aynı dönüştürme kuralları dizi öğesi türleri için de geçerlidir. Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY'e**otomatik olarak kopyalanır. Örnek:  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Güvenli dizilerin sıralaması her zaman 1 ve alt sınır her zaman 0'dır. Boyut, geçirilen yönetilen dizinin boyutuna göre çalışma zamanında belirlenir.  
  
 Dizi, öznitelik kullanılarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> C stili dizi olarak da düzenlenebilir. Örnek:  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
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
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Mareşal, diziyi mareşallemek için gereken uzunluk bilgilerine sahip olsa da, dizi uzunluğu genellikle uzunluğu callee'ye iletmek için ayrı bir bağımsız değişken olarak geçirilir.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 **bir ELEMENT_TYPE_ARRAY** parametresi içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY'ine** dönüştürülür. Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY'e**otomatik olarak kopyalanır. Örnek:  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Güvenli dizilerin sıralaması, boyutu ve sınırları, yönetilen dizinin özelliklerine göre çalışma zamanında belirlenir.  
  
 Dizi, öznitelik uygulanarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> C stili dizi olarak da marshaled olabilir. Örnek:  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
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
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 İç içe diziler marshaled olamaz. Örneğin, Tür [Kitaplığı İhracatçısı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışa aktarıldığında aşağıdaki imza bir hata oluşturur.  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array>  
 <xref:System.Array?displayProperty=nameWithType> Parametre içeren bir yöntem bir .NET derlemesinden tür kitaplığına dışa aktarıldığında, dizi parametresi **_Array** arabirimine dönüştürülür. Yönetilen dizinin içeriğine yalnızca **_Array** arabiriminin yöntemleri ve özellikleri yle erişilebilir. **System.Array** özniteliği kullanılarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> **safearray** olarak da marshaled olabilir. Güvenli bir dizi olarak marshaled zaman, dizi öğeleri varyantları olarak marshaled. Örnek:  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Yapılar içindeki diziler  
 Yönetilmeyen yapılar katıştırılmış diziler içerebilir. Varsayılan olarak, bu katıştılı dizi alanları SAFEARRAY olarak marshaled. Aşağıdaki örnekte, `s1` doğrudan yapının kendi içinde ayrılmış gömülü bir dizidir.  
  
#### <a name="unmanaged-representation"></a>Yönetilmeyen gösterim  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Diziler, <xref:System.Runtime.InteropServices.UnmanagedType> <xref:System.Runtime.InteropServices.MarshalAsAttribute> alanı ayarlamanızı gerektiren bir dizi olarak düzenlenebilir. Boyutu yalnızca sabit olarak ayarlanabilir. Aşağıdaki kod, 'nin ilgili `MyStruct`yönetilen tanımını gösterir.  
  
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

- [Varsayılan Sıralama Davranışı](default-marshaling-behavior.md)
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Yön Özellikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
