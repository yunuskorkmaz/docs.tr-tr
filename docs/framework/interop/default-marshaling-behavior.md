---
title: Varsayılan Sıralama Davranışı
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 18282d14540027e4fae4fe152d3867ad8c223c37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181477"
---
# <a name="default-marshaling-behavior"></a>Varsayılan Sıralama Davranışı
Interop marshaling, yöntem parametreleri ile ilişkili verilerin yönetilen ve yönetilmeyen bellekler arasında geçerken nasıl çalıştığını belirleyen kurallar üzerinde çalışır. Bu yerleşik kurallar, veri türü dönüşümleri, bir callee'nin ona aktarılan verileri değiştirip değiştiremeyeceği ve bu değişiklikleri arayana döndürüp döndüremeyeceği ve mareşalin performans optimizasyonları sağladığı koşullar altında bu tür etkinliklerin denetlenmesini sağlar.  
  
 Bu bölümde, interop mareşallik hizmetinin varsayılan davranış özellikleri tanımnıla. Bu diziler, Boolean türleri, char türleri, temsilciler, sınıflar, nesneler, dizeleri ve yapıları mareşal hakkında ayrıntılı bilgi sunar.  
  
> [!NOTE]
> Genel türlerin mareşalliği desteklenmez. Daha fazla bilgi için bkz: [Genel Türleri Kullanarak Ara Çalışma.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Interop mareşal ile bellek yönetimi  
 Interop mareşal her zaman yönetilmeyen kod tarafından ayrılan belleği serbest etmeye çalışır. Bu davranış, COM bellek yönetimi kurallarına uygundur, ancak yerel C++'ı yöneten kurallardan farklıdır.  
  
 Platform çağrısı nı kullanırken yerel C++ davranışını (bellek serbestiyeti yok) tahmin ederseniz, bu da işaretçiler için belleği otomatik olarak serbest bırakır. Örneğin, bir C++ DLL'den aşağıdaki yönetilmeyen yöntemi çağırmak otomatik olarak herhangi bir belleği serbest bırakmaz.  
  
### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Ancak, yöntemi bir platform çağrısı prototipi olarak tanımlarsanız, <xref:System.String> her **BSTR** türünü bir türle değiştirin ve ortak dil çalışma zamanı denemelerini iki kez ücretsiz `MethodOne` `b` olarak arayın. **String** türleri yerine türleri kullanarak <xref:System.IntPtr> mareşal davranışını değiştirebilirsiniz.  
  
 Çalışma süresi her zaman ücretsiz bellek **için CoTaskMemFree** yöntemini kullanır. Çalıştığınız bellek **CoTaskMemAlloc** yöntemiyle ayrılmadıysa, bir **IntPtr** kullanmalı ve uygun yöntemi kullanarak belleği el ile serbest bilmelidir. Benzer şekilde, kernel32.dll'den **GetCommandLine** işlevini kullanırken olduğu gibi belleğin asla serbest bırakılmaması gereken durumlarda otomatik bellek serbest bırakMasını önleyebilirsiniz. Belleği el ile serbest etme yle ilgili ayrıntılar için [Arabellek Örneği'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))bakın.  
  
## <a name="default-marshaling-for-classes"></a>Sınıflar için varsayılan mareşalleme  
 Sınıflar yalnızca COM interop tarafından marshaled olabilir ve her zaman arayüz olarak marshaled vardır. Bazı durumlarda sınıfı mareşallemek için kullanılan arabirim sınıf arabirimi olarak bilinir. Seçtiğiniz bir arabirimile sınıf arabirimini geçersiz kılma hakkında bilgi [için](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)bkz.  
  
### <a name="passing-classes-to-com"></a>Sınıfları COM'a Geçirme  
 Yönetilen bir sınıf COM'a geçirildiğinde, interop mareşal otomatik olarak bir COM proxy ile sınıfı sarar ve proxy tarafından üretilen sınıf arabirimini COM yöntemi çağrısına geçirir. Proxy daha sonra sınıf arabirimindeki tüm çağrıları yönetilen nesneye geri verir. Proxy, sınıf tarafından açıkça uygulanmayan diğer arabirimleri de ortaya çıkarır. Proxy, sınıf adına **IUnknown** ve **IDispatch** gibi arabirimleri otomatik olarak uygular.  
  
