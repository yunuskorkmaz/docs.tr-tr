---
title: Yönetilen Kodda Prototipler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
ms.openlocfilehash: 712040c3482b51c4dafe0ee87fdda8cd848fb7fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123612"
---
# <a name="creating-prototypes-in-managed-code"></a>Yönetilen Kodda Prototipler Oluşturma
Bu konu, yönetilmeyen işlevlere nasıl erişmekte olduğunu ve yönetilen kodda Yöntem tanımına açıklama eklenen çeşitli öznitelik alanlarını tanıtır. Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
 Yönetilen koddan yönetilmeyen bir DLL işlevine erişebilmek için önce işlevin adını ve onu dışarı aktaran DLL 'nin adını bilmeniz gerekir. Bu bilgilerle, DLL 'de uygulanan yönetilmeyen bir işlev için yönetilen tanımı yazmaya başlayabilirsiniz. Ayrıca, platform çağırma işlevinin işlevi nasıl oluşturduğunu ve işlevden veri sıraladığı yöntemi ayarlayabilirsiniz.  
  
> [!NOTE]
> Bir dize ayıran Windows API işlevleri, gibi bir yöntemi kullanarak dizeyi boşaltmaya olanak sağlar `LocalFree`. Platform çağırma, bu tür parametreleri farklı işler. Platform çağırma çağrıları için parametreyi `IntPtr` `String` tür yerine bir tür yapın. Türü bir dizeye el ile dönüştürmek için <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> sınıfı tarafından sunulan yöntemleri kullanın ve el ile boşaltın.  
  
## <a name="declaration-basics"></a>Bildirim temelleri  
 Yönetilmeyen işlevlere yönetilen tanımlar, aşağıdaki örneklerde görebileceğiniz gibi dile bağımlıdır. Daha kapsamlı kod örnekleri için bkz. [Platform çağırma örnekleri](platform-invoke-examples.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute> ,,,, Veya alanlarını bir Visual Basic bildirimine uygulamak için, `Declare` ifadesini kullanarak özniteliğini kullanmanız gerekir. <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a>Tanımı ayarlama  
 Onları açıkça ayarlayıp ayarlamazsanız, öznitelik alanları yönetilen kodun davranışını tanımlayan çalışmalardır. Platform çağırma, bir derlemede meta veriler olarak var olan çeşitli alanlarda ayarlanan varsayılan değerlere göre çalışır. Bir veya daha fazla alanın değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz. Çoğu durumda, bir değer ayarlamak <xref:System.Runtime.InteropServices.DllImportAttribute> için öğesini kullanırsınız.  
  
 Aşağıdaki tablo, platform Invoke ile ilgili olan öznitelik alanlarının tamamını listeler. Her alan için tablo, varsayılan değeri ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanların nasıl kullanılacağına ilişkin bilgilere bir bağlantı içerir.  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|En uygun eşlemeyi etkinleştirilir veya devre dışı bırakır.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Yöntem bağımsız değişkenlerini geçirilerek kullanılacak çağırma kuralını belirtir. Varsayılan değer `WinAPI`, 32 bit Intel tabanlı `__stdcall` platformlar için karşılık gelir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Denetim adı değiştirmeyi ve dize bağımsız değişkenlerinin işleve sıralanması gereken yolu. Varsayılan değer: `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Çağrılacak DLL giriş noktasını belirtir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Bir giriş noktasının karakter kümesine karşılık olarak değiştirilmesi gerekip gerekmediğini denetler. Varsayılan değer programlama diline göre değişir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Yönetilen yöntem imzasının bir HRESULT döndüren yönetilmeyen imzaya dönüştürülmesi gerekip gerekmediğini ve dönüş değeri için ek bir [Out, retval] bağımsız değişkenine sahip olup olmadığını denetler.<br /><br /> Varsayılan değer `true` (imza dönüştürülmemelidir).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Çağıran, metodu yürütürken bir hata `Marshal.GetLastWin32Error` oluşup oluşmadığını anlamak için API işlevini kullanmasını sağlar. Visual Basic, varsayılan olarak `true`; C# ve C++ ' da varsayılan değer `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Bir ANSI "?" karakterine dönüştürülmüş, eşlenebilir bir Unicode karakter üzerinde özel durum üretilmesini denetler.|  
  
 Ayrıntılı başvuru bilgileri için bkz <xref:System.Runtime.InteropServices.DllImportAttribute>..  
  
## <a name="platform-invoke-security-considerations"></a>Platform çağırma güvenlik konuları  
 `Assert`, `Deny` `PermitOnly` Ve <xref:System.Security.Permissions.SecurityAction> numaralandırmanın üyeleri *Yığın ilerleme değiştiricileri*olarak adlandırılır. Bu Üyeler platform çağırma bildirimleri ve COM arabirim tanım dili (IDL) deyimlerinde bildirime dayalı öznitelikler olarak kullanılıyorsa yok sayılır.  
  
### <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri  
 Bu bölümdeki platform çağırma örnekleri, yığın yürüme değiştiricilerine sahip `RegistryPermission` özniteliğin kullanımını gösterir.  
  
 Aşağıdaki örnekte <xref:System.Security.Permissions.SecurityAction> `Assert` `Deny`,, ve `PermitOnly` değiştiricileri yok sayılır.  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 Ancak, aşağıdaki `Demand` örnekteki değiştirici kabul edilir.  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction>değiştiriciler, platform çağırma çağrısını içeren (sarmalanmış) bir sınıfa yerleştirilirse doğru çalışır.  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <xref:System.Security.Permissions.SecurityAction>değiştiriciler, platform çağırma çağrısının çağıranına yerleştirildikleri iç içe geçmiş bir senaryoda da doğru çalışır:  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a>COM birlikte çalışabilirlik örnekleri  
 Bu bölümdeki COM birlikte çalışabilirlik örnekleri, yığın yürüme değiştiricilerine `RegistryPermission` sahip özniteliğin kullanımını gösterir.  
  
 Aşağıdaki com birlikte çalışma arabirimi bildirimleri, önceki `Assert`bölümde `Deny`bulunan Platform `PermitOnly` çağırma örneklerine benzer şekilde,, ve değiştiricilerini yoksayar.  
  
```csharp
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 Ek olarak, `Demand` aşağıdaki örnekte gösterildiği gibi, değiştirici com birlikte çalışma arabirimi bildirim senaryolarında kabul edilmez.  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)
- [Giriş Noktası Belirtme](specifying-an-entry-point.md)
- [Karakter Kümesi Belirtme](specifying-a-character-set.md)
- [Platform Çağırma Örnekleri](platform-invoke-examples.md)
- [Platform çağırma güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [DLL'lerde İşlevleri Tanımlama](identifying-functions-in-dlls.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](creating-a-class-to-hold-dll-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
