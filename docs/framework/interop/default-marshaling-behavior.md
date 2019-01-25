---
title: Varsayılan Hazırlama Davranışı
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587ae32c27a3c779f5f2e4f27bf521e2ca557106
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689006"
---
# <a name="default-marshaling-behavior"></a>Varsayılan Hazırlama Davranışı
Birlikte çalışma hazırlama kurallar arasında yönetilen ve yönetilmeyen bellek geçerken yöntem parametreleri ile ilişkili verileri nasıl davranacağını bu dikte çalışır. Yerleşik kurallar bir çağrılan geçirilen verileri değiştirebilir ve bu değişiklikleri çağırana döndürmesi ve performans iyileştirmelerini sağlayıp altında Sıralayıcı koşulda veri türü dönüşümleri olarak sıralama gibi etkinlikler denetler.  
  
 Bu bölümde, birlikte çalışma hazırlama hizmet varsayılan davranış özelliklerini tanımlar. Bu, diziler, Boole türleri, char türü, temsilciler, sınıflar, nesneleri, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgi sunar.  
  
> [!NOTE]
>  Genel türlerin sıralama desteklenmiyor. Daha fazla bilgi edinmek, [birlikte çalışma genel türleri kullanarak](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Birlikte çalışma sıralayıcısı ile bellek yönetimi  
 Birlikte çalışma sıralayıcısı, yönetilmeyen kod tarafından ayrılan bellek boşaltmak her zaman çalışır. Bu davranışı COM bellek yönetimi kuralları ile uyumludur, ancak yerel C++ yöneten kuralları farklıdır.  
  
 (Hiçbir bellek serbest bırakma) yerel C++ davranışını düşünüyorsanız karışıklık çıkabilir zaman platformunu kullanarak çağırmak, hangi otomatik olarak işaretçiler için belleği serbest bırakır. Örneğin, aşağıdaki yönetilmeyen C++ DLL'den metodunu otomatik olarak herhangi bir bellek boş değil.  
  
### <a name="unmanaged-signature"></a>Yönetilmeyen imzası  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Ancak, her bir platform çağırma gibi prototip yöntemi tanımlarsanız, değiştirin **BSTR** tür bir <xref:System.String> yazın ve arama `MethodOne`, ortak dil çalışma zamanı ücretsiz dener `b` iki kez. Kullanarak da hazırlama davranışını değiştirebilirsiniz <xref:System.IntPtr> türleri yerine **dize** türleri.  
  
 Çalışma zamanı, her zaman kullanır **CoTaskMemFree** belleği boşaltmak için yöntemi. Birlikte çalıştığınız bellek ile ayrılıp değil **CoTaskMemAlloc** yöntemini kullanmalıdır bir **IntPtr** ve uygun yöntemi kullanarak el ile bellek. Benzer şekilde, otomatik bellek boşaltma burada bellek hiçbir zaman bellekten kaldırılmalıdır durumlarda, tür kaçınabilirsiniz olarak kullanırken **GetCommandLine** işlevi Kernel32.dll dosyasından çekirdek bellek için bir işaretçi döndürür. El ile bellek serbest bırakma hakkında daha fazla bilgi için bkz [arabellekler örneği](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Sınıflar için varsayılan sıralama  
 Sınıflar yalnızca COM birlikte çalışma tarafından sıralanabilir ve her zaman arabirimleri olarak sıralanmış. Bazı durumlarda, sınıf hazırlamak için kullanılan arabirimi sınıf arabirimi bilinir. Tercih ettiğiniz bir arabirime sahip sınıf arabirimi geçersiz kılma hakkında daha fazla bilgi için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>COM sınıflarına geçirme  
 Yönetilen bir sınıf için COM geçirildiğinde, birlikte çalışma sıralayıcısı, otomatik olarak bir COM Ara sunucu ile sınıfa sarmalar ve COM yöntem çağrısına Ara sunucu tarafından üretilen sınıf arabirimi geçirir. Proxy, ardından tüm çağrılarda sınıf arabirimi yönetilen nesnesine atar. Proxy sınıfı tarafından açıkça uygulanmaz ve diğer arabirimleri de sunar. Proxy otomatik olarak arabirimlerini gibi uygular **IUnknown** ve **IDispatch** adına sınıfı.  
  
### <a name="passing-classes-to-net-code"></a>.NET kodu sınıflarına geçirme  
 COM yöntemi bağımsız değişken olarak coclass'ları genellikle kullanılmaz Bunun yerine, varsayılan bir arabirim yerine coclass'ı genellikle geçirilir.  
  
 Bir arabirim yönetilen koda geçirildiğinde, doğru sarmalayıcı arabirimiyle sarmalama ve sarmalayıcı yönetilen yönteme geçirmek için birlikte çalışma sıralayıcısı sorumludur. Belirleme kullanmak için hangi sarmalayıcı zor olabilir. Her bir COM nesnesinin örneği benzersiz, tek bir sarmalayıcı kaç arabirimleri ne olursa olsun nesne uygulayan sahiptir. Örneğin, yalnızca bir sarmalayıcı beş farklı arabirimleri uygulayan tek bir COM nesnesi vardır. Aynı kapsayıcı tüm beş arabirimleri kullanıma sunar. İki örneğini COM nesnesi oluşturulur, ardından sarmalayıcı iki örneği oluşturulur.  
  
 Sarmalayıcı ömrü boyunca aynı türde korumak, nesne tarafından sunulan bir arabirim Sıralayıcı geçirilen ilk kez doğru sarmalayıcı birlikte çalışma sıralayıcısı tanımlamanız gerekir. Sıralayıcı nesne uygulayan arabirimlerinden birini bakarak nesneyi tanımlar.  
  
 Örneğin, Sıralayıcı sınıfı sarmalayıcı yönetilen koda geçirildi arabirimi sarmalamak için kullanılması gerektiğini belirler. Arabirimi Sıralayıcı ilk geçirildiğinde, Sıralayıcı arabirimi bilinen bir nesneden kullanıma sunulacak olup olmadığını denetler. Bu denetim, iki durumda gerçekleşir:  
  
-   Bir arabirim için COM başka bir yerde geçirildi başka bir yönetilen nesne tarafından uygulanır. Sıralayıcı yönetilen nesneler tarafından kullanıma sunulan arabirimler kolayca tanımlayabilirsiniz ve arabirim uygulamasını sağlayan yönetilen bir nesne ile eşleşecek şekilde edebilir. Yönetilen Nesne sonra yöntemine geçirilir ve hiçbir sarmalayıcı gereklidir.  
  
-   Zaten sarmalanmış bir nesne arabirimi uygular. Durumun bu olup olmadığını belirlemek için nesne için sıralayıcı sorgular, **IUnknown** arabirim ve döndürülen arabirim sarmalanır ve diğer nesnelerin arabirimlere karşılaştırır. Arabirimi, başka bir sarmalayıcı aynı olduğunda, nesneler aynı kimliğe sahip ve mevcut sarmalayıcı yöntemine geçirilir.  
  
 Sıralayıcı, bilinen bir nesneden bir arabirim değil, şunları yapar:  
  
1.  Nesne için sıralayıcı sorgular **IProvideClassInfo2** arabirimi. Sağlanırsa, döndürülen CLSID Sıralayıcı kullanan **IProvideClassInfo2.GetGUID** arayüzü sağlama coclass'ı tanımlamak için. Derleme önceden kayıtlı olup olmadığını CLSID ile kapsayıcı kayıt defterinden Sıralayıcı bulabilirsiniz.  
  
2.  Arabirim için sıralayıcı sorgular **Iprovideclassınfo** arabirimi. Sağladıysanız Sıralayıcı kullanan **ITypeInfo** döndürüldüğü **IProvideClassInfo.GetClassinfo** arabirimi gösterme sınıfı CLSID değeri belirlemek için. Sıralayıcı CLSID sarmalayıcı için meta verileri bulmak için kullanabilirsiniz.  
  
3.  Sıralayıcı hala sınıfı tanımlanamıyor, adlı bir genel sarmalayıcı sınıf arabirimi sarmalar **System.comobject'e**.  
  
## <a name="default-marshaling-for-delegates"></a>Temsilciler için varsayılan sıralama  
 Yönetilen bir temsilci, bir COM arabirimi veya çağıran mekanizmasına dayalı bir işlev işaretçisi olarak sıralanır:  
  
-   İçin platform çağırma, varsayılan olarak bir temsilci bir yönetilmeyen işlev işaretçisi sıralanır.  
  
-   COM birlikte çalışması için bir temsilci türü bir COM arabirimi sıralanır **_Delegate** varsayılan olarak. **_Delegate** arabirimi Mscorlib.tlb tür kitaplığında tanımlanan ve içeren <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> başvuran temsilci yöntemi çağırma olanak tanıyan yöntemi.  
  
 Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçeneklerini gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi değerleri sıralama temsil eder.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Bir yönetilmeyen işlev işaretçisi.|  
|**UnmanagedType.Interface**|Bir arabirim türü **_Delegate**Mscorlib.tlb içinde tanımlanan gibi.|  
  
 Aşağıdaki kod örneği göz önünde bulundurun yöntemlerinin `DelegateTestInterface` bir COM tür kitaplığı dışarı aktarılır. Yalnızca temsilci bildirimi ile işaretlenen **ref** (veya **ByRef**) anahtar sözcüğü In/Out parametresi geçirilir.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a>Tür kitaplığı gösterimi  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Yalnızca diğer herhangi bir yönetilmeyen bir işleve işaretçi başvurusu olarak, bir işlev işaretçisi başvurusunun.  

Bu örnekte, iki temsilci olarak sıralandığı zaman <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, sonuç bir `int` ve işaretçi bir `int`. Temsilci türleri başvuruya çünkü `int` burada için bir void bir işaretçi temsil eder (`void*`), bellekte temsilci adresini olduğu. Diğer bir deyişle, bu tarihten sonra 32 bit Windows sistemlerine sonucudur `int` burada işlev işaretçisi boyutunu temsil eder.

> [!NOTE]
>  İşlev işaretçisi tarafından yönetilmeyen kod tutulan, yönetilen bir temsilci bir başvuru ortak dil çalışma zamanı, çöp toplama yönetilen bir nesnede gerçekleştirmesini engellemez.  
  
 Örneğin, aşağıdaki kodu yanlış olduğundan başvuru `cb` nesnesi, geçirilen `SetChangeHandler` yöntemi saklamaz `cb` ömrünü dışında tutma `Test` yöntemi. Bir kez `cb` çöp olarak toplanacak nesnedir, işlev işaretçisi geçirilen `SetChangeHandler` artık geçerli değil.  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 Beklenmeyen bir çöp toplama için dengelemek için çağıranın emin olmanız gerekir `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesne Canlı tutulur. İsteğe bağlı olarak, yönetilen kod işlev işaretçisi artık, aşağıdaki örnekte gösterildiği gibi gerekli olduğunda bildirim yönetilmeyen kod olabilir.  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a>Değer türleri için varsayılan sıralama  
 Tamsayı ve kayan nokta numaraları gibi birçok değer türleri [blittable](blittable-and-non-blittable-types.md) ve hazırlama gerektirmez. Diğer [kopyalanamaz](blittable-and-non-blittable-types.md) türleri yönetilen ve yönetilmeyen bellekte farklı temsilleri olabilir ve hazırlama gerektirir. Yine de diğer türler, açık birlikte çalışabilirlik sınırında biçimlendirme gerektirir.  
  
 Bu konu, biçimlendirilen değer türleri üzerinde izleme bilgileri sağlar:  
  
-   [Değer türleri platformunda kullanılan çağırma](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [COM birlikte çalışma kullanılan değer türleri](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 Biçimlendirilmiş türlerini açıklayan ek olarak, bu konu tanımlar [sistem değer türleri](#cpcondefaultmarshalingforvaluetypesanchor1) olağan dışı hazırlama davranışı vardır.  
  
 Biçimlendirilmiş bir tür üyelerini bellekte düzenini açıkça denetleyen bilgilerini içeren karmaşık bir türdür. Üye düzeni bilgilerini kullanarak sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği. Düzeni aşağıdakilerden biri olabilir <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değerleri:  
  
-   **LayoutKind.Automatic**  
  
     Ortak dil çalışma zamanı verimliliği için türün üyeleri yeniden sıralamak ücretsiz olduğunu gösterir. Ancak, yönetilmeyen koda bir değer türü geçirildiğinde, üyeleri düzenini öngörülebilir olur. Böyle bir yapı otomatik olarak hazırlamak girişimi, bir özel durum neden olur.  
  
-   **LayoutKind.Sequential**  
  
     Yönetilen tür tanımında göründükleri sırayla yönetilmeyen bellekte düzenlendiği için türün üyeleri olduğunu gösterir.  
  
-   **LayoutKind.Explicit**  
  
     Üyeleri göre düzenlenmiştir gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> her alanı ile sağlanan.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a>Değer türleri platformunda kullanılan çağırma  
 Aşağıdaki örnekte `Point` ve `Rect` türler, üye düzen bilgilerini sağlamak kullanarak **StructLayoutAttribute**.  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 Bu biçimlendirilmiş türleri için yönetilmeyen kod sıralandığı zaman C stili yapıları olarak sıralanmış. Bu yapı bağımsız değişkenlere sahip bir yönetilmeyen API çağırmak için kolay bir yol sağlar. Örneğin, `POINT` ve `RECT` yapıları için Microsoft Win32 API geçirilebilir **PtInRect** gibi işlev:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Yapıları geçirebilirsiniz platformu kullanarak çağırma tanımı:  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 `Rect` Değer türü yönetilmeyen API için bir işaretçi bekliyor olduğundan başvuru ile geçirilmelidir bir `RECT` işleve geçirilecek. `Point` Yönetilmeyen API beklediği değer türü değere göre geçirilir `POINT` yığında geçirilecek. Bu fark çok önemlidir. Başvuruları yönetilmeyen koda işaretçileri geçirilir. Değerleri, yönetilmeyen koda yığına geçirilir.  
  
> [!NOTE]
>  Biçimlendirilmiş bir tür bir yapı sıralanır, alanlar yalnızca türü içinde erişilebilir. Tür yöntemleri, özellikleri veya olayları sahipse, yönetilmeyen koddan erişilemez.  
  
 Sabit üye Düzen sağlanan sınıfları ayrıca yönetilmeyen koda C stili yapıları olarak sıralanabilir. Bir sınıf üyesine ilişkin düzen bilgilerini de ile sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği. Değer türleri ile arasındaki temel fark, bu da düzenin sabit ve sabit biçimli sınıflar, yönetilmeyen koda sıralanmış yoludur. Değer türleri (yığın üzerinde) değere göre geçirilir ve sonuç olarak türün üyeleri için Aranan tarafından yapılan değişiklikler arayan tarafından görülmez. Başvuru türleri (bir başvuru türü yığın üzerine geçirilir) başvuruyla geçirilir; Sonuç olarak, bir tür blittable-tür üyelerine Aranan tarafından yapılan tüm değişiklikler arayan tarafından görülür.  
  
> [!NOTE]
>  Bir başvuru türü kopyalanamaz türlerin üyelerini varsa, dönüştürme iki kez gereklidir: ne zaman bir bağımsız değişken geçirilir yönetilmeyen yan ve ikinci ilk kez zaman çağrısından dönüşte. Aranan tarafından yapılan değişiklikleri görmek çağıranın istiyorsa, bu nedenle eklenen yükü, In/Out parametreleri açıkça bir bağımsız değişken uygulanması gerekir.  
  
 Aşağıdaki örnekte, `SystemTime` sınıf üyesi sıralı düzene sahip ve Win32 API için geçirilen **GetSystemTime** işlevi.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 **GetSystemTime** işlevi şu şekilde tanımlanır:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Eşdeğer platform çağırma tanımı **GetSystemTime** aşağıdaki gibidir:  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 Dikkat `SystemTime` çünkü bağımsız değişkeni bir başvuru bağımsız değişkeni değil yazılan `SystemTime` sınıfı, bir değer türü değil. Değer türlerinin aksine, sınıflar her zaman başvuruyla geçirildi.  
  
 Aşağıdaki kod örneği farklı bir gösterir `Point` adlı yöntemi içeren sınıf `SetXY`. Ardışık Düzen türüne sahip olduğundan, yönetilmeyen kod için geçirilen ve bir yapı sıralanır. Ancak, `SetXY` üye yönetilmeyen koddan çağrılabilir değil nesne başvuru tarafından geçirilmediğine olsa bile.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a>COM birlikte çalışma kullanılan değer türleri  
 Biçimlendirilmiş türleri COM birlikte çalışma yöntem çağrıları için de geçirilebilir. Aslında, bir tür kitaplığına dışarı aktardığınızda, değer türleri otomatik olarak yapılarını dönüştürülür. Aşağıdaki örnekte gösterildiği gibi `Point` değer türü olur (typedef) adlı bir tür tanımı `Point`. Tüm başvuruları `Point` tür kitaplığı içindeki başka bir yerde değer türü ile değiştirilir `Point` typedef.  
  
 **Tür kitaplığı gösterimi**  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 Değerleri ve platform başvuruları hazırlamak için kullanılan aynı kurallara çağrılarını çağırmak COM arabirimleri sıralama kullanılır. Örneğin, örneği `Point` değer türü, COM, .NET Framework'den geçirilir `Point` değere göre geçirilir. Varsa `Point` değer türü bir işaretçi, başvuru tarafından geçirilen bir `Point` yığına geçirilir. Birlikte çalışma sıralayıcısı, yüksek düzeyde yöneltme desteklemez (**noktası** \* \*) herhangi bir yönde.  
  
> [!NOTE]
>  Yapıları sahip <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değeri **açık** dışarı aktarılan tür kitaplığı açık bir düzen express olamaz COM birlikte kullanılamaz.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>Sistem değer türleri  
 <xref:System> Ad alanı olan çalışma zamanı temel türleri paketlenmiş biçiminde temsil eden birden çok değer türleri. Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısı temsil eder, kutulanmış biçiminde **ELEMENT_TYPE_I4**. Biçimlendirilmiş diğer türler gibi bu tür yapıları olarak hazırlama yerine, bunları bunlar kutusunda ilkel türler olarak aynı şekilde hazırlama. **System.Int32** olarak bu nedenle sıralanmış **ELEMENT_TYPE_I4** yerine tek bir üye türü içeren bir yapıya olarak **uzun**. Aşağıdaki tabloda değer türlerinin bir listesini içeren **sistem** paketlenmiş temsillerini ilkel türleri olan ad alanı.  
  
|Sistem değer türü|Öğe türü|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**ELEMENT_TYPE_BOOLEAN**|  
|<xref:System.SByte?displayProperty=nameWithType>|**ELEMENT_TYPE_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**ELEMENT_TYPE_UI1**|  
|<xref:System.Char?displayProperty=nameWithType>|**ELEMENT_TYPE_CHAR**|  
|<xref:System.Int16?displayProperty=nameWithType>|**ELEMENT_TYPE_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**ELEMENT_TYPE_U2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**ELEMENT_TYPE_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**ELEMENT_TYPE_U4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**ELEMENT_TYPE_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**ELEMENT_TYPE_U8**|  
|<xref:System.Single?displayProperty=nameWithType>|**ELEMENT_TYPE_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**ELEMENT_TYPE_R8**|  
|<xref:System.String?displayProperty=nameWithType>|**ELEMENT_TYPE_STRING**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_I**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_U**|  
  
 Başka bir değer türleri içinde **sistem** ad alanı farklı bir şekilde işlenir. Sıralayıcı, yönetilmeyen kod için bu tür tanınmış biçimler olduğundan, bunları hazırlama için özel kurallar vardır. Özel değer türleri aşağıdaki tabloda **sistem** ad alanı, bunlar için hazırlanır yönetilmeyen tür yanı sıra.  
  
|Sistem değer türü|IDL türü|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**TARİH**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**ONDALIK**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Aşağıdaki kod, yönetilmeyen türlerinin tanımını göstermektedir **tarih**, **GUID**, **ondalık**, ve **OLE_COLOR** Stdole2 türü Kitaplığı.  
  
#### <a name="type-library-representation"></a>Tür kitaplığı gösterimi  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 Aşağıdaki kod, karşılık gelen tanımları yönetilen gösterir `IValueTypes` arabirimi.  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a>Tür kitaplığı gösterimi  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)
- [Kopyalama ve Sabitleme](copying-and-pinning.md)
- [Diziler için Varsayılan Hazırlama](default-marshaling-for-arrays.md)
- [Nesneler için Varsayılan Hazırlama](default-marshaling-for-objects.md)
- [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)