### <a name="passing-classes-to-net-code"></a>Sınıfları .NET Koduna Geçirme  
 Ortak sınıflar genellikle COM'da yöntem bağımsız değişkenleri olarak kullanılmaz. Bunun yerine, varsayılan arabirim genellikle ortak sınıfın yerine geçirilir.  
  
 Bir arabirim yönetilen koda geçirildiğinde, interop mareşal doğru sarıcı ile arabirimi sarma ve yönetilen yönteme sarıcı geçmekten sorumludur. Hangi sarıcının kullanılacağını belirlemek zor olabilir. Com nesnesinin her örneğinde, nesne nin kaç arabirimi uygularsa uygulanın, tek, benzersiz bir sarıcı bulunur. Örneğin, beş farklı arabirimi uygulayan tek bir COM nesnesi yalnızca bir sarıcıya sahiptir. Aynı sarıcı beş arabirimi de ortaya çıkarır. COM nesnesinin iki örneği oluşturulursa, sarıcının iki örneği oluşturulur.  
  
 Sarılayıcının ömrü boyunca aynı türü koruyabilmesi için, interop mareşalinin nesne tarafından açığa çıkarılan bir arabirim mareşalden ilk kez doğru sarılayıcıyı tanımlaması gerekir. Mareşal, nesnenin uyguladığı arabirimlerden birine bakarak nesneyi tanımlar.  
  
 Örneğin, mareşal, yönetilen koda geçirilen arabirimi sarmak için sınıf sarıcının kullanılması gerektiğini belirler. Arabirim mareşalden ilk geçirildiğinde, mareşal arabirimin bilinen bir nesneden gelip gelmediğini denetler. Bu denetim iki durumda oluşur:  
  
- Bir arabirim, başka bir yerde COM'a geçirilen başka bir yönetilen nesne tarafından uygulanMaktadır. Marshaler, yönetilen nesneler tarafından maruz kalan arabirimleri kolayca tanımlayabilir ve arabirimi uygulamayı sağlayan yönetilen nesneyle eşleşebilir. Yönetilen nesne daha sonra yönteme geçirilir ve sarıcı gerekmez.  
  
- Zaten sarılmış bir nesne arabirimi uyguluyor. Bu durumda olup olmadığını belirlemek için, mareşal **nesneyi IUnknown** arabirimi için sorgular ve döndürülen arabirimi zaten sarılmış olan diğer nesnelerin arabirimlerinin karşılaştırır. Arabirim başka bir sarıcıyla aynıysa, nesneler aynı kimliğe sahiptir ve varolan sarıcı yönteme geçirilir.  
  
 Bir arabirim bilinen bir nesneden değilse, mareşal aşağıdakileri yapar:  
  
1. Mareşal, **iProvideClassInfo2** arabirimi için nesneyi sorgular. Sağlanırsa, mareşal clsid **iProvideClassInfo2.GetGUID** gelen arayüz sağlayan coclass tanımlamak için döndürülür kullanır. CLSID ile, montaj daha önce kaydedilmişse, mareşal ambalajı kayıt defterinden bulabilir.  
  
2. Mareşal, **IProvideClassInfo** arabiriminin arabirimini sorgular. Sağlanırsa, mareşal **iProvideClassInfo.GetClassinfo** gelen **iTypeInfo** sınıfının CLSID arayüzü açığa belirlemek için döndürülür kullanır. Mareşal, sarıcının meta verilerini bulmak için CLSID'yi kullanabilir.  
  
3. Mareşal hala sınıfı tanımlayamıyorsa, **system.__ComObject**adlı genel bir sarmalayıcı sınıfı ile arabirimi sarar.  
  
## <a name="default-marshaling-for-delegates"></a>Temsilciler için varsayılan mareşalleme  
 Yönetilen bir temsilci, arama mekanizmasına bağlı olarak COM arabirimi veya işlev işaretçisi olarak sıralanır:  
  
- Platform çağrısı için, bir temsilci varsayılan olarak yönetilmeyen bir işlev işaretçisi olarak marshaled.  
  
