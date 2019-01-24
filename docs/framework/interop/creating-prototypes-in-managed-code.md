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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae4dd9adbdad313afa53721e83d7b7d5212df91e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564298"
---
# <a name="creating-prototypes-in-managed-code"></a>Yönetilen Kodda Prototipler Oluşturma
Bu konu, yönetilmeyen işlevleri nasıl açıklar ve yönetilen kod yöntem tanımında açıklama birkaç öznitelik alanları tanıtır. Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](marshaling-data-with-platform-invoke.md).  
  
 Yönetilen koddan yönetilmeyen bir DLL işlevini erişmeden önce işlevin adını ve bunu aktarır DLL adını bilmeniz gerekir. Bu bilgileri kullanarak yönetilen bir DLL içinde uygulanır, yönetilmeyen bir işlev tanımı yazmaya başlayabilirsiniz. Ayrıca, biçimini ayarlayabilirsiniz. Bu platform çağırma işlev oluşturur ve işlev veri sürekliliğe devreder.  
  
> [!NOTE]
>  Bir dize tahsis Win32 API işlevleri gibi bir yöntem kullanarak dize ücretsiz etkinleştir `LocalFree`. Platform çağırma tür parametreleri farklı işler. Çağrıları için platform çağırma, parametre olun bir `IntPtr` türü yerine bir `String` türü. Tarafından sağlanan yöntemleri kullanın <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> türü el ile bir dizeye Dönüştür ve el ile ücretsiz sınıfı.  
  
## <a name="declaration-basics"></a>Bildirim temelleri  
 Aşağıdaki örneklerde görüldüğü gibi yönetilen tanımları yönetilmeyen işlevlerle dile bağlı. Tam kod örnekleri için bkz: [Platform çağırma örnekleri](platform-invoke-examples.md).  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 Uygulanacak <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> alanlarını bir [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] bildirimi kullanmalıdır <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği yerine `Declare` deyimi.  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a>Tanım'ı ayarlama  
 Bunları açıkça ayarlanıp olsun, öznitelik alanları yönetilen kodun davranışını tanımlayan İşte. Platform çağırma bir derlemenin meta verilerde mevcut çeşitli alanları ayarlamak varsayılan değerlere göre çalışır. Bir veya daha fazla alan değerleri ayarlayarak bu varsayılan davranışı değiştirebilirsiniz. Çoğu durumda, kullandığınız <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için.  
  
 Aşağıdaki tabloda, tam bir set çağırmada platforma ait alanları özniteliğinin listeler. Tablo, her alan için varsayılan değer ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanları kullanmak hakkında bilgi için bir bağlantı içerir.  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Etkinleştirir veya en iyi uyan eşlemeyi devre dışı bırakır.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Yöntem bağımsız değişkenleri geçirirken kullanmak için çağırma kuralını belirtir. Varsayılan değer `WinAPI`, karşılık gelen `__stdcall` 32-bit Intel tabanlı platformlar için.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Denetimleri ad değiştirmeyi ve bağımsız değişkenleri dize şekilde işleve sıralanmalıdır. Varsayılan, `CharSet.Ansi` değeridir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Çağrılacak DLL giriş noktası belirtir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Bir giriş noktası karakter kümesine karşılık gelen değişiklik olup olmadığını denetler. Varsayılan değer programlama dili olarak değişiklik gösterir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Yönetilen yöntem imzası bir HRESULT döndürür ve döndürülen değer [out, retval] ek bağımsız değişken olan yönetilmeyen bir imza içine dönüştürülür olup olmadığını denetler.<br /><br /> Varsayılan değer `true` (imza değil dönüştürülmesi).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Kullanılacak çağıran sağlar `Marshal.GetLastWin32Error` metodu yürütülürken bir hata oluştu olup olmadığını belirlemek için API işlevi. Visual Basic'te varsayılandır `true`; C# ve C++ varsayılan `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Denetimleri için ANSI dönüştürülür eşlenemez bir Unicode karakter üzerinde bir özel durum atma "?" karakter.|  
  
 Ayrıntılı başvuru bilgileri için bkz. <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Platform çağırmayla ilgili güvenlik konuları  
 `Assert`, `Deny`, Ve `PermitOnly` üyeleri <xref:System.Security.Permissions.SecurityAction> sabit listesi denir *yığın ilerlemesi değiştiriciler*. Bildirim temelli öznitelikleri platformunda bildirimleri ve COM arabirimi tanım dili (IDL) ifadeleri çağırma kullanılıyorsa, bu üyeler göz ardı edilir.  
  
### <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri  
 Platform çağırma örnekleri bu bölümde kullanımını gösteren `RegistryPermission` yığın ilerlemesi değiştiricileri ile özniteliği.  
  
 Aşağıdaki kod örneğinde, <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, ve `PermitOnly` değiştiricileri yoksayılır.  
  
```  
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
  
 Ancak, `Demand` değiştiricisi aşağıdaki örnekte kabul edilir.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler çalışma doğru Platformu (sarar) içeren bir sınıf üzerinde yerleştirdiyseniz çağrısı başlatılacak.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler doğru platformun çağrı üzerinde nereye yerleştirileceğini iç içe geçmiş senaryosunda ayrıca iş çağrısı başlatılacak:  
  
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
  
#### <a name="com-interop-examples"></a>COM birlikte çalışma örnekleri  
 Bu bölümdeki COM birlikte çalışma örnekleri kullanımını gösteren `RegistryPermission` yığın ilerlemesi değiştiricileri ile özniteliği.  
  
 Aşağıdaki COM birlikte çalışma arabirimi bildirimleri Yoksay `Assert`, `Deny`, ve `PermitOnly` değiştiriciler, benzer şekilde platform çağırma örnekleri önceki bölümde.  
  
```  
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
  
 Ayrıca, `Demand` aşağıdaki örnekte gösterildiği gibi değiştirici COM birlikte çalışma arabirimi bildirimi senaryolarda değil kabul.  
  
```  
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
- [Platform çağırmayla ilgili güvenlik konuları](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))
- [DLL'lerde İşlevleri Tanımlama](identifying-functions-in-dlls.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](creating-a-class-to-hold-dll-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
