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
ms.openlocfilehash: 96300808ba3024a138678494200b10ef722c6fd9
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894239"
---
# <a name="default-marshaling-for-arrays"></a>Diziler için Varsayılan Sıralama
Tamamen yönetilen koddan oluşan bir uygulamada, ortak dil çalışma zamanı dizi türlerini ın/out parametreleri olarak geçirir. Buna karşılık, birlikte çalışma sıralayıcısı varsayılan olarak parametre olarak bir diziyi geçirir.  
  
 [Sabitleme iyileştirmesi](copying-and-pinning.md)ile, bir blittable dizisi aynı apartman içindeki nesnelerle etkileşim kurarken bir ın/out parametresi olarak çalışmak üzere görünebilir. Ancak, daha sonra kodu, platformlar arası ara sunucu oluşturmak için kullanılan bir tür kitaplığına dışa aktardığınızda ve bu kitaplık, çağrılarınızı gruplar arasında sıralamak için kullanılırsa, çağrılar parametre davranışındaki true değerine dönebilir.  
  
 Diziler doğası gereği karmaşıktır ve yönetilen ve yönetilmeyen diziler arasındaki farklılıklar diğer blittable olmayan türlerden daha fazla bilgi vermez.  
  
## <a name="managed-arrays"></a>Yönetilen diziler  
 Yönetilen dizi türleri farklılık gösterebilir; Ancak, <xref:System.Array?displayProperty=nameWithType> sınıfı tüm dizi türlerinin temel sınıfıdır. **System. Array** sınıfında, bir dizinin derecesini, uzunluğunu ve alt ve üst sınırlarını belirlemek için özellikler ve ayrıca, dizilere erişme, sıralama, arama, kopyalama ve oluşturma yöntemleri vardır.  
  
 Bu dizi türleri dinamiktir ve temel sınıf kitaplığında tanımlı bir statik türe sahip değildir. Öğe türü ve derecenin her birleşiminin ayrı bir dizi türü olarak düşünmek yararlıdır. Bu nedenle, tek boyutlu bir tamsayılar dizisi, Çift türlerden oluşan tek boyutlu bir diziden farklı türde. Benzer şekilde iki boyutlu tamsayılar dizisi, tek boyutlu tamsayılar dizisinden farklıdır. Dizi sınırları, türler karşılaştırılırken düşünülmez.  
  
 Aşağıdaki tabloda gösterildiği gibi, yönetilen bir dizinin herhangi bir örneği belirli bir öğe türü, derece ve alt sınır olmalıdır.  
  
|Yönetilen dizi türü|Öğe türü|boyut sayısı|Alt sınır|İmza gösterimi|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Türe göre belirtilen.|Derecesine göre belirtilen.|İsteğe bağlı olarak sınırlara göre belirtilir.|*tür* **[** *n*,*e* **]**|  
|**ELEMENT_TYPE_CLASS**|Bilinmiyor|Bilinmiyor|Bilinmiyor|**System. Array**|  
|**ELEMENT_TYPE_SZARRAY**|Türe göre belirtilen.|1\.|0|*tür* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Yönetilmeyen diziler  
 Yönetilmeyen diziler, sabit veya değişken uzunlukla birlikte, COM stili güvenli diziler veya C stili diziler olabilir. Güvenli diziler, ilişkili dizi verilerinin türünü, derecesini ve sınırlarını taşıyan kendi kendine açıklayıcı dizilerdir. C stili diziler, sabit bir alt sınırı 0 olan tek boyutlu bir tür dizilerdir. Sıralama hizmeti, her iki dizi türü için sınırlı destek içerir.  
  
## <a name="passing-array-parameters-to-net-code"></a>Dizi parametrelerini .NET koduna geçirme  
 Hem C stili diziler hem de güvenli diziler, yönetilmeyen koddan güvenli bir dizi ya da C stili dizi olarak .NET koduna geçirilebilir. Aşağıdaki tabloda, yönetilmeyen tür değeri ve içeri aktarılan tür gösterilmektedir.  
  
|Yönetilmeyen tür|İçeri aktarılan tür|  
|--------------------|-------------------|  
|**SAFEARRAY (** *tür* **)**|**element_type_szarray** **\<** *ConvertedType* **>**<br /><br /> Derece = 1, alt sınır = 0. Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir. Rank = 1 veya alt sınır = 0 olmayan güvenli diziler **Szarray**olarak sıralanamaz.|  
|*Tür* **[]**|**element_type_szarray** **\<** *ConvertedType* **>**<br /><br /> Derece = 1, alt sınır = 0. Boyut yalnızca yönetilen İmzada sağlanmışsa bilinir.|  
  
