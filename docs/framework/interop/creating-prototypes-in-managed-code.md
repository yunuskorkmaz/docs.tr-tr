---
title: Yönetilen Kodda Prototipler Oluşturma
description: .NET tarafından yönetilen kodda prototipler oluşturun, bu sayede yönetilmeyen işlevlere erişebilir ve yönetilen kodda Yöntem tanımına açıklama eklemek için öznitelik alanlarını kullanabilirsiniz.
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
ms.openlocfilehash: e83979e5843c52fc3a446a5b669ae8822b32ddad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555594"
---
# <a name="creating-prototypes-in-managed-code"></a>Yönetilen Kodda Prototipler Oluşturma
Bu konu, yönetilmeyen işlevlere nasıl erişmekte olduğunu ve yönetilen kodda Yöntem tanımına açıklama eklenen çeşitli öznitelik alanlarını tanıtır. Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
 Yönetilen koddan yönetilmeyen bir DLL işlevine erişebilmek için önce işlevin adını ve onu dışarı aktaran DLL 'nin adını bilmeniz gerekir. Bu bilgilerle, DLL 'de uygulanan yönetilmeyen bir işlev için yönetilen tanımı yazmaya başlayabilirsiniz. Ayrıca, platform çağırma işlevinin işlevi nasıl oluşturduğunu ve işlevden veri sıraladığı yöntemi ayarlayabilirsiniz.  
  
> [!NOTE]
> Bir dize ayıran Windows API işlevleri, gibi bir yöntemi kullanarak dizeyi boşaltmaya olanak sağlar `LocalFree` . Platform çağırma, bu tür parametreleri farklı işler. Platform çağırma çağrıları için parametreyi `IntPtr` tür yerine bir tür yapın `String` . <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>Türü bir dizeye el ile dönüştürmek için sınıfı tarafından sunulan yöntemleri kullanın ve el ile boşaltın.  
  
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
  
 ,,,,, <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> Veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> alanlarını bir Visual Basic bildirimine uygulamak için, ifadesini kullanarak özniteliğini kullanmanız gerekir <xref:System.Runtime.InteropServices.DllImportAttribute> `Declare` .  
  
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
 Onları açıkça ayarlayıp ayarlamazsanız, öznitelik alanları yönetilen kodun davranışını tanımlayan çalışmalardır. Platform çağırma, bir derlemede meta veriler olarak var olan çeşitli alanlarda ayarlanan varsayılan değerlere göre çalışır. Bir veya daha fazla alanın değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz. Çoğu durumda, <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için öğesini kullanırsınız.  
  
 Aşağıdaki tablo, platform Invoke ile ilgili olan öznitelik alanlarının tamamını listeler. Her alan için tablo, varsayılan değeri ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanların nasıl kullanılacağına ilişkin bilgilere bir bağlantı içerir.  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|En uygun eşlemeyi etkinleştirilir veya devre dışı bırakır.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Yöntem bağımsız değişkenlerini geçirilerek kullanılacak çağırma kuralını belirtir. Varsayılan değer `WinAPI` , `__stdcall` 32 bit Intel tabanlı platformlar için karşılık gelir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Denetim adı değiştirmeyi ve dize bağımsız değişkenlerinin işleve sıralanması gereken yolu. Varsayılan değer: `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Çağrılacak DLL giriş noktasını belirtir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Bir giriş noktasının karakter kümesine karşılık olarak değiştirilmesi gerekip gerekmediğini denetler. Varsayılan değer programlama diline göre değişir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Yönetilen yöntem imzasının bir HRESULT döndüren yönetilmeyen imzaya dönüştürülmesi gerekip gerekmediğini ve dönüş değeri için ek bir [Out, retval] bağımsız değişkenine sahip olup olmadığını denetler.<br /><br /> Varsayılan değer `true` (imza dönüştürülmemelidir).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Çağıran, `Marshal.GetLastWin32Error` metodu yürütürken bir hata oluşup oluşmadığını anlamak için API işlevini kullanmasını sağlar. Visual Basic ' de, varsayılan ' dir `true` ; C# ve C++ ' ta varsayılandır `false` .|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Bir ANSI "?" karakterine dönüştürülmüş, eşlenebilir bir Unicode karakter üzerinde özel durum üretilmesini denetler.|  
  
 Ayrıntılı başvuru bilgileri için bkz <xref:System.Runtime.InteropServices.DllImportAttribute> ..  
  
## <a name="platform-invoke-security-considerations"></a>Platform çağırma güvenlik konuları  
 `Assert`, `Deny` Ve `PermitOnly` <xref:System.Security.Permissions.SecurityAction> numaralandırmanın üyeleri *Yığın ilerleme değiştiricileri*olarak adlandırılır. Bu Üyeler platform çağırma bildirimleri ve COM arabirim tanım dili (IDL) deyimlerinde bildirime dayalı öznitelikler olarak kullanılıyorsa yok sayılır.  
  
### <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri  
 Bu bölümdeki platform çağırma örnekleri, `RegistryPermission` yığın yürüme değiştiricilerine sahip özniteliğin kullanımını gösterir.  
  
 Aşağıdaki örnekte,, <xref:System.Security.Permissions.SecurityAction> `Assert` `Deny` ve `PermitOnly` değiştiricileri yok sayılır.  
  
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
  
 Ancak, `Demand` Aşağıdaki örnekteki değiştirici kabul edilir.  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler, platform çağırma çağrısını içeren (sarmalanmış) bir sınıfa yerleştirilirse doğru çalışır.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler, platform çağırma çağrısının çağıranına yerleştirildikleri iç içe geçmiş bir senaryoda da doğru çalışır:  
  
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
 Bu bölümdeki COM birlikte çalışabilirlik örnekleri, `RegistryPermission` yığın yürüme değiştiricilerine sahip özniteliğin kullanımını gösterir.  
  
 Aşağıdaki COM birlikte çalışma arabirimi bildirimleri, `Assert` `Deny` `PermitOnly` önceki bölümde bulunan Platform çağırma örneklerine benzer şekilde,, ve değiştiricilerini yoksayar.  
  
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
  
 Ek olarak, `Demand` Aşağıdaki örnekte gösterildiği gibi, DEĞIŞTIRICI com birlikte çalışma arabirimi bildirim senaryolarında kabul edilmez.  
  
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
- [Platform çağırma güvenlik konuları](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [DLL'lerde İşlevleri Tanımlama](identifying-functions-in-dlls.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](creating-a-class-to-hold-dll-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
