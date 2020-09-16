---
title: Varsayılan Sıralama Davranışı
description: .NET ' te varsayılan sıralama davranışını öğrenin. Birlikte çalışabilirlik sıralaması ile bellek yönetimini gözden geçirin ve sınıflar, temsilciler ve değer türleri için varsayılan sıralama bölümüne bakın.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: f2a508b87d2f4a9ad92bc0f27fc44d74d8e916d3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555282"
---
# <a name="default-marshaling-behavior"></a>Varsayılan Sıralama Davranışı
Birlikte çalışabilirlik sıralaması, yöntem parametreleriyle ilişkili verilerin yönetilen ve yönetilmeyen bellek arasında geçerken nasıl davranacağını dikte eden kurallar üzerinde çalışır. Bu yerleşik kurallar, verileri veri türü dönüşümleri olarak sıralama, bir çağrılan verilerin kendisine geçirilen verileri değiştirip çağıramayacağını ve bu değişiklikleri arayana döndürmesini ve bu değişiklikleri, Sıralayıcı 'nın performans iyileştirmeleri sağladığı koşullarda değiştirmesini sağlar.  
  
 Bu bölüm, birlikte çalışma sıralama hizmetinin varsayılan davranış özelliklerini tanımlar. Dizileri, Boole türlerini, karakter türlerini, temsilcileri, sınıfları, nesneleri, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgiler sunar.  
  
