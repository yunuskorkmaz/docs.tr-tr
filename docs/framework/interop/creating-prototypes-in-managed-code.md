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
ms.openlocfilehash: b305158ac87f01044bae5455cea07ca3b3a2e491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-prototypes-in-managed-code"></a>Yönetilen Kodda Prototipler Oluşturma
Bu konu, yönetilmeyen işlevlere erişim açıklar ve yönetilen kod yöntemi tanımında açıklama birkaç öznitelik alanları tanıtır. Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](marshaling-data-with-platform-invoke.md).  
  
 Yönetilen koddan yönetilmeyen DLL işlev erişebilmeniz için önce işlevin adını ve bunu aktarır DLL adını bilmeniz gerekir. Bu bilgilerle DLL'de uygulanır, yönetilmeyen bir işleve yönetilen tanımı yazmaya başlayabilirsiniz. Ayrıca, şeklini ayarlayabilirsiniz bu platform çağırma işlev oluşturur ve veri işlevi gelen ve giden sıralar.  
  
> [!NOTE]
>  Bir dize tahsis Win32 API işlevleri dize gibi bir yöntem kullanarak boşaltmak etkinleştirme `LocalFree`. Platform çağırma gibi parametreleri farklı şekilde ele alır. Çağrıları için platform çağırma, parametre olun bir `IntPtr` türü yerine bir `String` türü. Tarafından sağlanan yöntemleri kullanın <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> türü el ile bir dizeye dönüştürmek ve el ile boş sınıfı.  
  
## <a name="declaration-basics"></a>Bildirim temelleri  
 Aşağıdaki örneklerde görüldüğü gibi yönetilen tanımları yönetilmeyen işlevleri için dile bağlı. Daha eksiksiz kod örnekleri için bkz: [Platform çağırma örnekleri](platform-invoke-examples.md).  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 Uygulanacak <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> alanları bir [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] bildirimi kullanmalıdır <xref:System.Runtime.InteropServices.DllImportAttribute> yerine özniteliği `Declare` deyimi.  
  
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
  
## <a name="adjusting-the-definition"></a>Tanım ayarlama  
 Bunları açıkça veya değil ayarlanmış olup olmadığını özniteliği yönetilen kod davranışını tanımlama İşte alanlardır. Platform çağırma bir derlemenin meta verilerde mevcut çeşitli alanlarını Ayarla varsayılan değerlere göre çalışır. Bir veya daha fazla alan değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz. Çoğu durumda, kullandığınız <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için.  
  
 Aşağıdaki tabloda tamamını çağırmada platformuna ilgilidir alanları özniteliği listeler. Her bir alan tablo, varsayılan değer ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanları kullanma hakkında bilgi için bir bağlantı içerir.  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Etkinleştirir veya en uygun eşlemeyi devre dışı bırakır.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Yöntem bağımsız değişkenleri geçirme kullanılacak çağırma kuralı belirtir. Varsayılan değer `WinAPI`, hangi karşılık gelen `__stdcall` Intel tabanlı 32-bit platformu için.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Denetimleri ad bozma ve bağımsız değişkenleri dize şekilde işleve sıralanmalıdır. Varsayılan, `CharSet.Ansi` değeridir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Çağrılacak DLL giriş noktası belirtir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Bir giriş noktası için karakter kümesi karşılık gelecek şekilde değiştirilmiş olup olmadığını denetler. Varsayılan değer programlama dili olarak değişir.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Yönetilen yöntem imzası HRESULT döndürür ve dönüş değeri için [out, retval] ek bağımsız değişken olan yönetilmeyen bir imza içine dönüştürülmüş olup olmadığını denetler.<br /><br /> Varsayılan değer `true` (imza değil dönüştürülmesi).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Kullanılacak çağıran etkinleştirir `Marshal.GetLastWin32Error` yöntemi yürütülürken bir hata oluştu olup olmadığını belirlemek için API işlevi. Visual Basic'te varsayılandır `true`; C# ve C++, varsayılan `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Denetimleri için ANSI dönüştürülür eşlenemez bir Unicode karakter üzerinde bir özel durum atma "?" karakter.|  
  
 Ayrıntılı başvuru bilgileri için bkz: <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Platform çağırma güvenlik konuları  
 `Assert`, `Deny`, Ve `PermitOnly` üyeleri <xref:System.Security.Permissions.SecurityAction> numaralandırma denir *ilerlemesi değiştiricileri yığın*. Bildirimler ve COM arabirimi tanım dili (IDL) deyimleri platform bildirim temelli özniteliklerinde çağırma olarak kullanılıyorsa, bu üyeler göz ardı edilir.  
  
### <a name="platform-invoke-examples"></a>Platform Çağırma Örnekleri  
 Platform çağırma örnekleri bu bölümde göstermeye kullanımını `RegistryPermission` yığın ilerlemesi değiştiricileri özniteliğiyle.  
  
 Aşağıdaki kod örneğinde, <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, ve `PermitOnly` değiştiricileri yok sayılır.  
  
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
  
 Ancak, `Demand` aşağıdaki örnekte değiştiricisi tarafından kabul edilir.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler iş doğru platform (sarmalayan) içeren bir sınıf girdiyseniz çağrısı başlatılacak.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> değiştiriciler platform çağıran üzerinde nereye yerleştirileceğini doğru bir senaryoda iç içe geçmiş iş ayrıca çağrısı başlatılacak:  
  
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
 Bu bölümdeki COM birlikte çalışma örnekler kullanımını göstermek `RegistryPermission` yığın ilerlemesi değiştiricileri özniteliğiyle.  
  
 Aşağıdaki COM birlikte çalışma arabirimi bildirimlerini Yoksay `Assert`, `Deny`, ve `PermitOnly` benzer şekilde platform değiştiriciler çağırma önceki bölümdeki örnekleri.  
  
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
  
 Ayrıca, `Demand` aşağıdaki örnekte gösterildiği gibi değiştiricisi COM birlikte çalışma arabirimi bildirimi senaryolarda değil kabul.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
 [Giriş Noktası Belirtme](specifying-an-entry-point.md)  
 [Karakter Kümesi Belirtme](specifying-a-character-set.md)  
 [Platform Çağırma Örnekleri](platform-invoke-examples.md)  
 [Platform çağırma güvenlik konuları](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))  
 [DLL'lerde İşlevleri Tanımlama](identifying-functions-in-dlls.md)  
 [DLL İşlevleri için bir Sınıf Oluşturma](creating-a-class-to-hold-dll-functions.md)  
 [DLL İşlevini Çağırma](calling-a-dll-function.md)