### <a name="safe-arrays"></a>Güvenli diziler  
 Bir tür kitaplığından bir .NET derlemesine bir güvenli dizi aktarıldığında, dizi bilinen bir türün ( **int**gibi) tek boyutlu dizisine dönüştürülür. Parametrelere uygulanan aynı tür dönüştürme kuralları dizi öğeleri için de geçerlidir. Örneğin, bir **BSTR** türündeki güvenli dizi, yönetilen dizelerin bir dizisi haline gelir ve bir dizi güvenli değişken yönetilen bir nesne dizisi haline gelir. **SAFEARRAY** öğe türü tür kitaplığından yakalanır ve <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmanın **SAFEARRAY** değerine kaydedilir.  
  
 Güvenli dizinin derecesi ve sınırları tür kitaplığından belirlenemediğinden, derece 1 ' e eşit kabul edilir ve alt sınır 0 ' a eşit kabul edilir. Sıralama ve sınırların, [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından üretilen yönetilen İmzada tanımlanması gerekir. Çalışma zamanında yönteme geçirilen derece farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> oluşturulur. Çalışma zamanında geçirilen dizi türü farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> oluşturulur. Aşağıdaki örnekte, yönetilen ve yönetilmeyen koddaki güvenli diziler gösterilmektedir.  
  
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
  
 Tlbimp. exe tarafından üretilen Yöntem imzası, **element_type_szarray**yerine **element_type_array** öğe türünü gösterecek şekilde değiştirilirse, çok boyutlu veya sıfır dışında bağlantılı güvenli diziler yönetilen koda sıralanabilir. Alternatif olarak, tüm dizileri nesne olarak <xref:System.Array?displayProperty=nameWithType> içeri aktarmak için **/sysarray** anahtarını Tlbimp. exe ile birlikte kullanabilirsiniz. Geçirilen dizinin çok boyutlu olduğu bilindiğinde, Tlbimp. exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyebilir ve sonra yeniden derleyebilirsiniz. MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>C stili diziler  
 Bir C stili dizi bir tür kitaplığından .NET derlemesine aktarıldığında, dizi **element_type_szarray**olarak dönüştürülür.  
  
 Dizi öğesi türü tür kitaplığından belirlenir ve içeri aktarma sırasında korunur. Parametrelere uygulanan aynı dönüştürme kuralları dizi öğeleri için de geçerlidir. Örneğin, **LPSTR** türünden oluşan bir dizi **dize** türü dizisi haline gelir. Tlbimp. exe, dizi öğesi türünü yakalar ve <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğini parametresine uygular.  
  
 Dizi derecesi 1 ' e eşit kabul edilir. Sıra 1 ' den büyükse, dizi sütun birincil sırada tek boyutlu bir dizi olarak sıralanır. Alt sınır her zaman 0 ' a eşittir.  
  
 Tür kitaplıklarında sabit veya değişken uzunlukta diziler bulunabilir. Tür kitaplıklarında değişken uzunluklu dizileri sıralamak için gereken bilgiler bulunmadığından, Tlbimp. exe yalnızca tür kitaplıklarından sabit uzunluklu diziler alabilir. Sabit uzunluklu diziler ile, boyut tür kitaplığından içeri aktarılır ve parametreye uygulanan **MarshalAsAttribute** içinde yakalanır.  
  
 Aşağıdaki örnekte gösterildiği gibi, değişken uzunluklu diziler içeren tür kitaplıklarını el ile tanımlamanız gerekir.  
  
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
  
 Boyutu bir istemciye iletmek için, bir arabirim tanım dili (IDL) kaynağındaki bir **diziye veya** **length_is** özniteliklerini uygulayabilseniz de, Microsoft arabirim tanımlama dili (MIDL) derleyicisi bunu yayılmaz tür kitaplığına ilişkin bilgiler. Boyut bilinmeden, birlikte çalışma sıralama hizmeti dizi öğelerini sıralayamaz. Sonuç olarak, değişken uzunluklu diziler başvuru bağımsız değişkenleri olarak içeri aktarılır. Örneğin:  
  
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
  
 Tlbimp. exe tarafından üretilen Microsoft ara dili (MSIL) kodunu düzenleyerek ve sonra yeniden derleyerek dizi boyutu ile Sıralayıcı sağlayabilirsiniz. MSIL kodunu değiştirme hakkında daha fazla bilgi için bkz. [çalışma zamanında çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Dizideki öğe sayısını göstermek için, <xref:System.Runtime.InteropServices.MarshalAsAttribute> türü yönetilen yöntem tanımının dizi parametresine aşağıdaki yöntemlerden biriyle uygulayın:  
  
- Dizideki öğe sayısını içeren başka bir parametre tanımla. Parametreler, 0 numaralı ilk parametre ile başlayarak konuma göre tanımlanır.     
  
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
  
- Dizinin boyutunu bir sabit olarak tanımlayın. Örneğin:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Yönetilmeyen koddan yönetilen koda diziler hazırlama sırasında Sıralayıcı, dizi boyutunu belirlemede parametresiyle ilişkili **MarshalAsAttribute** denetler. Dizi boyutu belirtilmemişse yalnızca bir öğe sıralanır.  
  
> [!NOTE]
> **MarshalAsAttribute** yönetilen dizileri yönetilmeyen koda hazırlamayı etkilemez. Bu yönde, dizi boyutu İnceleme tarafından belirlenir. Yönetilen dizinin bir alt kümesini sıralama yöntemi yoktur.  
  
 Birlikte çalışma sıralayıcısı, bellek ayırmak ve almak için **CoTaskMemAlloc** ve **CoTaskMemFree** yöntemlerini kullanır. Yönetilmeyen kod tarafından gerçekleştirilen bellek ayırma Ayrıca bu yöntemleri de kullanmalıdır.  
  
## <a name="passing-arrays-to-com"></a>Dizileri COM 'a geçirme  
 Tüm yönetilen dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir. Yönetilen türe ve ona uygulanan özniteliklere bağlı olarak, aşağıdaki tabloda gösterildiği gibi diziye bir güvenli dizi veya C stili dizi olarak erişilebilir.  
  
|Yönetilen dizi türü|Farklı olarak verildi|  
|------------------------|-----------------|  
|**element_type_szarray** **\<** *tür* **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *tür* **)**<br /><br /> **UnmanagedType. LPArray**<br /><br /> Tür, İmzada verilmiştir. Rank her zaman 1, alt sınır her zaman 0 ' dır. Boyut her zaman çalışma zamanında bilinirdi.|  
|**element_type_array** **\<** *tür* *sıralaması [* *sınır]* **>** **\<** **>** **>** **\<**|**UnmanagedType. SAFEARRAY (** *tür* **)**<br /><br /> **UnmanagedType. LPArray**<br /><br /> İmzada tür, derece, sınırlar verilmiştir. Boyut her zaman çalışma zamanında bilinirdi.|  
|**ELEMENT_TYPE_CLASS** **\<** <xref:System.Array?displayProperty=nameWithType> **>**|**UT_Interface**<br /><br /> **UnmanagedType. SAFEARRAY (** *tür* **)**<br /><br /> Tür, derece, sınır ve boyut her zaman çalışma zamanında bilinirler.|  
  
 OLE Otomasyonunda LPSTR veya LPWSTR içeren yapıların dizileri ile ilgili bir sınırlama vardır.  Bu nedenle, **dize** alanlarının **UnmanagedType. BSTR**olarak sıralanması gerekir. Aksi takdirde, bir özel durum oluşturulur.  
  
### <a name="element_type_szarray"></a>ELEMENT_TYPE_SZARRAY  
 Bir **element_type_szarray** parametresi (tek boyutlu dizi) içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür. Aynı dönüştürme kuralları dizi öğesi türleri için de geçerlidir. Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır. Örneğin:  
  
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
  
 Güvenli dizilerin sıralaması her zaman 1 ' dir ve alt sınır her zaman 0 ' dır. Boyut, çalışma zamanında geçirilmekte olan yönetilen dizinin boyutuna göre belirlenir.  
  
 Dizi, <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği kullanılarak C stili bir dizi olarak da sıralanabilir. Örneğin:  
  
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
  
 Sıralayıcı, diziyi sıralamak için gereken uzunluk bilgilerine sahip olsa da, dizi uzunluğu genellikle ayrı bir bağımsız değişken olarak geçirilir ve bu da uzunluğu aranan olarak iletmiştir.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 Bir **element_type_array** parametresi içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi belirli bir türün **SAFEARRAY** değerine dönüştürülür. Yönetilen dizinin içeriği yönetilen bellekten **SAFEARRAY**'e otomatik olarak kopyalanır. Örneğin:  
  
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
  
 Güvenli dizilerin derece, boyut ve sınırları, çalışma zamanında yönetilen dizinin özelliklerine göre belirlenir.  
  
 Dizi, <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği uygulanarak C stili bir dizi olarak da sıralanabilir. Örneğin:  
  
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
  
 İç içe diziler sıralanamaz. Örneğin, aşağıdaki imza [tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışarı aktarıldığında bir hata üretir.  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>Element_type_class \<System. Array >  
 Bir <xref:System.Array?displayProperty=nameWithType> parametre içeren bir yöntem bir .net derlemesinden bir tür kitaplığına aktarıldığında, dizi parametresi bir **_array** arabirimine dönüştürülür. Yönetilen dizinin içeriğine yalnızca **_array** arabiriminin Yöntemler ve özellikleri aracılığıyla erişilebilir. **System. Array** , <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği kullanılarak bir **SAFEARRAY** olarak da sıralanabilir. Güvenli bir dizi olarak sıralandığınızda, dizi öğeleri de çeşitler olarak sıralanır. Örneğin:  
  
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
 Yönetilmeyen yapılar, gömülü diziler içerebilir. Varsayılan olarak, bu katıştırılmış dizi alanları bir SAFEARRAY olarak sıralanır. Aşağıdaki örnekte, `s1` doğrudan yapının içinde ayrılmış bir katıştırılmış dizidir.  
  
#### <a name="unmanaged-representation"></a>Yönetilmeyen Gösterim  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Diziler, <xref:System.Runtime.InteropServices.MarshalAsAttribute> alanı ayarlamanızı gerektiren <xref:System.Runtime.InteropServices.UnmanagedType>olarak sıralanabilir. Boyut yalnızca bir sabit olarak ayarlanabilir. Aşağıdaki kod, karşılık gelen yönetilen tanımını `MyStruct`gösterir.  
  
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
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