> [!NOTE]
> Genel türlerin sıralaması desteklenmez. Daha fazla bilgi için bkz. [Genel türler kullanılarak birlikte çalışma](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Birlikte çalışma sıralayıcısı ile bellek yönetimi  
 Birlikte çalışma sıralayıcısı, her zaman yönetilmeyen kod tarafından ayrılan belleği serbest bırakma girişiminde bulunur. Bu davranış, COM bellek yönetimi kurallarına uyar, ancak yerel C++ ' ı yöneten kurallardan farklıdır.  
  
 Platform çağırma kullanılırken yerel C++ davranışını (bellek boşaltma yok) tahmin ediyorsanız karışıklığa neden olabilir. Bu, işaretçiler için belleği otomatik olarak boşaltır. Örneğin, bir C++ DLL 'den aşağıdaki yönetilmeyen yöntemi çağırmak herhangi bir belleği otomatik olarak serbest vermez.  
  
### <a name="unmanaged-signature"></a>Yönetilmeyen imza  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Ancak, yöntemi bir platform çağırma prototipi olarak tanımlarsanız, her **BSTR** türünü bir tür ile değiştirin <xref:System.String> ve çağırın `MethodOne` , ortak dil çalışma zamanı iki kez ücretsiz olarak çalışır `b` . Sıralama davranışını <xref:System.IntPtr> **dize** türleri yerine türler kullanarak değiştirebilirsiniz.  
  
 Çalışma zamanı, belleği boşaltmak için her zaman **CoTaskMemFree** yöntemini kullanır. Çalıştığınız bellek **CoTaskMemAlloc** yöntemiyle ayrıldıysa, bir **IntPtr** kullanmanız ve uygun yöntemi kullanarak belleği el ile boşaltmalısınız. Benzer şekilde, çekirdek belleğine bir işaretçi döndüren Kernel32.dll **GetCommandLine** işlevini kullanırken, belleğin asla boşaltılmaması gereken durumlarda otomatik bellek boşaltmasını önleyebilirsiniz. Belleği el ile boşaltma hakkında ayrıntılı bilgi için bkz. [arabellekler örneği](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Sınıflar için varsayılan sıralama  
 Sınıflar yalnızca COM birlikte çalışabilirliğine göre sıralanabilir ve her zaman arabirim olarak sıralanır. Bazı durumlarda, sınıfı sıralamak için kullanılan arabirim sınıf arabirimi olarak bilinir. Sınıf arabirimini tercih ettiğiniz bir arabirimle geçersiz kılma hakkında daha fazla bilgi için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Sınıfları COM 'a geçirme  
 Yönetilen bir sınıf COM 'a geçirildiğinde, birlikte çalışma sıralayıcısı otomatik olarak sınıfı bir COM proxy 'si ile sarmalanmış ve proxy tarafından üretilen sınıf arabirimini COM yöntem çağrısına geçirir. Ardından ara sunucu, sınıf arabirimindeki tüm çağrıları yönetilen nesneye yeniden devreder. Proxy Ayrıca, sınıfı tarafından açıkça uygulanmayan diğer arabirimleri de kullanıma sunar. Proxy, sınıf adına **IUnknown** ve **IDispatch** gibi arabirimleri otomatik olarak uygular.  
  
### <a name="passing-classes-to-net-code"></a>Sınıfları .NET koduna geçirme  
 Ortak sınıflar genellikle COM 'da Yöntem bağımsız değişkenleri olarak kullanılmaz. Bunun yerine, varsayılan bir arabirim genellikle coclass 'ın yerine geçirilir.  
  
 Bir arabirim yönetilen koda geçirildiğinde, birlikte çalışma sıralayıcısı, arabirimin doğru sarmalayıcı ile sarmalanması ve sarmalayıcı yönetilen yönteme geçirilmesinden sorumludur. Hangi sarmalayıcı kullanacağınızı belirlemek zor olabilir. Bir COM nesnesinin her örneği, nesnenin kaç arabirim uyguladığını fark etmeksizin tek ve benzersiz bir sarmalayıcı içerir. Örneğin, beş farklı arabirimi uygulayan tek bir COM nesnesi yalnızca bir sarmalayıcı içerir. Aynı sarmalayıcı beş arabirimi de kullanıma sunar. COM nesnesinin iki örneği oluşturulursa, sarmalayıcının iki örneği oluşturulur.  
  
 Sarmalayıcının ömrü boyunca aynı türü koruabilmesi için, nesne tarafından kullanıma sunulan bir arabirim Sıralayıcı üzerinden geçirildiğinde, birlikte çalışma sıralayıcısı doğru sarmalayıcı tanımlamalıdır. Sıralayıcı nesnenin uyguladığı arayüzlerden birine bakarak nesneyi tanımlar.  
  
 Örneğin Sıralayıcı, sınıf sarmalayıcının yönetilen koda geçirilen arabirimi sarmalamak için kullanılması gerektiğini belirler. Arabirim Sıralayıcı tarafından ilk kez geçirildiğinde Sıralayıcı, arabirimin bilinen bir nesneden geliyor olup olmadığını denetler. Bu denetim iki durumda gerçekleşir:  
  
- Bir arabirim, COM 'a başka bir yerde geçirilmiş başka bir yönetilen nesne tarafından uygulanıyor. Sıralayıcı yönetilen nesneler tarafından sunulan arabirimleri kolayca tanımlayabilir ve arabirimi, uygulamayı sağlayan yönetilen nesneyle eşleştirebilir. Yönetilen nesne daha sonra yönteme geçirilir ve sarmalayıcı gerekmez.  
  
- Zaten sarmalanmış bir nesne arabirimini uygulama. Bunun durum olup olmadığını anlamak için sıralayıcı, nesneyi **IUnknown** arabirimine sorgular ve döndürülen arabirimi zaten sarmalanmış diğer nesnelerin arabirimlerine karşılaştırır. Arabirim, başka bir sarmalayıcı ile aynıysa, nesneler aynı kimliğe sahip olur ve varolan sarmalayıcı yöntemine geçirilir.  
  
 Bir arabirim bilinen bir nesneden değilse Sıralayıcı şunları yapar:  
  
1. Sıralayıcı, **IProvideClassInfo2** arabirimi için nesneyi sorgular. Sağlanmışsa, Sıralayıcı, arabirimi sağlayan coclass 'ı tanımlamak için **IProvideClassInfo2. GetGUID** ÖĞESINDEN döndürülen CLSID 'yi kullanır. CLSID ile, derleme daha önce kaydedilmişse, Sıralayıcı kayıt defterinden sarmalayıcı bulabilir.  
  
2. Sıralayıcı, **IProvideClassInfo** arabirimi için arabirimi sorgular. Belirtilmişse, Sıralayıcı, arabirimi kullanıma sunmadan sınıfın CLSID 'sini belirlemede **IProvideClassInfo. GetClassInfo** öğesinden döndürülen **ITypeInfo bilgisini** kullanır. Sıralayıcı, sarmalayıcının meta verilerini bulmak için CLSID 'yi kullanabilir.  
  
3. Sıralayıcı hala sınıfı tanımlayamıyor, arabirimi **System. __ComObject**adlı bir genel sarmalayıcı sınıfı ile sarmalanmış hale gelir.  
  
## <a name="default-marshaling-for-delegates"></a>Temsilciler için varsayılan sıralama  
 Yönetilen bir temsilci, çağırma mekanizmasına bağlı olarak bir COM arabirimi veya bir işlev işaretçisi olarak sıralanır:  
  
- Platform çağırma için bir temsilci varsayılan olarak yönetilmeyen bir işlev işaretçisi olarak sıralanır.  
  
- COM birlikte çalışması için bir temsilci, varsayılan olarak **_Delegate** türünde bir com arabirimi olarak sıralanır. **_Delegate** arabirimi mscorlib. tlb tür kitaplığında tanımlanmıştır ve <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> temsilcinin başvurduğu yöntemi çağırabilmenizi sağlayan yöntemini içerir.  
  
 Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçenekleri gösterilmektedir. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> temsilcileri sıralamak için birkaç numaralandırma değeri sağlar.  
  
|Sabit listesi türü|Yönetilmeyen biçimin açıklaması|  
|----------------------|-------------------------------------|  
|**UnmanagedType. FunctionPtr**|Yönetilmeyen bir işlev işaretçisi.|  
|**UnmanagedType. Interface**|Mscorlib. tlb ' de tanımlandığı şekilde **_Delegate**türünde bir arabirim.|  
  
 Yöntemlerinin `DelegateTestInterface` BIR com tür kitaplığına aktarılması için aşağıdaki örnek kodu göz önünde bulundurun. Yalnızca **ref** (veya **ByRef**) anahtar sözcüğüyle Işaretlenen temsilcilerin ın/out parametrelerine geçtiğini unutmayın.  
  
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
  
### <a name="type-library-representation"></a>Tür kitaplığı temsili  
  
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
  
 Bir işlev işaretçisine, diğer yönetilmeyen işlev işaretçilerine başvurulanlar gibi başvurulmalıdır.  

Bu örnekte, iki temsilci olarak sıralandığınızda <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> , sonuç bir `int` ve bir işaretçisidir `int` . Temsilci türleri sıralanmakta olduğundan, `int` `void*` Bu, bellekteki temsilcinin adresi olan void () için bir işaretçi temsil eder. Diğer bir deyişle, bu sonuç 32 bitlik Windows sistemlerine özgüdür, bu nedenle `int` işlev işaretçisinin boyutunu temsil eder.

> [!NOTE]
> Yönetilmeyen kod tarafından tutulan yönetilen bir temsilciye yönelik işlev işaretçisine yönelik bir başvuru, ortak dil çalışma zamanının yönetilen nesnede çöp toplama gerçekleştirmesini engellemez.  
  
 Örneğin, `cb` yöntemine geçirilen nesneye yapılan başvuru, `SetChangeHandler` `cb` yöntemin ömrünün ötesinde etkin olmadığından, aşağıdaki kod yanlış `Test` . `cb`Nesne çöp topladıktan sonra, geçirilen işlev işaretçisi `SetChangeHandler` artık geçerli değildir.  
  
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
  
 Beklenmedik atık toplamayı dengelemek için çağıran, `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesnenin canlı tutulduğundan emin olmalıdır. İsteğe bağlı olarak, aşağıdaki örnekte gösterildiği gibi, işlev işaretçisine artık ihtiyaç duyulmadığında, yönetilmeyen kodun yönetilen koda bildirilmesini sağlayabilirsiniz.  
  
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
 Tamsayılar ve kayan nokta numaraları gibi çoğu değer türleri [blittable](blittable-and-non-blittable-types.md) ve sıralama gerektirmez. Diğer [blittable dışı](blittable-and-non-blittable-types.md) türler yönetilen ve yönetilmeyen bellekte benzer temsiller ve sıralama gerektirir. Hala diğer türler, birlikte çalışma sınırları genelinde açık biçimlendirme gerektirir.  
  
 Bu bölüm aşağıdaki biçimli değer türleri hakkında bilgi sağlar:  
  
- [Platform çağırmada kullanılan değer türleri](#value-types-used-in-platform-invoke)  
  
- [COM birlikte çalışabilirliğine kullanılan değer türleri](#value-types-used-in-com-interop)  
  
 Bu konuda, biçimlendirilen türlerin açıklanmasına ek olarak, olağan dışı sıralama davranışına sahip [Sistem değeri türleri](#system-value-types) tanımlanmaktadır.  
  
 Biçimlendirilen bir tür, içindeki üyelerinin doğrudan, bellekteki yerleşimini açıkça denetleyen bilgiler içeren karmaşık bir türdür. Üye düzen bilgileri, özniteliği kullanılarak sağlanır <xref:System.Runtime.InteropServices.StructLayoutAttribute> . Düzen aşağıdaki <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değerlerinden biri olabilir:  
  
- **LayoutKind. Auto**  
  
     Ortak dil çalışma zamanının, verimlilik için tür üyelerini yeniden sıralamak için boş olduğunu gösterir. Ancak, bir değer türü yönetilmeyen koda geçirildiğinde, üyelerin düzeni öngörülebilir olur. Böyle bir yapıyı sıralama girişimi özel duruma otomatik olarak neden olur.  
  
- **LayoutKind. Sequential**  
  
     Türün üyelerinin yönetilmeyen bellekte, yönetilen tür tanımında göründükleri sırada düzenleneceğini gösterir...  
  
- **LayoutKind. Explicit**  
  
     Üyelerin her alanla sağlanan öğesine göre düzenlendiğini gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> .  
  
### <a name="value-types-used-in-platform-invoke"></a>Platform çağırmada kullanılan değer türleri  
 Aşağıdaki örnekte, `Point` ve `Rect` türleri **StructLayoutAttribute**kullanarak üye düzen bilgilerini sağlar.  
  
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
  
 Yönetilmeyen koda sıralandığınızda, bu biçimli türler C stili yapılar olarak sıralanır. Bu, yapı bağımsız değişkenlerine sahip yönetilmeyen bir API çağırmanın kolay bir yolunu sağlar. Örneğin, `POINT` ve `RECT` yapıları MICROSOFT Windows API **ptinrect** işlevine aşağıdaki gibi geçirilebilir:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Aşağıdaki platform çağırma tanımını kullanarak yapıları geçirebilirsiniz:  
  
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
  
 `Rect`YÖNETILMEYEN API, işleve geçirilecek bir işaretçi beklediği için değer türü başvuruya göre geçirilmelidir `RECT` . `Point`YÖNETILMEYEN API 'nin yığına geçirilmesini beklediği için değer türü değere göre geçirilir `POINT` . Bu hafif fark çok önemlidir. Başvurular yönetilmeyen koda işaretçiler olarak geçirilir. Değerler yığında yönetilmeyen koda geçirilir.  
  
> [!NOTE]
> Biçimlendirilen bir tür yapı olarak sıralanmışsa, yalnızca tür içindeki alanlara erişilebilir. Türün yöntemleri, özellikleri veya olayları varsa, bunlar yönetilmeyen koddan erişilmez.  
  
 Sınıflar, Ayrıca, sabit üye düzenine sahip olmaları şartıyla, yönetilmeyen koda C stili yapılar olarak sıralanabilir. Bir sınıf için üye düzen bilgileri de özniteliğiyle birlikte sağlanır <xref:System.Runtime.InteropServices.StructLayoutAttribute> . Sabit düzen ve sınıflar ile değer türleri arasındaki temel fark, yönetilmeyen kod için sıralandıkları yoldur. Değer türleri değeri (yığında) ile geçirilir ve sonuç olarak, aranan tarafından türün üyelerinde yapılan değişiklikler arayan tarafından görülmez. Başvuru türleri başvuruya göre geçirilir (türe bir başvuru yığına geçirilir); Sonuç olarak, aranan tarafından bir türün blittable-Type üyelerinde yapılan tüm değişiklikler arayan tarafından görülür.  
  
> [!NOTE]
> Bir başvuru türünde blittable olmayan türlerde Üyeler varsa, dönüştürme iki kez gereklidir: bir bağımsız değişkenin yönetilmeyen tarafa geçirilmesi ve çağrıdan ikinci kez döndürülmesinin ilk zamanı. Bu eklenen ek yük nedeniyle, çağıran tarafından yapılan değişiklikleri görmek istiyorsa, ın/out parametreleri açıkça bir bağımsız değişkene uygulanmalıdır.  
  
 Aşağıdaki örnekte, `SystemTime` sınıfı sıralı üye düzenine sahiptir ve WINDOWS API **GetSystemTime** işlevine geçirilebilir.  
  
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
  
 `SystemTime`Bağımsız değişkenin bir başvuru bağımsız değişkeni olarak yazılmadığından `SystemTime` , bir değer türü değil bir sınıf olduğundan emin olun. Değer türlerinin aksine, sınıflar her zaman başvuruya göre geçirilir.  
  
 Aşağıdaki kod örneği, `Point` adlı bir yöntemi olan farklı bir sınıfı gösterir `SetXY` . Türün sıralı düzeni olduğundan, yönetilmeyen koda geçirilebilir ve bir yapı olarak sıralanmış olabilir. Ancak, `SetXY` nesne başvuru ile geçirilse bile, yönetilmeyen koddan üye çağrılabilir değildir.  
  
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
  
### <a name="value-types-used-in-com-interop"></a>COM birlikte çalışabilirliğine kullanılan değer türleri  
 Biçimlendirilen türler, COM birlikte çalışma yöntemi çağrılarına de geçirilebilir. Aslında, bir tür kitaplığına aktarıldığında, değer türleri otomatik olarak yapılara dönüştürülür. Aşağıdaki örnekte gösterildiği gibi, `Point` değer türü adıyla bir tür tanımı (typedef) olur `Point` . `Point`Tür kitaplığının başka bir yerinde değer türüne yapılan tüm başvurular typedef ile değiştirilmiştir `Point` .  
  
 **Tür kitaplığı temsili**  
  
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
  
 Değerleri ve platform çağırma çağrılarına başvuruları sıralamak için kullanılan kurallar, COM arabirimleri üzerinden sıralama yapılırken kullanılır. Örneğin, `Point` değer türünün bir örneği .NET Framework com 'a geçirildiğinde, `Point` değeri tarafından geçirilir. `Point`Değer türü başvuruya göre geçirilirse, yığına bir işaretçisi `Point` geçirilir. Birlikte çalışma sıralayıcısı,**Point** \* \* iki yönde de daha yüksek yöneltme (nokta) düzeylerini desteklemez.  
  
> [!NOTE]
> <xref:System.Runtime.InteropServices.LayoutKind>Sabit listesi değeri **Açık** olarak ayarlanmış olan yapılar, içe aktarılmış tür kitaplığı açık bir düzen Ifade ettiğinden, com birlikte çalışma içinde kullanılamaz.  
  
### <a name="system-value-types"></a>Sistem değer türleri  
 <xref:System>Ad alanı, çalışma zamanı temel türlerinin paketlenmiş formunu temsil eden çeşitli değer türlerine sahiptir. Örneğin, değer türü yapısı, <xref:System.Int32?displayProperty=nameWithType> **ELEMENT_TYPE_I4**kutulanmış biçimini temsil eder. Bu türleri yapılar olarak sıralamak yerine, diğer biçimlendirilen türler olduğu gibi, bunları kendi temel türleriyle aynı şekilde sıralamanız gerekir. Bu nedenle **System. Int32** , **Long**türünde tek bir üye içeren bir yapı olarak değil **ELEMENT_TYPE_I4** olarak sıralanır. Aşağıdaki tablo, temel türlerin kutulanmış temsilleri olan **sistem** ad alanındaki değer türlerinin bir listesini içerir.  
  
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
  
 **Sistem** ad alanındaki bazı diğer değer türleri farklı şekilde işlenir. Yönetilmeyen kodun bu türler için zaten iyi belirlenmiş biçimleri olduğundan, Sıralayıcı bunları hazırlamayı sağlayacak özel kurallara sahiptir. Aşağıdaki tabloda, **sistem** ad alanındaki özel değer türlerinin yanı sıra, sıralandıkları yönetilmeyen tür listelenmektedir.  
  
|Sistem değer türü|IDL türü|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**GÜNCEL**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**KATEGORI**|  
|<xref:System.Guid?displayProperty=nameWithType>|**'INI**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Aşağıdaki kodda, Stdole2 tür kitaplığındaki yönetilmeyen türlerin **tarihi**, **GUID**, **DECIMAL**ve **OLE_COLOR** tanımı gösterilmektedir.  
  
#### <a name="type-library-representation"></a>Tür kitaplığı temsili  
  
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
  
 Aşağıdaki kod, yönetilen arabirimde karşılık gelen tanımları gösterir `IValueTypes` .  
  
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
  
#### <a name="type-library-representation"></a>Tür kitaplığı temsili  
  
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