- COM interop için, varsayılan olarak _Delegate **tür** com arabirimi olarak bir temsilci marshaled. **_Delegate** arabirimi Mscorlib.tlb türü kitaplığında <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> tanımlanır ve temsilcinin başvuruladığı yöntemi aramanızı sağlayan yöntemi içerir.  
  
 Aşağıdaki tablo, yönetilen temsilci veri türü için mareşal seçenekleri gösterir. Öznitelik, <xref:System.Runtime.InteropServices.MarshalAsAttribute> mareşal temsilcilerine birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.  
  
|Numaralandırma türü|Yönetilmeyen biçimin açıklaması|  
|----------------------|-------------------------------------|  
|**YönetilmeyenType.FunctionPtr**|Yönetilmeyen bir işlev işaretçisi.|  
|**YönetilmeyenType.Interface**|Mscorlib.tlb'de tanımlandığı gibi tip **_Delegate**arabirimi.|  
  
 Yöntemlerinin COM türü kitaplığına `DelegateTestInterface` dışa aktarıldığı aşağıdaki örnek kodu göz önünde bulundurun. Yalnızca **ref** (veya **ByRef)** anahtar sözcüğüyle işaretlenmiş temsilcilerin Giriş/Çıkış parametreleri olarak geçirildiğine dikkat edin.  
  
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
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Diğer yönetilmeyen işlev işaretçisi de reference'dan arındırılmış olabilir.  

Bu örnekte, iki temsilci olarak <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>marshaled olduğunda , `int` sonuç bir `int`ve bir işaretçi . Temsilci türleri marshaled olduğundan, `int` burada bellekte temsilcinin adresi olan bir boşluk için`void*`bir işaretçi temsil eder. Başka bir deyişle, burada işlev işaretçisinin boyutunu `int` temsil ettiği için, bu sonuç 32 bit Windows sistemlerine özgüdür.

> [!NOTE]
> İşlemeyen kod tarafından tutulan yönetilen bir temsilciye işlev işaretçisine yapılan başvuru, ortak dil çalışma zamanının yönetilen nesne üzerinde çöp toplama gerçekleştirmesini engellemez.  
  
 `cb` Örneğin, `SetChangeHandler` yönteme aktarılan nesneye yapılan başvuru `cb` `Test` yöntemin ömrü dışında canlı tutmadığından, aşağıdaki kod yanlıştır. `cb` Nesne çöp toplandıktan sonra, geçirilen `SetChangeHandler` işlev işaretçisi artık geçerli değildir.  
  
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
  
 Beklenmeyen çöp toplamayı telafi etmek için, `cb` arayan, yönetilmeyen işlev işaretçisi kullanıldığı sürece nesnenin canlı tutulduğundan emin olmalıdır. İsteğe bağlı olarak, aşağıdaki örnekte görüldüğü gibi, işlev işaretçisi artık gerekli olmadığında, yönetilmeyen kodun yönetilen kodu bildirmesini sağlayabilirsiniz.  
  
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
  
## <a name="default-marshaling-for-value-types"></a>Değer türleri için varsayılan mareşalleme  
 Tamsayılar ve kayan nokta sayıları gibi çoğu değer türü [blittable](blittable-and-non-blittable-types.md) ve mareşallik gerektirmez. Diğer [blittable olmayan](blittable-and-non-blittable-types.md) türleri yönetilen ve yönetilmeyen bellekfarklı gösterimleri var ve mareşalgerektirir. Yine de diğer türler, işlem ler arası sınır boyunca açık biçimlendirme gerektirir.  
  
 Bu bölümde aşağıdaki biçimlendirilmiş değer türleri hakkında bilgi verilmektedir:  
  
