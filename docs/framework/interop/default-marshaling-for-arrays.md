---
title: "Diziler için Varsayılan Sıralama"
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
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb66908c28a54d4dc24cb77bd82c59862a7fd789
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="default-marshaling-for-arrays"></a>Diziler için Varsayılan Hazırlama
Tamamen yönetilen kod oluşan bir uygulamada, ortak dil çalışma zamanı dizi türleri olarak In/Out parametreleri geçirir. Buna karşılık, birlikte çalışabilirlik Sıralayıcı parametreleri olduğu gibi bir dizi varsayılan olarak geçirir.  
  
 İle [sabitleme iyileştirme](../../../docs/framework/interop/copying-and-pinning.md), blittable dizi olarak bir giriş/çıkış parametresi aynı grup nesneleri ile kullanılırken çalışması için yer alabilir. Ancak, makineler arası proxy oluşturmak için kullanılan bir tür kitaplığı daha sonra kodu verme ve bu kitaplık aramalarınız grupların hazırlamak için kullanılır, çağrı parametresi davranış true için geri dönebilirsiniz.  
  
 Diziler doğası gereği karmaşık ve diğer kopyalanamaz türler daha fazla bilgi yönetilen ve yönetilmeyen diziler arasındaki farklılıklar garanti. Bu konu, dizileri sıralama hakkında aşağıdaki bilgileri sağlar:  
  
