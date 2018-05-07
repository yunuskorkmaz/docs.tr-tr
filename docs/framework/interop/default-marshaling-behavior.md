---
title: Varsayılan Hazırlama Davranışı
ms.date: 03/30/2017
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
ms.openlocfilehash: 7ed306098852e93d43a4055fd1d9b8cf97a01766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="default-marshaling-behavior"></a>Varsayılan Hazırlama Davranışı
Birlikte çalışma hazırlama kurallarında yönetilen ve yönetilmeyen bellek arasında geçerken yöntem parametreleri ile ilişkili verileri nasıl davranacağını bu dikte çalışır. Bu yerleşik kurallar bir Aranan kendisine geçirilen verileri değiştirebilir ve bu değişiklikleri çağırana dönün ve altında Sıralayıcı koşulda performans iyileştirmelerini sağlar hazırlama gibi etkinlikler veri türü dönüşümleri olarak denetler.  
  
 Bu bölüm, hizmet hazırlama birlikte çalışabilirliği varsayılan davranış özelliklerini tanımlar. Diziler, Boolean türleri, karakter türleri, temsilciler, sınıflar, nesneler, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgi sunar.  
  
> [!NOTE]
>  Genel türlerin hazırlama desteklenmiyor. Daha fazla bilgi için [birlikte kullanarak genel türler](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Bellek yönetimi ile birlikte çalışma Sıralayıcı  
 Birlikte çalışma sıralayıcı tarafından yönetilmeyen kod ayrılan belleği boşaltmak her zaman çalışır. Bu davranış COM bellek yönetimi kurallarıyla uyumlu, ancak yerel C++ yöneten kurallarından farklıdır.  
  
 Karışıklığı önlemek için yerel C++ davranışı (hiçbir bellek boşaltma) öngörüyorsanız çıkabilir zaman platformu kullanılarak çağırma, hangi işaretçileri için bellek otomatik olarak boşaltır. Örneğin, C++ DLL'den aşağıdaki yönetilmeyen yöntemi çağırma otomatik olarak diğer bellek boş değil.  
  
### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Bununla birlikte, her bir platform çağırma olarak prototip yöntemi tanımlayın, yerini **BSTR** ile yazın bir <xref:System.String> yazın ve arama `MethodOne`, ortak dil çalışma zamanı serbest girişimlerini `b` iki kez. Kullanarak hazırlama davranışı değiştirebilirsiniz <xref:System.IntPtr> türleri yerine **dize** türleri.  
  
 Çalışma zamanı her zaman kullanır **CoTaskMemFree** belleği boşaltmak için yöntem. Çalıştığınız bellek ile ayrılmamış varsa **CoTaskMemAlloc** yöntemini kullanmalıdır bir **IntPtr** ve uygun yöntem kullanılarak el ile bellek boş. Otomatik bellek boşaltma burada bellek hiçbir zaman serbest durumlarda, bu tür benzer şekilde, önleyebilirsiniz olarak kullanırken **GetCommandLine** çekirdek bellek için bir işaretçi döndürür Kernel32.dll işlevinden. El ile bellek boşaltma hakkında daha fazla bilgi için bkz [arabellekleri örnek](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Varsayılan sınıflar için hazırlama  
 Sınıflar yalnızca COM birlikte çalışma tarafından sıralanabilir ve arabirimleri olarak her zaman hazırlanırlar. Bazı durumlarda sınıfı sıralama için kullanılan arabirim sınıf arabirimi olarak bilinir. Tercih ettiğiniz bir arabirim ile sınıf arabirimi geçersiz kılma hakkında daha fazla bilgi için bkz: [sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>COM sınıflarına geçirme  
 Yönetilen bir sınıfın COM geçirildiğinde, birlikte çalışabilirlik Sıralayıcı otomatik olarak bir COM proxy ile sınıfı sarmalar ve COM yöntem çağrısı proxy'sine tarafından üretilen sınıf arabirimi geçirir. Proxy sınıfı arabirimde tüm çağrıları yönetilen nesneye sonra atar. Proxy sınıfı tarafından açıkça uygulanmadı diğer arabirimleri de sunar. Proxy otomatik olarak arabirimlerini gibi uygular **IUnknown** ve **IDispatch** sınıfı adına.  
  
### <a name="passing-classes-to-net-code"></a>.NET kodu için geçirme sınıfları  
 Coclass'ları genellikle COM yöntemi bağımsız değişken olarak kullanılan değil Bunun yerine, varsayılan arabirimi genellikle yerine coclass'ı geçirilir.  
  
 Arabirim yönetilen koda geçirildiğinde, birlikte çalışabilirlik Sıralayıcı uygun sarmalayıcı arabirimiyle kaydırma ve yönetilen yöntemi sarmalayıcı geçirme sorumludur. Kullanmak için hangi sarmalayıcı zor olabilir belirleme. Her bir COM nesnesinin örneği tek ve benzersiz bir sarmalayıcı nesne uygulayan kaç arabirimleri olsun sahiptir. Örneğin, beş farklı arabirimlerini uygular tek bir COM nesnesi yalnızca bir sarmalayıcı sahiptir. Aynı sarmalayıcı tüm beş arabirimleri kullanıma sunar. COM nesnesi iki örneğini oluşturduysanız, sarmalayıcısı iki örneği oluşturulur.  
  
 Sarmalayıcı yaşam süresi boyunca aynı türde korumak, nesne tarafından kullanıma sunulan bir arabirim Sıralayıcı geçirilen ilk kez doğru sarmalayıcı birlikte çalışma Sıralayıcı tanımlamanız gerekir. Sıralayıcı, bir nesne uygulayan arabirimleri at bakarak nesne tanımlar.  
  
 Örneğin, Sıralayıcı sınıfı sarmalayıcı yönetilen koda geçildi arabirimi sarmalamak için kullanılacağını belirler. Arabirimi Sıralayıcı ilk geçirildiğinde Sıralayıcı arabirimi bilinen bir nesneden gelen olup olmadığını denetler. Bu onay iki durumlarda gerçekleşir:  
  
-   Bir arabirim COM başka bir yerde geçildi başka bir yönetilen nesne tarafından uygulanır. Sıralayıcı yönetilen nesneler tarafından sergilenen arabirimlerle kolayca belirleyebilir ve uygulamasını sağlar Yönetilen Nesne arabirimiyle eşleşecek şekilde edebilir. Yönetilen Nesne sonra yönteme geçirilen ve hiçbir sarmalayıcı gereklidir.  
  
-   Zaten sarmalanmış bir nesne arabirimi uygulama. Bu durumda olup olmadığını belirlemek için nesne için sıralayıcı sorgular kendi **IUnknown** arabirim ve diğer nesnelerin zaten Sarmalanan arabirimlerine döndürülen arabirimi karşılaştırır. Arabirim, başka bir sarmalayıcı aynı olduğunda, nesneleri aynı kimliğe sahip ve mevcut sarmalayıcı yönteme geçirilen.  
  
 Arabirim bilinen bir nesneden değilse, Sıralayıcı şunları yapar:  
  
1.  Nesne için sıralayıcı sorgular **IProvideClassInfo2** arabirimi. Sağlanırsa, döndürülen CLSID Sıralayıcı kullanan **IProvideClassInfo2.GetGUID** arabirim sağlayan coclass'ı tanımlamak için. Derleme önceden kaydedilmişse CLSID ile kayıt defterinden sarmalayıcı Sıralayıcı bulabilirsiniz.  
  
2.  Arabirim için sıralayıcı sorgular **IProvideClassInfo'yu** arabirimi. Sağlanan, Sıralayıcı kullanıyorsa **ITypeInfo** döndürülen **IProvideClassInfo.GetClassinfo** arabirimi gösterme sınıfı CLSID belirlemek için. Sıralayıcı CLSID sarmalayıcı için meta verileri bulmak için kullanabilirsiniz.  
  
3.  Sıralayıcı hala sınıfı tanımlayamıyor, bir genel sarmalayıcı sınıfı adlı arabirimi sarmalar **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Varsayılan temsilcileri sıralama  
 Yönetilen bir temsilci COM arabirimi veya arama mekanizmasını temel bir işlev işaretçisi olarak sıralanmış olduğundan:  
  
-   İçin platform çağırma, bir temsilci varsayılan olarak bir yönetilmeyen işlev işaretçisi sıralanmış.  
  
-   COM birlikte çalışma için bir temsilci türü bir COM arabirimi sıralanmış **_Delegate** varsayılan olarak. **_Delegate** arabirimi Mscorlib.tlb tip Kitaplığı'nda tanımlanan ve içeren <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> temsilci başvuran yöntemini çağırmak sağlar yöntemi.  
  
 Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçeneklerini gösterir. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri sıralama temsil eder.  
  
|Numaralandırma türü|Yönetilmeyen biçimi açıklaması|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Bir yönetilmeyen işlev işaretçisi.|  
|**UnmanagedType.Interface**|Bir arabirim türü **_Delegate**, Mscorlib.tlb içinde tanımlanan.|  
  
 Aşağıdaki kod örneği, göz önünde bulundurun yöntemlerinin `DelegateTestInterface` bir COM tür kitaplığı dışarı aktarılır. Yalnızca temsilci uyarısı işaretlenmiş **ref** (veya **ByRef**) anahtar sözcüğü olarak In/Out parametreleri geçirilir.  
  
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
  
 Yalnızca başka bir yönetilmeyen işlev işaretçisi başvuru yapıldı gibi bir işlev işaretçisi, başvuru yapıldı.  
  
> [!NOTE]
>  Yönetilmeyen kod tarafından tutulan yönetilen bir temsilci için işlev işaretçisi başvuru, yönetilen bir nesne üzerinde çöp toplama gerçekleştirme ortak dil çalışma zamanı engellemez.  
  
 Örneğin, aşağıdaki kodu yanlış olduğundan referansı `cb` geçirilen nesne `SetChangeHandler` yöntemi, tutmak değil `cb` ömrünü dışında tutma `Test` yöntemi. Bir kez `cb` nesne çöp toplama, işlev işaretçisi geçirilen `SetChangeHandler` artık geçerli değil.  
  
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
  
 Beklenmeyen atık toplama için dengelemek için arayan emin olmanız gerekir `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesne Canlı tutulur. İsteğe bağlı olarak, yönetilen kod işlev işaretçisi artık, aşağıdaki örnekte gösterildiği gibi gerekli olduğunda bildir yönetilmeyen kod olabilir.  
  
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
  
## <a name="default-marshaling-for-value-types"></a>Varsayılan değer türleri için hazırlama  
 Tamsayı ve kayan nokta sayıları gibi çoğu değer türleri [blittable](blittable-and-non-blittable-types.md) ve hazırlama gerektirmez. Diğer [blittable olmayan](blittable-and-non-blittable-types.md) türleri farklı Beyanları yönetilen ve yönetilmeyen bellekte ve hazırlama gerektirir. Hala diğer türleri arasında birlikte çalışabilirlik sınır açık biçimlendirme gerektirir.  
  
 Bu konuda biçimlendirilmiş değer türleri üzerinde izleme bilgileri sağlar:  
  
-   [Değer türleri platformunda kullanılan çağırma](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [COM birlikte çalışma içinde kullanılan değer türleri](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 Biçimlendirilmiş türlerini açıklayan ek olarak, bu konu tanımlar [sistem değer türleri](#cpcondefaultmarshalingforvaluetypesanchor1) olağan dışı hazırlama davranışı sahiptir.  
  
 Açıkça üyeleri bellekte düzenini denetimleri bilgi içeren bir karmaşık türü bir biçimlendirilmiş türüdür. Üye düzen bilgilerini kullanarak sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği. Düzeni aşağıdakilerden biri olabilir <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değerlerinin:  
  
-   **LayoutKind.Automatic**  
  
     Ortak dil çalışma zamanı türü verimliliği için üyeleri yeniden sıralamak boş olduğunu gösterir. Ancak, bir değer türü yönetilmeyen koda geçirildiğinde üyeleri düzenini tahmin edilebilir. Böyle bir yapı otomatik olarak sıralama girişimi bir özel durum neden olur.  
  
-   **LayoutKind.Sequential**  
  
     Tür üyeleri yönetilen tür tanımında göründükleri sırada yönetilmeyen bellekte düzenlendiği gerektiğini gösterir.  
  
-   **LayoutKind.Explicit**  
  
     Üyeleri göre düzenlenmiştir gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> her alanıyla sağlanan.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a>Değer türleri platformunda kullanılan çağırma  
 Aşağıdaki örnekte `Point` ve `Rect` türleri düzen bilgilerini üye sağlamak kullanarak **StructLayoutAttribute**.  
  
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
  
 Yönetilmeyen kod için sıralanmış, bu biçimlendirilmiş türleri C tarzı yapıları olarak hazırlanırlar. Bu yapı bağımsız değişkenlere sahiptir bir yönetilmeyen API çağırma için kolay bir yol sağlar. Örneğin, `POINT` ve `RECT` yapıları için Microsoft Win32 API geçirilebilir **PtInRect** gibi işlev:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Yapıları geçirebilirsiniz aşağıdaki platform kullanarak çağırma tanımı:  
  
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
  
 `Rect` Değer türü gerekir bayraklarıdır başvuru tarafından yönetilmeyen API için bir işaretçi bekleniyor çünkü bir `RECT` işleve geçirilecek. `Point` Değer türü yönetilmeyen API beklediği değeri tarafından geçirilen `POINT` yığında geçirilecek. Bu fark çok önemlidir. Başvuruları yönetilmeyen koda işaretçi olarak geçirilir. Değerler yönetilmeyen koda yığında geçirilir.  
  
> [!NOTE]
>  Biçimlendirilmiş bir türü yapısı sıralanmış, yalnızca alanları türü içinde erişilebilir. Yöntemler, özellikler veya olayların türündeyse, yönetilmeyen koddan erişilemez.  
  
 Üye düzeni sabit koşuluyla sınıfları ayrıca yönetilmeyen koda C tarzı yapıları olarak sıralanabilir. Bir sınıf için üye düzen bilgilerini de ile sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği. Değer türleri ile arasındaki temel fark düzeni sabit ve sabit düzeni sınıflarıyla, yönetilmeyen koda sıralanmış yoludur. Değer türleri (yığında) değeriyle geçirilir ve sonuç olarak türün üyeleri Aranan tarafından yapılan değişiklikler çağıran tarafından görülmez. Başvuru türleri (türüne bir başvuru yığında geçirilen) başvuruya göre geçirilir; Sonuç olarak, bir tür blittable türü üyelerine Aranan tarafından yapılan tüm değişiklikler çağıran tarafından görülür.  
  
> [!NOTE]
>  Bir başvuru türü kopyalanamaz türler üyeleri varsa dönüştürme iki kez gerekli değildir: ne zaman bir bağımsız değişken geçirilir yönetilmeyen yan ve ikinci ilk kez zaman çağrısından döndürülen. Aranan tarafından yapılan değişiklikleri görmek arayan istiyorsa, bunu nedeniyle yükü eklenen parametreleri giriş/çıkış açıkça bir bağımsız uygulanmış olması gerekir.  
  
 Aşağıdaki örnekte, `SystemTime` sınıfı sıralı üye düzenine sahip ve Win32 API geçirilebilir **GetSystemTime** işlevi.  
  
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
  
 Dikkat `SystemTime` olduğundan bağımsız değişkeni bir başvuru bağımsız değişkeni değil yazılan `SystemTime` bir sınıf, bir değer türü. Değer türlerinin aksine, sınıflar her zaman başvuruya göre geçirilir.  
  
 Aşağıdaki kod örneği farklı bir gösterir `Point` adlı bir yöntemi olan sınıfı `SetXY`. Ardışık Düzen türüne sahip olduğundan, yönetilmeyen kod için geçirilen ve yapısı olarak sıralanmış. Ancak, `SetXY` üyesi olmayan yönetilmeyen koddan çağrılabilir rağmen başvuruya göre nesnesi geçirildi.  
  
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
### <a name="value-types-used-in-com-interop"></a>COM birlikte çalışma içinde kullanılan değer türleri  
 Biçimlendirilmiş türleri COM birlikte çalışma yöntem çağrıları için de geçirilebilir. Aslında, bir tür kitaplığı dışarı aktardığınızda değer türleri otomatik olarak yapılara dönüştürülür. Aşağıdaki örnekte gösterildiği gibi `Point` değer türü olur (typedef) adlı bir tür tanımı `Point`. Tüm başvuruları `Point` başka bir tür kitaplığı içinde değer türüne değiştirildiğini `Point` typedef.  
  
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
  
 Değerleri ve platform başvurular sıralama için kullanılan aynı kuralları çağrıları çağırma COM arabirimleri aracılığıyla sıralama sırasında kullanılır. Örneğin, bir örneği olduğunda `Point` değer türü, COM .NET Framework'teki geçirilen `Point` değeri geçirilir. Varsa `Point` değer türü başvurusu, bir işaretçi olarak geçirilir bir `Point` yığında geçirilir. Birlikte çalışma Sıralayıcı yöneltme daha yüksek düzeyde desteklemez (**noktası \* \*** ) her iki yönde.  
  
> [!NOTE]
>  Yapıları sahip <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değeri ayarlamak **Explicit** verilen tür kitaplığı açık bir düzen express yapılamıyor çünkü COM birlikte çalışma içinde kullanılamaz.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>Sistem değer türleri  
 <xref:System> Ad alanına sahip çalışma zamanı ilkel türler Kutulu biçiminde temsil eden birkaç değer türleri. Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısını temsil eden Kutulu biçiminde **ELEMENT_TYPE_I4**. Biçimlendirilmiş diğer türleri gibi bu tür yapıları olarak hazırlama yerine, bunları bunlar kutusunda ilkel türler aynı şekilde sıralama. **System.Int32** bu nedenle olarak sıralanmış **ELEMENT_TYPE_I4** yerine türü tek bir üyeyi içeren bir yapı olarak **uzun**. Aşağıdaki tabloda değer türlerinin bir listesini içeren **sistem** paketlenmiş gösterimlerini ilkel türleri olan ad alanı.  
  
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
  
 Başka bir değer türleri **sistem** ad alanı farklı bir şekilde işlenir. Yönetilmeyen kod bu tür tanınmış biçimleri zaten sahip olduğu Sıralayıcı bunları hazırlama için özel kurallar vardır. Aşağıdaki tabloda özel değer türlerini listeler **sistem** ad alanı, bunlar için hazırlanır yönetilmeyen tür yanı sıra.  
  
|Sistem değer türü|IDL türü|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**TARİH**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**ONDALIK**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Aşağıdaki kod yönetilmeyen türlerinin tanımını gösterir **tarih**, **GUID**, **ondalık**, ve **OLE_COLOR** Stdole2 türü Kitaplığı.  
  
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
  
 Aşağıdaki kod karşılık gelen tanımları yönetilen gösterir `IValueTypes` arabirimi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](blittable-and-non-blittable-types.md)  
 [Kopyalama ve Sabitleme](copying-and-pinning.md)  
 [Diziler için Varsayılan Hazırlama](default-marshaling-for-arrays.md)  
 [Nesneler için Varsayılan Hazırlama](default-marshaling-for-objects.md)  
 [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)