- [Platform Çağırmada Kullanılan Değer Türleri](#value-types-used-in-platform-invoke)  
  
- [COM Interop'ta Kullanılan Değer Türleri](#value-types-used-in-com-interop)  
  
 Biçimlendirilmiş türleri açıklamaya ek olarak, bu konu olağandışı mareşal davranışı olan [Sistem Değer Türlerini](#system-value-types) tanımlar.  
  
 Biçimlendirilmiş tür, bellekteki üyelerinin düzenini açıkça denetleyen bilgiler içeren karmaşık bir türdür. Üye düzeni bilgileri öznitelik <xref:System.Runtime.InteropServices.StructLayoutAttribute> kullanılarak sağlanır. Düzen aşağıdaki <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değerlerinden biri olabilir:  
  
- **LayoutKind.Otomatik**  
  
     Ortak dil çalışma zamanının, türdeki üyeleri verimlilik için yeniden sıralamak için ücretsiz olduğunu gösterir. Ancak, bir değer türü yönetilmeyen koda geçirildiğinde, üyelerin düzeni tahmin edilebilir. Böyle bir yapıyı mareşalleme girişimi otomatik olarak bir özel durum neden olur.  
  
- **LayoutKind.Sequential**  
  
     Türün üyelerinin yönetilen tür tanımında göründükleri aynı sırada yönetilmeyen bellekte ortaya konacaklarını gösterir.  
  
- **LayoutKind.Explicit**  
  
     Üyelerin her alanla <xref:System.Runtime.InteropServices.FieldOffsetAttribute> birlikte verilen alana göre yerleştirildiğini gösterir.  
  
### <a name="value-types-used-in-platform-invoke"></a>Platform Çağırmada Kullanılan Değer Türleri  
 Aşağıdaki örnekte `Point` ve `Rect` türleri **StructLayoutAttribute**kullanarak üye düzeni bilgileri sağlar.  
  
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
  
 Yönetilmeyen koda marshaled zaman, bu biçimlendirilmiş türleri C tarzı yapılar olarak marshaled. Bu, yapı bağımsız değişkenleri olan yönetilmeyen bir API'yi çağırmanın kolay bir yolunu sağlar. Örneğin, ve `POINT` `RECT` yapıları Aşağıdaki gibi Microsoft Windows API **PtInRect** işlevine geçirilebilir:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Yapıları aşağıdaki platform çağırma tanımını kullanarak geçirebilirsiniz:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 Yönetilmeyen API bir işaretçi `Rect` `RECT` işlevine geçirilecek bekliyor, çünkü değer türü başvuru tarafından geçirilmelidir. Yönetilmeyen API yığında `Point` `POINT` geçirilmeyi beklediğinden, değer türü değere göre geçirilir. Bu ince fark çok önemlidir. Başvurular yönetilmeyen koda işaretçi olarak geçirilir. Değerler yığındaki yönetilmeyen koda aktarılır.  
  
> [!NOTE]
> Biçimlendirilmiş bir tür yapı olarak sıralandığında, yalnızca tür içindeki alanlara erişilebilir. Türde yöntemler, özellikler veya olaylar varsa, bunlara yönetilmeyen koddan erişilemezler.  
  
 Sınıflar, sabit üye düzenine sahip olmaları koşuluyla, yönetilmeyen koda C stili yapılar olarak da marshaled olabilir. Bir sınıfın üye düzeni bilgileri de <xref:System.Runtime.InteropServices.StructLayoutAttribute> öznitelik ile sağlanır. Sabit düzene sahip değer türleri ile sabit düzene sahip sınıflar arasındaki temel fark, bunların yönetilmeyen koda marshaled yoludur. Değer türleri değere göre geçirilir (yığında) ve dolayısıyla callee tarafından türün üyelerine yapılan değişiklikler arayan tarafından görülmez. Başvuru türleri başvuru ile geçirilir (yığında türe bir başvuru geçirilir); sonuç olarak, callee tarafından bir türün blittable türünde üyeler için yapılan tüm değişiklikler arayan tarafından görülür.  
  
> [!NOTE]
> Bir başvuru türünde blittable olmayan türlerin üyeleri varsa, dönüştürme iki kez gereklidir: ilk kez bir bağımsız değişken yönetilmeyen tarafa geçirildiğinde ve ikinci kez çağrıdan dönüşte. Eklenen bu ek yükü nedeniyle, arayan callee tarafından yapılan değişiklikleri görmek istiyorsa, In/Out parametreleri açıkça bir bağımsız değişkene uygulanmalıdır.  
  
 Aşağıdaki örnekte, `SystemTime` sınıf sıralı üye düzeni vardır ve Windows API **GetSystemTime** işlevine geçirilebilir.  
  
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
  
 **GetSystemTime** işlevi aşağıdaki gibi tanımlanır:  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 **GetSystemTime** için eşdeğer platform çağırma tanımı aşağıdaki gibidir:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 `SystemTime` Bir sınıf değil, bir değer türü `SystemTime` olduğundan bağımsız değişkenin başvuru bağımsız değişkeni olarak yazıldığına dikkat edin. Değer türlerinden farklı olarak, sınıflar her zaman başvuru ile geçirilir.  
  
 Aşağıdaki kod örneği, `Point` .. `SetXY` Tür sıralı düzene sahip olduğundan, yönetilmeyen koda geçirilebilir ve bir yapı olarak marshaled. Ancak, `SetXY` nesne başvuru tarafından geçirilse bile, üye yönetilmeyen koddan çağrılabilir değildir.  
  
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
  
### <a name="value-types-used-in-com-interop"></a>COM Interop'ta Kullanılan Değer Türleri  
 Biçimlendirilmiş türler com interop yöntemi çağrılarına da aktarılabilir. Aslında, bir tür kitaplığına dışa aktarıldığında, değer türleri otomatik olarak yapılara dönüştürülür. Aşağıdaki örnekte görüldüğü `Point` gibi, değer türü bir tür tanımı `Point`(typedef) adı ile olur. Tür kitaplığındaki `Point` değer türüne yapılan tüm başvurular `Point` typedef ile değiştirilir.  
  
 **Tür kitaplığı gösterimi**  
  
```cpp  
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
  
 Değerleri ve platform çağrı çağrılarına yapılan başvuruları mareşallemek için kullanılan aynı kurallar, COM arabirimleri aracılığıyla gezinirken kullanılır. Örneğin, `Point` değer türünün bir örneği .NET Framework'den COM'a geçirildiğinde, değere göre `Point` geçirilir. `Point` Değer türü başvuru yla geçirilirse, `Point` a işaretçisi yığına geçirilir. Interop mareşal her iki yönde de daha yüksek yönlendirme **(Nokta)** \* \*düzeylerini desteklemez.  
  
> [!NOTE]
> <xref:System.Runtime.InteropServices.LayoutKind> Dışa aktarılan tür kitaplığı açık bir düzeni ifade edemediğinden, numaralandırma değeri **Explicit** olarak ayarlanmış yapılar COM interop'ta kullanılamaz.  
  
### <a name="system-value-types"></a>Sistem Değer Türleri  
 Ad <xref:System> alanı, çalışma zamanı ilkel türlerinin kutulanmış biçimini temsil eden birkaç değer türüne sahiptir. Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısı **ELEMENT_TYPE_I4**kutulu biçimini temsil eder. Bu türleri, diğer biçimlendirilmiş türler gibi yapı olarak sıralamayerine, kutuladıkları ilkel türlerle aynı şekilde sıralarsınız. **System.Int32** bu nedenle ELEMENT_TYPE_I4 **yerine** tip **uzun**tek bir üyesi içeren bir yapı olarak marshaled olduğunu. Aşağıdaki tablo, **Sistem** ad alanında ilkel türlerin kutulu gösterimleri olan değer türlerinin bir listesini içerir.  
  
|Sistem değer türü|Eleman türü|  
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
  
 **Sistem** ad alanındaki diğer bazı değer türleri farklı şekilde işlenir. Yönetilmeyen kod zaten bu tür için iyi kurulmuş biçimleri olduğundan, mareşal bunları mareşaliçin özel kurallar vardır. Aşağıdaki **tabloda, Sistem** ad alanında özel değer türlerinin yanı sıra, yürütülemeyen türler listelenir.  
  
|Sistem değer türü|IDL türü|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**Tarih**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**On -da -lık**|  
|<xref:System.Guid?displayProperty=nameWithType>|**Guıd**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**Ole_color**|  
  
 Aşağıdaki kod, Stdole2 türü kitaplığında yönetilmeyen **DATE**, **GUID**, **DECIMAL**ve **OLE_COLOR** türlerinin tanımını gösterir.  
  
#### <a name="type-library-representation"></a>Tür kitaplığı gösterimi  
  
```cpp  
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
  
 Aşağıdaki kod, yönetilen `IValueTypes` arabirimdeki karşılık gelen tanımları gösterir.  
  
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
  
```cpp  
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
- [Diziler için Varsayılan Sıralama](default-marshaling-for-arrays.md)
- [Nesneler için Varsayılan Hazırlama](default-marshaling-for-objects.md)
- [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)