-   [Yönetilen diziler](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Yönetilmeyen diziler](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [.NET kodu için dizi parametreleri geçirme](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [COM dizileri geçirme](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a>Yönetilen diziler  
 Dizi türleri değişebilir yönetilen; Ancak, <xref:System.Array?displayProperty=nameWithType> tüm dizi türleri temel sınıfını bir sınıftır. **System.Array** sınıfı derece, uzunluğu ve alt ve üst sınırları erişmek, sıralama, arama, kopyalama ve diziler oluşturma yöntemleri yanı sıra, bir dizi belirlemek için özellikler vardır.  
  
 Bu dizi türleri dinamik ve temel sınıf kitaplığı'nda tanımlanan karşılık gelen bir statik türüne sahip değil. Her öğe türü ve sıra birleşimi dizi ayrı bir türü olarak düşünmek uygundur. Bu nedenle, bir tek boyutlu tamsayı çift türlerinin tek boyutlu dizi daha farklı bir tür dizisidir. Benzer şekilde tamsayıların iki boyutlu bir dizi tek boyutlu tamsayı diziden farklıdır. Dizinin sınırları türleri karşılaştırılırken dikkate alınmaz.  
  
 Aşağıdaki tabloda gösterildiği gibi yönetilen bir dizi herhangi bir örneğini bir özel öğe türü, derece ve alt sınır olması gerekir.  
  
|Yönetilen dizi türü|Öğe türü|RANK|Alt sınır|İmza gösterimi|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Türü tarafından belirtilen.|RANK tarafından belirtilen.|İsteğe bağlı olarak sınırları tarafından belirtilen.|*tür* **[**  *n* ,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Bilinmiyor|Bilinmiyor|Bilinmiyor|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|Türü tarafından belirtilen.|1.|0|*tür* **[**  *n*  **]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a>Yönetilmeyen diziler  
 COM Stili güvenli dizileri ya da sabit veya değişken uzunluğu ile C türü dizileri bunun yönetilmeyen dizidir. Güvenli diziler türü, derece ve ilişkili dizi veri sınırları taşımak dizileri otomatik olarak tanımlar. C türü, sabit bir alt sınırı 0 ile yazılmış tek boyutlu diziler dizidir. Hazırlama Hizmeti her iki tür diziler için destek sınırlıdır.  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a>.NET kodu için dizi parametreleri geçirme  
 C türü diziler ve güvenli diziler .NET kodu için güvenli diziye veya C tarzı dizisi olarak yönetilmeyen koddan geçirilebilir. Aşağıdaki tabloda, yönetilmeyen tür değeri ve içeri aktarılan türü gösterilmektedir.  
  
|Yönetilmeyen tür|İçeri aktarılan türü|  
|--------------------|-------------------|  
|**SafeArray (** *türü* **)**|**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> RANK = 1, alt sınır = 0. Boyutu, yalnızca yönetilen imzada sağladıysanız denir. Rank olmayan güvenli diziler = 1 ya da alt sınır = 0 olamaz sıralanmış olarak **SZARRAY**.|  
|*Tür***]** |**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> RANK = 1, alt sınır = 0. Boyutu, yalnızca yönetilen imzada sağladıysanız denir.|  
  
### <a name="safe-arrays"></a>Güvenli diziler  
 Bir .NET derlemesi için güvenli diziye bir tür kitaplığından içeri aktarıldığında dizi bilinen bir türde tek boyutlu bir diziye dönüştürülür (gibi **int**). Parametreleri uygulamak aynı tür dönüştürme kurallarını dizi öğeleri için de geçerlidir. Örneğin, güvenli bir dizi **BSTR** türleri yönetilen dizisini olur ve bir yönetilen nesneler dizisi güvenli dizisi olur. **SAFEARRAY** öğe türü tür kitaplığından yakalanan ve kaydedilen **SAFEARRAY** değerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırması.  
  
 Rank ve güvenli dizinin sınırları tür kitaplığından belirlenemediğinden, derecesini eşit 1 olarak kabul edilir ve alt sınırı eşit 0 olarak varsayılır. Rank ve sınırları tarafından üretilen yönetilen imza tanımlanmalıdır [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Çalışma zamanında yönteme geçirilen derece farklıysa, bir <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> oluşturulur. Dizi türü çalışma zamanında aktarılırsa farklıdır, bir <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> oluşturulur. Aşağıdaki örnek, yönetilen ve yönetilmeyen kodunda güvenli diziler gösterir.  
  
 **Yönetilmeyen imza**  
  
```  
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
  
 Çok boyutlu veya sınırı sıfır olmayan güvenli diziler sıralanmış yönetilen koda Tlbimp.exe tarafından üretilen yöntem imzası bir öğe türünü belirtmek için değiştirilirse **ELEMENT_TYPE_ARRAY** yerine **ELEMENT_ TYPE_SZARRAY**. Alternatif olarak, kullanabileceğiniz **/sysarray** tüm dizileri olarak almak için Tlbimp.exe anahtarı <xref:System.Array?displayProperty=nameWithType> nesneleri. Çok boyutlu geçirilen dizi olduğu bilinen durumlarda Ara dili (MSIL) kod üretilen Microsoft Tlbimp.exe tarafından düzenleyin ve yeniden derleyin. MSIL kodu değiştirme hakkında daha fazla bilgi için bkz [çalışma zamanı aranabilir sarmalayıcıları özelleştirme](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).  
  
### <a name="c-style-arrays"></a>C türü diziler  
 C türü dizi bir .NET derlemesi bir tür kitaplığından içeri aktarıldığında dizi dönüştürülür **ELEMENT_TYPE_SZARRAY**.  
  
 Dizi öğesi türü tür kitaplığından belirlenir ve içeri aktarma sırasında korunur. Parametreleri uygulamak aynı dönüştürme kurallarını dizi öğeleri için de geçerlidir. Örneğin, bir dizi **LPStr** türleri dizisi hale **dize** türleri. Tlbimp.exe dizi öğesi türü yakalar ve geçerlidir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği parametresi.  
  
 Dizi sıralaması 1'e eşit kabul edilir. Derece 1'den büyükse, dizi sütun öncelikli bir sırada tek boyutlu bir dizi olarak sıralanmış olduğundan. Alt sınır her zaman 0'a eşit.  
  
 Tür kitaplıkları sabit veya değişken uzunlukta diziler içerebilir. Tür kitaplıkları değişken uzunlukta diziler hazırlamak için gereken bilgileri bulunmadığından Tlbimp.exe tür kitaplıklarından yalnızca sabit uzunlukta diziler içeri aktarabilirsiniz. Sabit uzunluklu dizilerle boyutu tür kitaplığından içeri aktarıldı ve içinde yakalanan **MarshalAsAttribute** parametresi uygulanır.  
  
 Değişken uzunlukta diziler içeren tür kitaplıklarının, aşağıdaki örnekte gösterildiği gibi el ile tanımlamalısınız.  
  
 **Yönetilmeyen imza**  
  
```  
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
  
 Geçerli olabilir ancak **size_is** veya **length_is** arabirimi tanım dili (IDL) kaynak boyutu bir istemci, Microsoft arabirimi tanım dili (MIDL) iletmek için bir dizi öznitelikleri derleyici tür kitaplığı için bu bilgileri dağıtılmaz. Hizmet hazırlama birlikte çalışabilirliği boyutu bilmeden dizi öğeleri sıralanamıyor. Sonuç olarak, değişken uzunlukta diziler başvuru bağımsız değişken olarak içe aktarılır. Örneğin:  
  
 **Yönetilmeyen imza**  
  
```  
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
  
 Ara dil (MSIL) kodu üretilen Microsoft Tlbimp.exe tarafından düzenleme ve daha sonra yeniden derlenmesi dizi boyutuyla Sıralayıcı sağlayabilir. MSIL kodu değiştirme hakkında daha fazla bilgi için bkz [çalışma zamanı aranabilir sarmalayıcıları özelleştirme](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be). Dizideki öğelerin sayısını belirtmek için uygulamanız <xref:System.Runtime.InteropServices.MarshalAsAttribute> Yönetilen yöntemi tanımı'nda aşağıdaki yollardan biriyle dizi parametre türü:  
  
-   Dizideki öğelerin sayısını içeren başka bir parametre tanımlayın. Parametreler, birinci parametreyle başlangıç numarası 0 konuma göre tanımlanır.     
  
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
  
-   Dizinin boyutu bir sabit değer olarak tanımlayın. Örneğin:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Yönetilmeyen koddan yönetilen koda dizileri sıralama sırasında Sıralayıcı denetler **MarshalAsAttribute** dizi boyutu belirlemek için parametre ile ilişkilendirilmiş. Dizi boyutu belirtilmezse, yalnızca tek bir öğe başvuruya.  
  
> [!NOTE]
>  **MarshalAsAttribute** hazırlama üzerinde hiçbir etkisi diziler yönetilmeyen kod için yönetilen sahiptir. Bu yönde dizi boyutu inceleme tarafından belirlenir. Yönetilen bir dizinin bir alt sıralamakta yolu yoktur.  
  
 Birlikte çalışma Sıralayıcı kullanan **CoTaskMemAlloc** ve **CoTaskMemFree** ayırmak ve bellek almak için yöntemleri. Yönetilmeyen kodu tarafından gerçekleştirilen bellek ayırma de bu yöntemleri kullanmanız gerekir.  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a>COM dizileri geçirme  
 Tüm yönetilen dizi türleri yönetilen koddan yönetilmeyen koda geçirilebilir. Yönetilen türü ve uygulanan öznitelikleri bağlı olarak, dizi güvenli bir dizi veya bir C tarzı dizisi aşağıdaki tabloda gösterildiği gibi erişilebilir.  
  
|Yönetilen dizi türü|Olarak dışarı aktarıldı|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY**  **\<**  *türü***>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *türü* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Türü imzada sağlanır. RANK her zaman 1, alt sınır her zaman 0. Boyut her zaman çalışma zamanında denir.|  
|**ELEMENT_TYPE_ARRAY**  **\<**  *türü*  **>**   **\<**  *derece*  **>** [ **\<**  *sınırları*  **>** ]|**UnmanagedType.SafeArray (** *türü* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Türü, sıralama, sınırların imzada sağlanır. Boyut her zaman çalışma zamanında denir.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray (** *türü* **)**<br /><br /> Türü, derece, sınırları ve boyutu her zaman çalışma zamanında bilinir.|  
  
 OLE Otomasyonu'ndaki LPSTR veya LPWSTR içeren yapılarını diziler için ilgili bir sınırlama yoktur.  Bu nedenle, **dize** alanları olarak sıralanması zorunda **UnmanagedType.BSTR**. Aksi halde, bir özel durum oluşturulur.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 İçeren bir yöntemi, bir **ELEMENT_TYPE_SZARRAY** parametre (tek boyutlu dizi) bir .NET derleme için bir tür kitaplığı aktarılan, dizi parametresi dönüştürülür bir **SAFEARRAY** belirli bir türde. Dizi öğesi türleri için aynı dönüştürme kurallarını uygulayın. Yönetilen dizinin içeriğini yönetilen belleğe otomatik olarak kopyalandığı **SAFEARRAY**. Örneğin:  
  
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
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Güvenli diziler derecesini her zaman 1 ve alt sınır her zaman 0. Boyutu çalışma zamanında geçirilen yönetilen dizi boyutu tarafından belirlenir.  
  
 Diziye ayrıca bir C tarzı dizisi olarak kullanarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Örneğin:  
  
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
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Sıralayıcı dizi hazırlamak için gereken uzunluğu bilgileri olsa da, dizi uzunluğu genellikle Aranan uzunluğu iletmek için ayrı bir bağımsız değişken olarak geçirilir.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 İçeren bir yöntemi, bir **ELEMENT_TYPE_ARRAY** parametresi için bir tür kitaplığı .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **SAFEARRAY** belirli bir türde. Yönetilen dizinin içeriğini yönetilen belleğe otomatik olarak kopyalandığı **SAFEARRAY**. Örneğin:  
  
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
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Derece, boyutu ve güvenli diziler sınırları çalışma zamanında yönetilen dizi özelliklerine göre belirlenir.  
  
 Diziye ayrıca bir C tarzı dizisi olarak uygulayarak sıralanabilir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Örneğin:  
  
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
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 İç içe diziler sıralanamaz. Örneğin, aşağıdaki imzası ile verildiğinde bir hata oluşturur [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Yönetilen imza  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array >  
 İçeren bir yöntemi, bir <xref:System.Array?displayProperty=nameWithType> parametresi için bir tür kitaplığı .NET derlemesinden dışarı, dizi parametresi dönüştürülür bir **_Array** arabirimi. Yönetilen dizinin içeriğini yalnızca yöntemleri ve özellikleri erişilebilir **_Array** arabirimi. **System.Array** olarak sıralanabilir bir **SAFEARRAY** kullanarak <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği. Güvenli bir dizi olarak sıralanmış, dizi öğeleri çeşitleri hazırlanırlar. Örneğin:  
  
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
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Yapıları içindeki diziler  
 Yönetilmeyen yapılar katıştırılmış diziler içerebilir. Varsayılan olarak, bu katıştırılmış dizi alanları SAFEARRAY hazırlanırlar. Aşağıdaki örnekte, `s1` doğrudan yapısında kendisine ayrılan katıştırılmış bir dizidir.  
  
#### <a name="unmanaged-representation"></a>Yönetilmeyen gösterimi  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Diziler sıralanmış olarak <xref:System.Runtime.InteropServices.UnmanagedType>, ayarlamanızı gerektiren <xref:System.Runtime.InteropServices.MarshalAsAttribute> alan. Boyut yalnızca bir sabit değer olarak ayarlayabilirsiniz. Aşağıdaki kod karşılık gelen yönetilen tanımını gösterir `MyStruct`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varsayılan Hazırlama Davranışı](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Tek yönlü öznitelikleri](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopyalama ve Sabitleme](../../../docs/framework/interop/copying-and-pinning.md)
